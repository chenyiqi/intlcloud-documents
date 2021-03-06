## 按量计费

按量计费实例，可随时登录 [云数据库 Redis 控制台](https://console.cloud.tencent.com/redis)，在实例列表单击【销毁】进行自助退还。



## 包年包月

为更方便您使用云数据库，如果您在购买包年包月云数据库后有任何不满意，我们支持以下两种自助退货退款。

 

- 5天无理由退还
- 普通自助退还

 

以上方式均可登录 Redis 控制台，在实例列表单击【退货退费】自助操作。

### 退还说明

1. 包年包月实例自助退还后，实例的状态一旦变为销毁中或已销毁时，就不再产生与该实例相关的费用。
2. 包年包月实例彻底销毁后 IP 资源同时释放，实例无法访问。
3. 包年包月实例自助退还后，实例被移入云数据库回收站保留七天，期间实例无法访问。如您想恢复已经自助退还的包年包月实例，可以在云数据库回收站进行续费恢复。
4. 如出现疑似异常/恶意退货，腾讯云有权拒绝您的退货申请。

 

### 5天无理由退还

如果您在购买云数据库后有任何不满意，我们支持5天内无理由自助退还。规则如下：

 

1. 云数据库 Redis 新购之日起5天之内（含5天），支持**1台**实例无理由退还，一个账号只有一次机会。

2. 如出现疑似异常/恶意退货，腾讯云有权拒绝您的退货申请。

3. 符合5天无理由退还场景的订单，退款金额为购买时花费的全部消耗金额，包括现金账户金额、收益转入账户金额以及赠送账户金额。 						

   >  								注意：
   >
   > - 抵扣或代金券不予以退还。
   >- 退还金额将全部原路退回到您的腾讯云账户。

 

### 普通自助退还

如果您已经享用5天无理由退还，我们还支持普通自助退还。规则如下：

 

1. 支持**199台**实例普通自助退还。
2. 普通自助退还将扣除您已使用的费用，退款金额将按购买使用的现金和赠送金支付比例返还到您的腾讯云账户。

 

**普通自助退还使用限制**
以下场景暂不支持普通包年包月实例自助退还：

 

1. 某些活动资源不支持自助退还，具体以官网展示为准。
2. Redis 标准版（引擎为 Redis 2.8）256MB的实例，暂时不支持控制台自助退还。

 

**普通自助退还计算规则**
**退款金额 = 当前有效订单金额 + 未开始订单金额 - 资源已使用价值**

 

当前有效订单金额：指生效中订单的付款金额，不包含折扣和代金券。
未开始订单金额：将来生效订单的付款金额，不包含代金券。
资源已使用价值按照如下策略计算：

 

- 已使用部分，发起退费当天已满整月按整月扣除，不满整月则按量计费扣除。
- 已使用部分精确到秒。
- 退款金额 ≤ 0，按0计算并清退资源。

  ​						

>  								注意： 							
>
> - 抵扣或代金券不予以退还。
>- 退还金额将按购买使用的现金和赠送金支付比例返还到您的腾讯云账户。

 						

### 退还计费示例

 						

>  								说明： 							
>
> 以下示例价格均为虚拟价格，实际价格请以官网为准。

 						

**5天无理由退还场景**
 广州二区规格2GB内存标准版，22美元/月，使用10美元代金券，购买1年，包年享83折。
折扣价为22 * 12 * 0.83  = 219.12美元
支付价为219.12 - 10 = 209.12美元
购买5天内发现不满意，想要退还，为该账户首次退还。
退费金额 = 实际支付价209.12美元

**普通自助退还场景**
广州二区规格2GB内存标准版，22美元/月，使用10美元代金券，购买1年，包年享83折。
折扣价为22 * 12 * 0.83 = 219.12美元
支付价为219.12 - 10 = 209.12美元


【示例1】：购买5天内，且不是该账户首次退还，总使用时长48小时。
退还现金金额 = 209.12 - 48 * 0.06（0.06美元为同样配置按量计费的单价）= 206.24美元


【示例2】：购买5天内，且不是该账户首次退还，已使用时长48小时；其中又续费1年，包年官网83折，续费实际支付金额219.12美元。
退还现金金额 = 209.12 - 48 * 0.06（0.06美元为同样配置按量计费的单价)（生效订单退款金额）+ 219.12美元（未开始订单金额） = 425.36美元

 

【示例3】：购买5天内，且不是该账户首次退还，已使用时长12小时后升级配置，升配实际支付金额10美元，总使用时长72小时。
退还现金金额 = 209.12 - 12 * 0.06（0.06为同样配置按量计费的单价）+ 10 / 365（升配的每天单价）*（365 - 3)（升配未使用天数）= 218.3178082美元