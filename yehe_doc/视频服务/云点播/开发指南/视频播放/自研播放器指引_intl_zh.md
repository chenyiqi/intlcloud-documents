云点播针对长视频和视频加密场景，提供了 Android、iOS 和 Web 三端 [播放器 SDK](https://intl.cloud.tencent.com/document/product/266/7836)。通过使用点播 SDK，您可以快速集成点播播放能力。如果点播超级播放器 SDK 无法满足您的定制化需求，您也可参照播放器 SDK 与点播后台的通信协议，实现自研播放器。下面将详细介绍播放器 SDK 与云点播后台的通信协议。

## 协议
请求以 HTTP Get 的方式发起，URL 为`https://playvideo.qcloud.com/{interface}/{version}/{appId}/{fileId}?psign=xxx&cipheredOverlayKey=xxx&cipheredOverlayIv=xxx&keyId=x`。

### 域名
* 主域名：`playvideo.qcloud.com`
* 备份域名：`bkplayvideo.qcloud.com`

### 请求字段
#### path 字段

| 字段含义 | 是否必填 | 字段取值 |
| -- | -- | -- |
| appId | 是 | 填写 appid（如果使用了子应用，则填 subappid）。 |
| fileId | 是 | 要播放的视频文件 ID。 |
| version | 是 | 固定填写 v4。 |
| interface | 是 | 固定填写 getplayinfo。 |

#### querystring 字段

| 字段含义 | 是否必填 | 字段取值 |
| -- | -- | -- |
| psign | 否 | 超级播放器签名，填写参数参考下述超级播放器签名章节，签名方法请参考 [超级播放器签名文档](https://intl.cloud.tencent.com/document/product/266/38099) 。 |
|context|否|透传字段，回包中原样带回。|
|cipheredOverlayKey|否 |额外对 Key 加密使用的加密 Key，用256个字符的16进制表示，例如：5872bd2fcc76176a2db6fcd1341c04e891643e938bf8901310846de62d6942f49e7393cbaf96fd48bfeb7f50878d5bafe93017670e4483e6ccc3c8908ee2ae42823b875aa171a44781cc417163d19d503dda2ba1e6242f41b49c1de12bed52de310a71ba3d8660a9a086289a54f573f1141c451b6ec88ca917c586b4d7735e20。|
|cipheredOverlayIv|否|额外对 Key 加密使用的加密 初始向量，用256个字符的16进制表示，例如：5872bd2fcc76176a2db6fcd1341c04e891643e938bf8901310846de62d6942f49e7393cbaf96fd48bfeb7f50878d5bafe93017670e4483e6ccc3c8908ee2ae42823b875aa171a44781cc417163d19d503dda2ba1e6242f41b49c1de12bed52de310a71ba3d8660a9a086289a54f573f1141c451b6ec88ca917c586b4d7735e20。|
|keyId|否|密钥的版本。取值范围为：[0,1]。当取值为0时，表示 cipheredOverlayKey 和 cipheredOverlayIv 无效；当取值为1时，表示 cipheredOverlayKey 和 cipheredOverlayIv 有效。|

### 超级播放器签名
#### 签名参数

| 参数名称 | 必选 | 类型 | 说明 |
| -- | -- | -- | -- |
| appId | 是 | Integer | 账号 appId。|
| fileId | 是 | String | 文件 ID。|
| currentTimeStamp | 是 | Integer | 派发签名当前 Unix 时间戳。 |
| expireTimeStamp | 是 | Integer | 派发签名到期 Unix 时间戳，不填表示签名派发后1天内过期。 |
| pcfg | 否 | String | 使用的超级播放配置名称。如果是 Default，可以不填。|
| urlAccessInfo | 否 | Object | 播放链接的防盗链配置参数，为 UrlAccessInfo 类型。 |
| drmLicenseInfo | 否 | Object | 加密内容的密钥配置参数，为 DrmLicenseInfo 类型。 |

##### UrlAccessInfo 类型

| 参数名称 | 必选 | 类型 | 说明 |
| -- | -- | -- | -- |
| t | 否 | String | 16进制字符串，表示链接的过期时间。具体含义和取值参考 [防盗链参数](https://intl.cloud.tencent.com/document/product/266/33986) 中的 t 参数。不填表示签名生成后1天内过期。|
| exper | 否 | Integer |  试看时长，单位为秒，以十进制表示；如果要指定试看时长，时长必须不小于30秒（即半分钟）；具体含义和取值参考 [防盗链参数](https://intl.cloud.tencent.com/document/product/266/33986) 中的 exper 参数。|
| rlimit | 否 | Integer | 最多允许多少个不同 IP 的终端播放，以十进制表示；具体含义和取值参考 [防盗链参数](https://intl.cloud.tencent.com/document/product/266/33986) 中的 rlimit 参数。 |
| us | 否 | String | 链接标识，用户增强链接的唯一性；具体含义和取值参考 [防盗链参数](https://intl.cloud.tencent.com/document/product/266/33986) 中的 us 参数。|

##### DrmLicenseInfo 类型

| 参数名称 | 必选 | 类型 | 说明 |
| -- | -- | -- | -- |
| expireTimeStamp | 否 | Integer | 密钥的到期 Unix 时间戳，不填表示签名派发后1天过期。 |
| strictMode | 否 | Integer | 校验级别。取值范围[0,1,2]。当取值为0时，表示允许对内容密钥直接透传或采用对称密钥对内容密钥加密以及采用对成密钥和非对称密钥对内容密钥加密三种策略；当取值为1时，表示允许采用对成密钥对内容密钥加密或采用对称密钥和非对称密钥对内容密钥加密两种策略；当取值为2时，表示仅允许采用对称密钥和非对称密钥对内容密钥加密。当内容密钥直接透传，任意端均可以播放；当内容密钥加密后，需要客户端对内容密钥解密才能播放。 |

### 应答字段

| 参数名 | 类型 | 描述 |
| -- | -- | -- |
| code | Integer | 错误码，当 code 非0时表示错误。 |
| message | String | 错误信息，当 code 非0时有值。 |
| version | Integer | 当前返回的结果版本类型，取值固定为4。 |
| warning | String | 警告信息，如未开防盗链时携带 psign 参数，则返回警告。 |
| media | Object | 媒体信息，元素类型为 Media。

#### Media 类型

| 参数名 | 类型 | 描述 |
| -- | -- | -- |
| basicInfo | Object | 视频基本信息，类型为 BasicInfo 类型。 |
| streamingInfo | Object | 多码率视频信息，类型为 StreamingInfo 类型。 |
| imageSpriteInfo | Object | 缩略图信息，主要用于实现播放器对视频的预览，类型为 ImageSpriteInfo 类型。 |
| keyFrameDescInfo | Object | 视频打点信息，用于播放器在时间轴上的打点，类型为 KeyFrameDescInfo 类型。 |

#### BasicInfo 类型

| 参数名 | 类型 | 描述 |
| -- | -- | -- |
| name | String | 视频名称。 |
| size | Integer | 视频大小，单位：字节。 |
| duration | Float | 视频时长，单位：秒。 |
| description | String | 视频描述。 |
| coverUrl | String | 视频封面。 |

#### StreamingInfo 类型

| 参数名 | 类型 | 描述 |
| -- | -- | -- |
|plainOutput|String|未加密的输出，类型为 StreamingOutput。 |
|drmOutput|Array|对视频做 DRM 加密后输出，类型为 StreamingOutput。 |
|drmToken|String|播放 DRM 加密输出时，使用的 DRM Token。需要将该字段拼到 streamingOutput.url 中播放。 |

#### StreamingOutput 类型

| 参数名 | 类型 | 描述 |
| -- | -- | -- |
| type | String | 自适应码流保护类型，目前取值有 plain 和 simpleAES。plain 表示不加密，simpleAES 表示 HLS 普通加密。 |
| url | String | 播放 URL。 |
| subStreams | Array | 子流信息，类型为 SubStreamInfo。 |

#### SubStreamInfo 类型

| 参数名 | 类型 | 描述 |
| -- | -- | -- |
| type | String | 子流的类型，目前可能的取值仅有 video。 |
| width | Integer | 子流视频的宽，单位：px。 |
| height | Integer | 子流视频的高，单位：px。 |
| resolutionName | String | 子流视频在播放器中展示的规格名。 |

#### ImageSpriteInfo 类型

| 参数名 | 类型 | 描述 |
| -- | -- | -- |
| imageUrls | Array | 缩略图下载 URL 数组，类型为 String 。 |
| webVttUrl | String | 缩略图 VTT 文件下载 URL 。 |

### 播放加密输出

请求返回的结果是加密后的视频（即 streamingOutput.type 为 simpleAES），需要将 streamingInfo.drmToken 拼接到 streamingOutput.url 的文件名中，生成链接播放。

**拼接规则**：新文件名 = voddrm.token.{要拼接的 token}.{原文件名}

例如，streamingOutput.url 是`http://125xxx167.vod2.myqcloud.com/xxx/xxx/xx.m3u8?t=5c08d9fa&us=someus&sign=xxx`，drmToken 是`JhbGciOxxxsInR5cCI6Ikp`。
则播放的 URL 如下：
`http://125xxx167.vod2.myqcloud.com/xxx/xxx/voddrm.token.JhbGciOxxxsInR5cCI6Ikp.xx.m3u8?t=5c08d9fa&us=someus&sign=xxx`。


## 加密私有化详述

HLS 普通加密的原理是，在 m3u8 文件的 EXT-X-KEY 标签中的 URI 中指定了获取内容密钥 Key 的地址，播放器播放时会实时获取内容密钥 Key 后解密播放。
因为该 Key 是以明文形式传递的，安全级别较低，部分浏览器插件可能会破解。
云点播针对这个问题，为您提供了加密私有化的方案，即使用您实时生成的 OverlayKey 和 OverlayIv 对内容密钥 Key 采用 AES-128 CBC 算法做二次加密，并在客户端采用指定公钥用 RSA 算法对 OverlayKey 和 OverlayIv 加密，防止内容密钥 Key 泄露。
具体方案步骤如下。
### 1 获取 Psign
**播放器：**
您的播放器在播放开始时，需要先请求业务服务器获取 Psign 。
**业务服务器：**
您需要根据不同的场景填写 StrictMode 参数，计算并派发 Psign 。
### 2 对临时密钥加密
**播放器：**
播放器随机生成临时的密钥 OverlayKey 和 OverlayIv，然后，指定密钥版本 KeyId 为1，并使用 KeyId 为1对应的 PublicKey 分别对 OverlayKey 和 OverlayIv 采用 RSA 进行加密得到 CipheredOverlayKey 和 CipheredOverlayIv ，然后跟步骤1得到的 Psign 一并填写到请求云点播的 querystring 中。

### 3 使用临时密钥对 Key 解密
**播放器：**
当播放加密的视频时，m3u8 从 EXT-X-KEY 指定的 URL 获取到的 Key，已经被 OverlayKey 和 OverlayIV 加密了。这时您的播放器需要使用 OverlayKey 和 OverlayIV 对 Key 进行解密之后，再用解密后的 Key 解密播放。

### 4 加密升级方案整体业务流程图：

![](https://main.qcloudimg.com/raw/872e8921a291877be233da67f25138bb.png)


## 示例
下面以播放一个视频的加密输出为例。

### 请求
```json
https://playvideo.qcloud.com/getplayinfo/v4/125xxx167/52858xxx74597?psign=0eef1a12dxxxf0f48ebf34b4&cipheredOverlayKey=5872bd2fcc76176a2db6fcd1341c04e891643e938bf8901310846de62d6942f49e7393cbaf96fd48bfeb7f50878d5bafe93017670e4483e6ccc3c8908ee2ae42823b875aa171a44781cc417163d19d503dda2ba1e6242f41b49c1de12bed52de310a71ba3d8660a9a086289a54f573f1141c451b6ec88ca917c586b4d7735e20&cipheredOverlayIv=5872bd2fcc76176a2db6fcd1341c04e891643e938bf8901310846de62d6942f49e7393cbaf96fd48bfeb7f50878d5bafe93017670e4483e6ccc3c8908ee2ae42823b875aa171a44781cc417163d19d503dda2ba1e6242f41b49c1de12bed52de310a71ba3d8660a9a086289a54f573f1141c451b6ec88ca917c586b4d7735e20&keyId=1
```

### 应答
```json
{
    "code":0,
    "message":"",
    "requestId":"377d94185f0342c5b67b038501f54974",
    "version":4,
    "context":"",
    "warning":"",
    "media":{
        "basicInfo":{
            "name":"动物世界",
            "size":26246026,
            "duration":30.5,
            "description":"来自CCTV的经典动物节目",
            "coverUrl":"http://125xxx167.vod2.myqcloud.com/xxx/xxx/xx.jpg?t=5c08d9fa&amp;someus&amp;sign=xxx"
        },
        "streamingInfo":{
            "plainOutput":{

            },
            "drmOutput":[
                {
                    "type":"simpleAes",
                    "url":"http://125xxx167.vod2.myqcloud.com/xxx/xxx/xx.m3u8?t=5c08d9fa&amp;us=someus&amp;sign=xxx",
                    "subStreams":[
                        {
                            "type":"video",
                            "width":427,
                            "height":240,
                            "resolutionName":"流畅"
                        },
                        {
                            "type":"video",
                            "width":853,
                            "height":480,
                            "resolutionName":"标清"
                        },
                        {
                            "type":"video",
                            "width":1280,
                            "height":720,
                            "resolutionName":"高清"
                        }
                    ]
                }
            ],
            "drmToken":"JhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9xxx",
        },
        "imageSpriteInfo":{
            "imageUrls":[
                "http://125xxx167.vod2.myqcloud.com/xxx/xxx/xx.jpg?t=5c08d9fa&amp;us=someus&amp;sign=xxx"
            ],
            "webVttUrl":"http://125xxx167.vod2.myqcloud.com/xxx/xxx/xx.vtt?t=5c08d9fa&amp;us=someus&amp;sign=xxx"
        },
        "keyFrameDescInfo":{
            "keyFrameDescList":[
                {
                    "timeOffset":1.1,
                    "content":"片头开始..."
                },
                {
                    "timeOffset":100.2,
                    "content":"即将结束..."
                }
            ]
        }
    }
}
```

## 术语表
| 参数名 | 类型 | 描述 |
| -- | -- | -- |
| OverlayKey | String | 客户端二次加密的密钥，用于对内容密钥 Key 做加密。为128位密钥经十六进制编码得到的、长度为 32 字节的字符串。|
| OverlayIv | String | 客户端二次加密的初始向量，用于对内容密钥 Key 做加密。为32位字符，每个字符表示一个16进制数。 |
| cipheredOverlayKey | String | 额外对 Key 加密使用的加密 Key，用256个字符的16进制表示。|
| cipheredOverlayIv | String | 额外对 Key 加密使用的加密初始向量，用256个字符的16进制表示。|



## 调试建议
建议采用以下步骤调试：
1. 非加密播放。
2. 加密私有化播放。

## 公钥
 KeyId 等于1对应的公钥为：
```
-----BEGIN PUBLIC KEY-----
MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQC3pDA7GTxOvNbXRGMi9QSIzQEI
+EMD1HcUPJSQSFuRkZkWo4VQECuPRg/xVjqwX1yUrHUvGQJsBwTS/6LIcQiSwYsO
qf+8TWxGQOJyW46gPPQVzTjNTiUoq435QB0v11lNxvKWBQIZLmacUZ2r1APta7i/
MY4Lx9XlZVMZNUdUywIDAQAB
-----END PUBLIC KEY-----
```
