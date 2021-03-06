## 简介

本文档提供关于存储桶基本操作的相关 API 概览以及 SDK 示例代码。


| API                                                          | 操作名             | 操作描述                           |
| ------------------------------------------------------------ | ------------------ | ---------------------------------- |
| [GET Service](https://intl.cloud.tencent.com/document/product/436/8291) | 查询存储桶列表	|查询指定账号下所有的存储桶列表|
| [PUT Bucket](https://intl.cloud.tencent.com/document/product/436/7738) | 创建存储桶         | 在指定账号下创建一个存储桶         |
| [HEAD Bucket](https://intl.cloud.tencent.com/document/product/436/7735) | 检索存储桶及其权限 | 检索存储桶是否存在且是否有权限访问 |
| [DELETE Bucket](https://intl.cloud.tencent.com/document/product/436/7732) | 删除存储桶         | 删除指定账号下的空存储桶           |



## 查询存储桶列表

#### 功能说明

用于查询指定账号下所有存储桶列表（GET Service）。

#### 方法原型

```
list_buckets()
```

#### 请求示例

[//]: # (.cssg-snippet-get-service)
```python
response = client.list_buckets(
)
```

#### 返回结果说明

查询存储桶列表，类型为 dict。

```python
{
    'Buckets': {
        'Bucket': [
            {
                'Name': 'string',
                'Location': 'string',
                'CreationDate': 'string'
            },
        ],
    },
    'Owner': {
        'DisplayName': 'string',
        'ID': 'string'
    }
}
```

| 参数名称   | 参数描述   |类型 | 
| -------------- | -------------- |---------- |
| Buckets   | 存储桶列表  | Dict |
| Bucket   | 存储桶列表 | List |
| Name   |  存储桶名称  | String|
| Location   |  存储桶所在的地域名  | String|
| CreationDate   |  存储桶创建的时间  | String|
| Owner   |  存储桶所有者信息  | Dict|
| DisplayName   |  存储桶所有者的名字信息  | String|
| ID   | 存储桶所有者 ID | String|


## 创建存储桶

#### 功能说明

在指定账号下创建一个存储桶（PUT Bucket）。

#### 方法原型

```
create_bucket(Bucket, **kwargs)
```
#### 请求示例

[//]: # (.cssg-snippet-put-bucket-comp)
```python
response = client.create_bucket(
    Bucket='examplebucket-1250000000'
)
```
#### 全部参数请求示例

```python
response = client.create_bucket(
    Bucket='examplebucket-1250000000',
    ACL='private'|'public-read'|'public-read-write',
    GrantFullControl='string',
    GrantRead='string',
    GrantWrite='string'    
)
```
#### 参数说明

| 参数名称   | 参数描述   |类型 | 是否必填 | 
| -------------- | -------------- |---------- | ----------- |
|Bucket|待创建的存储桶名称，由 BucketName-APPID 构成|String| 是|
| ACL |设置存储桶的 ACL，例如 'private'，'public-read'，'public-read-write' |String| 否|
| GrantFullControl |赋予指定账户对存储桶的读写权限，格式为`id="OwnerUin"`|String|否|
|GrantRead |赋予指定账户对存储桶的读权限，格式为`id="OwnerUin"`|String|否|
| GrantWrite|赋予指定账户对存储桶的写权限，格式为`id="OwnerUin"`|String|否|

#### 返回结果说明
该方法返回值为 None。


## 检索存储桶及其权限

#### 功能说明

检索存储桶是否存在且是否有权限访问（HEAD Bucket）。

#### 方法原型

```
head_bucket(Bucket)
```
#### 请求示例

[//]: # (.cssg-snippet-head-bucket)
```python
response = client.head_bucket(
    Bucket='examplebucket-1250000000'
)
```
#### 参数说明

| 参数名称   | 参数描述   |类型 | 是否必填 | 
| -------------- | -------------- |---------- | ----------- |
|Bucket |待查询的存储桶名称，由 BucketName-APPID 构成|String|是|

#### 返回结果说明
该方法返回值为 None。


## 删除存储桶

#### 功能说明

删除指定账号下的空存储桶（DELETE Bucket）。

#### 方法原型

```
delete_bucket(Bucket)
```
#### 请求示例

[//]: # (.cssg-snippet-delete-bucket)
```python
response = client.delete_bucket(
    Bucket='examplebucket-1250000000'
)
```
#### 参数说明

| 参数名称   | 参数描述   |类型 | 是否必填 | 
| -------------- | -------------- |---------- | ----------- |
|Bucket |待删除的存储桶名称，由 BucketName-APPID 构成|String|是|

#### 返回结果说明
该方法返回值为 None。


