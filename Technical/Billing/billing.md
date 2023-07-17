
# Calculating cost of MediaLive pipeline

Following AWS services are part of MediaLive pipeline, so we'll be calculating cost for each of them.

1. MediaLive
2. MediaPackage
3. CloudFront
4. S3
5. MediaConvert

***Total cost = Medialive cost + MediaPackage cost + CloudFront cost + S3 cost + MediaConvert cost***

# MediaLive Cost

Inputs (including both primary and secondary ingest, as well as AWS Elemental Link devices) and outputs (including each individual encode within your output groups) for every channel are billed at their corresponding rates for as long as the channel is running. (See regional rates below.) Costs are incurred even if the inputs are not receiving any content and outputs are not producing content, while the channel is running. Since each live channel has one or more inputs and one or more outputs, you simply add the cost of each input (if applicable) and output to arrive at the total cost for running your live channel. There is an additional charge for running channels with advanced audio features enabled (one charge per channel).

AWS Elemental MediaLive provides two pricing models: On-Demand and Reserved.

* On-Demand pricing: You pay an hourly rate for running inputs, outputs, and add-on features. The duration of each running resource will be rounded up to the nearest minute, above a 10-minute minimum. No long-term commitments or upfront payments are needed. You can increase or decrease your usage depending on the needs of your channels and only pay the specified hourly rates for the inputs, outputs and features you use.

* Reserved pricing: Inputs, outputs, and add-on features are available with a 12 month commitment, and provide a significant discount compared to On-Demand pricing. This rate is charged for every hour in the month, for each month of your commitment period.

For calculations in the VisionStream, we've considered only On-Demand pricing model.

## Input pricing

The price for each input to your live channel is determined by a combination of codec, bitrate, and resolution of the input stream. If you create a channel with the Input Switching feature enabled (i.e. using more than one input) the cost of two active inputs will be applied to that channel even if more than two inputs are configured in the schedule.

```
async function getMedialiveInputPricing(
  channelClass = MediaLiveChannelClass.ChannelClassSinglePipeline,
) {
  logger.trace('getMedialiveInputPricing');
  const params = {
    Filters: [
      {
        Type: 'TERM_MATCH',
        Field: 'usageType',
        Value: `EML${mapChannelClass(channelClass)}-USW2-IN-MPEG2-HD-L20`, //EML<CHANNEL TYPE (1: SINGLE PIPELINE | 2: STANDARD)>-<REGION>-<OPERATION (IN | OUT)>-<INPUT (MPEG2 | AVC | HVEC)-<DEFINITION (SD: Standard Definition | HD: High Definition | UHD: Ultra HD)>-L<MAX BITRATE>
      },
    ],
    FormatVersion: 'aws_v1',
    ServiceCode: 'AWSElementalMediaLive',
  };
  const offer = await pricing.getProducts(params).promise();
  return PricingUtils.getPriceRange(offer)[0].cost;
}
```

## Output pricing

The cost for each output for your live channel is determined by a combination of bitrate, resolution, and frame rate for AVC outputs. For AVC Enhanced VQ, and HEVC outputs a combination of resolution and frame determined the cost. The total output price is the sum of all outputs generated for the channel.

```
async function getMedialiveOutputPricing(
  channelClass = MediaLiveChannelClass.ChannelClassSinglePipeline,
) {
  logger.trace('getMedialiveOutputPricing');
  const params = {
    Filters: [
      {
        Type: 'TERM_MATCH',
        Field: 'usageType',
        Value: `EML${mapChannelClass(channelClass)}-USW2-OUT-AVC-HD-L10-30-S`, //EML<CHANNEL TYPE (1: SINGLE PIPELINE | 2: STANDARD)>-<REGION>-<OPERATION (IN | OUT)>-<OUTPUT (AVC | HVEC)-<DEFINITION (SD: Standard Definition | HD: High Definition | UHD: Ultra HD)>-L<MAX BITRATE>-<MAX FRAMERATE>-<Video Quality (S: Standard | E: Enhanced)>
      },
    ],
    FormatVersion: 'aws_v1',
    ServiceCode: 'AWSElementalMediaLive',
  };
  const offer = await pricing.getProducts(params).promise();
  return PricingUtils.getPriceRange(offer)[0].cost;
}
```

