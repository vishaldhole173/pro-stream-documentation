# <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/flag.svg" width="20" height="20"> Event
An Event is a core VisionStream component.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20"> Overview
Admin users create Events which encapsulate one or more 'Breakouts'.

Events have discreet start/end times, location, venue, room, description, and graphic.

##  <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/plus.svg" width="20" height="20"> Create new Event

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

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/toggle-on.svg" width="20" height="20"> Show Active Events

Show Active Events toggle allows you to quickly filter out events which have already completed.

* You can filter Events to show only the those currently in progress.
  - Events which have been completed will be removed from the list.
    - This setting persists over browser sessions.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/circle-play.svg" width="20" height="20"> Show Recordings

Every breakout is automatically recorded in VisionStream.
* Show Recordings feature allows admins the ability to see all recordings for any Event in a single view.
    - Recordings are output both as HLS and MP4 format.
      - Recordings can be viewed once a breakout has been completed.
      - Recordings can be downloaded and saved by stream viewers.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/gauge-high.svg" width="20" height="20"> Show Usage

A Usage profile is generated after every breakout has been completed. At the event level, Usage is calculated as the cumulative usage of all breakouts belonging to the event.

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

##  <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/users.svg" width="20" height="20"> Show Attendance

Attendance is automatically tracked for every breakout.

At the event level, Attendance is calculated as the cumulative attendance of all breakouts belonging to the event.

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

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/pen-to-square.svg" width="20" height="20"> Edit Event

You can edit any Event and change the values of any field.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/layer-group.svg" width="20" height="20"> Show Breakouts

To view all the breakouts associated with an Event, select the Show Breakouts control.

You will be navigated to a new page containing a listing which includes all the breakouts belonging to the event.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/circle.svg" width="20" height="20"> Active and Published indicators

VisionStream maintains a simple UI construct which allows for the easy identification of Active and Published Events.

* Active Events
  - Events which have not completed.
    - Active Events are designated by a green icon.
    - Completed Events are designated by an amber icon.
* Published Events
  - Published Events will display in your calendar.
  - Unpublished Events are hidden and cannot be accessed by a user.
