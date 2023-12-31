# <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/flag.svg" width="20" height="20"> Log

## <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/magnifying-glass-chart.svg" width="20" height="20"> Overview
- This feature allows you to view alerts and errors related to your event, which originate from the AWS services employed for streaming purposes.
- It proves to be a useful tool for monitoring the progress of your event and ensuring that everything is running smoothly.

## Reading the log file
- When you click on a specific log record, a pop-up box will appear displaying the following details:
    - Type: The category or classification of the log.
    - Timestamp: The exact time when the log was generated.
    - Name: The name associated with the log.
    - Breakout: The specific breakout for which the log was generated.
    - Details: A comprehensive message providing further information and explaining the log.

- Same details are provided on each log tile except Details. If you click on the breakout name provided on the log tile, it will redirect you to the edit breakout page.
- Additionally, you have the option to sort the logs based on Type, Event, Timestamp, and Breakout. Simply click on the respective titles in the topmost row to perform the sorting. 
- Furthermore, you can filter the records based on Type, Event, Timestamp, and Breakout by clicking on the magnifying glass icon at the beginning of each title in the topmost row. 
- You have the flexibility to utilize multiple filters simultaneously according to your preferences. For instance, you can apply filters such as Type and Event, or Type, Event, and Timestamp.
- The selected filters will be displayed at the top, accompanied by a cross icon at the end. To remove an applied filter, simply click on the cross icon associated with that specific filter.

- ### View Logs from the stream viewer page 
    To view the logs for a specific broadcast channel, follow these steps:
    - Navigate to the left side navigation bar and click on "Channels".
    - Click on Broadcast viewer icon ( <img src="https://raw.githubusercontent.com/vishaldhole173/pro-stream-documentation/main/fontawesome/svgs/solid/video.svg" width="20" height="20"> ).
    - In the HEALTH section, click on "Show stream events".
    - A pop-up dialog box will appear, displaying the logs related to the selected broadcast channel.
