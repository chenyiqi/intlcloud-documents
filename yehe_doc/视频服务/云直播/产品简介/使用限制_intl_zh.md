在使用云直播服务前，您需要了解本服务的使用限制信息。

<table>
    <tr><th width="15%">限制项</th><th width="75%">说明</th></tr>
    <tr>
        <td>直播域名</td>
        <td>默认每个账号下可创建多个播放和推流域名，如果播放域名选择区域包含中国内地（大陆），则该域名必须在工信部备案，且当前备案信息正常可用。</td>
    </tr>
    <tr>
        <td>直播推流</td>
        <td>云直播服务不限制推流码率，支持常见分辨率以及对应码率。为避免推流卡顿，建议码率不超过 4Mbps。</td>
    </tr>
    <tr>
        <td>直播播放</td>
        <td><ul style="margin-bottom:0">
            	<li>直播地址 StreamName 与推流地址 StreamName 一致才可以播放对应的流。
            	<li>不限制直播播放观看人数，支持设置带宽封顶。
            </ul></td>
    </tr>
    <tr>
        <td>模板配置</td>
        <td>配置模板关联成功后约5分钟 - 10分钟生效。</td>
    </tr>
    <tr>
        <td>日结计费方式切换</td>
        <td>日结计费支持流量/峰值带宽两种计费方式切换，每日仅限切换1次（变更成功后次日生效）。</td>
    </tr>
		    <tr>
        <td>推流支持协议</td>
				<td>支持 RTMP 输出协议，详细说明请参见 <a href="https://intl.cloud.tencent.com/document/product/267/7968">常见问题</a>。</td>
    </tr>
		    <tr>
        <td>播放支持协议</td>
        <td>支持 RTMP、 FLV 和 HLS 播放协议，详细说明请参见 <a href="https://intl.cloud.tencent.com/document/product/267/7968">常见问题</a>。</td>
    </tr>
    <tr>
        <td>导播台</td>
        <td><ul style="margin-bottom:0">
            	<li>每个账号可创建1个导播台实例，删除导播台实例后即可重新添加。若您需要多个导播台，请 <a href="https://console.cloud.tencent.com/workorder/category">提工单</a> 申请。 
            	<li>点播输入播放列表，最多支持5个点播文件。 
            	<li>转推第三方，最多支持转推3路其他厂家。
            </ul>
        </td>
    </tr>
</table>

