您可以将弹性云硬盘（作为云服务器的数据盘使用）挂载到同一可用区中的任意云服务器上使用，每台云服务器最多支持挂载20个数据盘。您可以通过以下方法挂载云硬盘：
- 在启动新的云服务器时，指定对应的自定义镜像和数据盘快照。
自动挂载后，不需要进行分区、格式化等初始化磁盘的操作即可直接读写数据盘。
- 单独购买的云硬盘，通过控制台或 API 接口手动将弹性云硬盘挂载到同一可用区中的已有云服务器实例上。
 - 直接创建的云硬盘
 手动挂载后，需要对磁盘进行分区、格式化等初始化操作，具体操作请参考 [初始化云硬盘（小于2TB）](https://intl.cloud.tencent.com/document/product/362/31597)或 [初始化云硬盘（大于等于2TB）](https://intl.cloud.tencent.com/document/product/362/31598)。
 - 从快照创建的云硬盘
    若云硬盘容量等于快照容量，手动挂载后不需要进行分区、格式化等初始化磁盘的操作即可直接读写数据盘。
	若云硬盘容量大于快照容量，需要扩展文件系统或转换分区形式。

 >部分 Linux 云服务器可能出现无法识别弹性云硬盘的情况，您可以先在云服务器中开启磁盘热插拔功能，详细信息请参考 [开启磁盘热插拔功能](#modprobeacpiphp)。

## 自动挂载
### 挂载数据盘（Windows）
若您需要在启动 Windows 云服务器实例时，自动挂载由对应数据盘快照创建的云硬盘，指定的自定义镜像和数据盘快照必须满足以下要求：
- 数据盘在制作快照前**必须**已经被格式化为`ntfs`或`fat32`格式。
- 自定义镜像中的 SAN 策略为`onlineAll`。
 >腾讯云目前提供的 Windows 公有镜像已默认进行相关设置，但仍建议用户在制作自定义镜像前检查下此配置，检查方法如下：
 ![](https://main.qcloudimg.com/raw/edac7337395de380c0ec801646e0a627.png)


### 挂载数据盘（Linux）
若您需要在启动 Linux 云服务器实例时，自动挂载由对应数据盘快照创建的云硬盘，指定的自定义镜像和数据盘快照必须满足以下要求：
- 数据盘在制作快照前**必须**已经进行格式化，即在源云服务器上已经 mount 成功。
- 系统盘在制作自定义镜像前，需要在 `/etc/rc.local` 文件中添加以下命令，将数据盘挂载点写入文件中。
 ```
 mkdir -p <mount-point>
 mount <device-id> <mount-point>
 ```
 其中，参数说明如下：
 - `<mount-point>`需设置为文件系统的挂载点，例如`/mydata`。
 - `<device-id>`需设置为实际文件分区位置。例如，无分区有文件系统时填写`/dev/vdb`，有分区有文件系统时填写`/dev/vdb1`。

## 手动挂载

### 使用控制台挂载云硬盘
1. 登录 [云硬盘控制台](https://console.cloud.tencent.com/cvm/cbs)。
2. 在云硬盘列表页，您可以通过以下方法挂载云硬盘：
 a. 单击状态为**待挂载**的云硬盘所在行的【更多】>【挂载】。
 b. 勾选状态为**待挂载**的云硬盘，单击云硬盘列表上方的【挂载】进行批量挂载。
3. 在弹出框中选择目标云服务器，单击【确定】。
4. 刷新云盘列表。
 若云硬盘的状态变为【已挂载】，表示挂载成功。
5. 根据云硬盘的情况，您需要选择执行对应的后续操作使云硬盘可用。
 <table>
 <tr>
 <th>创建模式</th>
 <th>云硬盘容量</th>
 <th>后续操作</th>
 </tr>
 <tr>
 <td  rowspan="2">直接创建</td>
 <td>云硬盘容量 < 2TB</td>
 <td><a href="https://intl.cloud.tencent.com/document/product/362/31597">初始化云硬盘（小于2TB）</a></td>
 </tr>
 <tr>
  <td>云硬盘容量 ≥ 2TB</td>
	<td><a href="https://intl.cloud.tencent.com/document/product/362/31598">初始化云硬盘（大于等于2TB）</a></td>
 </tr>
  <tr>
	<td  rowspan="3">从快照创建</td>
	<td>云硬盘容量 = 快照容量</td>
	<td>无需后续操作，挂载后直接可使用。</td>
 </tr>
 </tr>
 <tr>
 <td nowrap="nowrap">快照容量 < 云硬盘容量 ≤ 2TB<br/>或者<br/>2TB < 快照容量 < 云硬盘容量</td>
<td><ul><li>挂载至 Windows 云服务器：<a href="https://intl.cloud.tencent.com/document/product/362/31601">扩展分区及文件系统（Windows）</a></li><li>挂载至 Linux 云服务器：<a href="https://intl.cloud.tencent.com/document/product/362/31602">扩展分区及文件系统（Linux）</a></li></ul></td>
 </tr> 
 <tr>
 <td>快照容量 ≤ 2TB < 云硬盘容量</td>
<td nowrap="nowrap"><ul><li>若快照中使用 MBR 分区形式：</li>需参考 <a href="https://intl.cloud.tencent.com/document/product/362/31598">初始化云硬盘（大于等于2TB）</a>使用 GPT 重新分区，<b>该操作将会删除原有数据</b><li>若快照中使用 GPT 分区形式：<ul><li>挂载至 Windows 云服务器：<a href="https://intl.cloud.tencent.com/document/product/362/31601">扩展分区及文件系统（Windows）</a></li><li>挂载至 Linux 云服务器：<a href="https://intl.cloud.tencent.com/document/product/362/31602">扩展分区及文件系统（Linux）</a></li></ul></td>
 </tr> 
 </table>

### 使用 API 挂载云硬盘
您可以使用 AttachDisks 接口创建快照，具体操作请参考 [挂载云硬盘](https://intl.cloud.tencent.com/document/product/362/16313)。

<span id="modprobeacpiphp"></span>

### 开启磁盘热插拔功能
目前提供的所有镜像已经支持弹性云硬盘的挂载/卸载操作。**卸载云硬盘前需先执行`umount`（Linux）或脱机（Windows）操作，否则可能会导致该云服务器再次挂载弹性云硬盘时无法识别。**
但若您在此时间之前购买了以下操作系统的云服务器并计划为其挂载弹性云硬盘，建议您先在云服务器中添加相关驱动获得热插拔功能。
<table>
<tbody>
<tr><th>CVM 操作系统类型</th><th>版本</th>
<tr><td rowspan="4">CentOS</td><td>5.11 64位</td>
<tr><td>5.11 32位</td>
<tr><td>5.8 64位</td>
<tr><td>5.8 32位</td>
<tr><td >Debian</td><td>6.0.3 32位</td>
<tr><td rowspan="2">Ubuntu</td><td>10.04 64位</td>
<tr><td>10.04 32位</td>
<tr><td rowspan="2">openSUSE</td><td>12.3 64位</td>
<tr><td>12.3 32位</td>
</tbody>
</table>

1. 以 root 用户 [登录 Linux 云服务器](https://intl.cloud.tencent.com/document/product/213/5436)。
2. 执行以下命令，添加驱动。
```
modprobe acpiphp
```
>若需要在关机或者重启云服务器后，仍需加载 `acpiphp` 驱动模块，建议执行 [步骤3](#step3) 将 `acpiphp` 模块设置成开机自动加载。
<span id="step3"></span>
3. （可选）根据不同操作系统，选择对应的操作方法将 `acpiphp` 模块设置成开机自动加载：
 - **CentOS 5 系列**
 a. 执行以下命令，创建并打开`acpiphp.modules`文件。
```
vi /etc/sysconfig/modules/acpiphp.modules
```
b. 在文件中添加以下内容，并保存。
```
 #!/bin/bash
 modprobe acpiphp >& /dev/null
```
c. 执行以下命令，添加可执行权限。
```
chmod a+x /etc/sysconfig/modules/acpiphp.modules
```
 - **Debian 6 系列、Ubuntu 10.04 系列**
 a. 执行以下命令，修改文件。
```
vi /etc/modules
```
b. 在文件中添加以下内容，并保存。
```
acpiphp
```
 - **openSUSE 12.3 系列**
 a. 执行以下命令，修改文件。
```
vi /etc/sysconfig/kernel
```
b. 在文件中添加以下内容，并保存。
```
MODULES_LOADED_ON_BOOT="acpiphp"
```
