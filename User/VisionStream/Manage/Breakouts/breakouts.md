# Breakout
A Breakout is a fundamental object in the VisionStream platform, and is essentially an encapsulation of a live streaming session.
### Overview
A Breakout is a child of an Event, in that an Event (usually) consists of many Breakouts.

Admin users will create new Breakout records, entering name, date, time, duration and location of the live stream.

Breakout start time and duration should always be less than the Event end time.

---

#### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/plus.svg" width="20" height="20"> Create a new Breakout

Press the '+' icon in the upper right of the Breakout listing page to open the create new Breakout page

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
  - Search
    - Assign a search to display files associated with a breakout.
  - Picture
    - Picture you want to display for your breakout in the calendar.
  - Description
    - Additional information about your breakout.
  - Pipeline
    - The Pipeline you want to use for streaming.
  - Source IP
    - IP of the system you are streaming from.
  - Start Time
    - Time at which you want to start the breakout.
    - Note that Start time is entered as UTC value, though the local equivalent is output for reference.
  - Hours
    - Hours for which you want to stream.
  - Minutes 
    - Minutes for which you want to stream.

---

#### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/toggle-on.svg" width="20" height="20"> Show Active Breakouts

You can filter Breakout listings to show only the Breakouts which are not completed.
* Breakouts which have been completed will now be displayed.
  - This setting persists over browser sessions.
---

#### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/video.svg" width="20" height="20"> Show Stream Viewer
If Breakout is active, you will see the Stream Viewer view, which contains the following controls outlined below.

* Raise Curtain switch
  - Used to make the stream live
  - Once the stream is live audience is able to see the live stream
####
* Pipeline status indicator
    - Used to view the status of a MediaLive channel
        - Idle channel status is designated by an amber icon
        - Starting channel status is designated by a blue icon
        - Running channel status is designated by a green icon
####
* Cloudfront distribution status indicator
    - Used to view the status of a Cloudfront distribution
        - In progress Cloudfront distribution status is designated by an amber icon
        - Deployed Cloudfront distribution status is designated by a green icon
####
* Cloudfront switch
  - Used to make audience only use the Cloudfront distribution playback URL
####
* Breakout Status
  - Breakout status is displayed to the right of Cloudfront switch
  - Breakout status can be IDLE, STARTING, RUNNING, or COMPLETED
####
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
####
* Health
  - Help you to monitor the stream's health.
    - If dropped frames are non-zero then there is a lag.
    - If FPS is between 0 and 30 then stream health is considered good.
####
* Show Stream Events
  - Used to show IVS or MediaLive channel events in a separate grid window.
####
* Attendance
  - Shows the count of viewers currently watching the stream.
####
* Show Files
  - Display & Download media files uploaded via MediaManager.
####
* Refresh Button
  - Used to reload the Stream Viewer.
####
* Video Player
  - Used for viewing the streaming session.
####
* Comments
  - Allows you to engage with audience without the need for a secondary device.
---
* If Breakout is completed, you will see the 'Show Is Over' view
    - Show Files
      - View & download uploaded media files.
    - View Recording
      - View the breakout's on-demand recording.
    - Comments
      - Comments are disabled once the breakout is completed.
    - Job Status
      - Shows the convert job status which is either in progress or complete.
        - Convert job is responsible to generate the breakout recording.
    - Copy S3 URI
      - Used to copy the S3 of the final recording on the clipboard.

---

#### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/gauge-high.svg" width="20" height="20"> Show Usage

* A Usage profile is generated after every breakout has been completed
* Show Usage feature allows the admin user the ability to see the breakout usage
* Usage is delivered in two categories
  - Usage
    - Streaming in hours
    - Packaging in GB's
    - Delivery in ???
    - Conversion in minutes
    - Storage in GB
  - Charges
    - Streaming in USD
    - Packaging in USD
    - Delivery in USD
    - Conversion in USD
    - Storage in USD

---

#### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/users.svg" width="20" height="20"> Show Attendance

Attendance is automatically tracked for every breakout.

* View attendee
  - Name
  - Email
  - Country
  - Region
  - City
  - Viewing time
    - Live
    - On-demand
    - Total viewing time

---

#### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/pen-to-square.svg" width="20" height="20"> Edit Breakout

You can edit any Breakout and change the values of any fields.

---

#### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle.svg" width="20" height="20"> Active and Published indicators

* Active Breakouts
  - Breakouts that are active are currently in progress
    - Active Breakouts are designated by a green icon 
    - Completed Breakouts are designated by an amber icon
* Published Breakouts
  - Published Breakouts will display in your calendar
  - Unpublished Breakouts are hidden and cannot be accessed by a user
