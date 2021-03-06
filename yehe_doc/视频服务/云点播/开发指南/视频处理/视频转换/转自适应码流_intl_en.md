Adaptive bitrate streaming refers to the process of transcoding a video and muxing it into adaptive bitstream for output. It involves audio/video files with various bitrates and a descriptive file (manifest). A player can dynamically select the most appropriate bitrate for playback based on the current bandwidth. The most widely used adaptive bitstream format is HLS in the [Master Playlist](https://developer.apple.com/documentation/http_live_streaming/example_playlists_for_http_live_streaming/creating_a_master_playlist) format.

VOD supports transcoding videos to adaptive bitstream in HLS format. This feature has the following benefits:
* The player can dynamically select the most appropriate bitrate for playback based on the current bandwidth, delivering a smooth viewing experience.
* Mainstream players natively support HLS adaptive bitstream with no customization required.
* VOD provides a [superplayer SDK](https://intl.cloud.tencent.com/document/product/266/7836) which can play back adaptive bitstreams quickly and conveniently after integration.

>! Differences between **adaptive bitrate streaming** and **transcoding**:
>- An adaptive bitrate streaming URL contains outputs in multiple resolutions, while a transcoding URL contains an output in only one resolution.
>- When adaptive bitstreams are played back, the player will switch to the optimal resolution under the current network conditions in real time, while videos output by transcoding do not support intelligent switch during playback.
>- The superplayer SDK provided by VOD supports playing back only outputs of adaptive bitrate streaming but not outputs of transcoding.
<span id = "zsy"></span>
## Adaptive Bitrate Streaming Template

The adaptive bitrate streaming parameters can specify "video transcoding parameter" and "audio transcoding parameter" of each substream. VOD uses an adaptive bitrate streaming template to represent the set of parameters as shown below:

| Parameter | Description |
| -- | -- |
| Container type | Adaptive bitstream format. Currently, only HLS is supported |
| Substream specification | Controls how many substreams are output and the video and audio transcoding parameters of each substream: <li>Video transcoding parameters: resolution, bitrate, frame rate, codec, etc.</li><li>Audio transcoding parameters: sample rate, sound channel, codec, etc.</li> |
| Whether to filter "low resolution to high resolution" | Generally, a source video with a low resolution cannot be converted to high resolution to improve the video and sound quality. Enabling filtering "low resolution to high resolution" can help avoid unnecessary transcoding |

For common parameter combinations, VOD provides a [preset adaptive bitrate streaming template](https://intl.cloud.tencent.com/document/product/266/33932), which cannot be customized for the time being.

## Task Initiation

There are three ways to initiate an adaptive bitrate streaming, namely, directly initiating through server API, directly initiating through the console, and specifying a task upon upload. For more information, please see [Task Initiation](https://intl.cloud.tencent.com/document/product/266/33931#OriginatingTask) for video processing.

Below are instructions for initiating adaptive bitrate streaming tasks in these ways:

* Call the server API [ProcessMedia](https://intl.cloud.tencent.com/document/product/266/34125) to initiate a task: specify the [adaptive bitrate streaming template](#zsy) ID in the `MediaProcessTask.AdaptiveDynamicStreamingTaskSet` parameter in the request.
* Initiate a task on a video through the console: call a [server API](https://intl.cloud.tencent.com/document/product/266/34167) to create a task flow, configure an adaptive bitrate streaming task in it (by specifying `MediaProcessTask.AdaptiveDynamicStreamingTaskSet`), and use it to [initiate video processing](https://intl.cloud.tencent.com/document/product/266/33892) in the console.
* Specify a task upon upload from server: call a [server API](https://intl.cloud.tencent.com/document/product/266/34167) to create a task flow, configure an adaptive bitrate streaming task in it (by specifying `MediaProcessTask.AdaptiveDynamicStreamingTaskSet`), and specify it as the `procedure` in the [ApplyUpload](https://intl.cloud.tencent.com/document/product/266/34120#2.-.E8.BE.93.E5.85.A5.E5.8F.82.E6.95.B0) request.
* Specify a task upon upload from client: call a [server API](https://intl.cloud.tencent.com/document/product/266/34167) to create a task flow, configure an adaptive bitrate streaming task in it (by specifying `MediaProcessTask.AdaptiveDynamicStreamingTaskSet`), and specify it as the `procedure` in the [signature for upload from client](https://intl.cloud.tencent.com/document/product/266/33922#p3).
* Upload through console: call a [server API](https://intl.cloud.tencent.com/document/product/266/34167) to create a task flow, configure an adaptive bitrate streaming task in it (by specifying `MediaProcessTask.AdaptiveDynamicStreamingTaskSet`), upload a video through the console, select **[Automatic Processing After Upload](https://intl.cloud.tencent.com/document/product/266/33890)**, and specify to execute this task flow upon video upload completion.

## Result Getting

After initiating an adaptive bitrate streaming task, you can wait for [result notification](https://intl.cloud.tencent.com/document/product/266/33931#ResultNotification) asynchronously or perform [task query](https://intl.cloud.tencent.com/document/product/266/33931#TaskQuery) synchronously to get the task execution result. Below is an example of getting the result notification in normal callback mode after the adaptive bitrate streaming task is initiated (the fields with null value are omitted):

```json
{
    "EventType":"ProcedureStateChanged",
    "ProcedureStateChangeEvent":{
        "TaskId":"1256768367-Procedure-2e1af2456351812be963e309cc133403t0",
        "Status":"FINISH",
        "FileId":"5285890784246869930",
        "FileName":"Animal World",
        "FileUrl":"http://1256768367.vod2.myqcloud.com/xxx/xxx/AtUCmy6gmIYA.mp4",
        "MetaData":{
            "AudioDuration":60,
            "AudioStreamSet":[
                {
                    "Bitrate":383854,
                    "Codec":"aac",
                    "SamplingRate":48000
                }
            ],
            "Bitrate":1021028,
            "Container":"mov,mp4,m4a,3gp,3g2,mj2",
            "Duration":60,
            "Height":480,
            "Rotate":0,
            "Size":7700180,
            "VideoDuration":60,
            "VideoStreamSet":[
                {
                    "Bitrate":637174,
                    "Codec":"h264",
                    "Fps":23,
                    "Height":480,
                    "Width":640
                }
            ],
            "Width":640
        },
        "MediaProcessResultSet":[
            {
                "Type":"AdaptiveDynamicStreaming",
                "AdaptiveDynamicStreamingTask":{
                    "Status":"SUCCESS",
                    "ErrCode":0,
                    "Message":"",
                    "Input":{
                        "Definition":10
                    },
                    "Output":{
                        "Definition":10,
                        "Package":"hls",
                        "DrmType":"",
                        "Url":"http://1256768367.vod2.myqcloud.com/xxx/xxx/adp.10.m3u8"
                    }
                }
            },
            {
                "Type":"AdaptiveDynamicStreaming",
                "AdaptiveDynamicStreamingTask":{
                    "Status":"SUCCESS",
                    "ErrCode":0,
                    "Message":"",
                    "Input":{
                        "Definition":20
                    },
                    "Output":{
                        "Definition":20,
                        "Package":"dash",
                        "DrmType":"",
                        "Url":"http://1256768367.vod2.myqcloud.com/xxx/xxx/adp.20.mpd"
                    }
                }
            }
        ],
        "TasksPriority":0,
        "TasksNotifyMode":""
    }
}
```

In the callback result, `ProcedureStateChangeEvent.MediaProcessResultSet` contains two adaptive bitstreams in `Type` of `AdaptiveDynamicStreaming`, where `Definition` is 10 and 20, respectively.
