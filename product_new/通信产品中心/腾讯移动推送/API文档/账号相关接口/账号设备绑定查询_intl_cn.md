
## 接口说明
**请求方式**：POST。

接口请求地址与服务接入点一一对应，请选择与您的应用服务接入点对应的请求地址。

广州服务接入点：
```shell
https://api.tpns.tencent.com/v3/device/account/query
```
中国香港服务接入点:
```shell
https://api.tpns.hk.tencent.com/v3/device/account/query
```
新加坡服务接入点:
```shell
https://api.tpns.sgp.tencent.com/v3/device/account/query
```
**接口功能**：查询 Account 与 Token 的绑定关系。



## 参数说明
#### 请求参数
| 参数名 | 类型 | 是否必需 | 参数说明 |
| -------------- | ------- | ---- | ---------------------------------------- |
| operator_type | Integer | 是 | 操作类型：<li>根据 Account 批量查询对应 Token<li>根据 Token查询 Account |
| account_list | Array | 否 | 当 operator_type = 1 时有效且必填，待查询 Account 列表每个元素含一组 Account 。 具体示例如下：`[{"account":"account1"},{"account":"account2"}]` |
| token_list | Array | 否 | 当 operator_type = 2 时有效且必填待查询 Token 的列表|

#### 响应参数

| 参数名 | 类型 | 参数说明 |
| -------------- | ------- | ---------------------------------------- |
| retCode | Integer | 返回码 |
| errMsg | String | 错误信息|
| account_tokens | Array |Account 到 Token 的映射关系数组。示例如下：<br>`[{"account":"account1","token_list":["token1","token2"]}{"account":"account2","token_list":["token2","token3"]}`] |
| token_accounts | Array |Token 到 Account 的映射关系数组。示例如下：<br>`[{"token":"token1","account_list":[{"account":"926@126.com"},{"account":"1527000000",}]},`<br/>`{"token":"token2","account_list":[{"account":"926@163.com"},{"account":"1527000001"}]}]` |


## 示例说明
#### 请求示例

- 批量查询 Account 绑定的 Token 关系
```json
{
    "operator_type": 1,
    "account_list": [
        {
            "account": "account1"
        },
        {
            "account": "account2"
        }
    ]
}
```
- 批量查询 Token 绑定的 Account 关系
```json
{
    "operator_type": 2,
    "token_list": [
        "token1",
        "token2"
    ]
}
```

#### 返回示例
- 批量查询 Account 绑定的 Token
```json
{
    "retCode": 0,
    "errMsg": "ok",
    "result": [
        "0",
        "0"
    ],
    "account_tokens": [
        {
            "account": "account1",
            "token_list": [
                "token1",
                "token2"
            ]
        },
        {
            "account": "account2",
            "token_list": [
                "token2",
                "token3"
            ]
        }
    ]
}
```
- 批量查询 Token 绑定的 Account
```json
{
    "retCode": 0,
    "errMsg": "ok",
    "result": [
        "0",
        "0"
    ],
    "token_accounts": [
        {
            "token": "token1",
            "account_list": [
                {
                    "account": "926@126.com"
                },
                {
                    "account": "1527000000"
                }
            ]
        },
        {
            "token": "token2",
            "account_list": [
                {
                    "account": "926@163.com"
                },
                {
                    "account": "1527000001"
                }
            ]
        }
    ]
}
```


