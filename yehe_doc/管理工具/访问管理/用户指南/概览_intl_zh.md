[访问管理控制台](https://console.cloud.tencent.com/cam/overview) 的概览页包括六大模块：**访问管理资源**、**登录链接**、**敏感操作**、**上次登录信息**、**安全分析报告**、**安全指引**。下文将对各个模块进行介绍。
- 具有 **QcloudCamSummaryAccess 策略** 权限的用户登录控制台，可查看所有模块的信息，如下图示：
![](https://main.qcloudimg.com/raw/01db21bb84efbe32cbf7991d77c6c2ac.jpg)
- 没有 **QcloudCamSummaryAccess 策略** 权限的用户登录控制台，只能查看 **登录链接** 和 **上次登录信息**，如下图示：
主账号可以通过 **QcloudCamSummaryAccess 策略** 授权给需要的子账号，允许子账号查看控制台概览页的信息。
![](https://main.qcloudimg.com/raw/b5f5df2051187ead797afa6b52a1d858.jpg)

## 访问管理资源
访问管理资源模块展示当前主账号下所创建的用户、用户组、自定义策略、角色、身份提供商数量。您可以通过单击数量下方的按钮，进入对应的创建页面。
![](https://main.qcloudimg.com/raw/4c1498665023d1af8f5943a19d633139.jpg)
## 登录链接
登录链接模块展示了子用户的登录链接。主账号和子账号均可通过链接右侧的复制按钮复制链接。
![](https://main.qcloudimg.com/raw/df6adbde1788221c0646455af92e7e57.jpg)
- 子用户登录链接：适用于子用户。

## 敏感操作
敏感操作模块展示最近3天（最高50条）当前主账号下所有敏感操作的概览信息，展示信息包括：账号 ID、操作者 ID、详细敏感操作和操作时间。用户还可以通过单击【查看所有记录】，进入云审计控制台，查看更详细的敏感操作记录。
![](https://main.qcloudimg.com/raw/e9249aaf9989ef5d1fbe5f95bd69dc5f.jpg)


## 上次登录信息
上次登录信息模块展示当前账号的上次登录时间，上次登录 IP、身份安全状态、管理 API 密钥、管理 MFA 设置快捷操作入口。
![](https://main.qcloudimg.com/raw/a0270ed9f12a9c4851e9f744bd8c7ec0.png)
## 安全分析报告
安全分析报告模块提供了【下载报告】按钮，您可以单击该按钮获取当前主子账号的安全状态，以及基于 [最佳实践](https://intl.cloud.tencent.com/document/product/598/10592) 我们发现的风险点以及推荐方案。单次报告生成有效缓存期为 4 小时。
![](https://main.qcloudimg.com/raw/5a7b93966dbfb9ed458925b151a2bfcc.png)
## 安全指引
>?为了保障您的账户以及云上资产的安全，我们强烈建议您完成安全指引下的所有设置。
>
安全指引模块为用户提供基础 CAM 功能学习和必要的安全操作指引，包括主账号绑定 MFA 设备、主账号开启账号保护、创建子账号和创建组并添加子账号等。
>- 操作权限：**主账号绑定 MFA 设备** 和 **主账号开启账号保护** 两项设置只有主账号具有操作权限；其余五项设置，获得授权的所有用户都可以进行操作。
>- 指引状态：各指引项分为 **未完成** 和 **已完成** 两种状态。主账号登录控制台可以看到各指引项的状态，具有权限的子账号无法查看状态。
>- 设置入口：具有权限的子账号可通过单击各指引项左侧的三角符号查看对应的功能介绍和相应的设置入口。下图是主账号登录控制台后的安全指引模块示例。
![](https://main.qcloudimg.com/raw/f605c11d1e46f3171cbb663471164114.jpg)

### 主账号绑定 MFA 设备
MFA（Multi-Factor Authentication）是腾讯云提供在用户名和密码之外再额外增加的一层保护，目前支持两种 MFA 设备： 硬件 MFA 设备和虚拟 MFA 设备。
主账号可以单击详细介绍下方的【去绑定 MFA 设备】进入具体设置页面，详细步骤指引参考：
- [硬件 MFA 设备](https://intl.cloud.tencent.com/document/product/378/32528)
- [虚拟 MFA 设备](https://intl.cloud.tencent.com/document/product/378/32528)

### 主账号开启账号保护
账号保护分为登录保护和操作保护。开启登录保护后，您在登录腾讯云时需要通过 MFA验证 完成身份验证。开启操作保护后，在您进行敏感操作前需要先通过二次身份校验，以确保是您本人操作。
主账号可以单击详细介绍下方的【去开启账号保护】进入具体设置页面，详细步骤指引参考：
- [登录保护](https://intl.cloud.tencent.com/document/product/378/8392)
- [操作保护](https://intl.cloud.tencent.com/document/product/378/10740)

### 创建子账号
子账号类型分为子用户、协作者和消息接收人。您可根据业务需要选择创建具有不同职责的子账号协助您。
具有权限的用户可以单击详细介绍下方的【创建用户】进入具体设置页面，详细步骤指引参考：
- [新建子用户](https://intl.cloud.tencent.com/document/product/598/13674)
- [新建协作者](https://intl.cloud.tencent.com/document/product/598/32639)
- [消息接收人](https://intl.cloud.tencent.com/document/product/598/13667)

### 创建组并添加子账号
创建用户组并给用户组分配权限，添加用户至相应用户组，可以帮助您简化子账号的权限管理和审核。
具有权限的用户可以单击详细介绍下方的【创建组】进入具体设置页面，详细步骤指引参考：
- [用户组](https://intl.cloud.tencent.com/document/product/598/10599)

### 管理授权策略
CAM 支持两种类型的策略：预设策略和自定义策略。
- 预设策略是由腾讯云创建和管理的一些常见的权限集合，粒度比较粗，用户不可编辑。
- 自定义策略是由用户自行创建的策略，允许作细粒度的权限划分，允许用户编辑。 

给用户组或用户分配权限，可以简化您对账户中 CAM 用户的权限管理和审核。
具有权限的用户可以单击详细介绍下方的【创建自定义策略】进入具体设置页面，详细步骤指引参考：
- [策略](https://intl.cloud.tencent.com/document/product/598/10601)

### 子账号开启账号保护
在用户列表内选取子账号，在【安全】页开启登录保护、操作保护。开启后，用户在进行登录或者敏感操作时将进行二次身份校验。目前支持子账号的二次身份检验方式为虚拟 MFA 设备校验、硬件 MFA 设备校验、手机验证码校验。
具有权限的用户可以单击详细介绍下方的【子用户开启帐号保护】进入具体设置页面，详细步骤指引参考：
- [为子用户设置安全保护](https://intl.cloud.tencent.com/document/product/598/32657)
- [为协作者设置安全保护](https://intl.cloud.tencent.com/document/product/598/32660)

### 子账号绑定 MFA 设备
在用户列表内选取子用户或协作者，在【安全】页为其开启账号保护并选择 MFA 校验方式，该用户会在下次登录时进行 MFA 设备绑定。
具有权限的用户可以单击详细介绍下方的【子账号绑定 MFA 设备】进入具体设置页面，详细步骤指引参考：
- [为子用户设置安全保护](https://intl.cloud.tencent.com/document/product/598/32657)
- [为协作者设置安全保护](https://intl.cloud.tencent.com/document/product/598/32660)

## 使用限制
如果您想了解子账号、用户组、策略等相关数量限制，请参阅 [使用限制](https://intl.cloud.tencent.com/document/product/598/10609)。

