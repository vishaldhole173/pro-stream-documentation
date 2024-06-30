# <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/user.svg" width="20" height="20"> Users

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20">  Overview

* Admin users can grant other admin users privileges, provided they are the account (root) owner.
* A user can be disabled / blocked from accessing VisionStream by the account owner.
* Demo users have limited privileges. Upon account upgrade, all privileges are granted.

## User basics

- ### There are 3 classes of VisionStream user:
  - #### Admin root user (Account owner)
  - #### Basic admin user
  - #### External user

### Admin root user

VisionStream root users are created through an onboarding process where the user will walk through several screens,
entering account information, service plan, terms and optional service preferences. Upon account creation,
the user will be granted all admin privileges and becomes the account owner & root user.

### Basic admin user

The account owner can invite other users to join the VisionStream account. These users are granted a subset of privileges,
which the account owner can change.

### External user

External users are usually imported directly into a VisionStream account, though they can be entered manually as well.
These users are essentially the attendees of an event, and can log in and view any breakout from any event offered by the account.

### Guest user

Any breakout can be setup to provide guest user access. In this scenario, a guest user can authenticate themselves using
2-factor authorization, and can then view any livestream presentation the account has to offer.

## Privileges

| Name             | Options             | Description                                       |
|------------------|---------------------|---------------------------------------------------|
| Accounts         | add, update         | User can add, update account records              |  
| Analytics        | view                | User can view analytics records                   |
| Attendance       | view                | User can view attendance records                  |  
| Breakouts        | add, update, delete | User can add, update, delete breakout records     |
| Channels         | add, update, delete | User can add, update, delete channel records      |  
| Distributions    | update, delete      | User can update, delete distribution records      |
| Events           | add, update, delete | User can add, update, delete event records        |  
| Forum Postings   | delete              | User can delete forum postings                    |
| Invoices         | view                | User can view invoice records                     |  
| Payments         | view                | User can view payment records                     |
| Pipelines        | add, update, delete | User can add, update, delete pipeline records     | 
| Platform         | view                | User can view platform data                       |
| Stream Event Log | view                | User can view stream event log records            |  
| Streaming        | start, abort, stop  | User can start, abort, stop a live stream session |
| Subdomains       | add, update, delete | User can add, update, delete sub-domain records   |  
| Usage            | view                | User can view usage data                          |
| Users            | view, update        | User can view, update, records                    |  
