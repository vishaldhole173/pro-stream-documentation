# <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/screwdriver-wrench.svg" width="20" height="20"> Failover

VisionStream employs a robust failover methodology for protecting your livestreams from failure.

## <img src="https://raw.githubusercontent.com/FortAwesome/Font-Awesome/6.x/svgs/solid/magnifying-glass-chart.svg" width="20" height="20"> Overview

MediaLive always creates two endpoints:
- If you set up the channel as a standard channel, both endpoints will be used.
- If you set up the channel as a single-pipeline channel, only the first endpoint will be used. MediaLive won't expect to receive content at the second endpoint.
  - In other words, if you are using Standard channel you can stream on all the endpoint urls provided by them.

<a href="https://docs.aws.amazon.com/medialive/latest/ug/input-create-rtmp-push.html" target="_blank">Read more about RTMP push inputs</a>

| Channel class | Number of Inputs | No of streaming endpoints available |
| ------ | ------ | ------ |
| Single Pipeline | 1 | 1 |
| Single Pipeline | 2 | 2 |
| Standard | 1 | 2 |
| Standard | 2 | 4 |

## About input failover

You can set up two push inputs as failover pairs. One input will be primary input and other will be the secondary input. Setting up input failover provides resiliency for the source, in case of failure between input and the channel.

**In our experience running hundreds of livestream events, internet-related issues at the host venue is the primary cause of streaming issues requiring a failover solution.**

### How does the channel decides failover between inputs?

You can configure the channel so that MediaLive detects one or more of the following problems in the input:
  - Black video (video failure) - MediaLive will perform a failover if content is considered black for the specified period.
  - Audio silence or audio failure – MediaLive will perform a failover if the specified audio selector is silent for the specified period.

Each input in the input pair provides content to the channel. One of the inputs is the active input and one is on standby. MediaLive ingests both inputs, in order to always be ready to switch, but it usually discards the standby input immediately.

If the active input fails, MediaLive immediately fails over and starts processing from the standby input, instead of discarding it.

## AWS SSM parameters

- ENABLE_MEDIALIVE_INPUT_FAILOVER
    - Description: Configure inputs as failover pairs or not.
    - Type: boolean
    - Default value: true
- MEDIALIVE_INPUT_PREFERENCE
    - Description: which input to give preference during switching.
    - Type: string
    - Default value: PRIMARY_INPUT_PREFERRED
    - Allowed values: EQUAL_INPUT_PREFERENCE, PRIMARY_INPUT_PREFERRED

## Failover configuration

You can check input failover configuration in the following file:
- Source: server/helpers/stream/lib/medialive/index.js
- Function name: buildInputAttachments

```
function buildInputAttachments(awsInputId1, awsInputId2) {
  const config = getConfigObj();
  const inputAttachments = [getDeafultInputAttachment(awsInputId1, 1)];

  if (awsInputId2) {
    inputAttachments.push(getDeafultInputAttachment(awsInputId2, 2));

    const inputFailOverEnabled = !!config.get(Config.ENABLE_MEDIALIVE_INPUT_FAILOVER);
    if (inputFailOverEnabled) {
      const inputFailoverSettings = {
        SecondaryInputId: awsInputId2,
        InputPreference: config.get(Config.MEDIALIVE_INPUT_PREFERENCE),
        ErrorClearTimeMsec: 30000,
        FailoverConditions: [
          {
            FailoverConditionSettings: {
              InputLossSettings: {
                InputLossThresholdMsec: 3000,
              },
            },
          },
        ],
      };
      inputAttachments[0].AutomaticInputFailoverSettings = inputFailoverSettings;
    }
  }
  return inputAttachments;
}
```

* ErrorClearTimeMsec:
  - This clear time defines the requirement a recovered input must meet to be considered healthy. The input must have no failover conditions for this length of time. Enter a time in milliseconds. This value is particularly important if the input_preference for the failover pair is set to PRIMARY_INPUT_PREFERRED, because after this time, MediaLive will switch back to the primary input (input-1).
  - Currently, we've hardcoded it to 30 seconds.

* FailoverConditions:
  - A list of failover conditions. If any of these conditions occur, MediaLive will perform a failover to the other input.

* InputLossSettings
  - MediaLive will perform a failover if content is not detected in this input for the specified period.
  - Currently, we've hardcoded it to 3 seconds.

## References
1. <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-medialive-channel-failoverconditionsettings.html" target="_blank">Failover Condition Settings</a>
2. <a href="https://docs.aws.amazon.com/medialive/latest/ug/automatic-input-failover.html" target="_blank">Implementing Automatic Input Failover</a>
3. <a href="https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-medialive-channel-automaticinputfailoversettings.html" target="_blank">Automatic Input Failover Settings</a>
