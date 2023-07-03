# <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/screwdriver-wrench.svg" width="20" height="20"> Distributions

CloudFront delivers your content through a worldwide network of data centers called edge locations. When a user requests content that you're serving with CloudFront, the request is routed to the edge location that provides the lowest latency (time delay), so that content is delivered with the best possible performance.

- If the content is already in the edge location with the lowest latency, CloudFront delivers it immediately.

- If the content is not in that edge location, CloudFront retrieves it from an origin that you've defined—such as an Amazon S3 bucket, a MediaPackage channel, or an HTTP server (for example, a web server) that you have identified as the source for the definitive version of your content.

## Lifecycle

### Create distribution

**Distribution is created when you set up Medialive pipeline:** The CloudFront distribution is created during the process of setting up AWS Elemental MediaLive pipeline.

**Manually create and associate distribution with the pipeline:**
For a network analysis, after streaming through Medialive pipeline admin may decide to detach distribution from the AWS Medialive pipeline. For detaching distibution, you can go into Distributions page from admin section and detach the distribution. Now to associate new distribution with your pipeline, go to pipeline page and use create distribution link shown next to pipeline name to create new one.

**Auto created if no distribution is associated with the pipeline**
If you've started the pipeline from breakout stream viewer page, and your Medialive pipeline has no companion distibution associated then server will create a new distribution and associate with the pipeline. As you know setting up distribution takes more time, it is always advised to make sure distribution is already created much before you decide to stream. In above scenario, there is a `ensureDistribution()` function which takes care of creating new distribution.

```
  async ensureDistribution() {
    try {
      const channelId = this.channel.id;
      logger.trace(`ensureDistribution ${channelId}`);
      const distribution = await DistributionModel.findDistributionByChannelId(channelId);
      if (!distribution || !distribution.active) {
        logger.trace(`No Distribution exists in DB`);
        await this.createDistribution();
      } else {
        logger.trace(`Distribution [${distribution.aws_distribution_id}] exists in DB`);
        await this._ensureDistributionInAWS(distribution);
      }
    } catch (error) {
      logger.error('Error occurred: ', error);
    }
  }
```

**Configure Mediapackage Endppoint Origin**

By creating a CloudFront distribution with MediaPackage as the origin, you can take advantage of the scalability, security, and global edge network of CloudFront to efficiently deliver your video content to viewers around the world. Creating a CloudFront distribution with MediaPackage as the origin involves setting up CloudFront to use MediaPackage as the endpoint from which it fetches content.

You can see, we are configuring Mediapackage endpoint URL as orgin:

```
function buildCreateDistributionRequest(config) {
    const params = {
    DistributionConfig: {
      ...
      Enabled: true,
      Origins: {
        Items: [
          {
            DomainName: originDomainName,
            OriginPath: originPath,
            Id: originId,
            CustomOriginConfig: {
              HTTPPort: 80,
              HTTPSPort: 443,
              OriginProtocolPolicy: 'match-viewer',
            },
          },
        ],
        Quantity: 1,
      },
      CacheBehaviors: {
        ...
      }
    }
}
```

**Choosing price class**

Price Class 100 (fewer regions): We are using **Price Class 100** for our pipelines. Price Class 100 includes a subset of the edge locations available globally, focusing on major geographic areas. It offers reduced coverage compared to Price Class 200 but still provides reasonable performance for most users. This price class is a more cost-effective option if your audience is concentrated in specific regions.

You can read more about [price class here](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/PriceClass.html)

**CORS configuration**
We've defined CORS headers to be retured for streaming using response headers policy.

`ResponseHeadersPolicyId: configObj.get(Config.CLOUDFRONT_RESPONSE_HEADERS_POLICY_ID)`

You can find details of the headers set in the CF template.

```
"CFResponseHeadersPolicy": {
    "Type" : "AWS::CloudFront::ResponseHeadersPolicy",
    "Properties" : {
        "ResponseHeadersPolicyConfig": {
            "Name" : {
                "Fn::Sub": "${EnvironmentName}-vision-stream-cloudfront-response-headers-policy"
            },
            "CorsConfig" : {
                "AccessControlAllowCredentials" : false,
                "AccessControlAllowHeaders" : {
                    "Items" : [ "*" ]
                },
                "AccessControlAllowMethods" : {
                    "Items" : [ "ALL" ]
                },
                "AccessControlAllowOrigins" : {
                    "Items" : [ "*" ]
                },
                "OriginOverride" : true
            }
        }
    }
}
```

Details of [cache behaviors is explained here](./cloudFront-security.md).

### Delete distribution

When it comes to deleting a CloudFront distribution, there are a few steps involved to ensure a smooth and proper deletion process.

**Disable the Distribution:** Before deleting a CloudFront distribution, you must first disable it. Disabling the distribution stops the distribution's behavior of serving content to end users. It is an important step because deleting an active distribution can result in a temporary loss of service for your users.

**Wait for the Distribution to Disable:** After disabling the distribution, you need to wait for the changes to propagate throughout the CloudFront network. This propagation time can vary and may take a few minutes or longer depending on various factors like network conditions and the size of the distribution.

**Invalidate the Cache (optional):** If you have made any recent changes to your origin server or want to ensure that your content is not served from the CloudFront cache after deleting the distribution, you can perform a cache invalidation. This step is optional but can be useful to ensure that users receive the most up-to-date content.

**Delete the Distribution:** Once the distribution has been disabled and you have allowed enough time for the changes to propagate, you can proceed with deleting the CloudFront distribution. This action is irreversible, so make sure you double-check that you are deleting the correct distribution.

### How are we deleting distributions in the Vision Stream?

Step 1: Disable distribution and mark distribution stale: We disable distribution in the AWS when the pipeline is deleted. Also we mark `active = false` in the distributions table.

```
  async delete(){
    
    ...
    // Disabling Cloudfront Distribution
    await cloudfront.disableDistribution(distribution.aws_distribution_id);
  }
```

Step 2: Cron job to delete stale distributions (delete-stale-cf-distributions): As soon as the distribution status is changed to disabled, it will be picked up by the next Cron invocation as a stale distribution and will be deleted from the AWS as well as from DB.

```
  async deleteStaleDistributions() {
    ...
    let result = await DistributionModel.findAllStaleDistributions(pageNo, size);
    for (let distribution of result) {
      await this.deleteDistribution(distribution);    
    }
    ...
  }
```
---

## Recording and MediaManager CloudFront Distribution

We are using another shared distribution for serving VoD recordings (MP4 and HLS). Also same distribution is being used to serve media manager contents.

We've configured two origin's to this distribution that serve content from two different S3 buckets.

- Medialive Pipeline Archive Output bucket (aka recording bucket)
- Media Manager bucket

CF distribution default behavior is to serve content form the recording bucket whereas when path in the url starts with `/media-manager/`, it serves media manager content.

Rest of the configurations are same as distribution that we create during AWS Medialive pipeline create flow.
