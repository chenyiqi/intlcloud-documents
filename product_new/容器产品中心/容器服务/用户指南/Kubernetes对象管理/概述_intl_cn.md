## 对象管理说明

您可以通过控制台直接操作原生 Kubernetes 对象，例如 Deployment、DaemonSet等。
Kubernetes 对象是集群中持久实体，用来承载集群内运行的业务。不同的 Kubernetes 对象可以表达不同的含义：
- 正在运行的应用程序
- 应用程序可用的资源
- 应用程序关联的策略等

您可以直接通过 TKE 控制台或者 Kubernetes API 使用 Kubernetes 的对象，例如 Kubectl。

## 对象分类

Kubernetes 常用对象主要分为以下类型：
- 工作负载
    + Deployment：用于管理指定调度规则的 Pod。
    + StatefulSet：管理应用程序的工作负载 API 对象，且该应用程序为有状态的应用程序。
    + DaemonSet：确保所有或部分节点上运行 Pod，例如日志采集程序。
    + Job：一个 Job 创建一个或多个 Pod，直至运行结束。
    + CronJob：定时运行的 Job 任务。
- 服务
    + Service：提供 Pod 访问的 Kubernetes 对象，可以根据业务需求定义不同类型。
    + Ingress：管理集群中 Services 的外部访问的 Kubernetes 对象。
- 配置
    + ConfigMap：用于保存配置信息。
    + Secret：用于保存敏感信息，例如密码、令牌等。
- 存储
    + Volume：可以存储容器访问相关的数据。
    + Persistent Volumes（PV）：Kubernetes 集群中配置的一块存储。
    + Persistent Volumes Claim（PVC）：请求存储的声明。如果把 PV 比作 Pod，那么 PVC 相当于工作负载。
    + StorageClass：用于描述存储的类型。 创建 PVC 时，通过 StorageClass 创建指定类型的存储，即存储的模板。

Kubernetes 对象还包括 Namespaces、HPA、Resource Quotas等数十种，您可以根据业务需要使用不同的 Kubernetes 对象。 不同版本的 Kubernetes 可使用的对象也不相同，更多说明可登录 [Kubernetes 官方网站](https://kubernetes.io/docs/concepts/) 查询。


## 资源限制

TKE 使用 ResourceQuota/tke-default-quota 对所有**托管集群**进行以下资源限制，如果您需要更多的配额项数量，请 [提交工单](https://console.cloud.tencent.com/workorder/category?level1_id=6&level2_id=350&source=0&data_title=%E5%AE%B9%E5%99%A8%E6%9C%8D%E5%8A%A1TKE&step=1) 进行申请。
<table>
	<tr>
	<th rowspan=2>集群规模</th>
	<th colspan=2>限制总量（单位：个）</th>
	</tr>
	<tr>
	<th>Pod</th>
	<th>ConfigMap</th>	
	<tr>
	<td>节点数 ≤ 5</td>
	<td>4000</td>
	<td>3000</td>
	</tr>	
	<tr>
	<td>5 < 节点数 ≤ 20 </td>
	<td>8000</td>
	<td>6000</td>
	</tr>	
	<tr>
	<td>节点数 > 20</td>
	<td>暂无限制</td>
	<td>暂无限制</td>
	</tr>
</table>


## 对象管理操作

- 工作负载
    + [Deployment 管理](https://intl.cloud.tencent.com/document/product/457/30662)
    + [StatefulSet 管理](https://intl.cloud.tencent.com/document/product/457/30663)
    + [DaemonSet 管理](https://intl.cloud.tencent.com/document/product/457/30664)
    + [Job 管理](https://intl.cloud.tencent.com/document/product/457/30665)
    + [CronJob 管理](https://intl.cloud.tencent.com/document/product/457/30666)
- 服务
    + [Service 管理](https://intl.cloud.tencent.com/document/product/457/30672)
    + [Ingress 管理](https://intl.cloud.tencent.com/document/product/457/30673)
- 配置
    + [ConfigMap 管理](https://intl.cloud.tencent.com/document/product/457/30675)
    + [Secret 管理](https://intl.cloud.tencent.com/document/product/457/30676)
- 存储
    + [Volumes 管理](https://intl.cloud.tencent.com/document/product/457/30678)
    + [Persisten Volumes 管理](https://intl.cloud.tencent.com/document/product/457/30679)
    + [Persisten Volumes Claim 管理](https://intl.cloud.tencent.com/document/product/457/30679)
    + [Storage Classes 管理](https://intl.cloud.tencent.com/document/product/457/30680)
