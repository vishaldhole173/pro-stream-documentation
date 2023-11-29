# <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/cloud.svg" width="20" height="20"> Distributions

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20"> Overview

A distribution speeds up the distribution of your static and dynamic web content, such as .html, .css, .php, image, and media files.

When users request your content, a distribution delivers it through a worldwide network of edge locations that provide low latency and high performance.

## Status

* Deploying
    - The distribution is in the process of being provisioned and configured.
    - During this stage, AWS is setting up the necessary infrastructure and resources to enable content delivery.
    - Once the deployment is finished, the distribution status will change to 'Deployed'.
* Deployed
    - The distribution has been successfully provisioned and is currently active.
    - The associated resources, such as CDN edge servers or load balancers, are operational and ready to serve content to end-users.
    - This status indicates that the distribution is fully functional and delivering content as intended.

## Sync Distribution

* Used to synchronize or update the distribution status.
* The purpose of this button is to display the most up-to-date status of the distribution.
* This information is useful for monitoring availability of the distribution.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/scissors.svg" width="20" height="20">  Detach Distribution

* Used to disable a distribution and detach it from the MediaLive channel.
* Disabling the distribution means that it will no longer actively serve content to viewers.
* Detaching the distribution allows reconfiguring or assigning a new distribution to the channel if desired.

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/chevron-up.svg" width="20" height="20">  Show Distribution Config

* It allows users to toggle the visibility of the distribution configuration using a JSON viewer.
