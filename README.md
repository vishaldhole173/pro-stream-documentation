# Visionstream [https://visionstream.io](https://visionstream.io)

You get a custom built platform as an extension to your event. Regardless if your event is a solo guitar player streaming to their fans, or a multi-city conference with millions of attendees. Vision Stream supports it all.

# User

## Manage

* [Events](User/VisionStream/Manage/Events/events.md)

    * [Breakouts](User/VisionStream/Manage/Breakouts/breakouts.md)

    * [Recordings](User/VisionStream/Manage/Breakouts/recordings.md)

* [Accounts](User/VisionStream/Manage/Accounts/accounts.md)

* [Users](User/VisionStream/Manage/Users/users.md)

* [Payments](User/VisionStream/Manage/Payments/payments.md)

* [Subdomains](User/VisionStream/Manage/Subdomains/subdomains.md)

## Streaming

* [Pipelines](User/VisionStream/Streaming/Pipelines/pipelines.md)

* [Analytics](User/VisionStream/Streaming/Analytics/analytics.md)

* [Attendance](User/VisionStream/Streaming/Attendance/attendance.md)

* [Channels](User/VisionStream/Streaming/Channels/channels.md)

* [Log](User/VisionStream/Streaming/Log/log.md)

* [Live Streams](User/VisionStream/Streaming/LiveStream/live-stream.md)

## Admin

* [Platform](User/VisionStream/Admin/Platform/platform.md)

* [Distributions](User/VisionStream/Admin/Distributions/distributions.md)

* [Chats](User/VisionStream/Admin/Chats/chats.md)

* [Invoices](User/VisionStream/Admin/Invoices/invoices.md)

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
