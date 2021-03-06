本文档介绍如何通过 [云直播控制台](https://console.cloud.tencent.com/live) 创建水印配置。创建成功后，还需到对应的推流域名下关联 [水印配置](https://intl.cloud.tencent.com/document/product/267/31064)，关联成功后约5分钟 - 10分钟生效。用户也可以通过 API 对直播频道添加水印。


## 创建水印模板
登录云直播控制台，在左侧菜单栏选择【功能模板】>[【水印配置】](https://console.cloud.tencent.com/live/config/watermark)，单击【+】设置水印的基本信息。
您可自行选择水印的显示位置，通过拖动水印图片或调节 X 轴 和 Y轴方向将水印放置在自己想要的位置。
![](https://main.qcloudimg.com/raw/573023a1d1d6fd921209799edbfa96e8.png)

> 为了视觉效果，水印应为透明图片 png 格式；图片大小小于2M。

## 关联域名
1. 进入[【域名管理】](https://console.cloud.tencent.com/live/domainmanage)选择推流地址，单击【管理】进入推流域名详情页。
2. 选择【模板配置】，在水印配置中编辑选择已设置好的水印模板即可指定到该域名地址。
![](https://main.qcloudimg.com/raw/637ec4e2692c9b1fdd06ccf336e439d8.png)
>
>- 如果您需要解绑水印配置，在【模板配置】中，单击【编辑】，取消相应模板的勾选，然后单击【保存】，即可将该模板与域名取消关联。
>- 控制台的水印模板管理为域名维度，暂时无法取消关联接口创建的规则，如果是通过水印管理接口关联指定流的，则需要通过调用 [删除水印接口](https://intl.cloud.tencent.com/document/product/267/30824) 解除关联。
