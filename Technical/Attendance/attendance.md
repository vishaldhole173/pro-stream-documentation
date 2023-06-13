
# attendance


## Marking attendance

* First we update the socket information that user is attending breakout view stream page, and mark the entry points.

* User's ip address is fetched using socket, and with the help of this ip address we retrive and store user's city, region, country code, latitude and longitude in DB.

* With the help of socket we retrive and store user's browser, browser version and os in DB.

```
  async handleJoinChatRoomRequest(data, userDetails) {

    const breakoutId1 = this.getBreakoutId(data);
    const roomName = this.getRoomName(data);
    this.socket.join(roomName);
    redisService.subscribeToChannel(roomName);
    await redisService.updateSocketInfo(this.socketId, { breakoutId: breakoutId1 });
    await this.collectUserAnaytics(breakoutId1, userDetails);
    await this.sendLastComments(data);
    const socketInfo = await redisService.getSocketInfo(this.socketId);
    if (socketInfo) {
      const { userId, breakoutId } = socketInfo;
      if (breakoutId) {
        const clientIP = getClientIP(this.socket);
        const locationInfo = await IPGeoLocationService.getIPGeoLocation(clientIP);
        const userAgentInfo = parseUserAgent(this.socket);
        const sessionId = Utils.generateRandomString(10);
        this.socket.sessionId = sessionId;

      }
    }
  }
```

* When user joins the breakout, his current timestamp is recorded as entry_timestamp and stored in the DB.

* When breakout is over or user leaves the view stream page at that time, exit timestamp  is recorded as exit_timestamp in the DB using userId, breakoutId and sessionId as unique key.
```
  async handleLeaveChatRoomRequest(data) {
    
    const roomName = this.getRoomName(data);
    this.socket.leave(roomName);
    const socketInfo = await redisService.getSocketInfo(this.socketId);
    if (socketInfo) {
      const { userId, breakoutId } = socketInfo;
      if (breakoutId) {
        logger.trace('Recording User Exit');
        const sessionId = this.socket.sessionId;
        await AttendanceModel.recordUserExited(userId, breakoutId, sessionId);
      }
    }
    await redisService.updateSocketInfo(this.socketId, { breakoutId: undefined });
  }
```

* Inorder to mark the user's attendance we use userId, breakoutId and sessionId as unique key, and the entries of entry_timestamp and exit_timestamp related to that row in DB must be not null.