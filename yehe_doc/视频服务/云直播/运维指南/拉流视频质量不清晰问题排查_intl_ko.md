호스트 비디오는 로컬 카메라로 수집되며, 클라이언트 SDK에서 인코딩과 푸시 스트리밍을 진행해 클라우드의 CDN을 통해 관중에게 배포됩니다. 멀티 비트레이트 주소를 제공할 경우에도 클라우드에서는 다시 인코딩 처리를 하게 됩니다. 비디오의 품질은 카메라에서 수집되는 품질, 인코딩 해상도, 프레임 레이트, 비디오 키 프레임 간격의 크기, 비디오 인코딩의 비트레이트 등의 요인에 따라 달라집니다. 시청 딜레이와 인코딩에 미치는 영향을 종합적으로 고려하여 키 프레임 간격은 2~3초로 설정하는 것을 권장합니다.

다음 **두 가지** 유형의 재생 주소에 따라 풀 스트리밍 비디오가 선명하지 않은 문제를 진단하고 최적화하는 방법을 설명합니다.

## 원본 스트리밍 재생 주소
풀 스트리밍 주소가 **원본 스트리밍 재생 주소**(워터마크와 혼합 스트리밍 없음)일 때 비디오가 선명하지 않을 경우에는 푸시 스트리밍에서 문제 원인을 찾으십시오.
1. 먼지가 있는지, 수집과 초점이 맞는지 등을 확인하고 카메라의 물리적 원인을 제거합니다.
2. 푸시 스트리밍의 프레임 레이트와 비트레이트가 기대치에 부합하는지 확인합니다.
<table>
<thead><tr><th>해상도</th><th>프레임 레이트</th><th>비트레이트</th></tr></thead>
<tbody><tr>
<td>640 × 368</td>
<td>15fps</td>
<td>800kbps</td>
</tr><tr>
<td>960 × 544</td>
<td>15fps</td>
<td>1000kbps</td>
</tr><tr>
<td>1280 × 720</td>
<td>15fps</td>
<td>1500kbps</td>
</tr><tr>
<td>1920 × 1080</td>
<td>15fps</td>
<td>2500kbps</td>
</tr>
</tbody></table>

#### 최적화 방법
- 3rd party SDK를 사용할 경우에는 다음 비트레이트 권장사항을 참조하여 비디오 품질을 조정하거나 3rd party SDK 제작자에게 문의하여 해결하십시오.
- 미리보기 창은 선명하지만 풀 스트리밍 비디오가 선명하지 않을 경우에는 창과 실제 인코딩 푸시 스트리밍의 비디오 품질이 일치하지 않을 수 있습니다. 다음 설정을 참고하여 실제 인코딩 푸시 스트리밍의 비디오 품질을 조정하십시오.

 

## 낮은 비트레이트, 낮은 해상도의 재생 주소
풀 스트리밍 주소가 **낮은 비트레이트, 낮은 해상도 주소**일 경우에는 먼저 원본 스트림의 재생 주소의 비디오가 선명한지 확인하십시오. 원본 스트림 주소의 비디오가 선명하다면 클라이언트 푸시 스트리밍 품질에 문제가 없다는 의미입니다. 클라우드의 트랜스 코딩 매개변수 설정을 조정하고, 권장 비트레이트에 따라 비트레이트의 템플릿 설정을 조정하여 트랜스 코딩 풀의 출력 부호율을 늘리십시오.
<table>
<thead><tr><th>해상도</th><th>프레임 레이트</th><th>비트레이트</th></tr></thead>
<tbody><tr>
<td>640 × 368</td>
<td>15fps</td>
<td>800kbps</td>
</tr><tr>
<td>960 × 544</td>
<td>15fps</td>
<td>1000kbps</td>
</tr><tr>
<td>1280 × 720</td>
<td>15fps</td>
<td>1500kbps</td>
</tr><tr>
<td>1920 × 1080</td>
<td>15fps</td>
<td>2500kbps</td>
</tr>
</tbody></table>

예를 들어 비디오 해상도가 640 × 368인 경우 템플릿 프레임 레이트가 30fps이면 출력 부호율을 1.5배로 늘리는 것이 좋습니다. 따라서 권장하는 조정 비트레이트는 800kbps × 1.5 = 1200kbps입니다.


>!위의 방법으로 문제를 해결할 수 없을 경우 [티켓 제출](https://console.cloud.tencent.com/workorder/category?level1_id=29&level2_id=39&source=0&data_title=%E4%BA%91%E7%9B%B4%E6%92%AD%20%20CSS&step=1)을 통해 고객 서비스 지원 담당자에게 문의하십시오.



