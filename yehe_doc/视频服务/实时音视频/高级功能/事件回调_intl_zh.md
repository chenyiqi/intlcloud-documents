事件回调服务支持将实时音视频业务下的事件，以 HTTP/HTTPS 请求的形式通知到您的服务器。事件回调服务已集成房间事件组（Room Event）和媒体事件组（Media Event）下的一些事件，您可以向腾讯云提供相关的配置信息来开通该服务。

<span id="deploy"></span>
## 配置信息
实时音视频 TRTC 控制台支持自助配置回调信息，配置完成后即可接收事件回调通知。


>!您需要提前准备以下信息：
>- **必要项**：接收回调通知的 HTTP/HTTPS 服务器地址。
>- **可选项**：计算签名的密钥 key，由您自定义一个最大32个字符的 key，以大小写字母及数字组成。

## 超时重试
事件回调服务器在发送消息通知后，5秒内没有收到您的服务器的响应，即认为通知失败。首次通知失败后会立即重试，后续失败会以**10秒**的间隔继续重试，直到消息存续时间超过1分钟，不再重试。

<span id="format)"></span>
## 事件回调消息格式

事件回调消息以 HTTP/HTTPS POST 请求发送给您的服务器，其中：

- 字符编码格式：UTF-8。
- 请求：body 格式为 JSON。
- 应答：HTTP STATUS CODE = 200，服务端忽略应答包具体内容，为了协议友好，建议客户应答内容携带 JSON： {"code":0}。


## 参数说明
<span id="message)"></span>
### 回调消息参数

- 事件回调消息的 header 中包含以下字段：
<table id="header">
<tr><th>字段名</th><th>值</th></tr></thead><tr>
<td>Content-Type</td><td>application/json</td>
</tr><tr>
<td>Sign</td><td>签名值</td>
</tr><tr>
<td>SdkAppId</td><td>sdk application id</td>
</tr></table>
- 事件回调消息的 body 中包含以下字段：
<table id="body">
<tr><th>字段名</th><th>类型</th><th>含义</th>
</tr><tr>
<td>EventGroupId</td><td>Number</td>
<td><a href="#eventId">事件组 ID</a></td>
</tr><tr>
<td>EventType</td>
<td>Number</td>
<td><a href="#event_type">回调通知的事件类型</a></td>
</tr><tr>
<td>CallbackTs</td>
<td>Number</td>
<td>事件回调服务器向您的服务器发出回调请求的 Unix 时间戳，单位为毫秒</td>
</tr><tr>
<td>EventInfo</td>
<td>JSON Object</td>
<td><a href="#event_infor">事件信息</a></td>
</tr>
</tbody></table>

<span id="eventId)"></span>
### 事件组 ID

| 字段名            | 值   | 含义       |
| ----------------- | ---- | ---------- |
| EVENT_GROUP_ROOM  | 1    | 房间事件组 |
| EVENT_GROUP_MEDIA | 2    | 媒体事件组 |

<span id="event_type)"></span>
### 事件类型

| 字段名                  | 值   | 含义             |
| ----------------------- | ---- | ---------------- |
| EVENT_TYPE_CREATE_ROOM  | 101  | 创建房间         |
| EVENT_TYPE_DISMISS_ROOM | 102  | 解散房间         |
| EVENT_TYPE_ENTER_ROOM   | 103  | 进入房间         |
| EVENT_TYPE_EXIT_ROOM    | 104  | 退出房间         |
| EVENT_TYPE_START_VIDEO  | 201  | 开始推送视频数据 |
| EVENT_TYPE_STOP_VIDEO   | 202  | 停止推送视频数据 |
| EVENT_TYPE_START_AUDIO  | 203  | 开始推送音频数据 |
| EVENT_TYPE_STOP_AUDIO   | 204  | 停止推送音频数据 |
| EVENT_TYPE_START_ASSIT  | 205  | 开始推送辅路数据 |
| EVENT_TYPE_STOP_ASSIT   | 206  | 停止推送辅路数据 |

<span id="event_infor)"></span>
### 事件信息

| 字段名  | 类型   | 含义                              |
| ------- | ------ | --------------------------------- |
RoomId      |     String/Number       |     房间名（类型与客户端房间号类型一致）    |
| EventTs | Number | 时间发生的 Unix 时间戳，单位为秒    |
| UserId  | String | 用户 ID                            |
| Role    | Number | [角色类型](#role_type)（option：进退房时携带）  |
| Reason  | Number | [具体原因](#reason) （option：进退房时携带） |

<span id="role_type)"></span>
### 角色类型

| 字段名             | 值   | 含义 |
| ------------------ | ---- | ---- |
| MEMBER_TRTC_ANCHOR | 20   | 主播 |
| MEMBER_TRTC_VIEWER | 21   | 观众 |

<span id="reason)"></span>
### 具体原因

| 字段名    | 含义                              |
| -------  | --------------------------------- |
|进房   |<li/>1：正常进房<li/>2：切换网络<li/>3：超时重试<li/>4：跨房连麦进房 |
|退房 | <li/>1：正常退房<li/>2：超时离开<li/>3：用户在其他终端加入，本地退出<li/>4：房间用户被删除<li/>5：取消连麦退房<li/>6：强杀|



### 计算签名
签名由 HMAC SHA256 加密算法计算得出，您的事件回调接收服务器收到回调消息后，通过同样的方式计算出签名，相同则说明是腾讯云的实时音视频的事件回调，没有被伪造。签名的计算如下所示：
```
//签名 Sign 计算公式中 key 为计算签名 Sign 用的加密密钥。
Sign = base64（hmacsha256(key, body)）
```



