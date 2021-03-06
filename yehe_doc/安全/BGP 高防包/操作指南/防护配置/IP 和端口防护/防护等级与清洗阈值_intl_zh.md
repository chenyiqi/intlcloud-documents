本文档将为您介绍针对 DDoS 攻击，DDoS 高防包提供的不同防护等级的相关操作及应用场景，并为您介绍如何在控制台中设置 DDoS 防护等级。
## 应用场景
DDoS 高防包服务提供防护策略调整功能，针对 DDoS 攻击提供三种防护等级供您选择，各个防护等级的具体防护操作如下：
<table>
    <tr>
        <th>防护等级</th>
        <th>防护操作</th>
				<th>描述</th>
    </tr>
    <tr>
        <td>宽松</td>
        <td><ul><li>过滤明确攻击特征的 SYN、ACK 数据包。</li>
                     <li>过滤不符合协议规范的 TCP、UDP、ICMP 数据包。</li>
                     <li>过滤具有明确攻击特征的 UDP 数据包。</li></ul></td>
				<td><li>清洗策略相对宽松，仅对具有明确攻击特征的攻击包进行防护。</li><li>建议在怀疑有误拦截时启用，遇到复杂攻击时可能会有攻击透传。</li></td>
    </tr>
    <tr>
        <td>适中</td>
        <td><ul><li>过滤明确攻击特征的 SYN、ACK 数据包。</li>
                     <li>过滤不符合协议规范的 TCP、UDP、ICMP 数据包。</li>
                     <li>过滤具有明确攻击特征的 UDP 数据包。</li>
                     <li>过滤常见基于 UDP 的攻击数据包。</li>
                     <li>对部分访问源 IP 进行主动验证。</li></ul></td>
				<td><li>清洗策略适配绝大多数业务，可有效防护常见攻击。</li><li>默认为适中模式。</li></td>
    </tr> 
		<tr>
        <td>严格</td>
        <td><ul><li>过滤明确攻击特征的 SYN、ACK 数据包。</li>
                     <li>过滤不符合协议规范的 TCP、UDP、ICMP 数据包。</li>
                     <li>过滤具有明确攻击特征的 UDP 数据包。</li>
                     <li>过滤常见基于 UDP 的攻击数据包。</li>
                     <li>对部分访问源 IP 进行主动验证。</li>
                     <li>过滤 ICMP 攻击包。</li>
                     <li>过滤常见的 UDP 攻击数据包。</li>
                     <li>UDP 数据包严格检查。</li></ul></td>
				<td>清洗策略相对严格，建议在正常模式出现攻击透传时使用。</td>
    </tr>
</table>

 >?
 >- 如果您的业务需要使用 UDP，建议您 [联系销售](https://intl.cloud.tencent.com/contact-sales) 进行策略定制，以免严格模式影响业务流程。
 >- 默认情况下，您所购买的 DDoS 高防包实例采用“适中”防护等级。

## 前提条件
您需要成功 [购买 DDoS 高防包](https://intl.cloud.tencent.com/document/product/1029/36115) ，并设置防护对象。

## 操作步骤
1. 登录 [DDoS 高防包（新版）管理控制台](https://console.cloud.tencent.com/ddos/antiddos-native/package)，在左侧导航中，单击【防护配置】。
2. 在左侧的列表选中高防包 ID，如“bgp-000000iu”，在右侧的顶部选中【IP 端口防护】。
3. 在右侧“DDoS 防护等级”卡片中，设置防护等级即可。

