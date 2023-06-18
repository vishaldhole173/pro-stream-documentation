# Pipelines

A Pipeline is a core VisionStream object.

## Overview

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

##  (TODO: need icon here) Distributions

A distribution is an accompanying service which is created whenever a pipeline is created, and is disabled when a pipeline is deleted.

To see the distribution profile for any pipeline, toggle the 'Show Hide Distribution Config.' button.

TODO: LINK TO DISTRIBUTION PAGE FOR "MORE INFO".

##  (TODO: need icon here) Delete a pipeline

- Press the trash icon in the lower-left of the pipelines listing page.
- The application will prompt the user to confirm their intention to delete the pipeline.
* This confirmation step is crucial as the action cannot be undone.
* Upon confirmation, the application permanently removes the pipeline and any referenced to it.

## (TODO: need icon here) Add pipeline 

Press the '+' button in the Pipelines view to navigate to the Create Pipeline form, where you will enter information
about the pipeline.

- ### Pipeline Types
    - MediaLive
        - A broadcast-grade pipeline which is capable of encoding live video for broadcast and streaming to any device.
    - Interactive Video Service
        - TODO: Need description here

- ### Input Types
    - RTMP Push
        - TODO: Need description here
    - MP4 File
        - TODO: Need description here

- ### Input Class
    - Single Pipeline
        - TODO: Need description here
    - Standard Pipeline
        - TODO: Need description here

- ### Input Network
    - Public
        - TODO: Need description here
    - VPC
        - TODO: Need description here

- ### Number of Inputs
    - 1
        - TODO: Need description here
    - 2
        - TODO: Need description here

