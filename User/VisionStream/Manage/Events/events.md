# Event

### Overview

* An Event is a fundamental object in the VisionStream platform
* Admin users create Events which encapsulate one or more 'Breakouts'
* Events have a discreet start/end time, location, venue, room, description, and graphic

---

### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/plus.svg" width="20" height="20"> Create a new Event

Press the '+' icon in the upper right of the Event listing page to open the create new Event page.

* Required fields
  - Event Name
  - Start time
  - End time

Note that Start and End times are entered as UTC values, though their local equivalents are output for reference.

* Optional fields
  - Calendar Visibility
  - Venue
  - Location
  - Type
  - Picture
  - Description

---

### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/toggle-on.svg" width="20" height="20"> Show Active Events
* You can filter Event listings to show only the Events currently in progress
  - Events which have been completed will now be displayed
    - This setting persists over browser sessions

---

### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle-play.svg" width="20" height="20"> Show Recordings
* Every breakout is automatically recorded in VisionStream
* Show Recordings feature allows admins the ability to see all recordings for any Event
    - Recordings are output both as HLS and MP4 format
      - Recordings can be viewed once a breakout has been completed
      - Recordings can be downloaded and saved by stream viewers

---

### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/gauge-high.svg" width="20" height="20"> Show Usage

* A Usage profile is generated after every breakout has been completed
* Show Usage feature allows the admin user the ability to see the cumulative usage of each breakout
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

### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/users.svg" width="20" height="20"> Show Attendance

Attendance is automatically tracked for every breakout.

You can track the cumulative attendance for any Event by choosing the Show Attendance feature.

* View attendee
  - Name
  - Email
  - Country
  - Region
  - City
  - Cumulative viewing time
    - Live  
    - On-demand 
    - Total viewing time

---

### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/pen-to-square.svg" width="20" height="20"> Edit Event

You can edit any Event and change the values of any field.

NOTE TO SELF: Can you set an Event start time to be after an already established breakout start time?

---

### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/layer-group.svg" width="20" height="20"> Show Breakouts

To view all the breakouts associated with an Event, select the Show Breakouts control.

You will be navigated to a new page containing a listing which includes all the breakouts.

---

### <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle.svg" width="20" height="20"> Active and Published indicators

* Active Events
  - Events which are active are currently in progress
    - Active Events are designated by a green icon 
    - Completed Events are designated by an amber icon
* Published Events
  - Published Events will display in your calendar
  - Unpublished Events are hidden and cannot be accessed by a user
