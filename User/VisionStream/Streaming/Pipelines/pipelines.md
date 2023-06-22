# <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle-plus.svg" width="20" height="20"> Pipelines

A Pipeline is a core VisionStream object.

## <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/magnifying-glass-chart.svg" width="20" height="20"> Overview

Pipelines are used for streaming VisionStream breakouts, and for streaming Mp4 static content over VisionStream
channels.

A VisionStream pipeline is attached to a breakout to facilitate a live content stream. The input of the stream is
usually a live video feed from a device such as a video camera.

A VisionStream pipeline can be configured to allow for multiple inputs, and supports automatic failover.

## Pipeline States

- Idle
   - The pipeline is in inactive state. It is not processing any input streams. 
- Starting
    - The pipeline is starting, usually the result of starting a breakout.
- Running
    - The Pipeline is running, and is able to accept video from a source device
- Stopping
    - The Pipeline is stopping, usually the result of stopping a breakout.

## <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/cloud.svg" width="20" height="20">  Distributions

A distribution is an accompanying service which is created whenever a pipeline is created, and is disabled when a pipeline is deleted.

To see the distribution profile for any pipeline, toggle the 'Show Hide Distribution Config.' button. [Read more](../../Admin/Distributions/distributions.md).

## <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/trash.svg" width="20" height="20">  Delete a pipeline

- Press the trash icon in the lower-left of the pipelines listing page.
- The application will prompt the user to confirm their intention to delete the pipeline.
* This confirmation step is crucial as the action cannot be undone.
* Upon confirmation, the application permanently removes the pipeline and any referenced to it.

## <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/plus.svg" width="20" height="20">  Add pipeline 

Press the '+' button in the Pipelines view to navigate to the Create Pipeline form, where you will enter information
about the pipeline.

- ### Pipeline Types
    - MediaLive
        - A broadcast-grade pipeline which is capable of encoding live video for broadcast and streaming to any device.
    - Interactive Video Service
        - A broadcast-grade pipeline which enables interactive and engaging live streaming experiences.

- ### Input Types
    - RTMP Push
        - An input type that allows you to push live video streams using the Real-Time Messaging Protocol (RTMP).
        - RTMP is a popular protocol used for delivering live streams from an encoder to a streaming server.
    - MP4 File
        - An input type that allows you to use pre-recorded video content in MP4 format as a source for your live streams.
        - You can upload MP4 files to AWS MediaLive or IVS channels for broadcasting.

- ### Input Class
    - Single Pipeline
        - An input class that represents a configuration where a single input is connected to a pipeline.
        - This means that there is only one source feeding into the encoding and processing pipeline.
    - Standard Pipeline
        - An input class that represents a configuration where multiple inputs are connected to a pipeline. 
        - In this setup, multiple sources can be combined or switched between to create a more complex streaming workflow.

- ### Input Network
    - Public
        - An input network configuration where the inputs are accessible over the public internet.
        - This means that the source devices can connect to the AWS MediaLive or IVS channels using publicly routable IP addresses.
    - VPC
        - An input network configuration where the inputs are connected to a Virtual Private Cloud (VPC).
        - This setup allows you to isolate your streaming infrastructure within your private network, enhancing security and control over your streams.

- ### Number of Inputs
    - 1
        - Represents a configuration where there is a single input source connected to the pipeline.
    - 2
        - Represents a configuration where there are two input sources connected to the pipeline.