## Cost calculations

```
Pricing.updateMediaLiveCost = async function (costRecordId, breakout, channel) {
  logger.trace(`updateMediaLiveCost `, breakout.id);
  let sessionBegTime = convertToValidDate(breakout.session_start_time);
  let sessionEndTime = convertToValidDate(breakout.session_end_time);

  ...

  // The duration of each running resource will be rounded up to the nearest minute, above a 10-minute minimum.
  const timeRunningInHrs = roundDurationToHours(sessionBegTime, sessionEndTime, 10);

  const inputCost = inputPricing * timeRunningInHrs * inputsCount;
  const outputCost = outputPricing * timeRunningInHrs * outputsCount;
  const cost = inputCost + outputCost;
  ...
}
```

* Calculate session time using breakout session_start_time and session_end_time column values. Also, round it to 10 minutes minimum.
* Find the number of inputs and outputs of the channel.
* Find input and output pricing.
* Calculate cost of running channel for a session and store values into the billing table.

# MediaPackage Cost

## Pricing

AWS Elemental MediaPackage offers two pricing models: one for live packaging and one for video on demand (VOD) packaging.

Live Packaging: For live channels, you are charged based on the amount of video ingested into the channel (measured in GB) and the amount of content originated and packaged for the channel (measured in GB).

MediaPackagePricingAttr enum:

```
const MediaPackagePricingAttr = Object.freeze({
  LiveIngest: '<region>-EMP-ingest-bytes',
  LiveOriginationAndPackaging: '<region>-EMP-origin-packaging-bytes',
  VODOriginationAndPackaging: '<region>-EMP-vod-origin-pkg-bytes',
});
```

Get MediaPackage pricing:
```
async function getMediaPackagePricing() {
  logger.trace('getMediaPackagePricing');
  const [liveIngestPrice, originPkgPrice] = await Promise.all([
    getMediaPackagePricingByAttr(MediaPackagePricingAttr.LiveIngest),
    getMediaPackagePricingByAttr(MediaPackagePricingAttr.LiveOriginationAndPackaging),
  ]);
  return { liveIngestPrice, originPkgPrice };
}
```

```
async function getMediaPackagePricingByAttr(pricingAttr) {
  logger.trace('getMediaPackagePricingByAttr');
  const region = PricingUtils.getCurrentAwsRegionShortHand();
  const pricingAttribute = pricingAttr.replace('<region>', region);

  const params = {
    Filters: [
      {
        Type: 'TERM_MATCH',
        Field: 'usageType',
        Value: pricingAttribute,
      },
    ],
    FormatVersion: 'aws_v1',
    ServiceCode: 'AWSElementalMediaPackage',
  };

  const offer = await pricing.getProducts(params).promise();
  const onDemandPricing = Object.values(offer.PriceList[0].terms.OnDemand)[0].priceDimensions;
  const cost = Object.values(onDemandPricing)[0].pricePerUnit.USD;
  return parseFloat(cost);
}
```

## Get usage metrics from the CloudWatch

There are two metrics required for the cost calculations: IngressBytes and EgressBytes. We fetch these metrics from the CloudWatch.

* EgressBytes: Number of bytes that MediaPackage successfully sends for each request. If MediaPackage doesn't receive any requests for output in the specified interval, then no data is given.

* IngressBytes: Number of bytes of content that AWS Elemental MediaPackage receives for each input request. If MediaPackage doesn't receive any requests for input in the specified interval, then no data is given.

```
Pricing.getMediaPackageMetrics = async function (awsMediaPackageChannelId, startTime, endTime) {
    logger.trace(`getMediaPackageMetrics - awsMediaPackageChannelId: ${awsMediaPackageChannelId}`);
    const ingressBytes = await Cloudwatch.getMediaPackageMetrics(
      awsMediaPackageChannelId,
      startTime,
      endTime,
      MediaPackageMetricName.IngressBytes,
    );

    const egressBytes = await Cloudwatch.getMediaPackageMetrics(
      awsMediaPackageChannelId,
      startTime,
      endTime,
      MediaPackageMetricName.EgressBytes,
    );

    return new MediaPackageMetrics(ingressBytes, egressBytes);
};
```

