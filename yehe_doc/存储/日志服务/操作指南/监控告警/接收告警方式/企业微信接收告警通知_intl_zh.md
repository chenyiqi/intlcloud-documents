本文介绍如何通过企业微信群接收告警通知。

## 相关限制
企业微信群消息发送频率限制：每个机器人发送的消息不能超过20条/分钟。若您的告警策略较多，建议多创建几个机器人，分散绑定告警策略。避免多个告警策略在同一时间触发告警时，导致您无法接收部分告警通知。

> !
> 您成功创建企业微信机器人和设置回调地址后，日志服务自动推送告警消息到企业微信机器人。您即可在企业微信群收到告警通知。

## 操作步骤
### 在企业微信添加机器人
#### PC 版
1. 在 PC 版企业微信中找到需要接收告警通知的企业微信群。
2. 选中并右键单击企业微信群，在弹框中单击【添加群机器人】。
3. 在弹框中单击【新创建一个机器人】。
4. 在弹框中自定义机器人名称，填写完后单击【添加机器人】。
5. 复制 Webhook 地址后，可参考 [配置告警接口回调](#return) 来配置接口回调。

#### Web 版
1. 在企业微信 Web 版中打开您需要接收告警通知的企业微信群。
2. 单击右上角的群设置图标。
3. 在群设置页面单击【群机器人】>【添加机器人】。
4. 在添加机器人管理页，自定义机器人名称。
5. 单击【添加】，复制 Webhook 地址后，可参考 [配置告警接口回调](#return) 来配置接口回调。

> !
> 如需配置企业微信群机器人，请参见 [企业微信—配置群机器人](https://work.weixin.qq.com/help?doc_id=13376)。
<span id="return"></span>
### 配置告警接口回调

在日志服务通知模版中，填写 Webhook 地址，单击【确定】即可。
配置成功后，当告警策略被触发时，您可以在企业微信群接收到群机器人发送的告警通知，如下图所示：

