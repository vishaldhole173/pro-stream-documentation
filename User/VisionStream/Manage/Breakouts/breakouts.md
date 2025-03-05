# Breakout

A Breakout is a core VisionStream component.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20">  Overview

A Breakout is a child of an Event. An Event (usually) consists of many Breakouts.

Admin users will create new Breakout records, entering name, date, time, duration and location of the live stream.

Breakout start time and duration should always be less than the Event end time.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/circle-plus.svg" width="20" height="20">  Create new Breakout

Press the '+' icon in the upper right of the Breakout listing page to open the create new Breakout page.

* Required fields:
    - Name
        - The name of breakout which will be visible to the audience.
* Optional fields:
    - Calendar Visibility
        - Breakouts will display in the calendar if set to active.
    - Moderated Forum
        - Moderate the comments made by audience if set to active.
    - Location
        - Your physical streaming location.
    - Charge Amount
        - Amount you want to charge for the breakout.
    - Tip Jar
        - Set if you want to show a 'donation' page to your users.
    - Transcription
        - Set if you want to have a text transcription generated from your livestream.
    - Search
        - Assign a search to display files associated with a breakout.
          - Requires MediaManager 
    - Picture
        - Picture you want to display for your breakout in the calendar.
    - Description
        - Additional information about your breakout.
    - Pipeline
        - The input Pipeline you want to use for streaming.
    - Source IP
        - IP of the system you are streaming from.
    - Start Time
        - Time at which you want to start the breakout.
        - Note that Start time is entered as UTC value, though the local equivalent is output for reference.
    - Hours
        - Hours for which you want to stream.
    - Minutes
        - Minutes for which you want to stream.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/toggle-on.svg" width="20" height="20">  Hide Completed

Hide Completed Breakouts toggle allows you to quickly filter out breakouts which have already completed.

* You can filter Breakouts to show only the those currently in progress.
    - Breakouts which have been completed will be removed from the list.
        - This setting persists over browser sessions.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/video.svg" width="20" height="20">  Show Stream Viewer

Stream Viewer is where you kick off, view, monitor and stop your livestreaming sessions.

All breakouts associated with a streaming pipeline are eligible to be livestreamed.

If Breakout is active, you can navigate to the Stream Viewer view, which contains the following controls outlined below.

* Raise Curtain switch
    - Used to make the stream live
    - Once the stream is live audience is able to see the live stream
* Pipeline status indicator
    - Used to view the status of a pipeline
        - Idle channel status is designated by an amber icon
        - Starting channel status is designated by a blue icon
        - Running channel status is designated by a green icon
* Distribution status indicator
    - Used to view the status of a distribution (Pro channel only)
        - In progress distribution status is designated by an amber icon
        - Deployed distribution status is designated by a green icon
* Distribution switch
    - Used to make audience only use the Cloudfront distribution playback URL
* Breakout Status
    - Breakout status is displayed to the right of distribution switch
    - Breakout status can be IDLE, STARTING, RUNNING, or COMPLETED
* Stream Control Buttons
    - START Button
        - Set breakout status to Running
        - Start the pipeline and set its status to Running
        - Create and deploy a distribution if necessary
        - Set distribution status to Deployed
    - ABORT Button
        - Set breakout status to Idle
        - Stop the pipeline and set its status to Idle
        - Stop the distribution and set its status to Idle
    - STOP Button
        - Set breakout status to Completed
        - Stop the pipeline and set its status to Idle
        - Stop the distribution and set its status to Idle
        - Begins collecting various metric data
        - Starts the job to create on-demand mp4 files
        - The viewing session will end for all audience
* Health
    - Help you to monitor the stream's health.
        - If dropped frames are non-zero then there is a lag.
        - If FPS is between 0 and 30 then stream health is considered good.
* Show Stream Events
    - Used to show Cam or Pro channel events in a separate grid window.
* Attendance
    - Shows the count of viewers currently watching the stream.
* Show Files
    - Display & Download media files uploaded via MediaManager.
* Refresh Button
    - Used to reload the Stream Viewer.
* Video Player
    - Used for viewing the streaming session.
* Comments
    - Allows you to engage with audience without the need for a secondary device.

If Breakout is completed, you will see the `This stream has ended !` view.

* Show Files
    - View & download uploaded media files.
* View Recording
    - View the breakout's on-demand recording.
* Comments
    - Comments are disabled once the breakout is completed.
* Job Status
    - Shows the convert job status which is either in progress or complete.
        - Convert job is responsible to generate the breakout recording.
* Copy S3 URI
    - Used to copy the URL of the final recording to the clipboard.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/gauge-high.svg" width="20" height="20">  Show Usage

A Usage profile is generated after every breakout has completed.

* Usage is delivered in two categories
    - Usage
        - Streaming in hours
        - Packaging in GB's
        - Delivery in GB's
        - Conversion in minutes
        - Storage in GB
    - Charges
        - Streaming in USD
        - Packaging in USD
        - Delivery in USD
        - Conversion in USD
        - Storage in USD

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/users.svg" width="20" height="20">  Show Attendance

Attendance is automatically tracked for every breakout.

* View attendee table:
    - Name
    - Email
    - Country
    - Region
    - City
    - Viewing time
        - Live
        - On-demand
        - Total viewing time

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/pen-to-square.svg" width="20" height="20">  Edit Breakout

You can edit any Event and change the values of any field.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/calendar-check.svg" width="20" height="20"> Published / Hidden Events

VisionStream maintains a simple UI construct which allows for the easy identification of Hidden vs. Published Breakouts.

- Published Breakouts will display in your calendar.
- Published Breakouts are designated by a calendar icon with a check mark.
- Unpublished Breakouts are hidden and cannot be accessed by a user.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/video.svg" width="20" height="20"> Active / Completed Events

VisionStream maintains a simple UI construct which allows for the easy identification of Active vs. Completed Breakouts.

- Active Breakouts are designated by a Video Camera which will display 'Active' when you hover over the icon.
- Completed Breakouts are designated by a Play button icon which will display 'Completed' when you hover over the icon.
