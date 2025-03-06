### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/layer-group.svg" width="20" height="20"> Breakouts

A breakout is a show, performance or presentation.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20">  Overview

A Breakout is a child of an Event. An Event (usually) consists of many Breakouts.

Admin users will create new Breakouts, entering name, date, time, duration and location of the livestream.

Breakout start time and duration should always be less than the Event end time.

## Breakout Listing View

The Breakout Listing view is the page you are navigated to when you click the Event name in the Event listing view.

This page will contain a listing of all the breakouts contained in the event.

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/calendar-check.svg" width="20" height="20"> Published vs. Hidden Breakouts

- Published Breakouts will display in calendars and other forward-facing pages.
- Unpublished Breakouts are hidden and cannot be accessed by an attendee.
- In the Breakout listing page:
    - Published Breakouts are designated by a calendar icon with a check mark.
    - Unpublished Breakouts are designated by a disabled (grey) calendar icon.

###  <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/video.svg" width="20" height="20"> Active vs. Completed Breakouts

- Active Breakouts are designated by a Video Camera icon which will display 'Active' when hovering over the icon.
- Completed Breakouts are designated by a disabled (grey) Video Camera icon which will display 'Completed' when hovering over the icon.

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/video.svg" width="20" height="20">  Stream Viewer

The Active Breakout Video Camera icon can be clicked on if the breakout is in the Active state, and doing so will navigate the user to the stream viewer.

[Read more to learn about the Stream Viewer...](../../Streaming/StreamViewer/stream-viewer.md)

###  <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/toggle-on.svg" width="20" height="20">  Hide Completed

Hide Completed Breakouts toggle allows you to quickly filter out breakouts which have already completed.
- You can filter Breakouts to show only the those currently in progress.
- Breakouts which have been completed will be removed from the list.
- Filter Breakouts setting persists over browser sessions.

## Breakout Details View

The Breakout Details view is where you enter details specific to your breakout.

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/circle-plus.svg" width="20" height="20">  Create New Breakout

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
        - Picture URL (see usage below).
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

### Picture Field

Paste the URL of a custom picture file (.jpeg, .gif, .png) for use in your forward-facing Breakout and Calendar pages. Accepts MediaManager public URLs.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/pen-to-square.svg" width="20" height="20">  Edit Breakout

You can edit any Breakout and change the values of any field, except:

* When a Breakout has completed, the following fields are disabled and cannot be changed:
    - Moderated Forum
    - Transcription
    - MP4 Recording
    - Pipeline
    - Source IP
    - Start Time
    - Hours, Minutes

You can change Charge Amount and Tip Jar to enable (or disable) the monetization process after a breakout has completed.

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/video.svg" width="20" height="20">  Show Stream Viewer

Stream Viewer is where you kick off, view, monitor and stop your livestreaming sessions.

[Read more to learn about the Stream Viewer...](../../Streaming/StreamViewer/stream-viewer.md)

## Breakout Subview Page

The Breakout Subview Page allows you to view the high-level components which comprise a breakout.

- Usage
- Attendance

To enter the Breakout Subview Page, click on any Breakout title.

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/gauge-high.svg" width="20" height="20"> Usage

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

### <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/users.svg" width="20" height="20">  Attendance

Attendance is automatically tracked for every breakout.

* View attendee table:
    - Name
    - Email
    - Country
    - Region
    - City
