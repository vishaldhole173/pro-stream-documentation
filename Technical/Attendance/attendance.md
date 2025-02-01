# Calculating Attendance

Collecting attendance as a feature in VisionStream can greatly enhance the overall experience and provide numerous benefits. Here's how:

1. Seamless Attendance Tracking: VisionStream enables seamless tracking of attendance for virtual events. Attendees can easily log in to VisionStream, mark their presence, and participate in sessions. This eliminates the need for manual attendance management and ensures accurate tracking of attendee participation.

2. Data Insights: Attendance tracking provides valuable data insights to event organizers. They can gather information such as the number of attendees, their demographics, geographical distribution, and participation patterns. These insights help organizers understand their audience better, tailor future events to their preferences, and make data-driven decisions to improve event planning and execution.

3. Real-time Engagement Monitoring: VisionStream allows organizers to monitor attendee engagement in real time. They can track metrics such as active viewers, session duration, and interaction levels. This data provides valuable insights into attendee behavior and engagement patterns, enabling organizers to make timely adjustments to maximize participation and event success.

4. Personalized Experiences: With attendance data collected in VisionStream, organizers can deliver personalized experiences to attendees. By analyzing attendance history and preferences, organizers can recommend relevant sessions, networking opportunities, or resources tailored to each attendee's interests. This personalization enhances attendee satisfaction and fosters a more meaningful and engaging event experience.

5. Attendance Verification: VisionStream provides a reliable record for attendees to validate their participation in the event. By tracking attendance, VisionStream offers a verifiable attendance history that can be used for certification, continuing education credits, or professional development tracking.

6. Post-event Follow-up: Attendance tracking data in VisionStream helps organizers with post-event follow-up activities. They can identify highly engaged attendees, track their session preferences, and customize follow-up communications. This allows organizers to send personalized emails, share session recordings, and nurture leads generated during the event.

7. ROI Measurement: For event organizers and sponsors, measuring the return on investment (ROI) is vital. By tracking attendance, VisionStream provides valuable metrics for evaluating the success of an event. Organizers can analyze attendance numbers, engagement levels, attendee feedback, and other relevant data to assess the event's impact and make informed decisions for future events.

8. Analytics and Reporting: VisionStream enables comprehensive analytics and reporting. Organizers can analyze attendance trends, session popularity, viewer behavior, and overall event performance. These insights assist in evaluating event success, refining future strategies, and sharing key metrics with stakeholders.

In summary, collecting attendance in VisionStream enhances attendee experience, enables real-time engagement monitoring, facilitates personalized experiences, fosters networking and collaboration, provides attendance verification, supports post-event follow-up, and offers comprehensive analytics. These features contribute to the success of virtual events and enhance attendee satisfaction.

## How the attendance is collected in VisionStream?

User attendance is tracked using WebSocket connection to server. Here's how:

### Save user entry into the stream viewer page

1. User visits stream viewer page. Client sends `join-chat-room` socket message to server.
2. User WebSocket joins a socket.io room: `chat-room-${breakoutId}`. You can check implementation of `handleJoinChatRoomRequest` method of `AudienceRequestHandler`.

```
async handleJoinChatRoomRequest(data, userDetails) {
  ...
  const roomName = this.getRoomName(data);
  this.socket.join(roomName);
  ...
  await this.recordAttendance(breakoutId1, userDetails);
}
```

```
async recordAttendance(breakoutId, userDetails) {
    logger.trace('recordAttendance');
    const clientIP = getClientIP(this.socket);
    const locationInfo = await IPGeoLocationService.getIPGeoLocation(clientIP);
    // parse user agent to get metrics like device, browser, etc
    const userAgentInfo = parseUserAgent(this.socket);
    // Generate new sessionId to identify user logins on different devices.
    const sessionId = Utils.generateRandomString(10);
    await AttendanceModel.recordUserJoinedBreakout(
      userDetails.id,
      breakoutId,
      sessionId,
      locationInfo,
      userAgentInfo,
      this.socketId,
    );
    // Update socket info that user is attending breakout view stream page
    await redisService.updateSocketInfo(this.socketId, { breakoutId, sessionId });
  }
```

3. Collect some metrics about user - IP, browser, OS, device and user agent etc. using active WebSocket connection.
4. Generate a session id, a random string of length 10 to identify different active sessions of the user on different devices etc.
5. Save details into attendance database table.

### Save user exit from the stream viewer page

There are three ways that user can exit from stream viewer page.

1. Navigating to other page by means of clicking on some nav links in the top navbar or a back button.
2. Closing browser or a tab.
3. User device limit is reached.

```
async recordUserExit(activeSocketId) {
    const socketId = activeSocketId || this.socketId;
    logger.trace(`Recording User Exit for socketId ${socketId}`);
    const socketInfo = await redisService.getSocketInfo(socketId);
    if (socketInfo) {
      const { userId, breakoutId, sessionId } = socketInfo;
      if (breakoutId) {
        await AttendanceModel.recordUserExitedBreakout(userId, breakoutId, sessionId);
      }
    }
    // Update socket info that user has left breakout view stream page
    await redisService.updateSocketInfo(socketId, {
      breakoutId: undefined,
      sessionId: undefined,
    });
}
```

In a first case, when user navigate to other pages, we are sending another socket message to server: `leave-chat-room`. This event helps to know that user has exited from the stream viewer page by means of clicking on some links on page.

```
async handleLeaveChatRoomRequest(data) {
    logger.trace('handleLeaveChatRoomRequest');
    const roomName = this.getRoomName(data);
    this.socket.leave(roomName);
    await this.recordUserExit();
    await this.getViewerCount(data);
}
```

In a second case, there might be case that stream is completed or in between of event they would like to close browser or tab. In this case we are using WebSocket disconnect event to know that user has navigated away from the stream viewer page.

```
onSocketDisconnect() {
    this.recordUserExit();
}
```

In a third case, user is not allowed to view stream using stream viewer page because they are trying to view stream from the other device, browsers.

```
async expelUser(breakoutId, activeSocketId) {
    const socketId = activeSocketId || this.socketId;
    logger.trace(`expelUser breakoutId = ${breakoutId} socketId = ${socketId}`);
    const { webSocketId } = await redisService.getSocketInfo(socketId);
    if (webSocketId) {
      logger.trace('Sending playback command to: ', webSocketId);
      const socket = getClientSocket(webSocketId);
      socket.emit('playback', 'device-limit-exceeded');
      const roomName = getAudienceChatRoomName(breakoutId);
      socket.leave(roomName);
      await this.recordUserExit(socketId);
    }
}
```

Inorder to mark the user's attendance, we use userId, breakoutId and sessionId as unique key. Entry and exit timestamps are saved into the entry_timestamp and exit_timestamp columns.
