<span id="que1"></span>
###  桌面浏览器端 SDK 的支持哪些浏览器？	
目前主要在桌面版 Chrome 浏览器、桌面版 Edge 浏览器、桌面版 Firefox 浏览器、桌面版 Safari 浏览器以及移动版的 Safari 浏览器上有较为完整的支持，其他平台（例如 Android 平台的浏览器）支持情况均比较差，具体详情请参见 [支持的平台](https://intl.cloud.tencent.com/document/product/647/35143)。
您可以在浏览器打开 [WEBRTC 能力测试](https://trtc-1252463788.cos.ap-guangzhou.myqcloud.com/web/demo/env-detect/index.html) 测试是否完整的支持 WebRTC 的功能。

<span id="que2"></span>
###  实时音视频的桌面浏览器端、PC 端是不是同步的？
是的，实时音视频支持全平台互通。

<span id="que3"></span>
###  TRTC Native SDK有云端混流接口，桌面浏览器端怎么实现云端混流？
桌面浏览器端目前没有客户端接口，可以直接调用云直播的 [CreateCommonMixStream](https://intl.cloud.tencent.com/document/product/267/35997) 接口实现混流。

<span id="que4"></span>
###  运行桌面浏览器端 SDK 时，出现错误：“RtcError: no valid ice candidate found”该如何处理？

出现该错误说明 TRTC 桌面浏览器 SDK 在 STUN 打洞失败，请检查防火墙配置。TRTC 桌面浏览器 SDK 依赖以下端口进行数据传输，请将其加入防火墙白名单，配置完成后，您可以通过访问并体验 [官网 Demo](https://trtc-1252463788.file.myqcloud.com/web/demo/official-demo/index.html) 检查配置是否生效。
 - TCP 端口：8687
 - UDP 端口：8000，8080，8800，843，443，16285
 - 域名：qcloud.rtc.qq.com

<span id="que5"></span>
###  出现客户端错误："RtcError: ICE/DTLS Transport connection failed" 或 “RtcError: DTLS Transport connection timeout”该如何处理？
出现该错误说明 TRTC 桌面浏览器 SDK 在建立媒体传输通道时失败，请检查防火墙配置。TRTC 桌面浏览器 SDK 依赖以下端口进行数据传输，请将其加入防火墙白名单，配置完成后，您可以通过访问并体验 [官网 Demo](https://trtc-1252463788.file.myqcloud.com/web/demo/official-demo/index.html) 检查配置是否生效。
 - TCP 端口：8687
 - UDP 端口：8000，8080，8800，843，443，16285
 - 域名：qcloud.rtc.qq.com


<span id="que6"></span>
###  实时音视频桌面浏览器端的截图功能如何实现？
截图功能使用的是实例 HTMLVideoElement 中的 HTMLVideoElement.takeSnapshot。
``` 
/*
 * params:
 *   DeviceObject device
 * return:
 *   null
 */
    var video = document.getElementById(""video"")
    video.takeSnapshot(function(data){
        var img = document.createElement('img');
        img.src = data;
        $(""#some_div_id"").append( img );
    });
```

<span id="que7"></span>
###  桌面浏览器端 SDK 日志中报错 NotFoundError、NotAllowedError、NotReadableError、OverConstrainedError 以及 AbortError 分别是什么意思？


 | 错误名               | 描述                                                                                                                        | 处理建议                                                                                                                                                                                                                                                                                 |
 | -------------------- | --------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
 | NotFoundError        | 找不到满足请求参数的媒体类型（包括音频、视频、屏幕分享）。<br>例如：PC 没有摄像头，但是请求浏览器获取视频流，则会报此错误。 | 建议在通话开始前引导用户检查通话所需的摄像头或麦克风等设备，若没有摄像头且需要进行语音通话，可在 [TRTC.createStream({ audio: true, video: false })](https://trtc-1252463788.file.myqcloud.com/web/docs/TRTC.html?_ga=1.250015174.1562552652.1542703643#.createStream) 指明仅采集麦克风。 |
 | NotAllowedError      | 用户拒绝了当前的浏览器实例的访问音频、视频、屏幕分享请求。                                                                  | 提示用户不授权摄像头/麦克风访问将无法进行音视频通话。                                                                                                                                                                                                                                    |
 | NotReadableError     | 用户已授权使用相应的设备，但由于操作系统上某个硬件、浏览器或者网页层面发生的错误导致设备无法被访问。                        | 根据浏览器的报错信息处理，并提示用户“暂时无法访问摄像头/麦克风，请确保当前没有其他应用请求访问摄像头/麦克风，并重试”。                                                                                                                                                                   |
 | OverConstrainedError | cameraId/microphoneId 参数的值无效。                                                                                        | 请确保 cameraId/microphoneId 传值正确且有效。                                                                                                                                                                                                                                            |
 | AbortError           | 由于某些未知原因导致设备无法被使用。                                                                                        | -                                                                                                                                                                                                                                                                                        |


更多详情请参考 [initialize](https://trtc-1252463788.file.myqcloud.com/web/docs/LocalStream.html?#initialize)。


<span id="que8"></span>
###  桌面浏览器端 SDK 是否支持类似 enableSmallVideoStream 大小画面双路编码模式？	
目前暂时不支持。

<span id="que9"></span>
###  桌面浏览器端 SDK 在使用的过程中拔掉摄像头，怎么清除摄像头列表里面的数据？
可以尝试调用 [getCameras](https://trtc-1252463788.file.myqcloud.com/web/docs/TRTC.html?_ga=1.48566118.1562552652.1542703643#.getCameras) 方法是否能获取新的设备列表，如果仍然有拔掉的摄像头信息，说明浏览器底层也没有刷新这个列表，桌面浏览器端 SDK 也获取不到新的设备列表信息。

<span id="que10"></span>
###  桌面浏览器端 SDK 怎么录制纯音频推流？为什么在控制台开启自动旁路和自动录制录制不成功呢？	
需要设置 [createClient](https://trtc-1252463788.file.myqcloud.com/web/docs/TRTC.html?_ga=1.212323796.1562552652.1542703643#.createClient) 的 pureAudioPushMode 参数。

<span id="que11"></span>
###  桌面浏览器端 SDK 可以获取当前音量大小吗？
可以通过 [getAudioLevel](https://trtc-1252463788.file.myqcloud.com/web/docs/LocalStream.html?_ga=1.215278807.1562552652.1542703643#getAudioLevel) 获取当前音量大小。

<span id="que12"></span>
###  桌面浏览器端屏幕分享弹框的样式可以更改吗？	
桌面浏览器端屏幕分享弹框的样式是由浏览器控制的，Web 页面无法更改。

<span id="que13"></span>
###  桌面浏览器端用宽高设置推流的分辨率是所有浏览器都适用吗？
由于设备和浏览器的限制，视频分辨率不一定能够完全匹配，在这种情况下，浏览器会自动调整分辨率使其接近 Profile 对应的分辨率。详情可参考 [setVideoProfile](https://trtc-1252463788.file.myqcloud.com/web/docs/LocalStream.html?#setVideoProfile)。

<span id="que14"></span>
###  怎么确认桌面浏览器端 SDK 是否能正常获取到设备（摄像头/麦克风）列表？
1. 检查浏览器是否能够正常使用设备：
直接在页面打开控制台，输入`navigator.mediaDevices.enumerateDevices()`确认能否获取到设备列表。
 - 如果正常获取到设备会返回一个 Promise，里面会有 MediaDeviceInfo 对象数组，数组里的每个对象对应一个可用的媒体设备。
 - 如果枚举失败，Promise 将返回 rejected，说明浏览器都没有识别到设备，需检查浏览器或设备。
2. 如果能获取设备列表，则输入`navigator.mediaDevices.getUserMedia({ audio: true, video: true })`确认能否正常返回 MediaStream 对象，不能正常返回说明浏览器没有获取到数据，需检查浏览器的配置。

<span id="que15"></span>
###  桌面浏览器端的回声噪声问题怎么处理？
当其他端听到桌面浏览器端的声音存在回声、噪声、杂音等情况时，说明桌面浏览器端的 3A 处理没有生效。
WebRTC 标准提供了一套 3A 算法，可以通过指定 audio 的 MediaTrackConstrains 中的 AEC、ANS、AGC 开关控制 3A 的处理，当遇到回声、噪声、杂音、声音小等问题时，在桌面浏览器端的 localstream 中，creatStream 时，通过控制 echoCancellation、noiseSuppression、autoGainControl 这三个属性来分别控制回声消除、噪声抵制、音量增益。
如果出现下述情况，说明浏览器不兼容硬件设备，建议更换或检查设备。
- 如果 echoCancellation 设置为 true，依然存在回声问题。
- 如果 noiseSuppression 设置为 true，依然存在背景噪声。
- 如果 autoGainControl 设置为 true，依然存在声音偏小。

更多详情可参见 [媒体追踪约束](https://developer.mozilla.org/zh-CN/docs/Web/API/MediaTrackConstraints)。






<span id="que17"></span>
###  Windows 端怎么采集到被分享应用播放的声音？
通过调用 [startSystemAudioLoopback](https://intl.cloud.tencent.com/document/product/647/35131) 接口，可打开系统声音采集。

<span id="que18"></span>
###  Windows 会议模式中，如何实现主播对观众发起音视频连线的功能？
需要搭配另一个云产品 [即时通信 IM](https://intl.cloud.tencent.com/document/product/1047/33996) 达成连线需求。

呼叫的大致逻辑为：A 给 B 发送自定义消息 X 并唤起呼叫页面，X 展示效果自行处理，B 接收到 X 后调起被呼叫页面，B 单击 [enterRoom](https://intl.cloud.tencent.com/document/product/647/35131) 进入房间，并发送自定义消息 X1 给 A，A 收到 X1（自行决定是否展示）同时调用 enterRoom 进入房间。使用 IM 来发送自定义消息。

<span id="que19"></span>
###  观众如何查看房间里连线的画面？
当观众使用直播模式时，观众进入房间观看会通过 TRTCCloudDelegate 中的 [onUserVideoAvailable](http://doc.qcloudtrtc.com/group__ITRTCCloudCallback__cplusplus.html#a091f1c94ff1e2bc39c36e9d34285e87a) 回调获知主播的 userid（连麦的人也会 [enterRoom](http://doc.qcloudtrtc.com/group__ITRTCCloud__cplusplus.html#ac73c4ad51eda05cd2bcec820c847e84f) 进房，对于观众来说也是主播）。然后观众可以调用[startRemoteView](http://doc.qcloudtrtc.com/group__ITRTCCloud__cplusplus.html#a33a6e3765d6ca52d572224bc6e25dbcb) 方法来显示主播的视频画面。
更多详细操作，请参见  [跑通直播模式(Windows)](https://intl.cloud.tencent.com/document/product/647/35109) 。

<span id="que20"></span>
### Web 端是否可以监听远端离开房间？
支持监听远端退房事件，建议使用客户端事件中的 [client.on('peer-leave')](https://trtc-1252463788.file.myqcloud.com/web/docs/module-Event.html) 事件实现远端用户退房通知。
