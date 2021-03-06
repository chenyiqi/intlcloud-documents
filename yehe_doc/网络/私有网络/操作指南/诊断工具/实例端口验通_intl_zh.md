实例端口验通功能可以帮助您检测云服务器实例的安全组端口放通情况，定位故障所在，提升使用体验。
本功能提供常用端口和自定义端口的检测，常用端口如下表所示。
 <table>
<thead>
<tr>
<th>规则类型</th>
<th>端口</th>
<th>说明</th>
</tr>
</thead>
<tbody>
<tr>
<td rowspan="7">入站规则</td>
<td>ICMP 协议</td>
<td>用于提供网站 HTTP 服务。ICMP 为控制协议，不涉及端口号。</td>
</tr>
<tr>
<td>TCP:20</td>
<td rowspan="2">用于放通 FTP 服务的上传、下载。</td>
</tr>
<tr>
<td>TCP:21</td>
</tr>
<tr>
<td>TCP:22</td>
<td>用于放通 Linux SSH 登录。</td>
</tr>
<tr>
<td>TCP:3389</td>
<td>用于放通 Windows 远程登录。</td>
</tr>
<tr>
<td>TCP:443</td>
<td>用于提供网站 HTTPS 服务。</td>
</tr>
<tr>
<td>TCP:80</td>
<td>用于提供网站 HTTP 服务。</td>
</tr>


<tr>
<td>出站规则</td>
<td>ALL</td>
<td>用于放通所有出站流量，以访问外部网络。</td>
</tr>
</tbody></table>

## 操作指南
1. 登录 [私有网络控制台](https://console.cloud.tencent.com/vpc)。
2. 单击左侧目录下方的【诊断工具】>【实例端口验通】，进入管理页面。
3. 在页面上方选择【地域】，并在列表中，找到您要验证的实例所在行，单击【一键检测】。
<img src="https://main.qcloudimg.com/raw/04780280964c1d63698423b22ce764f5.png" width="80%" />
4. 您可以在弹窗中看到端口验通的详情，请根据实际情况选择执行如下操作。
   + 如不需要检测常用端口，可以取消勾选该条检测条目。
   + 如常用端口不满足检测要求，可在下方的自定义端口中输入需要检测的端口号，并单击【保存】。
      + 协议：可选择TCP或UDP。
      + 端口：输入需要验通的端口号，注意，端口号不可与常用端口号重复，如重复，需要取消勾选常用端口，再进行设置。
      + 方向：可选择入站或者出站。
      + IP：当方向为入站时，请填写输入源IP；当方向为出站时，请填写目的IP；所有来源或目的地址，请填写ALL。
      + 自定义端口检测最多支持15个。

 ![](https://main.qcloudimg.com/raw/c86ec2379a181fb6a210e72df5d7d73d.png)

5. 完成端口检查设置后，单击【开始检测】，【策略】列将展示检测结果。

 <img src="https://main.qcloudimg.com/raw/134efcaa4a488783d120e1a23079e0b8.png" width="60%" />

 如果您需要放通部分端口（例如 `TCP:22`），请在 [安全组控制台](https://console.cloud.tencent.com/vpc/securitygroup) 进入实例绑定的安全组，添加一条放通 `TCP:22` 端口的入站规则，可根据实际需求，在【来源】中默认选择 all 放通全部 IP，或填写指定 IP（IP 段），如下图所示。
![](https://main.qcloudimg.com/raw/6780b4df05168e19718ffe6c699c5159.png)

## 相关信息
- 如需了解安全组相关内容，请参见 [安全组概述](https://intl.cloud.tencent.com/document/product/215/38750)、 [添加安全组规则](https://intl.cloud.tencent.com/document/product/215/35513)。
- 如需了解服务器常用端口相关说明，请参见 [服务器常用端口](https://intl.cloud.tencent.com/document/product/215/35520)。
