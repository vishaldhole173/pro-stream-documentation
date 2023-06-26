# Visionstream [https://visionstream.io](https://visionstream.io)

You get a custom built platform as an extension to your event. Regardless if your event is a solo guitar player streaming to their fans, or a multi-city conference with millions of attendees. Vision Stream supports it all.

# VisionStream

## Manage

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/flag.svg" width="20" height="20"> [Events](User/VisionStream/Manage/Events/events.md)

    * [Breakouts](User/VisionStream/Manage/Breakouts/breakouts.md)

    * <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle-play.svg" width="20" height="20"> [Recordings](User/VisionStream/Manage/Breakouts/recordings.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/city.svg" width="20" height="20"> [Accounts](User/VisionStream/Manage/Accounts/accounts.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/user.svg" width="20" height="20"> [Users](User/VisionStream/Manage/Users/users.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/dollar-sign.svg" width="20" height="20"> [Payments](User/VisionStream/Manage/Payments/payments.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/rocket.svg" width="20" height="20"> [Subdomains](User/VisionStream/Manage/Subdomains/subdomains.md)

## Streaming

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle-plus.svg" width="20" height="20"> [Pipelines](User/VisionStream/Streaming/Pipelines/pipelines.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/chart-bar.svg" width="20" height="20"> [Analytics](User/VisionStream/Streaming/Analytics/analytics.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/calendar-check.svg" width="20" height="20"> [Attendance](User/VisionStream/Streaming/Attendance/attendance.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/tv.svg" width="20" height="20"> [Channels](User/VisionStream/Streaming/Channels/channels.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/flag.svg" width="20" height="20"> [Log](User/VisionStream/Streaming/Log/log.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/tower-broadcast.svg" width="20" height="20"> [Live Streams](User/VisionStream/Streaming/LiveStream/live-stream.md)

## Admin

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/user-plus.svg" width="20" height="20"> [Admin](User/VisionStream/Admin/admin.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/chart-line.svg" width="20" height="20"> [Platform](User/VisionStream/Admin/Platform/platform.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/cloud.svg" width="20" height="20"> [Distributions](User/VisionStream/Admin/Distributions/distributions.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/screwdriver-wrench.svg" width="20" height="20">  [Chats](User/VisionStream/Admin/Chats/chats.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/file-invoice-dollar.svg" width="20" height="20"> [Invoices](User/VisionStream/Admin/Invoices/invoices.md)

# MediaManager

## Find

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/heart.svg" width="20" height="20"> [Favorites](User/MediaManager/Find/Favorites/favorites.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/upload.svg" width="20" height="20"> [Recently Uploaded](User/MediaManager/Find/Recently-Uploaded/recently-uploaded.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/calendar.svg" width="20" height="20"> [Find by Date & Type](User/MediaManager/Find/Find-by-Date-and-Type/find-by-date-and-type.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/magnifying-glass.svg" width="20" height="20"> [Saved Searches](User/MediaManager/Find/Saved-Searches/saved-searches.md)

## Drives

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle-plus.svg" width="20" height="20"> [Create New Drive](User/MediaManager/Drives/Create-New-Drive/create-new-drive.md)

## Recent Projects

* [Show All Projects](User/MediaManager/Recent-Projects/All-Projects/all-projects.md)

## Recent Keywords

* [Show All Keywords](User/MediaManager/Recent-Keywords/All-Keywords/all-keywords.md)

## Usage

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/database.svg" width="20" height="20"> [Usage](User/MediaManager/Usage/Drives/drives.md)

* <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/circle-info.svg" width="20" height="20"> [Details](User/MediaManager/Usage/Details/drive-details.md)

# Technical

## Channel Types
There are two types of channels that can be used to stream events. Channels abstract out the sequence of aws media services and other services being used to make streaming possible. These channels are named based on the underlying aws media service it uses. For example, Medialive channels use AWS Elemental medialive service at its core whereas IVS channels use AWS IVS channels. For Medialive channels, it requires a pipeline of aws media services to be spinned up whereas IVS is much simpler to set up compared to former one.

* [Medialive](Technical/Channel-Types/AWS-Elemental-MediaLive/Setup)
* [IVS](Technical/Channel-Types/Amazon-Interactive-Video-Service/Setup)

## Attendance
* [Attendance](Technical/Attendance/attendance.md)
* [Device Limit](Technical/Attendance/device-limit.md)

## Billing
* [Billing](Technical/Billing/billing.md)

## CloudFront Distributions
* [CloudFront Distributions](Technical/CloudFront-Distributions/CloudFront-Distributions.md)
* [Security](Technical/CloudFront-Distributions/security.md)

## Tenants
* [Tenants](Technical/Tenants/tenants.md)
