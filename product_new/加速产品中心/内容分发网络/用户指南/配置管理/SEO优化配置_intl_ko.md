> SEO 최적화 구성은 CDN에 도메인 이름을 액세스한 후 CDN이 IP를 자주 변경하여 도메인 이름 검색 결과에 가중치를 부여하는 문제를 해결하는 기능입니다. 액세스한 IP가 검색 엔진에 속하는지 식별함으로써, 사용자는 원본 서버에 직접 액세스하여 검색 엔진 가중치의 안정성을 보장 할 수 있습니다.
>
> **참고** : 검색 엔진 IP가 자주 업데이트되므로 Tencent Cloud CDN은 대중적인 검색 엔진 IP 만 인식 할 수 있습니다.

## 구성 안내
[CDN 콘솔](https://console.cloud.tencent.com/cdn)에 로그인하고 왼쪽 메뉴의 [도메인 관리]를 선택한 다음 편집할 도메인 이름의 오른쪽의 [관리]를 클릭하십시오.
![](https://mc.qcloudimg.com/static/img/f92d2ef7e4be2b69185ab43228f025ef/1.png)
[고급 구성]을 클릭하면 **SEO 최적화 구성** 모듈이 표시됩니다. 일반적으로 검색 엔진은 자동으로 원본 가져오기가 비활성화 상태가 됩니다. **주의** : SEO 최적화 구성 기능은 도메인 액세스 방법이 **오리진 도메인 ** 인 경우에만 사용할 수 있습니다. SEO 최적화 구성 기능을 사용한 후 만약 도메인 이름에 여러 원본 서버 주소가 있는 경우 기본 원본 가져오기 주소는 추가된 첫 번째 서버 주소입니다. ![](https://mc.qcloudimg.com/static/img/18bc9019b47152b2e214e1ca6a4296e8/2.png)

현재 도메인 이름의 CNAME이 이전 버전의 CNAME 인 경우 SEO 최적화 구성 기능을 사용하려면 새 CNAME으로 업데이트해야 합니다.

CNAME을 업데이트하는 구체적인 단계는 다음과 같습니다.

1. 해당 도메인 이름의 CNAME을 새 버전 CNAME으로 변경하려면 티켓을 제출하십시오.

2. 사용자의 도메인 이름 확인 서비스 제공 업체에서 새 버전 CNAME으로 전환하십시오.

  
