# <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/flag.svg" width="20" height="20"> Events

Events can span days, weeks, months or years.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20"> Overview

Admin users create Events which encapsulate one or more 'Breakouts'.

Events have discreet start & end times, location, venue, room, description, and graphic.

## Event Listing View

The Event Listing view is the page you are navigated to when you click the Events option in the VisionStream sideNav.

This page will contain a listing of all the events in your account.

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/calendar-check.svg" width="20" height="20"> Published vs. Hidden Events

- Published Events will display in calendars and other forward-facing pages.
- Unpublished Events are hidden and cannot be accessed by an attendee.
- In the Event listing page:
  - Published Events are designated by a calendar icon with a check mark.
  - Unpublished Events are designated by a disabled (grey) calendar icon.

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/video.svg" width="20" height="20"> Active vs. Completed Events

- Active Events are designated by a Video Camera which will display 'Active' on mouse hover.
- Completed Events are designated by a disabled (grey) Video Camera which will display 'Completed' on mouse hover.

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/toggle-on.svg" width="20" height="20"> Hide Completed

Hide Completed toggle allows you to quickly filter out events which have already completed.

* You can filter Events to show only the those currently in progress.
  - Events which have completed will be removed from the list.
  - An Event is completed only after all breakouts have been completed.
  - Hide Completed setting persists over browser sessions.

## Event Details View

The Event Details view is where you enter details specific to your event.

###  <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/circle-plus.svg" width="20" height="20"> Create New Event

Press the '+' icon in the upper right of the Event listing page to open the Create New Event page.

* Required fields:
  - Event Name
  - Start time
  - End time

Note: Start and End times are entered as UTC values, though their local equivalents are output for reference, and are rendered in local time throughout the UI.

* Optional fields:
  - Venue
  - Location
  - Type
  - Picture
  - Description

### Picture Field

Paste the URL of a custom picture file (.jpeg, .gif, .png) for use in your forward-facing Event and Calendar pages. Accepts MediaManager public URLs.

### Calendar Visibility

It is often desirable to keep an event hidden from attendees until you have completed setting it up.
Once you toggle the Calendar Visibility control to Yes, the Event will display in the Calendar, and other forward-facing pages.

### User Login Options

VisionStream Events are made available to your attendees via a VisionStream subdomain portal.
There are several different login scenarios you can employ at the attendee login screen to allow access to your content.

* Login Options:
  - Default
    - The default behavior once you have imported your attendees directly into your account, and prefer to restrict viewership to only those attendees. The attendee only has to enter their email address to gain access to your published event.
  - Allow Guest Login
    - Use this option if you wish to provide anonymous attendees the ability to add themselves to your attendee list.
      - Attendees will be required to authenticate themselves using a valid email address. 
  - Require Authentication
    - Requires ALL attendees to authenticate themselves ONE TIME before access is granted to an Event.
      - Offers heightened security by ensuring the attendee is actually who they claim to be. 

### Sponsorship

* This feature requires MediaManager

VisionStream offers you the ability to incorporate sponsorship collateral into your subdomain portal.
This collateral is in the form of files, such as .pdf, image files, etc. These files are displayed when your attendee presses the 
Sponsor link. These files can then be downloaded and used for whatever purpose you had intended.

You will group these files together using various tagging strategies, and then create a Saved Search in MediaManager which you can then select in your VisionStream Event.

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/pen-to-square.svg" width="20" height="20"> Edit Event

You can edit any Event and change the values of any field.

## Event Toolbox View

The Event Toolbox view allows you to view the high-level components which comprise an event.

- Breakouts
- Usage
- Attendance
- Recordings

To enter the Event Toolbox view, click on any Event title in the Event listing page.

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/layer-group.svg" width="20" height="20"> Breakouts

To view all the breakouts associated with an Event, select the Breakouts control.

You will be navigated to a new page containing a listing which includes all the breakouts belonging to the event.

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/gauge-high.svg" width="20" height="20"> Usage

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

###  <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/users.svg" width="20" height="20"> Attendance

Attendance is automatically tracked for every breakout.

At the event level, Attendance is calculated as the cumulative attendance of all breakouts belonging to the event.

* View attendee table:
  - Name
  - Email
  - Country
  - Region
  - City

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/circle-play.svg" width="20" height="20"> Recordings

Every breakout is automatically recorded in VisionStream.

* Show Recordings feature allows admins the ability to see all recordings for any Event in a single view.
* Recordings are output both as HLS and MP4 (optional) format.
* Recordings can be viewed once a breakout has been completed.
* MP4 Recordings can be downloaded and saved by VisionStream admin users.
