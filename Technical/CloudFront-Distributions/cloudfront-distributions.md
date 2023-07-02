# <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/screwdriver-wrench.svg" width="20" height="20"> Distributions

## Lifecycle

1. Distribution is created when we create the Channel.

```
  async function create() {
    
    //  Creating the MediaLive channel
    const mediaLiveChannel = await mediaLive.createChannelMediaLive(
      channelObj.name,
      mediaPackageChannel.Id,
      inputObj.aws_input_id,
      tagsMap,
    );

    // Creating Distribution
    await this._createDistribution();
    return {
      id: channelObj.id,
      endPoints: [endPoints.Url],
      inputDestUrls: [inputObj.aws_input_dest_url_1, inputObj.aws_input_dest_url_2],
    };
  }
```

2. It will de Disabled when the Channel is deleted.

```
  async delete(){
    
    ...
    // Disabling Cloudfront Distribution
    await cloudfront.disableDistribution(distribution.aws_distribution_id);
  }
```

3. As soon as a Distribution is Disabled, it will be picked up by the next Cron Invocation as a stale distribution and will be deleted from AWS as well as from DB.

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



## Coupling

Distribution is attached with Breakout.

### Problems before Coupling:

1. More wait time to start the Distribution.
 
  * Earlier we have to wait for a while, to start the Distribution, but now we create Distribution along with the Channel.
  
  * Now when we start streaming, we will not have to wait explicitly to start Distributions as they are already created with Channel.
  
  * The wait time to start streaming is reduced upto 2 minutes.
  
2. Unable to collect metrics immediately once breakout is over. 
 
  * Earlier we were not able to collect metrics immediately once breakout is over. As cloudfront might propagate the metrics at a random delay to cloudwatch and cloudwatch might cause further delay in publishing the metrics. This effect is evident from [here](https://www.trek10.com/blog/cloudwatch-deep-dive#:~:text=We%20find%20that%20CloudWatch%20metrics,for%20import%20adds%20additional%20delay).
  ```
    async collectCFMetrics(breakout) {
    const distribution = await DistributionModel.findDistributionByChannelId(breakout.channel_id);
    if (distribution) {
      const metrics = await BillingModel.getCFMetrics(breakout, distribution);
      await BreakoutModel.updateWithBytesDownloaded(breakout.id, metrics.bytesDownloaded);
    }
  }
  ```
  This delay in metrics were observed primary for new Distributions, but with existing distribution with no State Changes in place, Metrics might be available at a very lesser time lag once a breakout is over.
  



## Failsafe

1. In case if distribution is deleted, when a breakout is started.

2. In such  case **prepare()** function called in medialive.channel.js file, which then calls the **_ensureDistribution()** function

```
  async _ensureDistribution() {
    try {
      const channelId = this.channel.id;
      const distribution = await DistributionModel.findDistributionByChannelId(channelId);
      if (!distribution) {
        await this._createDistribution();
      }
    } catch (error) {
    }
  }
```

3. While strating a breakout, if server notices that no distribution is attached with the channel (as if someone accidentally deleted the distribution), then **_ensureDistribution()** function creates a new distribution with same mediaPackage endpoint and attaches it with the channel in DB

---

## Recording and MediaManager CloudFront Distribution

* AWS Distribution Id: E3FEGSC0PV886G

* AWS Region: Global

* Used to deliver MediaManger media and stream recordings to the app.

* The properties to understand in the `MediaManagerBucket` configuration are:
  - cdcd
