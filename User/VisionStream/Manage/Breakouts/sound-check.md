# Getting Started with Sound Check

This feature is designed to give you peace of mind before your event goes live. It provides a private space where you can test your live stream, making sure your video and audio are coming through perfectly. You can monitor the stream's quality and health to catch any issues before your audience sees them.

---

### Before You Begin: A Quick Prerequisite

To access the Sound Check feature, your account needs to have the **`CanManagePipelines` permission**. If you do not have this permission, you will see a message stating: "You don't have permission to test sound check". If you believe you should have access, please contact your system administrator.

---

### How to Use Sound Check: A Step-by-Step Guide

Follow these steps to start, monitor, and end your stream test.

#### **Step 1: Start the Sound Check**

1.  Navigate to the Sound Check page from the main Stream Details page.
2.  Click the **"Init sound check"** button to begin.
3.  A confirmation box will pop up. When you confirm, the system will prepare a dedicated, secure channel for your test.

#### **Step 2: Connect Your Streaming Software**

Once the test channel is ready, the page will display a **Stream URL** and a **Stream Key**. Think of these as the unique address and password for your stream.

1.  Copy the **Stream URL** and **Stream Key** into your broadcasting software (like OBS, vMix, etc.). You can use the handy **`Copy`** button next to each field.
2.  For security, the Stream Key is hidden by default. Click the **"eye" icon** to make it visible.

``

#### **Step 3: Go Live and Monitor Your Stream**

1.  Start streaming from your broadcasting software.
2.  Once the system detects your feed, the **Stream Preview** player on the page will automatically start playing your live stream.
3.  Now you can monitor the feed using the tools on the page.

#### **Step 4: End Your Test**

1.  When you're satisfied with the test, simply **stop the stream** from your broadcasting software.
2.  After that, you can **navigate away** from the Sound Check page. The system will automatically end the session and clean everything up, making the test channel available for future use.

---

### Understanding the Monitoring Tools

The Sound Check page gives you several tools to check your stream's quality and stability.

``

- **Stream Preview**: This is the main video player where you can watch your live feed. It includes standard controls like play, pause, and volume.
- **Sound Meter**: Located to the right of the video player, this meter gives you a real-time visual of your audio levels. It helps you ensure your audio isn't too quiet (silent) or too loud (clipping).
- **Stream Health**: This dashboard shows key technical details about your stream's performance. The data refreshes automatically every 90 seconds, or you can click the refresh icon for the latest stats. Here's what the metrics mean in simple terms:
  - **Ingest Bitrate (bps)**: The amount of video and audio data you are sending to our servers. A stable, healthy number indicates a good connection.
  - **Ingest Frame Rate (fps)**: The smoothness of your video, measured in frames per second. This should match the settings in your streaming software (e.g., 30 fps).
  - **Keyframe Interval (seconds)**: A technical video setting. The system monitors this to ensure your stream is stable.
  - **Concurrent Views**: Shows how many people are watching the test stream. During a sound check, this will likely just be you!