## 1. 接口描述

接口：GetMonitorData
接口请求域名： `monitor.tencentcloudapi.com`

获取云产品的监控数据。传入产品的命名空间、对象维度描述和监控指标即可获得相应的监控数据。

接口调用频率限制为：20次/秒，1200次/分钟。 单请求最多可支持批量拉取10个实例的监控数据，单请求的数据点数限制为1440个。

若您需要调用的指标、对象较多，可能存在因限频出现拉取失败的情况，建议尽量将请求按时间维度均摊。

查询私有网络基础网络跨地域互联监控数据，入参取值如下：
&Namespace=QCE/PCX
&Instances.N.Dimensions.0.Name=peeringConnectionId
&Instances.N.Dimensions.0.Value 为基础网络跨地域互联 ID

## 2. 输入参数

以下请求参数列表仅列出了接口请求参数和部分公共参数，正式调用时需要加上公共请求参数，详情请参见 [公共请求参数](https://intl.cloud.tencent.com/document/product/248/33876#.E7.AD.BE.E5.90.8D.E6.96.B9.E6.B3.95-v1) 文档。

### 2.1输入参数

#### 2.1.1 输入参数总览

| 参数名称    | 是否必选 | 类型                                                         | 描述                                                         |
| :---------- | :------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| Action      | 是       | String                                                       | 公共参数，本接口取值：GetMonitorData                         |
| Version     | 是       | String                                                       | 公共参数，本接口取值： 2018-07-24                            |
| Region      | 否       | String                                                       | 公共参数，表示查询的是哪个地域实例的监控数据；可查看私有网络支持的 [地域列表](https://intl.cloud.tencent.com/document/product/215/15758) |
| Namespace   | 是       | String                                                       | 命名空间，每个云产品会有一个命名空间，如私有网络对等连接命名空间： QCE/PCX（API 3.0接口版本的必须是大写） |
| MetricName  | 是       | String                                                       | 指标名称，具体名称见2.2                                      |
| Instances.N | 是       | Array of [Instance](https://intl.cloud.tencent.com/document/product/248/33883) | 实例对象的维度组合                                           |
| Period      | 否       | Integer                                                      | 监控统计周期。默认为取值为300，单位为s                       |
| StartTime   | 否       | Timestamp                                                    | 起始时间，如"2016-01-01 10:25:00"。 默认时间为当天的”00:00:00” |
| EndTime     | 否       | Timestamp                                                    | 结束时间，默认为当前时间。 EndTime 不能小于 StartTime        |

#### 2.1.2 各维度对应参数总览

| 参数名称                       | 维度名称            | 维度解释                    | 格式                                             |
| :----------------------------- | :------------------ | :-------------------------- | :----------------------------------------------- |
| Instances.N.Dimensions.0.Name  | peeringConnectionId | 入参为基础网络跨地域互联 ID | 输入String 类型维度名称，如：peeringConnectionId |
| Instances.N.Dimensions.0.Value | peeringConnectionId | 具体的基础网络跨地域互联 ID | 输入基础网络跨地域互联具体 ID，如 ：pcx-086ypwc8 |

### 2.2 指标名称

每个指标对应的统计粒度（Period）及维度（dimension）可取值不一定相同，可通过 [DescribeBaseMetrics](https://intl.cloud.tencent.com/document/product/248/33882) 接口获取每个指标支持的统计粒度及维度信息。

| 指标名称     | 含义   | 单位  | 维度                |
| :----------- | :----- | :---- | :------------------ |
| Inpkg        | 入包量 | 个/秒 | peeringConnectionId |
| Inbandwidth  | 入带宽 | Mbps  | peeringConnectionId |
| Outpkg       | 出包量 | 个/秒 | peeringConnectionId |
| Outbandwidth | 出带宽 | Mbps  | peeringConnectionId |
| Pkgdrop      | 丢包率 | %     | peeringConnectionId |

## 3. 输出参数

| 参数名称   | 类型                  | 描述                                                         |
| :--------- | :-------------------- | :----------------------------------------------------------- |
| MetricName | String                | 监控指标                                                     |
| StartTime  | Timestamp             | 数据点起始时间                                               |
| EndTime    | Timestamp             | 数据点结束时间                                               |
| Period     | Integer               | 数据统计周期                                                 |
| DataPoints | Array of PointsObject | 监控数据列表                                                 |
| RequestId  | String                | 唯一请求 ID，每次请求都会返回。定位问题时需要提供该次请求的RequestId |

## 4. 错误码表

| 错误代码 | 错误描述       | 英文描述                             |
| :------- | :------------- | :----------------------------------- |
| -502     | 资源不存在     | OperationDenied.SourceNotExists      |
| -503     | 请求参数有误   | InvalidParameter                     |
| -505     | 参数缺失       | InvalidParameter.MissingParameter    |
| -507     | 超出限制       | OperationDenied.ExceedLimit          |
| -509     | 错误的维度组合 | InvalidParameter.DimensionGroupError |
| -513     | DB 操作失败    | InternalError.DBoperationFail        |

## 5. 示例

### 示例1

拉取某个私有网络基础网络跨地域互联某段时间内统计周期为60秒的入包量监控数据。

#### 输入示例



```
https://monitor.tencentcloudapi.com/?Action=GetMonitorData
&Namespace=QCE/PCX
&MetricName=Inpkg
&Period=60
&StartTime=2019-06-11T16:00:00+08:00
&EndTime=2019-06-11T16:05:00+08:00
&Instances.0.Dimensions.0.Name=peeringConnectionId
&Instances.0.Dimensions.0.Value=pcx-12345
&<公共请求参数>
```

#### 输出示例



```
{
  "Response": {
    "StartTime": "2019-06-11 16:00:00",
    "EndTime": "2019-06-11 16:05:00",
    "Period": 60,
    "MetricName": "Inpkg",
    "DataPoints": [
      {
        "Dimensions": [
          {
            "Name": "peeringConnectionId",
            "Value": "pcx-12345"
          }
        ],
        "Timestamps": [
          1560240000,
          1560240060,
          1560240120,
          1560240180,
          1560240240,
          1560240300
        ],
        "Values": [
          0,
          0,
          0,
          0,
          0,
          0
        ]
      }
    ],
    "RequestId": "e41e0928-0f62-4d2a-aa82-29b61dc19bd1"
  }
}
```

### 示例2

拉取多个私有网络基础网络跨地域互联某段时间内统计周期为60秒的入包量监控数据。

#### 输入示例



```
https://monitor.tencentcloudapi.com/?Action=GetMonitorData
&Namespace=QCE/PCX
&MetricName=Inpkg
&Period=60
&StartTime=2019-06-11T16:00:00+08:00
&EndTime=2019-06-11T16:05:00+08:00
&Instances.0.Dimensions.0.Name=peeringConnectionId
&Instances.0.Dimensions.0.Value=pcx-12345
&Instances.1.Dimensions.0.Name=peeringConnectionId
&Instances.1.Dimensions.0.Value=pcx-123456
&<公共请求参数>
```

#### 输出示例



```
{
  "Response": {
    "StartTime": "2019-06-11 16:00:00",
    "EndTime": "2019-06-11 16:05:00",
    "Period": 60,
    "MetricName": "Inpkg",
    "DataPoints": [
      {
        "Dimensions": [
          {
            "Name": "peeringConnectionId",
            "Value": "pcx-12345"
          }
        ],
        "Timestamps": [
          1560240000,
          1560240060,
          1560240120,
          1560240180,
          1560240240,
          1560240300
        ],
        "Values": [
          0,
          0,
          0,
          0,
          0,
          0
        ]
      },
      {
        "Dimensions": [
          {
            "Name": "peeringConnectionId",
            "Value": "pcx-123456"
          }
        ],
        "Timestamps": [
          1560240000,
          1560240060,
          1560240120,
          1560240180,
          1560240240,
          1560240300
        ],
        "Values": [
          0,
          0,
          0,
          0,
          0,
          0
        ]
      }
    ],
    "RequestId": "e41e0928-0f62-4d2a-aa82-29b61dc19bd1"
  }
}
```