```
async function getMediaPackageMetrics(channelId, startTime, endTime, metricName) {
  const params = {
    EndTime: endTime,
    MetricDataQueries: [
      {
        Id: 'a_' + new Date().getTime().toString(),
        MetricStat: {
          Metric: {
            Namespace: 'AWS/MediaPackage',
            MetricName: metricName,
            Dimensions: [
              {
                Name: 'Channel',
                Value: channelId,
              },
            ],
          },
          Period: getPeriod(startTime, endTime),
          Stat: 'Sum',
        },
      },
    ],
    StartTime: startTime,
  };
  let result = await CloudWatch.getMetricData(params).promise();
  return result.MetricDataResults[0].Values.reduce((a, sum) => a + sum, 0); // data in bytes
}
```

## Cost calculations

Multiply usage metrics with the pricing to know the cost.

```
Pricing.updateMediaPackageCost = async function (
    costRecordId,
    breakoutId,
    awsMediaPackageChannelId,
    startTime,
    endTime,
) {
    logger.trace(`updateMediaPackageCost`, breakoutId);

    const metrics = await Pricing.getMediaPackageMetrics(
      awsMediaPackageChannelId,
      startTime,
      endTime,
    );

    const { liveIngestPrice, originPkgPrice } = await PricingService.getMediaPackagePricing();
    logger.debug(
      `MediaPackage pricing - liveIngestPrice: ${liveIngestPrice} originPkgPrice: ${originPkgPrice}`,
    );

    const ingressInGB = PricingUtils.convertDataSize(metrics.ingressBytes, Sizes.Byte, Sizes.GB);
    const egressInGB = PricingUtils.convertDataSize(metrics.egressBytes, Sizes.Byte, Sizes.GB);
    logger.debug(`MediaPackage usage - ingressInGB: ${ingressInGB} egressInGB: ${egressInGB}`);

    const cost = liveIngestPrice * ingressInGB + egressInGB * originPkgPrice;
    logger.debug(`Updating MediaPackage cost in DB: ${cost}`);

    return DB.from(DbTable.Billing).where('id', costRecordId).increment({
      mediapackage_metrics_ingress_in_bytes: metrics.ingressBytes,
      mediapackage_metrics_egress_in_bytes: metrics.egressBytes,
      mediapackage_cost: cost,
    });
};
```

# CloudFront Cost

## Get CloudFront and Lambda@Edge metrics

* In order to retrieve the total bytes downloaded and the number of requests made for a particular CloudFront distribution we make use of CloudWatch.

* `Cloudwatch.getCloudFrontMetrics` method gives the total bytes downloaded metric for the CloudFront distribution within a particular time period if we pass **BytesDownloaded** in the params.

* The same method also gives the total requests made for the CloudFront distribution within a particular time period, if we pass **Requests** in the params.

* We retrieve the invocation count metric for the Lambda@Edge function by calling `Cloudwatch.getLambdaAtEdgeMetrics()`. This method gives the total invocations made for the Lambda function within a particular time period if we pass **invocations** in the params.

* Similarly we can find the total duration for which the lambda function was in the running state. The function retrieves the duration metric for the Lambda@Edge function, if we pass **Duration** in the params.

