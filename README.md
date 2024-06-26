# Visionstream [https://visionstream.io](https://visionstream.io)

You get a custom built platform as an extension to your event. Regardless if your event is a solo guitar player streaming to their fans, or a multi-city conference with millions of attendees. Vision Stream supports it all.

# VisionStream

## Manage

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/flag.svg" width="20" height="20"> [Events](User/VisionStream/Manage/Events/events.md)

    * [Breakouts](User/VisionStream/Manage/Breakouts/breakouts.md)

    * <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/circle-play.svg" width="20" height="20"> [Recordings](User/VisionStream/Manage/Breakouts/recordings.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/city.svg" width="20" height="20"> [Accounts](User/VisionStream/Manage/Accounts/accounts.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/user.svg" width="20" height="20"> [Users](User/VisionStream/Manage/Users/users.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/dollar-sign.svg" width="20" height="20"> [Payments](User/VisionStream/Manage/Payments/payments.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/rocket.svg" width="20" height="20"> [Subdomains](User/VisionStream/Manage/Subdomains/subdomains.md)

## Streaming

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/circle-plus.svg" width="20" height="20"> [Pipelines](User/VisionStream/Streaming/Pipelines/pipelines.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/chart-bar.svg" width="20" height="20"> [Analytics](User/VisionStream/Streaming/Analytics/analytics.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/calendar-check.svg" width="20" height="20"> [Attendance](User/VisionStream/Streaming/Attendance/attendance.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/tv.svg" width="20" height="20"> [Channels](User/VisionStream/Streaming/Channels/channels.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/flag.svg" width="20" height="20"> [Log](User/VisionStream/Streaming/Log/log.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/tower-broadcast.svg" width="20" height="20"> [Live Streams](User/VisionStream/Streaming/LiveStream/live-stream.md)

## Admin

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/user-plus.svg" width="20" height="20"> [Admin](User/VisionStream/Admin/admin.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/chart-line.svg" width="20" height="20"> [Platform](User/VisionStream/Admin/Platform/platform.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/cloud.svg" width="20" height="20"> [Distributions](User/VisionStream/Admin/Distributions/distributions.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/screwdriver-wrench.svg" width="20" height="20">  [Chats](User/VisionStream/Admin/Chats/chats.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/file-invoice-dollar.svg" width="20" height="20"> [Invoices](User/VisionStream/Admin/Invoices/invoices.md)

## Resources

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/blog.svg" width="20" height="20"> [Blogs](User/VisionStream/Resources/Blog/blog.md)

# MediaManager

## Find

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/heart.svg" width="20" height="20"> [Favorites](User/MediaManager/Find/Favorites/favorites.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/upload.svg" width="20" height="20"> [Recently Uploaded](User/MediaManager/Find/Find-by-Users/find-by-users.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/users.svg" width="20" height="20"> [Users](User/MediaManager/Find/Recently-Uploaded/recently-uploaded.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/calendar.svg" width="20" height="20"> [Find by Date & Type](User/MediaManager/Find/Find-by-Date-and-Type/find-by-date-and-type.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass.svg" width="20" height="20"> [Saved Searches](User/MediaManager/Find/Saved-Searches/saved-searches.md)

## Drives

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/circle-plus.svg" width="20" height="20"> [Create New Drive](User/MediaManager/Upload/upload.md)

## Recent Projects

* [Show All Projects](User/MediaManager/Projects/projects.md)

## Recent Keywords

* [Show All Keywords](User/MediaManager/Keywords/keywords.md)

## Usage

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/database.svg" width="20" height="20"> [Usage](User/MediaManager/Usage/Drives/drives.md)

* <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/circle-info.svg" width="20" height="20"> [Details](User/MediaManager/Usage/Details/drive-details.md)

# Technical

## Channel Types
There are two types of channels that can be used to stream events. Channels abstract out the sequence of aws media services and other services being used to make streaming possible. These channels are named based on the underlying aws media service it uses. For example, Medialive channels use AWS Elemental medialive service at its core whereas IVS channels use AWS IVS channels. For Medialive channels, it requires a pipeline of aws media services to be spinned up whereas IVS is much simpler to set up compared to former one.

* [Medialive](Technical/Pipeline-Types/AWS-Elemental-MediaLive/elemental-media-live.md)
    - [Automatic input failover configuration](Technical/Pipeline-Types/AWS-Elemental-MediaLive/Automatic-input-failover/automatic-input-failover-configuration.md)

    - [Automatic input failover in a single pipeline](Technical/Pipeline-Types/AWS-Elemental-MediaLive/Automatic-input-failover/automatic-input-failover-in-a-single-pipeline.md)

    - [Automatic input failover in a standard pipeline](Technical/Pipeline-Types/AWS-Elemental-MediaLive/Automatic-input-failover/automatic-input-failover-in-a-standard-pipeline.md)

    - [Manually forcing a failure](Technical/Pipeline-Types/AWS-Elemental-MediaLive/Automatic-input-failover/manually-forcing-a-failover.md.md)

* [IVS](Technical/Pipeline-Types/Amazon-Interactive-Video-Service/interactive-video-service.md)

## Attendance
* [Attendance](Technical/Attendance/attendance.md)

* [Device Limit](Technical/Attendance/device-limit.md)

## Billing
* [Billing](Technical/Billing/billing.md)

## CloudFront Distributions
* [CloudFront Distributions](Technical/CloudFront-Distributions/cloudfront-distributions.md)

* [CloudFront Security](Technical/CloudFront-Distributions/cloudfront-security.md)

* [Signed Cookies](Technical/CloudFront-Distributions/signed-cookies.md)

## Tenants
* [Tenants](Technical/Tenants/tenants.md)

## Deployment
* [Deployment](Technical/Deployment/deployment-overview.md)
