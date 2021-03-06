### TPNS 应用的 AccessID、AccessKey、SecretKey 如何使用？
- AccessID：TPNS 应用的唯一标识。使用场景：1. SDK 集成；2. 调用 Rest API 时生成鉴权签名。
- AccessKey：TPNS 应用客户端鉴权密钥。使用场景：SDK 集成。
- SecretKey：TPNS 应用服务端鉴权密钥。使用场景：调用 Rest API 时生成鉴权签名。




### 为什么在华为应用市场发布应用，审核不通过？
请下载华为官方 HMS SDK，将 assets 目录下的所有文件及子目录，拷贝到开发者 App 工程的同名 assets 目录下。（如果目录不存在，请先创建）


### 努比亚机型无法收到推送？
不支持2015年后发布的努比亚机型，因为努比亚新的系统版本增加了超级省电的功能（会迅速将后台进程停止），移动推送 TPNS  Service 无法启动，所以努比亚机型无法注册成功。


### iOS 打包生产环境无法收到推送？
1. 生产环境的测试满足条件：App 是 ad-hoc 打包/App Store 版本（发布证书 Production），上传了发布证书并验证通过。
2. 请检查 Xcode 工程中配置的 bundle id，是否与设置的 Provision Profile 文件匹配，且对应 App 的 Provision Profile 文件是否已配置消息推送能力。
3. 检查 embedded.mobileprovision 文件中的 aps-environment 字段对应的环境是否正确。



###  生产环境推送收不到？
生产环境的测试满足条件：App 是 ad-hoc 证书打包或者发布证书（Production）打包，上传到 App Store 的版本。

### iOS Token 失效的原因？
- 系统注销或者是应用被卸载。
- 用户在新的设备上安装 App。
- 用户从 backup 中恢复设备。
- 用户重新安装 OS。
- 其他系统定义的事件。（调用 unregisterNotification 接口之后再注册通知，清除 device data and settings）

### 集成小米通道的设备，为什么只能显示一条推送消息？
小米官网文档指明：默认情况下，通知栏只显示一条推送消息。如果通知栏要显示多条推送消息，需要针对不同的消息设置不同的 notify_id（相同 notify_id 的通知栏消息会覆盖之前的消息）。移动推送 TPNS 官网的参数为：n_id。


### 通知栏展示消息的条数有限制吗？
手机接收并展示通知栏消息的条数没有限制，没有展示出来可能的原因是：
- 小米手机的通知栏消息是展示最新的一条，如果每条都要展示，需要设置 n_id。
- 消息广播被手机管家屏蔽。
- 魅族手机有一个消息盒子，一些不常用的消息会直接进入到消息盒子中，请在消息盒子中查看。


### 如何设置自定义铃声？

1. 管理台设置方法：选择【推送通知】 > 【高级设置】 > 【提醒方式】 > 【声音】 > 【自定义】（Android 选择位于 raw 目录下的铃声文件，铃声文件不需要后缀名，例如 xg_ring。iOS 选择 bundle 目录下的铃声文件，需要后缀名，例如 xg_ring.wav）
2. Rest API V3 设置方法： Android 在推送的消息体中设置 ring=1，同时设置 ring_raw 为指定 Android 工程里 raw 目录中的铃声文件名，不需要后缀名。iOS 在推送的消息体中设置 sound 为指定工程里 bundle 目录中的铃声文件名，需要后缀。

>!如客户端集成厂商通道，由于华为和魅族的厂商的限制，厂商手机无法使用自定义声音文件，默认使用系统音效；小米目前已经适配自定义铃声。


### 如何适配 small icon 小图标？

- 谷歌原生 Android 5.0 以上的 ROM 都会对 target sdk 大于等于21的 App 的小图标进行处理，增加一层颜色，导致图标变灰。
- 若需要显示颜色效果，可以将 target sdk 设成低于21；如果并不想将 target sdk 设成低于21，可以将一张背景透明的 png 格式小图片名称改成 notification_icon.png（资源名称不能被混淆），并放在 drawable 目录下，该方式显示的小图标即可为灰色（但是图标有形状）。
- TPNS Android SDK 1.2.2.0 起，默认情况下 notification_icon.png 小图标资源将仅在谷歌 Pixel 手机上直接生效；其他品牌手机若需实现此类自定义通知小图标效果，还需指定推送 API 字段 message.android.small_icon 为资源文件名称（不带文件后缀）；同时自定义通知小图标支持染色为单一纯色，需指定推送 API 字段 message.android.icon_color 为 RGB 颜色的十进制值。

推送 API 字段设置示例如下，其中 icon_color: 123456，即为 RGB 颜色 #01e240：
```
{
    "message": {
        "android": {
            "small_icon": "notification_icon",
            "icon_color": 123456
        }
    }
}
```

适配后的具体效果如下，建议参考 Demo logo 图标进行作图。

<img src="https://main.qcloudimg.com/raw/d9f92fb413aa98a01af64b2c17680bef.jpg" width="60%"></img>


>?
>- small icon 必须是带 Alpha 透明通道的 PNG 图片。
>- 背景必须是透明。
>- 周围不宜留过多 padding。
>- 建议统一使用46 x 46px，过小图片会模糊，过大系统会自动缩小。




### 应用关闭或结束进程后，还能收到推送消息吗？
- 移动推送 TPNS 通道推送主要依赖移动推送 TPNS 的 Service 进行消息的收发，停止进程后，移动推送 TPNS  Service 也被停止，只能等待 Service 重新启动才可以收到推送。若手机中有其他接入移动推送 TPNS 的 App 被打开，则可以利用其他 App 的 Service 接收消息，但共享 Service 通道也受手机 ROM 限制，无法保证百分之百的成功率。
- 厂商通道支持结束进程后收到推送消息。


### Android 版本4.4.4编译报错，怎么办？
由于工程加载方法数超过65K，请对工程做分包处理。



### 设备注册为什么收不到回调信息？
- 厂商通道的回调由厂商服务器返回。
- 检查是否有安全软件拦截广播。

### 为什么通过 API 创建的推送，查询不到推送记录？
登录 [移动推送 TPNS 控制台](https://console.cloud.tencent.com/tpns)，在【推送管理】>【推送任务】页面选择【API 创建】创建方式，即可展示API 创建的推送记录。
![](https://main.qcloudimg.com/raw/0319075f0a90f18592e33b0da9698e9c.png)


### 账号切换绑定设备，给这个账号发信息会怎么样？
设备 B 上能够收到推送，设备 A 无法收到推送。只有最后一个绑定该账号的设备可以收到推送。


### 指定打开某个 Activity 页面，但经常不能正常跳转？
在部分手机，通知栏跳转到某个页面可能会出现权限问题。
处理方法：在 androidManifest.xml 中，需要打开的 Activity 加上 android:exported="true"。


### 用户重连上线后收到多条 Push 的顺序是怎样？
按照消息 ID 递增。客户端也是按照此规则收取消息，因此，收消息的顺序就是发消息的顺序。

### 定时 Push 选择过去的时间，会 Push 出去吗？
会，选择过去的时间系统则会立刻发送。


### 注册方法能在线程中创建吗？
注册方法可以在任何地方调用，但注意要传递 ApplicationContext。