```
  Pricing.getCFMetrics = async function (awsDistId, startTime, endTime) {
    logger.trace(`getCFMetrics - awsDistId: ${awsDistId}`);
    const config = getConfigObj();
    const result = new CloudFrontMetrics();
    result.bytesDownloaded = await Cloudwatch.getCloudFrontMetrics(
      awsDistId,
      startTime,
      endTime,
      CloudFrontMetricName.BytesDownloaded,
    );

    result.requestCount = await Cloudwatch.getCloudFrontMetrics(
      awsDistId,
      startTime,
      endTime,
      CloudFrontMetricName.Requests,
    );

    const lambdaAtEdgeMetrics = new LambdaMetrics(0, 0);
    const lambdaFnArn = config.get(Config.HLS_PROTECTION_CLOUDFRONT_LAMBDA_FUNCTION_ARN);
    lambdaAtEdgeMetrics.invocations = await Cloudwatch.getLambdaAtEdgeMetrics(
      lambdaFnArn,
      startTime,
      endTime,
      LambdaMetricName.Invocations,
    );

    lambdaAtEdgeMetrics.duration = await Cloudwatch.getLambdaAtEdgeMetrics(
      lambdaFnArn,
      startTime,
      endTime,
      LambdaMetricName.Duration,
    );

    result.lambdaAtEdgeMetrics = lambdaAtEdgeMetrics;

    return result;
  };
```

## Get CloudFront Download Pricing

* We determine the pricing for data transfer out from CloudFront and find the region with the highest cost.

* By iterating over the specified regions, we retrieve the pricing information for each region and select a region with the highest cost.

* CloudFront does not have EDGE LOCATIONS in All AWS Regions. They are only available in the following regions:
  - AP: Hong Kong, Philippines, South Korea, Taiwan, and Singapore (Asia Pacific)
  - AU: Australia
  - CA: Canada
  - EU: Europe and Israel
  - IN: India
  - JP: Japan
  - ME: Middle East
  - SA: South America
  - US: United States
  - ZA: South Africa

* This function provides the pricing for data transfer out from CloudFront based on the highest-cost region.

```
async function getCloudfrontDataDownloadPricing() {
  logger.trace('getCloudfrontDataDownloadPricing');
  const regions = ['IN', 'AU', 'US', 'AP', 'CA', 'EU', 'JP', 'ME', 'SA', 'ZA'];
  const offers = [];
  for (let region of regions) {
    const params = {
      Filters: [
        {
          Type: 'TERM_MATCH',
          Field: 'usagetype',
          Value: `${region}-DataTransfer-Out-Bytes`,
        },
      ],
      FormatVersion: 'aws_v1',
      ServiceCode: 'AmazonCloudFront',
    };
    const offer = await pricing.getProducts(params).promise();
    offers.push(PricingUtils.getPriceRange(offer)[0]);
  }
  return offers.sort((a, b) => b.cost - a.cost)[0].cost;
}
```

## Cost calculations

* We consider two costs for CloudFront billing - data transfer cost and Lambda@Edge cost.

* We calculate the dataDownloadCost by multiplying the dataDownloadPrice with bytesDownloaded in GBs.

* We calculate the httpReqCost by multiplying the perHttpReqPrice with httpReqCost.

* Data transfer cost = Data downloaded * Region for which changes are higher + HTTPS request cost

* Lambda@Edge cost is sum of the duration of which the lambda function was running and the number of invocations made to the lambda function.

* Lambda@Edge cost = Request cost + Compute cost

* Total CloudFront cost =  dataTransferOutCost + cloudFrontEdgeComputeCost;

