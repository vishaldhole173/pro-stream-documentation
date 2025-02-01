# <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/gauge.svg" width="20" height="20"> Usage

Get a snapshot your streaming usage at the Account, Event and Breakout levels.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20"> Overview

**How it works**
  - For both Cam and Pro pipelines, a live video feed is ingested from a camera or a broadcasting source.
  - Dual ingest support is provided in Pro instances for high availability and fault tolerance.

**Streaming using Pro pipelines**

1. **Streaming**
   - Pro pipelines handle **live video processing**.
   - The pipeline transcodes the video feed into multiple bitrates to enable adaptive bitrate streaming.
   - The processed streams are then sent to the packaging component.
2. **Packaging**
   - Packaging refers to the job **Just-in-Time (JIT) packaging**, converting the transcoded streams into formats such as **HLS**, **DASH**, **MSS**, and **CMAF** for compatibility with various devices.
   - Packaging ensures low-latency streaming and also supports encryption for secure content delivery.
3. **Delivery**
   - VisionStream employs a **Content Delivery Network (CDN)** for global distribution of the packaged streams.
   - It caches content at edge locations to reduce latency and enhance the streaming experience for viewers worldwide.
4. **Conversion**
   - VisionStream employs a conversion engine which allows us to process input files into various output formats.
   - It is used in VisionStream as a means of generating an MP4 video from an HLS archive.
5. **Storage**
   - Cloud storage is used to store segment files (.ts) generated from AWS MediaLive and recordings (VOD content) content.

**Streaming using Cam pipelines**

- Cam pipelines function similarly to Pro pipelines, with the following exception:
  - Cam pipelines do not support discreet Packaging and Delivery, as these functions are built into the Cam pipeline.

### Support for multiple OTT devices
    - Both Pro and Cam streams are compatible with a range of OTT (Over-The-Top) devices, including smart TVs, tablets, smartphones, and desktop players.
      - Users enjoy smooth playback across devices thanks to adaptive bitrate streaming.

If you are interested in a more technical overview of the streaming process you can [Read more](../../Admin/Distributions/distributions.md).
