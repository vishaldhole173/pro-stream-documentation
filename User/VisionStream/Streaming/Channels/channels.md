# <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/tv.svg" width="20" height="20"> Channels

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20">  Overview

* A Channel is a fundamental object in the VisionStream platform
* Admin users can create one or more Channels for broadcasting
* A Channel must have a unique pipeline associated with it

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/plus.svg" width="20" height="20"> Create new channel

Press the '+' icon in the upper right of the Channels listing page to open the create new Channel page

* Required fields
  - Name
    - The name of channel which will be visible to the audience

* Optional fields
  - Publish Channel
    - Channels will display in the calendar if set to active
  - Pipeline
    - MediaLive channel which you want to use for broadcasting
  - Picture URL
    - Picture URL you want to display for your channel
  - Description
    - Additional information about your channel

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/video.svg" width="20" height="20"> Broadcast viewer

* If a pipeline is associated with the channel, you will see the Broadcast Viewer view
    - Channel status indicator
        - Used to view the status of a MediaLive channel
            - Idle channel status is designated by an amber icon
            - Starting channel status is designated by a blue icon
            - Running channel status is designated by a green icon
    - Cloudfront distribution status indicator
        - Used to view the status of a Cloudfront distribution
            - In progress Cloudfront distribution status is designated by an amber icon
            - Deployed Cloudfront distribution status is designated by a green icon
    - Cloudfornt switch
        - Used to make the audience only use the Cloudfront distribution playback URL
    - Show Stream Events
        - Used to get MediaLive channel events
    - Viewing
        - Shows the count of viewers watching the stream
    - Refresh Button
        - Used to reload the Stream Viewer
    - Video Player
        - Used to play the broadcasting content

* If Breakout is completed, you will see the `This stream has ended !` view
    - Show Files
        - Download media uploaded to the MediaManager
    - View Recording
        - Used to view the breakout recording
    - Comments
        - Comments are disabled once the breakout is completed
    - Job Status
        - Shows the MediaConvert job status which is either in progress or complete
        - MediaConvert job is responsible to generate the breakout recording
    - Copy S3 URI
        - Used to copy the S3 of the final recording on the clipboard


## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/calendar-check.svg" width="20" height="20"> Set channel schedule

Press the calendar icon in the upper right of the Broadcast viewer icon to open the create schedule page

* Required fields
  - Start Time
    - Time at which you want to start the broadcast
    - Start time should always be greater than the End time
    - Note that Start time is entered as UTC value, though the local equivalent is output for reference
  - End Time
    - Time at which you want to end the broadcast
    - Note that End time is entered as UTC value, though the local equivalent is output for reference
* Optional fields
  - Number of Loops
    - Number of times you want to repeat the broadcast content
  - Select Days
    - Weekly days on which you want to broadcast content

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/layer-group.svg" width="20" height="20"> Set channel content

* First create channel content to associate it with the broadcast channel
  - Give channel content some title to quickly identify and manage the content
  - Add a description if required
  - Associate a media file to the channel content
* Set channel content order using move content up or move content down buttons
* Broadcast content will play sequentially from top to bottom as per the channel content list

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/circle.svg" width="20" height="20"> Published channel indicator

* Published Channels are designated by a green icon
* Unpublished Channels are designated by an amber icon

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/trash.svg" width="20" height="20"> Delete channel

* Press the trash icon to the right of the published channel indicator on the Channels listing page to delete the channel
* The application typically prompts users to confirm their intention to delete the channel. This confirmation step is crucial as the action cannot be undone
* Once the user confirms the deletion, the application permanently deletes all channel content records associated with the selected channel