```
  Pricing.updateCloudFrontCost = async function (breakout, awsDistId, startTime, endTime) {
    logger.trace(`updateCloudFrontCost breakoutId: ${breakout?.id}`);
    const metrics = await Pricing.getCFMetrics(awsDistId, startTime, endTime);
    const dataDownloadPrice = await PricingService.getCloudfrontDataDownloadPricing();
    logger.debug(`CloudFront pricing - dataDownloadPrice: ${dataDownloadPrice}`);
    const dataDownloadCost =
      dataDownloadPrice *
      PricingUtils.convertDataSize(metrics.bytesDownloaded, Sizes.Byte, Sizes.GB);
    logger.debug(`CloudFront data download cost: ${dataDownloadCost}`);

    // http and https requests cost
    const perHttpReqPrice = await PricingService.getCloudfrontPerHttpReqPrice();
    logger.debug(`CloudFront pricing - perRequestPrice: ${perHttpReqPrice}`);
    const httpReqCost = metrics.requestCount * perHttpReqPrice;
    logger.debug(`CloudFront http request cost: ${httpReqCost}`);

    const dataTransferOutCost = dataDownloadCost + httpReqCost;
    logger.debug(`CloudFront total data transfer cost: ${dataTransferOutCost}`);

    // lambda@edge cost
    const pricePerGBSecond = await PricingService.getLambdaEdgeDurationPricing();
    // We've lambda@edge configured with 128 MB
    const pricePerMemorySec = (pricePerGBSecond * 128) / 1024; // Price per 128 MB second
    // Convert duration to seconds and multiply with price per 128 MB second
    const durationCost = (metrics.lambdaAtEdgeMetrics.duration * pricePerMemorySec) / 1000;
    logger.debug(`CloudFront lambda@edge durationCost: ${durationCost}`);

    const perInvocationPrice = await PricingService.getLambdaEdgePerRequestPricing();
    const invocationCost = metrics.lambdaAtEdgeMetrics.invocations * perInvocationPrice;
    logger.debug(`CloudFront lambda@edge invocationCost: ${invocationCost}`);

    const cloudFrontEdgeComputeCost = durationCost + invocationCost;
    logger.debug(`CloudFront cloudFrontEdgeComputeCost: ${cloudFrontEdgeComputeCost}`);

    const cost = dataTransferOutCost + cloudFrontEdgeComputeCost;
    logger.debug(`ClodFront cost: ${cost}`);
  };
```

# S3 Cost

## Get S3 Storage Pricing

* `PricingService.getS3StoragePricing` retrieves the pricing for S3 storage in USD per GB-month.

```
async function getS3StoragePricing() {
  logger.trace('getS3StoragePricing');
  const params = {
    Filters: [
      {
        Type: 'TERM_MATCH',
        Field: 'storageClass',
        Value: 'General Purpose',
      },
      {
        Type: 'TERM_MATCH',
        Field: 'regionCode',
        Value: process.env.AWS_REGION,
      },
      {
        Type: 'TERM_MATCH',
        Field: 'volumeType',
        Value: 'Standard',
      },
    ],
    ServiceCode: 'AmazonS3',
  };
  const offers = await pricing.getProducts(params).promise();
  return PricingUtils.getBeginingRangeSKUPricing(offers);
}
```

## Get S3 Bytes Uploaded

* `Cloudwatch.getS3BytesUploaded` retrieves the total number of bytes uploaded to an S3 bucket within a specified time range.

* We convert these bytes to GBs to proceed with calculations.

```
async function getS3MetricsValue(bucketName, s3ReqMetricName, filterId, startTime, endTime) {
  const params = {
    Namespace: 'AWS/S3',
    Statistics: ['Sum'],
    Period: getPeriod(startTime, endTime),
    MetricName: s3ReqMetricName,
    Dimensions: [
      {
        Name: 'BucketName',
        Value: bucketName,
      },
      {
        Name: 'FilterId',
        Value: filterId,
      },
    ],
    StartTime: startTime,
    EndTime: endTime,
  };
  const stats = await CloudWatch.getMetricStatistics(params).promise();
  return stats.Datapoints.reduce((total, b) => total + b.Sum, 0);
}

async function getS3BytesUploaded(breakout, bucketName, startTime, endTime) {
  const metricsConfigId = getBreakoutMetricsConfigurationId(breakout.id);
  return getS3MetricsValue(
    bucketName,
    S3MetricsName.BytesUploaded,
    metricsConfigId,
    startTime,
    endTime,
  );
}
```

## Get S3 Request Pricing

* `PricingService.getS3RequestPricing` retrieves the pricing for S3 requests in USD.

* The function returns a promise that resolves to an object containing the pricing for S3 requests, with properties **getAndAllRequestPrice** representing the pricing for GET and all other request types, and **putPostRequestPrice** representing the pricing for PUT and POST request types.

```
async function getS3RequestPricing() {
  const [getAndAllRequestPrice, putPostRequestPrice] = await Promise.all([
    getS3RequestPricingByGroupDesc('GET and all other requests'),
    getS3RequestPricingByGroupDesc('PUT/COPY/POST or LIST requests'),
  ]);
  return { getAndAllRequestPrice, putPostRequestPrice };
}
```

