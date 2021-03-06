## 简介

本文档提供关于跨域访问、生命周期、版本控制和跨地域复制相关的 API 概览以及 SDK 示例代码。

**跨域访问**

| API                                                          | 操作名       | 操作描述                     |
| ------------------------------------------------------------ | ------------ | ---------------------------- |
| [PUT Bucket cors](https://cloud.tencent.com/document/product/436/8279) | 设置跨域配置 | 设置存储桶的跨域访问权限     |
| [GET Bucket cors](https://cloud.tencent.com/document/product/436/8274) | 查询跨域配置 | 查询存储桶的跨域访问配置信息 |
| [DELETE Bucket cors](https://cloud.tencent.com/document/product/436/8283) | 删除跨域配置 | 删除存储桶的跨域访问配置信息 |

**生命周期**

| API                                                          | 操作名       | 操作描述                       |
| ------------------------------------------------------------ | ------------ | ------------------------------ |
| [PUT Bucket lifecycle](https://cloud.tencent.com/document/product/436/8280) | 设置生命周期 | 设置存储桶的生命周期管理的配置 |
| [GET Bucket lifecycle](https://cloud.tencent.com/document/product/436/8278) | 查询生命周期 | 查询存储桶生命周期管理的配置   |
| [DELETE Bucket lifecycle](https://cloud.tencent.com/document/product/436/8284) | 删除生命周期 | 删除存储桶生命周期管理的配置   |

**版本控制**

| API | 操作名 | 操作描述 |
| ------------------- | ------------ | ------------------ |
| [PUT Bucket versioning](https://cloud.tencent.com/document/product/436/19889) | 设置版本控制   | 设置存储桶的版本控制功能 |
| [GET Bucket versioning](https://intl.cloud.tencent.com/document/product/436/19888) | 查询版本控制 | 查询存储桶的版本控制信息 |

**跨地域复制**

| API | 操作名 | 操作描述 |
| ------------------- | ------------ | ------------------ |
| [PUT Bucket replication](https://cloud.tencent.com/document/product/436/19223) | 设置跨地域复制   | 设置存储桶的跨地域复制规则 |
| [GET Bucket replication](https://cloud.tencent.com/document/product/436/19222) | 查询跨地域复制 | 查询存储桶的跨地域复制规则 |
| [DELETE Bucket replication](https://cloud.tencent.com/document/product/436/19221) | 删除跨地域复制 | 删除存储桶的跨地域复制规则 |

## 跨域访问

### 设置跨域配置

#### 功能说明

设置指定存储桶的跨域访问配置信息（PUT Bucket cors）。

#### 方法原型

```java
public void setBucketCrossOriginConfiguration(String bucketName, BucketCrossOriginConfiguration bucketCrossOriginConfiguration);
```

#### 参数说明

| 参数名称                       | 描述                                                         | 类型                           |
| ------------------------------ | ------------------------------------------------------------ | ------------------------------ |
| bucketName                     | 存储桶的命名格式为 BucketName-APPID，详情请参阅 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String                         |
| bucketCrossOriginConfiguration | 设置的存储桶跨域策略                                         | BucketCrossOriginConfiguration |

#### 返回结果说明

- 成功：无返回值。
- 失败：发生错误（如身份认证失败），抛出异常 CosClientException 或者 CosServiceException。具体请参阅 [异常处理](https://intl.cloud.tencent.com/document/product/436/30599)。

#### 请求示例

[//]: # (.cssg-snippet-put-bucket-cors)
```java
// bucket的命名格式为 BucketName-APPID ，此处填写的存储桶名称必须为此格式
String bucketName = "examplebucket-1250000000";
BucketCrossOriginConfiguration bucketCORS = new BucketCrossOriginConfiguration();
List<CORSRule> corsRules = new ArrayList<CORSRule>();
CORSRule corsRule = new CORSRule();
// 规则名称
corsRule.setId("set-bucket-cors-test");
// 允许的 HTTP 方法
corsRule.setAllowedMethods(CORSRule.AllowedMethods.PUT, CORSRule.AllowedMethods.GET, CORSRule.AllowedMethods.HEAD);
corsRule.setAllowedHeaders("x-cos-grant-full-control");
corsRule.setAllowedOrigins("http://mail.qq.com", "http://www.qq.com", "http://video.qq.com");
corsRule.setExposedHeaders("x-cos-request-id");
corsRule.setMaxAgeSeconds(60);
corsRules.add(corsRule);
bucketCORS.setRules(corsRules);
cosClient.setBucketCrossOriginConfiguration(bucketName, bucketCORS);
```

### 查询跨域配置

#### 功能说明

查询指定存储桶的跨域访问配置信息（GET Bucket cors）。

#### 方法原型

```java
public BucketCrossOriginConfiguration getBucketCrossOriginConfiguration(String bucketName)
throws CosClientException, CosServiceException;
```

#### 参数说明

| 参数名称   | 描述                                                         | 类型   |
| ---------- | ------------------------------------------------------------ | ------ |
| bucketName | 存储桶的命名格式为 BucketName-APPID，详情请参阅 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String |

#### 返回结果说明

- 成功：返回存储桶的跨域规则。
- 失败：发生错误（如身份认证失败），抛出异常 CosClientException 或者 CosServiceException。具体请参阅 [异常处理](https://intl.cloud.tencent.com/document/product/436/30599)。

#### 请求示例

[//]: # (.cssg-snippet-get-bucket-cors)
```java
// bucket的命名格式为 BucketName-APPID ，此处填写的存储桶名称必须为此格式
String bucketName = "examplebucket-1250000000";
BucketCrossOriginConfiguration corsGet = cosClient.getBucketCrossOriginConfiguration(bucketName);
List<CORSRule> corsRules = corsGet.getRules();
for (CORSRule rule : corsRules) {
    List<CORSRule.AllowedMethods> allowedMethods = rule.getAllowedMethods();
    List<String> allowedHeaders = rule.getAllowedHeaders();
    List<String> allowedOrigins = rule.getAllowedOrigins();
    List<String> exposedHeaders = rule.getExposedHeaders();
    int maxAgeSeconds = rule.getMaxAgeSeconds();
}
```

### 删除跨域配置

#### 功能说明

删除指定存储桶的跨域访问配置（DELETE Bucket cors）。

#### 方法原型

```java
public void deleteBucketCrossOriginConfiguration(String bucketName)
throws CosClientException, CosServiceException;
```

#### 参数说明

| 参数名称   | 描述                                                         | 类型   |
| ---------- | ------------------------------------------------------------ | ------ |
| bucketName | 存储桶的命名格式为 BucketName-APPID，详情请参阅 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String |

#### 返回结果说明

- 成功：无返回值。
- 失败：发生错误（如身份认证失败），抛出异常 CosClientException 或者 CosServiceException。 具体请参阅 [异常处理](https://intl.cloud.tencent.com/document/product/436/30599)。

#### 请求示例

[//]: # (.cssg-snippet-delete-bucket-cors)
```java
//存储桶的命名格式为 BucketName-APPID
String bucketName = "examplebucket-1250000000";
cosClient.deleteBucketCrossOriginConfiguration(bucketName);
```

## 生命周期

### 设置生命周期

#### 功能说明

设置指定存储桶的生命周期配置信息（PUT Bucket lifecycle）。

#### 方法原型

```java
public void setBucketLifecycleConfiguration(String bucketName, BucketLifecycleConfiguration bucketLifecycleConfiguration) 
        throws CosClientException, CosServiceException;
```

#### 参数说明

| 参数名称                     | 描述                                                         | 类型                         |
| ---------------------------- | ------------------------------------------------------------ | ---------------------------- |
| bucketName                   | 存储桶的命名格式为 BucketName-APPID，详情请参阅 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String                       |
| bucketLifecycleConfiguration | 生命周期配置                                                 | BucketLifecycleConfiguration |

#### 返回结果说明

- 成功：无返回值。
- 失败：发生错误（如身份认证失败），抛出异常 CosClientException 或者 CosServiceException。具体请参阅 [异常处理](https://intl.cloud.tencent.com/document/product/436/30599)。

#### 请求示例

[//]: # (.cssg-snippet-put-bucket-lifecycle)
```java
List<BucketLifecycleConfiguration.Rule> rules = new ArrayList<BucketLifecycleConfiguration.Rule>();
// 规则1  30天后删除路径以 hongkong_movie/ 为开始的文件
BucketLifecycleConfiguration.Rule deletePrefixRule = new BucketLifecycleConfiguration.Rule();
deletePrefixRule.setId("delete prefix xxxy after 30 days");
deletePrefixRule.setFilter(new LifecycleFilter(new LifecyclePrefixPredicate("hongkong_movie/")));
// 文件上传或者变更后, 30天后删除
deletePrefixRule.setExpirationInDays(30);
// 设置规则为生效状态
deletePrefixRule.setStatus(BucketLifecycleConfiguration.ENABLED);

// 规则2  20天后沉降到低频，一年后删除
BucketLifecycleConfiguration.Rule standardIaRule = new BucketLifecycleConfiguration.Rule();
standardIaRule.setId("standard_ia transition");
standardIaRule.setFilter(new LifecycleFilter(new LifecyclePrefixPredicate("standard_ia/")));
List<BucketLifecycleConfiguration.Transition> standardIaTransitions = new ArrayList<BucketLifecycleConfiguration.Transition>();
BucketLifecycleConfiguration.Transition standardTransition = new BucketLifecycleConfiguration.Transition();
standardTransition.setDays(20);
standardTransition.setStorageClass(StorageClass.Standard_IA.toString());
standardIaTransitions.add(standardTransition);
standardIaRule.setTransitions(standardIaTransitions);
standardIaRule.setStatus(BucketLifecycleConfiguration.ENABLED);
standardIaRule.setExpirationInDays(365);

// 将两条规则添加到策略集合中
rules.add(deletePrefixRule);
rules.add(standardIaRule);

// 生成 bucketLifecycleConfiguration
BucketLifecycleConfiguration bucketLifecycleConfiguration =
        new BucketLifecycleConfiguration();
bucketLifecycleConfiguration.setRules(rules);

// 存储桶的命名格式为 BucketName-APPID
String bucketName = "examplebucket-1250000000";
SetBucketLifecycleConfigurationRequest setBucketLifecycleConfigurationRequest =
        new SetBucketLifecycleConfigurationRequest(bucketName, bucketLifecycleConfiguration);

// 设置生命周期
cosClient.setBucketLifecycleConfiguration(setBucketLifecycleConfigurationRequest);
```

### 查询生命周期

#### 功能说明

查询指定存储桶的生命周期（GET Bucket lifecycle）。

#### 方法原型

```java
public BucketLifecycleConfiguration getBucketLifecycleConfiguration(String bucketName)
throws CosClientException, CosServiceException;

```

#### 参数说明

| 参数名称   | 描述                                                         | 类型   |
| ---------- | ------------------------------------------------------------ | ------ |
| bucketName | 存储桶的命名格式为 BucketName-APPID，详情请参阅 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String |

#### 返回结果说明

- 成功：返回 BucketLifecycleConfiguration 类， 包含存储桶的生命周期规则。
- 失败：发生错误（如身份认证失败），抛出异常 CosClientException 或者 CosServiceException。具体请参阅 [异常处理](https://intl.cloud.tencent.com/document/product/436/30599)。

#### 请求示例

[//]: # (.cssg-snippet-get-bucket-lifecycle)
```java
// 存储桶的命名格式为 BucketName-APPID ，此处填写的存储桶名称必须为此格式
String bucketName = "examplebucket-1250000000";
BucketLifecycleConfiguration queryLifeCycleRet =
        cosClient.getBucketLifecycleConfiguration(bucketName);
List<BucketLifecycleConfiguration.Rule> ruleLists = queryLifeCycleRet.getRules();
```

### 删除生命周期

#### 功能说明

删除指定存储桶的生命周期（DELETE Bucket lifecycle）。

#### 方法原型

```java
public void deleteBucketLifecycleConfiguration(String bucketName)
throws CosClientException, CosServiceException;
```

#### 参数说明

| 参数名称   | 描述                                                         | 类型   |
| ---------- | ------------------------------------------------------------ | ------ |
| bucketName | 存储桶的命名格式为 BucketName-APPID，详情请参阅 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String |

#### 返回结果说明

- 成功：无返回值。
- 失败：发生错误（如身份认证失败），抛出异常 CosClientException 或者 CosServiceException。具体请参阅 [异常处理](https://intl.cloud.tencent.com/document/product/436/30599)。

#### 请求示例

[//]: # (.cssg-snippet-delete-bucket-lifecycle)
```java
//存储桶的命名格式为 BucketName-APPID
String bucketName = "examplebucket-1250000000";
cosClient.deleteBucketLifecycleConfiguration(bucketName);
```


## 版本控制
### 设置版本控制

#### 功能说明

设置指定存储桶的版本控制功能（PUT Bucket versioning）。

#### 方法原型
```java
public void setBucketVersioningConfiguration(SetBucketVersioningConfigurationRequest setBucketVersioningConfigurationRequest)
    throws CosClientException, CosServiceException;
```

#### 参数说明
| 参数名称                                | 描述                                                         | 类型                                    |
| --------------------------------------- | ------------------------------------------------------------ | --------------------------------------- |
| setBucketVersioningConfigurationRequest | 版本控制配置                                                 | SetBucketVersioningConfigurationRequest |


#### 返回结果说明
  - 成功：无返回值。
  - 失败：发生错误（如身份认证失败），抛出异常 CosClientException 或者 CosServiceException。详情请参阅 [异常处理](https://intl.cloud.tencent.com/document/product/436/30599)。

#### 请求示例

**开启版本控制**

[//]: # (.cssg-snippet-put-bucket-versioning)
```java
String bucketName = "examplebucket-1250000000";
// 开启版本控制
cosClient.setBucketVersioningConfiguration(
        new SetBucketVersioningConfigurationRequest(bucketName,
                new BucketVersioningConfiguration(BucketVersioningConfiguration.ENABLED)));
```

**暂停版本控制**

```java
String bucketName = "examplebucket-1250000000";
// 暂停版本控制
cosClient.setBucketVersioningConfiguration(
new SetBucketVersioningConfigurationRequest(bucketName,
new BucketVersioningConfiguration(BucketVersioningConfiguration.SUSPENDED)));
```

### 查询版本控制

#### 功能说明

查询指定存储桶的版本控制信息（GET Bucket versioning）。

#### 方法原型
```java
// 方法1 传入存储桶名称即可
public BucketVersioningConfiguration getBucketVersioningConfiguration(String bucketName)
            throws CosClientException, CosServiceException;

// 方法2 通过GetBucketVersioningConfigurationRequest 获取
public BucketVersioningConfiguration getBucketVersioningConfiguration(
    GetBucketVersioningConfigurationRequest getBucketVersioningConfigurationRequest)
        throws CosClientException, CosServiceException;
```

#### 参数说明

| 参数名称                                | 描述                                                         | 类型                                    |
| --------------------------------------- | ------------------------------------------------------------ | --------------------------------------- |
| bucketName                              | 存储桶的命名格式为 BucketName-APPID，详情请参阅 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String                                  |
| getBucketVersioningConfigurationRequest | 获取版本控制配置请求                                         | GetBucketVersioningConfigurationRequest |


#### 返回结果说明
- 成功：返回存储桶的多版本配置。
- 失败：发生错误（如身份认证失败），抛出异常 CosClientException 或者 CosServiceException。详情请参阅 [异常处理](https://intl.cloud.tencent.com/document/product/436/30599)。

#### 请求示例
[//]: # (.cssg-snippet-get-bucket-versioning)
```java
String bucketName = "examplebucket-1250000000";
// 获取版本控制
BucketVersioningConfiguration bvc =
        cosClient.getBucketVersioningConfiguration(bucketName);
// 获取版本控制
BucketVersioningConfiguration bvc2 = cosClient.getBucketVersioningConfiguration(
        new GetBucketVersioningConfigurationRequest(bucketName));
```

## 跨地域复制
### 设置跨地域复制

#### 功能说明

设置指定存储桶的跨地域复制规则（PUT Bucket replication）。

#### 方法原型

```java
public void setBucketReplicationConfiguration(
        SetBucketReplicationConfigurationRequest setBucketReplicationConfigurationRequest)
                throws CosClientException, CosServiceException;
```

#### 参数说明

| 参数名                                   | 参数描述                                                     | 类型                                     |
| ---------------------------------------- | ------------------------------------------------------------ | ---------------------------------------- |
| bucketName                               | 存储桶的命名格式为 BucketName-APPID，详情请参阅 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String                                   |
| setBucketReplicationConfigurationRequest | 跨地域复制配置                                               | SetBucketReplicationConfigurationRequest |

#### 返回结果说明

  - 成功：无返回值。
  - 失败：发生错误（如身份认证失败），抛出异常 CosClientException 或者 CosServiceException。详情请参阅 [异常处理](https://intl.cloud.tencent.com/document/product/436/30599)。

#### 请求示例

[//]: # (.cssg-snippet-put-bucket-replication)
```java
// 源存储桶名称，需包含 appid
String bucketName = "examplebucket-1250000000";

BucketReplicationConfiguration bucketReplicationConfiguration = new BucketReplicationConfiguration();
// 设置发起者身份, 格式为： qcs::cam::uin/<OwnerUin>:uin/<SubUin>
bucketReplicationConfiguration.setRoleName("qcs::cam::uin/100000000001:uin/100000000001");

// 设置目标存储桶和存储类型，QCS 的格式为：qcs::cos:[region]::[bucketname-AppId]
ReplicationDestinationConfig replicationDestinationConfig = new ReplicationDestinationConfig();
replicationDestinationConfig.setBucketQCS("qcs::cos:ap-beijing::destinationbucket-1250000000");
replicationDestinationConfig.setStorageClass(StorageClass.Standard);

// 设置规则状态和前缀
ReplicationRule replicationRule = new ReplicationRule();
replicationRule.setStatus(ReplicationRuleStatus.Enabled);
replicationRule.setPrefix("");
replicationRule.setDestinationConfig(replicationDestinationConfig);
// 添加规则
String ruleId = "replication-to-beijing";
bucketReplicationConfiguration.addRule(ruleId, replicationRule);

SetBucketReplicationConfigurationRequest setBucketReplicationConfigurationRequest =
        new SetBucketReplicationConfigurationRequest(bucketName, bucketReplicationConfiguration);
cosClient.setBucketReplicationConfiguration(setBucketReplicationConfigurationRequest);
```

### 查询跨地域复制

#### 功能说明

查询指定存储桶的跨地域复制规则（GET Bucket replication）。

#### 方法原型
```java
// 获取存储桶跨地域复制配置方法1
public BucketReplicationConfiguration getBucketReplicationConfiguration(String bucketName)
            throws CosClientException, CosServiceException;

// 获取存储桶跨地域复制方法2		
public BucketReplicationConfiguration getBucketReplicationConfiguration(
            GetBucketReplicationConfigurationRequest getBucketReplicationConfigurationRequest)
            throws CosClientException, CosServiceException;
```
#### 参数说明

| 参数名                                   | 参数描述                                                     | 类型                                     |
| ---------------------------------------- | ------------------------------------------------------------ | ---------------------------------------- |
| bucketName                               | 存储桶的命名格式为 BucketName-APPID，详情请参阅 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String                                   |
| getBucketReplicationConfigurationRequest | 获取跨地域复制配置请求                                       | GetBucketReplicationConfigurationRequest |

#### 返回结果说明
- 成功：返回存储桶的跨地域复制规则。
- 失败：发生错误（如身份认证失败），抛出异常 CosClientException 或者 CosServiceException。详情请参阅 [异常处理](https://intl.cloud.tencent.com/document/product/436/30599)。

#### 请求示例
[//]: # (.cssg-snippet-get-bucket-replication)
```java
String bucketName = "examplebucket-1250000000";

// 获取存储桶跨地域复制配置方法1
BucketReplicationConfiguration brcfRet = cosClient.getBucketReplicationConfiguration(bucketName);

// 获取存储桶跨地域复制配置方法2
BucketReplicationConfiguration brcfRet2 = cosClient.getBucketReplicationConfiguration(
        new GetBucketReplicationConfigurationRequest(bucketName));
```

### 删除跨地域复制

#### 功能说明

删除指定存储桶的跨地域复制规则（DELETE Bucket replication）。

#### 方法原型
```java
// 删除存储桶跨地域复制配置方法1
public void deleteBucketReplicationConfiguration(String bucketName)
            throws CosClientException, CosServiceException;

// 删除存储桶跨地域复制方法2		
public void deleteBucketReplicationConfiguration(
            DeleteBucketReplicationConfigurationRequest deleteBucketReplicationConfigurationRequest)
            throws CosClientException, CosServiceException;
```

#### 参数说明

| 参数名                                      | 参数描述                                                     | 类型                                        |
| ------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------- |
| bucketName                                  | 存储桶的命名格式为 BucketName-APPID，详情请参阅 [命名规范](https://intl.cloud.tencent.com/document/product/436/13312) | String                                      |
| deleteBucketReplicationConfigurationRequest | 删除跨地域复制配置请求                                       | DeleteBucketReplicationConfigurationRequest |

#### 返回结果说明

  - 成功：无返回值。
  - 失败：发生错误（如身份认证失败），抛出异常 CosClientException 或者 CosServiceException。详情请参阅 [异常处理](https://intl.cloud.tencent.com/document/product/436/30599)。

#### 请求示例

[//]: # (.cssg-snippet-delete-bucket-replication)
```java
String bucketName = "examplebucket-1250000000";

// 删除存储桶跨地域复制配置方法1
cosClient.deleteBucketReplicationConfiguration(bucketName);

// 删除存储桶跨地域复制配置方法2
cosClient.deleteBucketReplicationConfiguration(new DeleteBucketReplicationConfigurationRequest(bucketName));
```
