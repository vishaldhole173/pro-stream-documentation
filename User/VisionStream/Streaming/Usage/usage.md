# <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/gauge.svg" width="20" height="20"> Usage

Get a snapshot your streaming usage at the Account, Event and Breakout levels.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20"> Overview

1. **Live Channel Source**
    - A live video feed is ingested from a camera or a broadcasting source.
    - Dual ingest support is provided for high availability and fault tolerance.

2. **Streaming with AWS Elemental MediaLive and AWS IVS**
    - MediaLive handles **live video processing**.
    - It transcodes the video feed into multiple bitrates to enable adaptive bitrate streaming.
    - The processed streams are then sent to the next component.

3. **Packaging with AWS Elemental MediaPackage**
    - MediaPackage provides **Just-in-Time (JIT) packaging**, converting the transcoded streams into formats such as **HLS**, **DASH**, **MSS**, and **CMAF** for compatibility with various devices.
    - MediaPackage ensures low-latency streaming and also supports encryption for secure content delivery.
    - **Only Pro pipelines will report this value.**

4. **Delivery with Amazon CloudFront**
    - CloudFront acts as a **Content Delivery Network (CDN)** for global distribution of the packaged streams.
    - It caches content at edge locations to reduce latency and enhance the streaming experience for viewers worldwide.
    - **Only Pro pipelines will report this value.**

5. **Conversion with MediaConvert.io**
   - MediaConvert.io is out own conversion engine which allows us to process files much faster and with more flexibility.
   - It is used in VisionStream as a means of generating an MP4 video from an HLS archive.

6**Storage with Amazon S3**
    - Shared Amazon S3 bucket is used to store segment files (.ts) generated from AWS MediaLive and recordings (VOD content) content.

7**Multiple OTT Devices**
    - The packaged and distributed streams are compatible with a range of OTT (Over-The-Top) devices, including smart TVs, tablets, smartphones, and desktop players.
    - Users enjoy smooth playback across devices thanks to adaptive bitrate streaming.