## Get S3 Request Metrics

* `Cloudwatch.getS3RequestMetrics` retrieves the request metrics for an S3 bucket within a specified time range.

* The function returns a promise that resolves to an object containing the request metrics for the S3 bucket, with properties **getReqCount** representing the count of GET requests, and **putPostAndAllReqCount** representing the count of PUT, POST, and all other request types.

```
async function getS3RequestMetrics(breakout, bucketName, startTime, endTime) {
  const metricsConfigId = getBreakoutMetricsConfigurationId(breakout.id);
  // 'GET and all other requests'
  const getTypeReqCounts = await Promise.all([
    getS3MetricsValue(bucketName, S3MetricsName.GetRequests, metricsConfigId, startTime, endTime),
    getS3MetricsValue(bucketName, S3MetricsName.HeadRequests, metricsConfigId, startTime, endTime),
  ]);
  const getReqCount = getTypeReqCounts.reduce((total, count) => total + count, 0);

  const allReqCount = await getS3MetricsValue(
    bucketName,
    S3MetricsName.AllRequests,
    metricsConfigId,
    startTime,
    endTime,
  );

  // Subtract get request count from all request count to know put and post request count
  // It'll avoid one cloudwatch api call. Also it'll help to bill all requests.
  const putPostAndAllReqCount = allReqCount - getReqCount; // 'PUT/COPY/POST or LIST requests

  return { getReqCount, putPostAndAllReqCount, allReqCount };
}
```

## Get S3 Data Download Pricing

* `PricingService.getS3DataDownloadPricing` retrieves the pricing for data downloaded from S3 in USD per GB.

## Cost Calculations

```
  Pricing.updateS3Cost = async function (costRecordId, breakout, startTime, endTime) {
    logger.trace('updateS3Cost', breakout.id);
    const config = getConfigObj();
    const bucket = config.get(Config.S3_RECORDING_BUCKET);

    const pricing = await PricingService.getS3StoragePricing();
    const bytesUploaded = await Cloudwatch.getS3BytesUploaded(breakout, bucket, startTime, endTime);
    const storageUsedGb = PricingUtils.convertDataSize(bytesUploaded, Sizes.Byte, Sizes.GB);
    logger.debug('S3 storage used GB: ', storageUsedGb);
    const storageCost = pricing * storageUsedGb;
    logger.debug('S3 storage cost: ', storageCost);

    const reqPricing = await PricingService.getS3RequestPricing();
    const reqCount = await Cloudwatch.getS3RequestMetrics(breakout, bucket, startTime, endTime);
    logger.debug(
      `S3 request counts | Get req - ${reqCount.getReqCount} | Post req - ${reqCount.putPostAndAllReqCount}`,
    );
    const requestCost =
      reqCount.getReqCount * reqPricing.getAndAllRequestPrice +
      reqCount.putPostAndAllReqCount * reqPricing.putPostRequestPrice;
    logger.debug('S3 request cost: ', requestCost);

    const dataDownloadPrice = await PricingService.getS3DataDownloadPricing();
    const bytesDownloaded = await Cloudwatch.getS3BytesDownloaded(
      breakout,
      bucket,
      startTime,
      endTime,
    );
    const dataTransferredGB = PricingUtils.convertDataSize(bytesDownloaded, Sizes.Byte, Sizes.GB);
    const dataTransferCost = dataDownloadPrice * dataTransferredGB;
    logger.debug('S3 data transfer cost: ', dataTransferCost);

    const cost = storageCost + requestCost + dataTransferCost;
  };

```

* S3 service cost = storageCost + requestCost + dataTransferCost;


# MediaConvert Cost

AWS MediaConvert provides two pricing models: On-Demand and Reserved.

* On-Demand pricing: You pay only for what you use and there are no minimum fees. Charges are based on a simple fee per minute of video in each output. On-demand pricing has two tiers: Basic, which is lower cost and supports a limited set of features, and Professional, which supports the full set of features. No long-term commitments or upfront payments are needed.

