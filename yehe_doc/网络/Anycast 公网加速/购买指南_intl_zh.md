>?
>- 目前 Anycast 公网加速处于内测中，如有需要，请提交 [内测申请](https://intl.cloud.tencent.com/apply/p/86ulv50u1e8)。
>- 目前仅支持如下地域开通 Anycast 公网加速：中国大陆、中国香港、日本、韩国、泰国、新加坡、印度、美国、俄罗斯、法兰克福。
## 计费说明
腾讯云 Anycast 公网加速服务的费用由两部分组成，包括公网网络费用和 IP 资源占用费用。
>?以下亚太地区包括中国香港、日本、韩国、泰国、新加坡、印度，北美地区包括美国，欧洲地区包括俄罗斯、法兰克福。

### 公网网络费用
Anycast 弹性公网 IP 产生的公网网络费用是按带宽收费，单价高于普通公网网络。将账户下所使用带宽的总曲线进行95消峰后，选择出带宽和入带宽中较高的方向收费，具体价格（单位：美元/Mbps/月）如下：
<table style="width:525px;">
<thead>
<tr>
<th style="width:207px !important;padding:7px;height:45px;position:relative;font-weight:700;" valign="top">
<div style="position:absolute;width:1px;height:213px;top:0;left:0;background-color: #d9d9d9;transform:rotate(-72deg);transform-origin:top;"></div><span style="width:98px -moz-available;display:block;padding-left:80px;">服务器所在地区</span><span style="width:98px -moz-available;display:block;padding-right:80px;padding-top:10px">公网出入口地区</span></th>

<th style="font-weight:700;width:80px;text-align:center;">中国大陆</th>
<th style="font-weight:700;width:80px;text-align:center;">亚太</th>
<th style="font-weight:700;width:80px;text-align:center;">北美</th>
<th style="font-weight:700;width:80px;text-align:center;">欧洲</th>
</tr>
</thead>
<tbody>
<tr>
<th style="font-weight:700;">中国大陆</th>
<td style="text-align:center;">18.86</td>
<td style="text-align:center;">-</td>
<td style="text-align:center;">-</td>
<td style="text-align:center;">-</td>
</tr>
<tr>
<th style="font-weight:700;">亚太</th>
<td style="text-align:center;">-</td>
<td style="text-align:center;">18.86</td>
<td style="text-align:center;">18.86</td>
<td style="text-align:center;">18.86</td>
</tr>
<tr>
<th style="font-weight:700;">北美    </th>
<td style="text-align:center;">-</td>
<td style="text-align:center;">18.86</td>
<td style="text-align:center;">18.86</td>
<td style="text-align:center;">18.86</td>
</tr>
<tr>
<th style="font-weight:700;">欧洲
</th>
<td style="text-align:center;">-</td>
<td style="text-align:center;">18.86</td>
<td style="text-align:center;">18.86</td>
<td style="text-align:center;">18.86</td>
</tr>
</tbody>
</table>

>?95消峰方式：按自然月结算，在一个自然月内取每5分钟有效带宽值的最大值进行降序排列，然后将带宽值最高的5%的点去掉，剩下的最高带宽就是95带宽峰值计费值。
>以一个月30天为例，默认均为有效取值点：每5分钟1个带宽取值点，每小时12个取值点，每月取值点数为12 × 24 × 30 = 8640个，将所有的点按带宽数值降序排列，去掉前5%的点：8640 × 5% = 432个点，即第433个点为计费点。

### Anycast 弹性公网 IP 的资源占用费
Anycast 弹性公网 IP 属于弹性公网 IP 的其中一种类型，未绑定实例的情况下会收取资源占用费。详情请参见 [IP 资源费用](https://intl.cloud.tencent.com/document/product/213/17156) 。

## 计费示例
假设您的账户下购买了以下多个 Anycast 弹性公网 IP，腾讯云对该账户下某月 Anycast 弹性公网 IP 产生的公网流量，按两端位置做聚合及95消峰后的带宽用量和价格如下：

| **服务器所在地区** | **公网出入口所在地区** | **带宽用量（单位：Mbps）** | **价格（单位：美元/Mbps/月）** |
| -------------- | ------------------ | --------------------- | ---------------------------- |
| 亚太           | 北美               | 10                    | 18.86                         |
| 亚太           | 中国大陆           | 100                   | 29.33                          |
| 欧洲           | 北美               | 200                   | 18.86                          |
| 亚太           | 亚太               | 300                   | 18.86                         |

最终收费 = 10 * 18.86 + 100 * 29.33 + 200 * 18.86 + 300 * 18.86 = 12551.60（美元）
