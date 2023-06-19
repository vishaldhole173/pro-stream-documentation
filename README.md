# Visionstream [https://visionstream.io](https://visionstream.io)

You get a custom built platform as an extension to your event. Regardless if your event is a solo guitar player streaming to their fans, or a multi-city conference with millions of attendees. Vision Stream supports it all.

## Events
* [Events](User/VisionStream/Manage/Events/events.md)

## Breakouts
* [Breakouts](User/VisionStream/Manage/Breakouts/breakouts.md)

## Subdomains
* [Subdomains](User/VisionStream/Manage/Subdomains/subdomains.md)

## Users
* [Users](User/VisionStream/Manage/Users/users.md)

## Account
* [Account](User/VisionStream/Manage/Accounts/accounts.md)

## Platform
* [Platform](User/VisionStream/Admin/Platform/platform.md)

## Chats
* [Chats](User/VisionStream/Admin/Chats/chats.md)

## Channels
* [Channels](User/VisionStream/Streaming/Channels/channels.md)

## Live Stream
* [Live Stream](User/VisionStream/Streaming/LiveStream/live-stream.md)

## Pipelines
* [Pipelines](User/VisionStream/Streaming/Pipelines/pipelines.md)

## Distributions
* [Distributions](User/VisionStream/Admin/Distributions/distributions.md)

## Attendance
* [Attendance](User/VisionStream/Streaming/Attendance/attendance.md)

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

## Database tables
1. [channels](Technical/Database/Tables/channels)
2. [inputs](Technical/Database/Tables/inputs)
3. [distributions](Technical/Database/Tables/distributions)
4. [recordings](Technical/Database/Tables/recordings)
5. [events](Technical/Database/Tables/events)
6. [breakouts](Technical/Database/Tables/breakouts)
7. [comments](Technical/Database/Tables/comments)
8. [survey](Technical/Database/Tables/survey)
9. [survey-reponse](Technical/Database/Tables/survey-reponse)
10. [payments](Technical/Database/Tables/payments)
11. [jobschedule](Technical/Database/Tables/jobschedule)
12. [external-clients](Technical/Database/Tables/external-clients)
13. [external-events](Technical/Database/Tables/external-events)
14. [users](Technical/Database/Tables/users)
15. [analytics](Technical/Database/Tables/analytics)
16. [attendance](Technical/Database/Tables/attendance)
17. [channel_stream_events](Technical/Database/Tables/channel_stream_events)
18. [tenants](Technical/Database/Tables/tenants.md)