* Reserved pricing: Purchase one or more reserved transcode slots for a fixed monthly charge (additional fees for Dolby Audio and Audio Normalization usage minutes), with a minimum 12-month commitment. Each slot runs a single job at a time, with access to all available encoding features, and can process jobs continuously one after the other.

For calculations in the VisionStream, we've considered only On-Demand pricing model as it is ideal for customers who are building applications with short-term or unpredictable workloads requiring fast turnaround times and scalability.

## Get Video Duration

* The MediaConvert cost is determined based on the duration of each output. The duration is calculated by counting the number of seconds in the output. This duration is then converted into fractional minutes to determine the total charge for the output.

* For example, if an output has a duration of 45 seconds, it will be considered as 0.75 minutes. The total charge for the output is calculated based on this fractional minute duration.

* It's important to note that there is a minimum billing duration of 10 seconds. So, if an output has a duration of less than 10 seconds, it will still be billed for a minimum of 10 seconds.

## Get Input Pricing

* `PricingService.getMediaConvertPricing` retireves the pricing for MediaConvert service in USD.

```
async function getMediaConvertPricing() {
  logger.trace('getMediaConvertPricing');
  // per minute pricing
  const params = {
    Filters: [
      {
        Type: 'TERM_MATCH',
        Field: 'usageType',
        Value: 'PDX-P-AVC-4K-S-30', //<REGION (Airport Code)>-<TIER (B: Basic | P: Pro)>-<VIDEO CODED (AVC | VP8 | VP9)>-<DEFINITION (SD | HD | UHD)>-<PASS ( S: Single | M: Multiple | SHQ | MHQ )>-<MAX FRAME RATE>
      },
    ],
    FormatVersion: 'aws_v1',
    ServiceCode: 'AWSElementalMediaConvert',
  };
  const offers = await pricing.getProducts(params).promise();
  return PricingUtils.getBeginingRangeSKUPricing(offers);
}
```

* The **Value** parameter in the `getMediaConvertPricing` function is used to specify a specific configuration for MediaConvert pricing. The value `'PDX-P-AVC-4K-S-30'` follows a specific format that represents different aspects of the MediaConvert configuration:
  - **<REGION (Airport Code)>** Represents the region or location code where the MediaConvert service is being used. For example, 'PDX' could represent the airport code for Portland, Oregon.

  - **<TIER (B: Basic | P: Pro)>** Indicates the pricing tier or level for the MediaConvert service. It can be either 'B' for Basic or 'P' for Pro.

  - **<VIDEO CODED (AVC | VP8 | VP9)>** Specifies the video codec used for the MediaConvert configuration. It can be 'AVC', 'VP8', or 'VP9'.

  - **<DEFINITION (SD | HD | UHD)>** Represents the video definition or resolution. It can be 'SD' for Standard Definition, 'HD' for High Definition, or 'UHD' for Ultra High Definition.

  - **<PASS ( S: Single | M: Multiple | SHQ | MHQ )>** Describes the pass or encoding mode for the MediaConvert configuration. It can be 'S' for Single pass, 'M' for Multiple passes, 'SHQ' for Super High Quality, or 'MHQ' for Multi-pass High Quality.

  - **< MAX FRAME RATE>** Specifies the maximum frame rate for the MediaConvert configuration.

## Cost Calculations

The cost of MediaConvert service is dependent on the duration of job running.

```
  Pricing.updateMediaConvertCost = async function (costRecordId, videoDurationInMs) {
    logger.trace('updateMediaConvertCost', costRecordId);
    const durationInMs = videoDurationInMs <= 10 ? 10 : videoDurationInMs;
    const durationInMinutes = durationInMs / 60000;

    const pricing = await PricingService.getMediaConvertPricing();
    logger.debug(`MediaConvert pricing: USD ${pricing} / minute.`);
    const cost = pricing * durationInMinutes;
  };
```

* MediaConvert service cost = (Job running in milliseconds) * (MediaConvert service based on region)