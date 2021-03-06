## 概述

完全正则模式指将一条完整日志按正则方式提取多个 key-value 的日志解析模式，若不需要提取 key-value，请参阅 [单行全文采集](https://cloud.tencent.com/document/product/614/17421) 或 [多行全文采集](https://cloud.tencent.com/document/product/614/17422) 进行配置。配置完全正则模式，您需先输入日志样例，其次自定义正则表达式，系统将根据正则表达式里的捕获组提取对应的 key-value。下面将为您详细介绍如何采集完全正则格式日志。

### 示例

假设您的一条日志原始数据为：

```shell
10.135.46.111 - - [22/Jan/2019:19:19:30 +0800] "GET /my/course/1 HTTP/1.1" 127.0.0.1 200 782 9703 "http://127.0.0.1/course/explore?filter%5Btype%5D=all&filter%5Bprice%5D=all&filter%5BcurrentLevelId%5D=all&orderBy=studentNum" "Mozilla/5.0 (Windows NT 10.0; WOW64; rv:64.0) Gecko/20100101 Firefox/64.0"  0.354 0.354
```

配置的自定义正则表达式为：

```shell
(\S+)[^\[]+(\[[^:]+:\d+:\d+:\d+\s\S+)\s"(\w+)\s(\S+)\s([^"]+)"\s(\S+)\s(\d+)\s(\d+)\s(\d+)\s"([^"]+)"\s"([^"]+)"\s+(\S+)\s(\S+).*
```

则日志服务会根据`()`捕获组提取对应的 key-value，您可以自定义每组的 key 名称，如下所示。

```shell
body_bytes_sent: 9703
http_host: 127.0.0.1
http_protocol: HTTP/1.1
http_referer: http://127.0.0.1/course/explore?filter%5Btype%5D=all&filter%5Bprice%5D=all&filter%5BcurrentLevelId%5D=all&orderBy=studentNum
http_user_agent: Mozilla/5.0 (Windows NT 10.0; WOW64; rv:64.0) Gecko/20100101 Firefox/64.0
remote_addr: 10.135.46.111
request_length: 782
request_method: GET
request_time: 0.354
request_url: /my/course/1
status: 200
time_local: [22/Jan/2019:19:19:30 +0800]
upstream_response_time: 0.354
```

> !完全正则目前只支持单行日志提取 key-value ，多行日志暂不支持提取，如需采集多行日志请参阅 [多行全文采集](https://cloud.tencent.com/document/product/614/17422) 文档。

## 采集配置

### 1. 登录控制台

登录 [日志服务控制台](https://console.cloud.tencent.com/cls)，在左侧导航栏中，单击【日志集管理】。

### 2. 新增日志主题

选择目标日志集，单击【新增日志主题】，并输入日志主题名称 test-whole ，单击【确定】，即可新增日志主题。 
![](https://main.qcloudimg.com/raw/ea3533f032c4eda28e3f4fa9c6f4c1f6.png)

### 3. 配置 LogListener 采集

单击 LogListener 采集的日志主题，在采集配置界面中单击右上角【编辑】，进入编辑模式，开启【采集状态】和【使用 LogListener】。
![](https://main.qcloudimg.com/raw/277b43f1db32451b340522f10d442c16.png)

### 4. 配置日志文件采集路径

日志采集路径格式为 **[目录前缀表达式]**/\*\*/**[文件名表达式]** ，LogListener 会按照 **[目录前缀表达式]** 匹配所有符合规则的公共前缀路径，并监听这些目录（包含子层目录）下所有符合 **[文件名表达式]** 规则的日志文件，参数详细说明如下：

| 字段     | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| 目录前缀 | 日志文件前缀目录结构，仅支持通配符 \* 和 ? ，\* 表示匹配多个任意字符，? 表示匹配单个任意字符 |
| 文件名   | 日志文件名，仅支持通配符 \* 和 ? ，\* 表示匹配多个任意字符，? 表示匹配单个任意字符 |

填写示例：

| 序号 | 目录前缀表达式 | 文件名表达式 | 说明                                                         |
| ---- | -------------- | ------------ | ------------------------------------------------------------ |
| 1.   | /var/log/nginx | access.log   | 此例中，日志路径配置为`/var/log/nginx/**/access.log`，LogListener 将会监听`/var/log/nginx`前缀路径下所有子目录中以`access.log`命名的日志文件 |
| 2.   | /var/log/nginx | \*.log       | 此例中，日志路径配置为 `/var/log/nginx/**/*.log`，LogListener 将会监听`/var/log/nginx`前缀路径下所有子目录中以 `.log` 结尾的日志文件 |
| 3.   | /var/log/nginx | error\*      | 此例中，日志路径配置为`/var/log/nginx/**/error*`，LogListener 将会监听`/var/log/nginx`前缀路径下所有子目录中以`error`开头命名的日志文件 |

>!
>1. 多层目录和通配符配置方式依赖2.2.2及以上版本的 loglistener，为兼容低版本 loglistener 路径配置修改方式，用户可切换旧配置进行历史修改，旧采集路径方式不支持多目录采集。
>2. 一个日志文件只能被一个日志主题采集。
>3. LogListener 不支持监听软连接方式的日志文件和 NFS、CIFS 等共享文件目录上的日志文件。

### 5. 关联机器组

从机器组列表中选择目标机器组，将其与当前日志主题进行关联，关联的机器组与日志主题所在的地域需保持一致。更多详情请参阅 [如何创建机器组](https://cloud.tencent.com/document/product/614/17412#.E5.88.9B.E5.BB.BA.E6.9C.BA.E5.99.A8.E7.BB.84)。
![](https://main.qcloudimg.com/raw/8ee36a4acdbb5301c41634b88a51c075.png)

### 6. 配置完全正则模式

【键值提取模式】请选择**完全正则**，如下图所示：

![](https://main.qcloudimg.com/raw/79786db542d1171f3d66fb972d104d28.png)

#### 6.1 定义正则表达式

在完全正则模式下，系统将根据定义好的正则表达式提取 key-value，单击【自动生成】完成正则提取模式。如果无法自动生成，可以切换成手动方式进行正则模式验证。
- 自动模式
 a. 输入日志样例。
 b. 根据检索分析需要，将一部分日志内容选中，单击【分组】，成功分组后会特殊显示，表示该部分会作为一个 key-value 分组提取。
 c. 重复上述步骤 b，直到分组完所有需提取的 key-value。
 d. 单击【自动生成】，系统将日志分组生成正则提取模式。
![](https://main.qcloudimg.com/raw/7c12371d56bd21fa5ba068e84521444b.png)
- 手动模式
 a. 输入日志样例。
 b. 手动输入正则提取表达式。
 c. 单击【验证】，系统将判断日志样例与正则表达式是否匹配。
![](https://main.qcloudimg.com/raw/f893329dde3e5200d4eb3ec68aa683a0.png)
>?无论是自动模式还是手动模式，一旦正则提取模式定义好并验证通过后，提取结果将会展示在下方，您需要对每一组 key-value 对定义好一个 key 名称，该名称会用于日志检索分析。

### 7. 配置采集时间
- 日志时间单位为：秒。
- 日志的时间属性有两种方式来定义：采集时间和原始时间戳。
- 采集时间：日志的时间属性由日志服务 CLS 采集该条日志的时间决定。
- 原始时间戳：日志的时间属性由原始日志中时间戳决定。

#### 7.1 采集时间作为日志的时间属性

保持采集时间状态为开启状态即可，如下图所示：
![](https://i.imgur.com/t673Jlj.png)

#### 7.2 日志的原始时间戳作为日志时间属性

关闭采集时间状态，在时间键和时间格式解析出填写原始时间戳的时间键以及对应的时间解析格式，转换格式支持 strftime 的所有函数。
![](https://i.imgur.com/xgEroee.png)

下面举例说明时间格式解析规则填写：  
例1：日志样例原始时间戳：`10/Dec/2017:08:00:00`，解析格式为：`%d/%b/%Y:%H:%M:%S`。
例2：日志样例原始时间戳：`2017-12-10 08:00:00`，解析格式为：`%Y-%m-%d %H:%M:%S` 。
例3：日志样例原始时间戳：`12/10/2017, 08:00:00`，解析格式为：`%m/%d/%Y, %H:%M:%S`。

>!日志时间支持以秒为单位，若时间格式填写错误日志时间将以采集时间为准。

### 8. 设定过滤器条件

过滤器旨在您根据业务需要添加日志采集过滤规则，帮助您方便筛选出有价值的日志数据。对于分隔符格式日志，可以根据所解析成的键值对配置过滤规则，过滤规则为正则表达式。所创建的过滤规则为命中规则，即匹配上正则表达式的日志才会被采集上报。

例如：采集 errorcode = 400或500的日志数据，则将 key 配置为 errorcode，过滤规则配置为（400|500）。

### 9. 检索日志

登录 [日志服务控制台](https://console.cloud.tencent.com/cls)，在左侧导航栏中，单击【日志检索】，输入日志集与日志主题，单击【搜索】，即可开始按照设定的查询条件检索日志。
![](https://main.qcloudimg.com/raw/13b64f9282e1fa6128d81d8187f77b86.png)

> !检索必须开启索引配置，否则无法检索。
