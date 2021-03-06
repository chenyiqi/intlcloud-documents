The event callback feature sends TRTC event notification via HTTP/HTTPS requests to your server. Currently, callbacks are available for room events (`Room Event`) and media events (`Media Event`). Follow the directions below to configure callbacks in the TRTC console.

<span id="step0"></span>
## Prerequisites
1. Log in to the TRTC console and click **[Application Management](https://console.cloud.tencent.com/trtc/app)**.
2. Find the application for which you want to configure callbacks, and click **Application Info** in the **Operation** column on the right.
3. In the details page, click the **Callback Configuration** tab.


<span id="setkey"></span>
## Setting Callback Key
1. In the **Callback Key** section of the [**Callback Configuration**](#step0) tab, click **Edit**.
![](https://main.qcloudimg.com/raw/a4436b87393c8feb5dae143b99474958.png)
2. Enter a callback key (optional).
>? A callback key can contain up to 32 uppercase and lowercase letters and digits.
3. Click **Confirm** to complete the configuration.

<span id="setadd"></span>
### Setting Callback Address
1. In the **Callback Address** section of the [**Callback Configuration**](#step0) tab, click **Edit**.
![](https://main.qcloudimg.com/raw/756eafb5c850c8c45fad6f3e3aea3c12.png)
2. Enter a callback address (required).
	- Room event callback: supports sending notifications about creating/closing a room, entering/exiting a room, etc.
	- Media event callback: supports sending notifications about starting or stopping video/audio/substream data push, etc.
>? Protocols for callback URLs: HTTP and HTTPS; up to 2,083 characters
3. Click **Confirm** to complete the configuration.
