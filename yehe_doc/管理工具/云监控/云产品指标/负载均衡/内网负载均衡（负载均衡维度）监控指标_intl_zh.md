## 命名空间

Namespace=QCE/LB_PRIVATE

## 监控指标

| 指标英文名 | 指标中文名 | 单位   |
| ---------------- | ----- | ---- |
| Connum           | 当前连接数 | 个    |
| NewConn         | 新增连接数 | 个/s |
| Intraffic        | 入流量   | Mbps |
| Outtraffic       | 出流量   | Mbps |
| Inpkg            | 入包量   | 个/s  |
| Outpkg           | 出包量   | 个/s  |

>每个指标对应的统计粒度（Period）可取值不一定相同，可通过 [DescribeBaseMetrics](https://intl.cloud.tencent.com/document/product/248/33882) 接口获取每个指标支持的统计粒度。

## 各维度对应参数总览

| 参数名称                       | 维度名称         | 维度解释                      | 格式                                                         |
| ------------------------------ | ---------------- | ----------------------------- | ------------------------------------------------------------ |
| Instances.N.Dimensions.0.name  | vip              | 负载均衡 VIP 的维度名称        | 输入String 类型维度名称：vip                                 |
| Instances.N.Dimensions.0.value | vip              | 负载均衡具体 VIP              | 输入具体 IP 地址，例如：111.111.111.11                       |
| Instances.N.Dimensions.1.name  | vpcId            | 私有网络 ID 的维度名称         | 输入 String 类型维度名称：vpcId                                |
| Instances.N.Dimensions.1.value | vpcId            | 负载均衡所在私有网络的具体 ID | 输入私有网络具体 ID，例如：1012345。需输入数值型 vpcId ，可参考 [根据证书ID查询负载均衡](https://intl.cloud.tencent.com/document/product/214/33800) 文档获取 NumericalvpcId |
| Instances.N.Dimensions.2.name  | loadBalancerPort | 负载均衡端口的维度名称        | 输入String 类型维度名称：loadBalancerPort                    |
| Instances.N.Dimensions.2.value | loadBalancerPort | 负载均衡的具体端口号          | 输入具体端口号，例如：80                                     |
| Instances.N.Dimensions.3.name  | protocol         | 协议维度名称                  | 输入String 类型维度名称：protocol                            |
| Instances.N.Dimensions.3.value | protocol         | 具体协议                      | 输入协议值具体名称，例如：http                              |


## 入参说明

内网负载均衡支持以下两种维度组合的查询方式，两种入参取值如下：

#### 1. 内网负载均衡维度，入参取值如下：

&Namespace=QCE/LB_PRIVATE
&Instances.N.Dimensions.0.Name=vip
&Instances.N.Dimensions.0.Value为 IP 地址
&Instances.N.Dimensions.1.Name=vpcId
&Instances.N.Dimensions.1.Value 为负载均衡所在私有网络的 ID

#### 2. 内网负载均衡端口维度，入参取值如下：

&Namespace=QCE/LB_PRIVATE
&Instances.N.Dimensions.0.Name=vip
&Instances.N.Dimensions.0.Value 为 IP 地址
&Instances.N.Dimensions.1.Name=vpcId
&Instances.N.Dimensions.1.Value 为负载均衡所在私有网络的 ID
&Instances.N.Dimensions.2.Name=loadBalancerPort
&Instances.N.Dimensions.2.Value 为端口号 
&Instances.N.Dimensions.3.Name=protocol
&Instances.N.Dimensions.3.Value 为协议类型
