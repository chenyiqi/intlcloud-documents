## 작업 시나리오

도메인 이름을 Tencent Cloud CDN 가속화 서비스에 액세스하고, 액세스한 도메인 이름을 조회, 활성화, 비활성화할 수 있습니다.
[CDN 콘솔](https://console.cloud.tencent.com/cdn)에 접속한 후, 메뉴에서 [Domain Management]를 선택해 작업을 진행합니다.

Tencent Cloud CDN 서비스는 사용자 정의 도메인 이름 리스트 페이지를 지원합니다. 해당 페이지에서 다양한 기본 설정을 표시, 순서 변경, 도메인 이름 가속 서비스 일괄 활성화/비활성화를 할 수 있어 보다 효율적인 작업이 가능합니다.

## 리스트 작업 가이드

### 사용자 정의 리스트 표시

검색창 우측의 <img src ="https://main.qcloudimg.com/raw/c8528c5a51cbea35ecb7e0414b51267e.png" style ="margin:0" data-nonescope="true"> 이미지를 클릭해 리스트 설정 선택창을 여십시오.
![](https://main.qcloudimg.com/raw/790ae4b6c47b8b5ccd72e517701d34db.png)
선택한 메뉴 보이기, 지정 필드 보이지 않기, 필드 표시 순서 변경을 지원합니다.
![](https://main.qcloudimg.com/raw/1d123a3948ee2450204fa8cc78a11a36.png)

도메인 이름 관리 리스트 페이지에서 사용자 정의 설정은 다음 설정 필드와 같습니다.

- 도메인 이름: 필수 선택, 보이지 않기 설정을 할 수 없음
- 작업 유형: 정적 가속화, 다운로드 가속, 스트리밍 가속
- 상태: 도메인 이름 상태가 활성화, 비활성화, 배정 중인 경우
- CNAME: 해당 도메인 이름의 CNAME
- 액세스 방식: 외부 원본 서버에서 직접 액세스하거나 객체 스토리지(COS 원본)에 액세스
- 서비스 지역: 중국, 해외, 전 세계
- 서브 프로젝트: 도메인 이름이 소속된 프로젝트 명칭
- 메인 원본 서버 설정: 메인 원본 서버 주소
- 스탠바이 원본 서버 설정: 스탠바이 원본 서버 주소
- HTTPS 설정: 활성화/비활성화
- 원본 가져오기 프로토콜: HTTP 원본 가져오기, HTTPS 원본 가져오기 프로토콜을 따름
- 원본 가져오기 Host: 원본 가져오기 도메인 설정
- 필터링 매개변수: 활성화/비활성화
- 태그: 사용자 정의 키 값, 리소스 분류 관리에 사용

### 리스트 내보내기 설정

검색창 우측의 <img src ="https://main.qcloudimg.com/raw/16b5654ecd298d7cadc63b243413a31d.png" style ="margin:0" data-nonescope="true"> 이미지를 클릭하면, 도메인 이름 리스트를 엑셀 형식으로 내보낼 수 있습니다. 한 번에 최대 1,000개의 도메인 이름을 내보낼 수 있습니다.
![](https://main.qcloudimg.com/raw/8065bb602460bf3fcf9a8dbec9c3bd67.png)

## 도메인 이름 작업 가이드

CDN 콘솔에서 액세스한 CDN의 가속화된 도메인 이름으로 서브 프로젝트의 서비스 시작, 종료, 삭제 및 수정 등의 작업을 수행할 수 있습니다.

<span ID="close"></span>

### 가속화 서비스 비활성화

가속화 서비스 비활성화 후, CDN 가속 노드에서 도메인 이름과 관련된 모든 설정이 해제됩니다. 이때 해당 도메인 이름에 액세스하면 그대로 CDN 노드에 진입하며, 404 Not Found 페이지가 출력됩니다. 따라서 도메인 이름을 비활성화하기 전에 도메인 이름의 경로가 Tencent Cloud CDN이 배정한 CNAME 주소가 아닌지 확인해야 합니다.

> !
> - 활성화한 가속 도메인 이름은 비활성화할 수 있지만, 이미 배정 중인 도메인 이름은 비활성화할 수 없습니다.
> - 도메인 이름 비활성화 시의 설정은 보존되며, 다음 활성화 때 즉시 적용됩니다.
> - 도메인 이름 가속화 서비스를 완전히 비활성화한 후에는 리소스 소비가 발생하지 않습니다.

도메인 이름 상태가 [활성화]일 경우, 우측의 [자세히]를 클릭해 도메인 이름을 비활성화하거나, [사용 중]인 도메인 이름을 선택해 상단의 [기타 작업]에서 비활성화할 수 있습니다.

![](https://main.qcloudimg.com/raw/6536bf6c02870b792031a2c65645c31a.png)

### 가속화 서비스 활성화

도메인 이름 상태가 [비활성화]일 경우, 가속화 서비스를 활성화하여 도메인 이름에 배정된 모든 노드에 다시 가속화를 진행할 수 있습니다.

도메인 이름 상태가 [비활성화]일 경우, 우측의 [자세히]를 클릭해 도메인 이름을 비활성화하거나, [비활성화]인 도메인 이름을 선택해 상단의 [기타 작업]에서 활성화할 수 있습니다.

>! 활성화 상태인 도메인 이름이 3개월 동안 업데이트되거나 리소스 소비가 발생하지 않을 경우, 사용하지 않는 도메인 이름으로 간주되어 Tencent Cloud CDN 시스템에서 가속화 서비스를 자동 비활성화합니다.

![](https://main.qcloudimg.com/raw/fd6d029c82e516965ea6e093ef41c9f5.png)


<span ID ="del"></span>
## 가속화 도메인 이름 삭제

도메인 이름 상태가 [비활성화]일 경우, 우측의 [More actions]를 클릭해 도메인 이름을 삭제할 수 있습니다. 삭제 시 해당 도메인 이름의 설정도 함께 삭제되어 관련 데이터를 확인할 수 없게 되므로 신중히 선택하십시오.
![](https://main.qcloudimg.com/raw/bc58fc9c225efb79a0ec1454b6748e1c.png)
