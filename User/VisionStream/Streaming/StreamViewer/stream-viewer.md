# <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/video.svg" width="20" height="20"> Stream Viewer

Stream Viewer is where you kick off, view, monitor and stop your livestreaming sessions.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20"> Overview

All breakouts associated with a streaming pipeline are eligible to be livestreamed.

All livestreams are started and stopped manually, and only by an admin user who has the corresponding 'Streaming' privilege.

## START Stream

Pressing this button will start your livestreaming session. There are a few things to take into consideration when starting your stream:

* Pipeline:
    - Pipelines should always be started first in VisionStream
    - When your video feed has been acquired, it will appear in the stream viewer
    - You MUST Raise Curtain on order to go live with your stream.

## STOP Stream

Pressing this button will stop your livestreaming session.

* Pipeline:
    - Pipeline will stop producing video immediately
    - Metric data, including analytics, attendance, and throughput, begin calculating 
    - You CANNOT restart a stream once it has been stopped
      - Your performance is essentially over and cannot be restarted

## Pipeline Details 

Press the Pipeline Details button to see and overview of the pipeline.
- Pipeline Name
- Pipeline type (Pro or Cam)
- Pipeline class (Single or Standard)
- Number of Inputs

For more information on Pipelines, you can [read more](../../Streaming/Pipelines/pipelines.md) here.

## Livestream Log

Press the Livestream Log button to see log messages associated with your pipeline.

The log will produce messages which allow you to monitor what is happening during a livestream session.

In most cases, you will simply receive Start and Stop log messages.

However, depending on your configuration and pipeline type, you may also receive additional messages, including:
- Recording start 
- Recording stop
- Failover to channel 1, or 2
- Stream health / degradation / recovery

## Raise Curtain

Use the Raise Curtain switch to
  - Make the stream live by enabling viewing for all attendees.
  - Setting the raise Curtain switch to Off will disable viewing for all attendees.

## Breakout Status
  - Breakout status is displayed to the right of distribution switch
  - Breakout status can be IDLE, STARTING, RUNNING, or COMPLETED

## Stream Health
  - Help you monitor the stream's health.
    - If dropped frames are non-zero then there is a lag.
    - If FPS is between 20 and 30 then stream health is considered good.

## Show Stream Events
  - Used to show Cam or Pro channel events in a separate grid window.

## Attendance
  - Shows the count of viewers currently watching the stream.

## Show Files
  - Display & Download media files uploaded via MediaManager.

## Refresh Button
  - Used to reload the Stream Viewer for all attendees.

## Video Player
  - Used for viewing the streaming session.

## Comments
  - Allows you to engage with audience without the need for a secondary device.

If Breakout is completed, you will see the `This stream has ended !` view.

## Job Status
- Shows the convert job status which is either in progress or complete.
  - Convert job is responsible to generate the breakout recording.

## View Recording
  - View the breakout's on-demand recording.

## Copy Recording URL
  - Used to copy the URL of the final recording to the clipboard.

## Comments
- Comments are disabled once the breakout is completed.
