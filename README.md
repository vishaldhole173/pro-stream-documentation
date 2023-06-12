# Visionstream [https://visionstream.io](https://visionstream.io)

You get a custom built platform as an extension to your event. Regardless if your event is a solo guitar player streaming to their fans, or a multi-city conference with millions of attendees. Vision Stream supports it all.

## Channel Types
There are two types of channels that can be used to stream events. Channels abstract out the sequence of aws media services and other services being used to make streaming possible. These channels are named based on the underlying aws media service it uses. For example, Medialive channels use AWS Elemental medialive service at its core whereas IVS channels use AWS IVS channels. For Medialive channels, it requires a pipeline of aws media services to be spinned up whereas IVS is much simpler to set up compared to former one.

* [Medialive](Channel-Types/AWS-Elemental-MediaLive/Setup)
* [IVS](Channel-Types/Amazon-Interactive-Video-Service/Setup)

## Attendance
* [Attendance](Attendance/attendance.md)
* [Device Limit](Attendance/device-limit.md)

## Billing
* [Billing](Billing/billing.md)

## CloudFront Distributions
* [CloudFront Distributions](CloudFront-Distributions/CloudFront-Distributions.md)
* [Security](CloudFront-Distributions/security.md)

## Tenants
* [Tenants](Tenants/tenants.md)

## Database tables
1. [channels](Database/Tables/channels)
2. [inputs](Database/Tables/inputs)
3. [distributions](Database/Tables/distributions)
4. [recordings](Database/Tables/recordings)
5. [events](Database/Tables/events)
6. [breakouts](Database/Tables/breakouts)
7. [comments](Database/Tables/comments)
8. [survey](Database/Tables/survey)
9. [survey-reponse](Database/Tables/survey-reponse)
10. [payments](Database/Tables/payments)
11. [jobschedule](Database/Tables/jobschedule)
12. [external-clients](Database/Tables/external-clients)
13. [external-events](Database/Tables/external-events)
14. [users](Database/Tables/users)
15. [analytics](Database/Tables/analytics)
16. [attendance](Database/Tables/attendance)
17. [channel_stream_events](Database/Tables/channel_stream_events)
18. [tenants](Database/Tables/tenants.md)
