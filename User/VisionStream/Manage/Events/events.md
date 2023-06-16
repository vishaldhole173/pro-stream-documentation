# Event
An Event is a fundamental object in the VisionStream platform.
### Overview
Admin users create Events which encapsulate one or more 'Breakouts'.

Events have discreet start/end times, location, venue, room, description, and graphic.

<hr>

####  Create a new Event

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/plus.svg" width="20" height="20">

Press the '+' icon in the upper right of the Event listing page to open the Create New Event page.

* Required fields:
  - Event Name
  - Start time
  - End time

Note: Start and End times are entered as UTC values, though their local equivalents are output for reference.

* Optional fields:
  - Calendar Visibility
  - Venue
  - Location
  - Type
  - Picture
  - Description

<hr>

#### Show Active Events
<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/toggle-on.svg" width="20" height="20">

* You can filter Event listings to show only the Events currently in progress.
  - Events which have been completed will now be displayed.
    - This setting persists over browser sessions.

<hr>

#### Show Recordings
<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle-play.svg" width="20" height="20">

Every breakout is automatically recorded in VisionStream.
* Show Recordings feature allows admins the ability to see all recordings for any Event in a single view.
    - Recordings are output both as HLS and MP4 format.
      - Recordings can be viewed once a breakout has been completed.
      - Recordings can be downloaded and saved by stream viewers.

<hr>

#### Show Usage
<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/gauge-high.svg" width="20" height="20">

A Usage profile is generated after every breakout has been completed.
* Show Usage feature allows the admin user the ability to see the cumulative usage of each breakout.
* Usage is delivered in two categories:
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

<hr>

####  Show Attendance

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/users.svg" width="20" height="20">

Attendance is automatically tracked for every breakout.

You can track the cumulative attendance for any Event by choosing the Show Attendance feature:

* View attendee table:
  - Name
  - Email
  - Country
  - Region
  - City
  - Cumulative viewing time
    - Live  
    - On-demand 
    - Total viewing time

<hr>

####  Edit Event

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/pen-to-square.svg" width="20" height="20">

You can edit any Event and change the values of any field.

NOTE TO SELF: Can you set an Event start time to be after an already established breakout start time?

<hr>

####  Show Breakouts

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/layer-group.svg" width="20" height="20">

To view all the breakouts associated with an Event, select the Show Breakouts control.

You will be navigated to a new page containing a listing which includes all the breakouts.

<hr>

#### Active and Published indicators

<img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle.svg" width="20" height="20"> 

VisionStream maintains a simple UI construct which allows for the easy identification of Active and Published Events.
* Active Events
  - Events which are active are currently in progress.
    - Active Events are designated by a green icon .
    - Completed Events are designated by an amber icon.
* Published Events
  - Published Events will display in your calendar.
  - Unpublished Events are hidden and cannot be accessed by a user.
