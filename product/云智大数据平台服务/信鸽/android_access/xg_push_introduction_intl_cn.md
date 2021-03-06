# XG推送服务介绍
<hr>
信鸽（XG Push）是一款专业的移动 App 推送平台，支持百亿级的通知/消息推送，秒级触达移动用户，现已全面支持 Android 和 iOS 两大主流平台,开发者可以方便地通过嵌入 SDK，通过 API 调用或者Web端可视化操作，实现对特定用户推送，大幅提升用户活跃度，有效唤醒沉睡用户，并实时查看推送效果

## 信鸽推送流程原理介绍

![](/assets/xg流程图.png)

**简要说明Andoid客户端实现推送流程的步骤（不含厂商通道版本）：**


- 客户端 App 启动的时候会启动一个信鸽主 Service, 信鸽主 Service 全局唯一，一台设备共享一个信鸽主 Service

- 信鸽主 Service 在接入信鸽的应用中随机启动一个备份的 Service, 2 个Service相互拉活，互为备份

- 信鸽主 Service 建立一个信鸽服务器的 Socket 长连接，并通过心跳等机制维持长连接一直存在

- 客户端主 Service 通过 Socket 长连接请求向信鸽服务器请求 Token

- 信鸽服务器通过 Socket 长连接推送消息到客户端主 Service

- 主 Service 把 Push 消息转发到对应的客户端 APP 上


**简要说明Andoid客户端实现推送流程的步骤（含厂商通道版本）：**


- 发送注册请求到第三方厂商服务请求Token

- 保存第三方 Token 并同步到信鸽服务器

- 第三方 Token 和 信鸽 Token 建立映射关系并保存

- 信鸽服务器根据 Token 关系调用第三方推送的 API 推送消息到第三方服务器

- 第三方服务器推送消息到客户端 APP

## 主要功能说明

Andoid SDK 是信鸽推送服务为客户端实现消息推送⽽而提供给开发者的接⼝  
主要负责完成：

* 提供通知和消息二种推送形式，方便用户使用
* 账号、标签与设备的绑定接⼝口，以便便开发者实现特定群组的消息推送，丰富推送⽅方式；
* 点击量量上报，统计消息被⽤用户点击的次数；
* 提供通知和消息二种推送形式，方便用户使用
* 提供多厂商通道集成功能，方便用户集成多厂商推送



