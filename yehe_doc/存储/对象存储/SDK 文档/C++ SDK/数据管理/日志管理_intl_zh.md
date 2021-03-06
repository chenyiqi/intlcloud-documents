## 简介

本文档提供关于日志管理的 API 概览以及 SDK 示例代码。

| API                                                          | 操作名       | 操作描述                   |
| ------------------------------------------------------------ | ------------ | -------------------------- |
| [PUT Bucket logging](https://intl.cloud.tencent.com/document/product/436/17054) | 设置日志管理 | 为源存储桶开启日志记录     |
| [GET Bucket logging](https://intl.cloud.tencent.com/document/product/436/17053) | 查询日志管理 | 查询源存储桶的日志配置信息 |

## 设置日志管理

#### 功能说明

PUT Bucket logging 用于为源存储桶开启日志记录，将源存储桶的访问日志保存到指定的目标存储桶中。

#### 方法原型

```cpp
CosResult CosAPI::PutBucketLogging(const PutBucketLoggingReq& request, PutBucketLoggingResp* response);
```

#### 请求示例

```cpp
qcloud_cos::CosConfig config("./config.json");
qcloud_cos::CosAPI cos(config);
std::string bucket_name = "examplebucket-1250000000";
qcloud_cos::PutBucketLoggingReq req(bucket_name);
qcloud_cos::PutBucketLoggingResp resp;

qcloud_cos::LoggingEnabled rules;
rules.SetTargetBucket(TargetBucketname);  // 存放日志的目标存储桶
rules.SetTargetPrefix(TargetPrefix);  // 日志存放在目标存储桶的指定路径    
req.SetLoggingEnabled(rules);

qcloud_cos::CosResult result = cos.PutBucketLogging(req, &resp);

if (result.IsSucc()) {
    // 请求成功，通过resp获取静态网站配置
} else {
    // 请求失败，可以调用 CosResult 的成员函数输出错误信息，例如 requestID 等
} 
```

#### 参数说明

| 参数 | 参数描述                     | 类型                | 是否必填  |
| ---- | -----------------------------|---------------------| ------|
| req  | PutBucketLogginge 操作的请求  | PutBucketLoggingReq | 是    |
| resp | PutBucketLogging 操作的响应   | PutBucketLoggingResp| 是    |


PutBucketLoggingReq 提供了如下方法设置存储桶日志的配置信息：
```cpp
void SetLoggingEnabled(const LoggingEnabled& rules);
```

LoggingEnabledt 提供如下方法设置配置信息：
```cpp
class LoggingEnabled {
public:
    void SetTargetBucket(const std::string &targetbucket);
    void SetTargetPrefix(const std::string &targetprefix);
```


## 查询日志管理

#### 功能说明

GET Bucket logging 用于查询指定存储桶的日志配置信息。

#### 方法原型

```cpp
CosResult CosAPI::GetBucketLogging(const GetBucketLoggingReq& request, GetBucketLoggingResp* response);
```

#### 请求示例

```cpp
qcloud_cos::CosConfig config("./config.json");
qcloud_cos::CosAPI cos(config);
std::string bucket_name = "examplebucket-1250000000";
qcloud_cos::GetBucketLoggingReq req(bucket_name);
qcloud_cos::GetBucketLoggingResp resp;

qcloud_cos::CosResult result = cos.GetBucketLogging(req, &resp);

if (result.IsSucc()) {
    // 请求成功，通过resp获取存储桶日志信息
} else {
    // 请求失败，可以调用 CosResult 的成员函数输出错误信息，例如 requestID 等
} 
```

#### 参数说明

| 参数 | 参数描述                     | 类型                | 是否必填  |
| ---- | -----------------------------|---------------------| ------|
| req  | GetBucketLogginge 操作的请求  | GetBucketLoggingReq | 是    |
| resp | GetBucketLogging 操作的响应   | GetBucketLoggingResp| 是    |

GetBucketLoggingResp 提供如下方法获取存储桶日志配置信息：

```cpp
LoggingEnabled GetLoggingEnabled() const;
```
