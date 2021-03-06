## 配置场景

若您需要将实际访问的 URL 修改为与源站匹配的 URL，腾讯云 CDN 为您提供了 URL 重写配置功能。

您可通过自定义 URL 重写配置，将 URL 302 重定向到目标 URL。

## 配置指南

### 查看配置

登录 [CDN 控制台](https://console.cloud.tencent.com/cdn)，在左侧菜单栏选择【域名管理】，单击域名操作列的【管理】，进入域名配置页面，切换 Tab 至【缓存配置】，即可找到【URL 重写配置】。

默认情况下，URL 重写配置为关闭状态：
![](https://main.qcloudimg.com/raw/01f93aaa70c523ae0bb1ab5debae8558.png)


### 新增规则

您可按需添加重写规则，并开启 URL 重写配置功能。

**配置约束**
+ 单个域名至多可添加10条重写规则。
+ 多条规则支持调整优先级：底部优先级大于顶部。
+ 待重写 URL：支持全路径匹配（以`/`开头），支持正则表达式。
+ 目标 URL：以`/`开头。
+ 待重写 URL 和目标 URL 的输入长度不可超过1024个字符。

单击【新增重写规则】：
![](https://main.qcloudimg.com/raw/97ea8713395f3af8654c39be97f124d3.png)
规则添加完成后，整体配置仍为默认的关闭状态，因此不会影响现网服务。

>?关闭状态下仍可修改下方配置，但不会发布至现网，仅当开启此开关时，进行现网配置下发。

可通过单击开关开启配置，将添加的重写规则发布至现网：
![](https://main.qcloudimg.com/raw/214b034e578d5eaac0a63cacd49f1e2d.png)

若请求的 URL 匹配了当前配置的规则，该请求将被302重定向跳转到对应的目标 URL。

### 修改规则

对已添加的重写规则，可进行修改。单击重写规则操作列的【修改】即可。

### 删除规则

可删除已添加的重写规则。单击重写规则操作列的【删除】即可。



>! 若您的加速域名服务区域为全球加速，**URL 重写配置**会全球生效，不支持境内、境外差异化配置。

## 配置示例

若加速域名`www.test.com`的 **URL 重写配置** 如下：
![](https://main.qcloudimg.com/raw/19edbf944b4e727b7c62270f2d8078cf.png)

则实际访问情况如下：

+ 客户端请求`www.test.com/access`，CDN 节点将返回`www.test.com/origin/index.html`的内容。
+ 客户端请求`www.test.com/test/a.jpg`，CDN 节点将返回`www.test.com/testnew/b.jpg`的内容。



