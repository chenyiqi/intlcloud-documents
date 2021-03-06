## 免费额度

| 用户对象 | 免费期限         | 免费额度                                                     | 如何获取                                                     |
| -------- | ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 新用户   | 开通服务后半年内 | 免费享受 COS 提供的一定量的标准存储容量，详见 [免费额度](https://intl.cloud.tencent.com/document/product/436/6240) | 开通 COS 服务后系统自动发放，[前往开通](https://console.cloud.tencent.com/cos5) |

> !在使用免费额度期间内产生的低频存储/归档存储容量、请求、流量等非标准存储容量计费项，不属于免费范畴。


## 计费方式

对象存储 COS 的计费方式为按量计费，说明如下：

| 计费方式                                                     | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [按量计费（后付费）](https://intl.cloud.tencent.com/document/product/436/32534) | 该方式为 COS 默认计费方式，支持 [所有地域](https://intl.cloud.tencent.com/document/product/436/6224) |

## 产品定价

COS 产品定价按照**按量计费定价**。关于 COS 的具体价格，请参见 [产品定价](https://intl.cloud.tencent.com/document/product/436/6239)。


## 计费项
对象存储 COS 的计费项包括：存储容量费用、请求费用、数据取回费用、流量费用和管理功能费用，如下图所示。更多介绍请参见 [计费项](https://intl.cloud.tencent.com/document/product/436/33776)。


![](https://main.qcloudimg.com/raw/0fa513bdc13eca45712fb9db34d3b232.png)





## 计费周期

对象存储 COS 各项计费项的计费周期和计费顺序说明如下：

<table>
   <tr>
      <th colspan=2>计费项</td>
      <th>计费周期</td>
      <th>计费周期说明</td>
      <th>计费顺序</td>
   </tr>
   <tr>
      <td colspan=2>存储容量费用</td>
      <td>月</td>
      <td rowspan=4>每月1日对上月产生的费用进行结算扣费，3日到5日输出账单</td>
      <td>免费额度 > 按量计费，若无对应免费额度，则按量计费</td>
   </tr>
   <tr>
      <td rowspan=3>请求费用</td>
      <td>读写请求费用</td>
      <td rowspan=3>月</td>
      <td>按量计费</td>
   </tr>
   <tr>
      <td>深度归档取回请求费用</td>
      <td>按量计费</td>
   </tr>
   <tr>
      <td>智能分层对象监控费用</td>
      <td>按量计费</td>
   </tr>
   <tr>
      <td rowspan=3>数据取回费用</td>
      <td>低频数据取回费用</td>
      <td rowspan=2>月</td>
      <td rowspan=2>每月1日对上月产生的费用进行结算扣费，3日到5日输出账单</td>
      <td rowspan=2>按量计费</td>
   </tr>
   <tr>
      <td>归档数据取回费用</td>
   </tr>
   <tr>
      <td>深度归档数据取回费用</td>
      <td>日</td>
      <td>每日对上一日产生的费用进行结算，输出账单</td>
      <td>按量计费</td>
   </tr>
   <tr>
      <td colspan=2>流量费用</td>
      <td>日</td>
      <td>每日对上一日产生的费用进行结算，输出账单</td>
      <td>按量计费</td>
   </tr>
   <tr>
      <td rowspan=4>管理功能费用</td>
      <td>清单功能费用</td>
      <td>日</td>
      <td>每日对上一日产生的费用进行结算，输出账单</td>
      <td> 按量计费</td>
   </tr>
   <tr>
      <td>检索功能费用</td>
      <td>日</td>
      <td>每日对上一日产生的费用进行结算，输出账单</td>
      <td> 按量计费</td>
   </tr>
   <tr>
      <td>批量处理费用</td>
      <td>日</td>
      <td>每日对上一日产生的费用进行结算，输出账单</td>
      <td> 按量计费</td>
   </tr>
   <tr>
      <td>对象标签费用</td>
      <td>日</td>
      <td>每日对上一日产生的费用进行结算，输出账单</td>
      <td> 按量计费</td>
   </tr>
</table>





## 相关链接


1. 关于 COS 的费用详细计算及不同场景下的计费详情，请参见 [计费示例](https://intl.cloud.tencent.com/document/product/436/6241)。
2. 关于 COS 的欠费停服策略：数据的保留和销毁时间、以及相关计费说明，请参见 COS [欠费说明](https://intl.cloud.tencent.com/document/product/436/10044)。
3. 在按量计费方式下，用户可自行估算使用量，通过 COS [价格计算器](https://buy.cloud.tencent.com/price/cos/calculator) 计算具体的费用。
4. 若您对 COS 计费仍有疑问，可参见计费 [常见问题](https://intl.cloud.tencent.com/document/product/436/32532) 寻求答案。
