﻿## 接口描述

- 域名：tag.api.qcloud.com。 
- 接口名：UpdateProject。
- 接口描述：修改项目信息。

## 输入参数

|参数名称|	必选|	类型|	描述|
|-----|-----|----|-----|
|projectId|	是|	Int	|项目 ID|
|name|	否	|String	|项目名称|
|info|	否|	String|	描述|

## 输出参数

|参数名称| 类型| 描述 |
|-----|------|-------|
|code| Int |错误码，0：成功；其他值：失败 |
|message |String |错误信息 |
|data |Array| 返回数组|

## 示例
### 输入

<pre>
https://tag.api.qcloud.com/v2/index.php?Action=UpdateProject 
&<a href="https://intl.cloud.tencent.com/document/product/378/4380">公共请求参数</a>
</pre>

### 输出
```
{
    "code": 0,
    "message": "",
    "data": []
}
```
