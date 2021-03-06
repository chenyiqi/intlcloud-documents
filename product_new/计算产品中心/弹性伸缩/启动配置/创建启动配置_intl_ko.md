AS는 용량을 확장할 때 어떤 사양으로 CVM을 생성할지 사전에 알고 있어야 하며 미러 이미지, 데이터 디스크의 데이터, 용례 사양, 키 쌍, 보안 그룹 및 블록 스토리지 장치 등 관련 리소스를 미리 지정해야 합니다.

작동 사양은 하나의 템플릿이며 자동 확장될 때 템플릿에 따라 기기가 산출됩니다.**작동 사양을 생성하면 기기는 산출되지 않으므로 안심하고 무료로 사용하십시오.**

[Auto Scaling 콘솔](https://console.cloud.tencent.com/autoscaling/config)에 로그인하고 사이드바의 [작동 사양]을 클릭하십시오.

### step 1. 리전 선택

화면 상단의 메뉴에서 스케일링 그룹에 적합한 필요 리전을 선택하십시오.

> 참고:
>스케일링 그룹이 바인딩될 Cloud Virtual Machine 소재 리전, 작동 사양 및 스케일링 그룹은 모두 리전 옵션이므로 주의하여 선택해야 합니다. 예를 들어 작동 사양의 리전이 광저우인 경우, 광저우의 스케일링 그룹만 바인딩할 수 있고 자동 추가되는 CVM도 광저우의 CVM입니다.

![](https://main.qcloudimg.com/raw/014744e64c1b5bb3f251a478baa84540.png)

### step 2. 파라미터 지정

[생성]을 클릭하고 지시에 따라 작동 사양을 생성하며 절차는 Cloud Virtual Machine를 구입할 때와 같습니다.

1. "프런트 엔드 서버 클러스터 사양 A"와 같은 [사양 이름]을 입력하십시오.

2. 1 코어 1G, 즉 1 코어 CPU, 1G 메모리와 같은 모델을 선택하십시오.

3. 미러 이미지를 선택하시십오. "공용 미러 이미지" 또는 이미 서비스를 배포한 "사용자 지정 이미지"를 선택할 수 있습니다.
기기 생성 후 바로 사용하려면 비지니스 애플리케이션을 사용자 지정 이미지에 배포하는 것을 권장합니다. ** 동시에 AS 용량 확장된 기기가 자동화하도록 미러이미지의 비지니스 애플리케이션을 작업 시스템과 함께 시작하도록 설정해야 합니다 **.

4. 시스템 디스크 크기 및 데이터 디스크 크기를 선택하십시오.
기기를 활성화한 후 데이터 디스크의 자체 데이터를 원한다면 기기 생성 후 데이터 디스크 스냅숏을 지정하면 스냅숏의 데이터를 산출할 수 있습니다.
> 참고:
> - 스케일링 그룹의 기기는 일반적으로 상태 비저장으로 편의를 위해 기기 데이터를 사용자 지정 이미지에 넣을 것을 권장합니다. 시스템 디스크 용량이 크지 않으면 티켓을 신청하여 높은 용량의 시스템 디스크를 신청할 수 있습니다.
> - 데이터 디스크를 사용하여 데이터를 저장하려면 자동으로 탑재되도록 설정하고 해당 확장은 수동으로 조작할 필요가 없습니다. [자세한 방법](https://intl.cloud.tencent.com/document/product/377/4166)을 참조하십시오.

5. 대역폭 선택은 Cloud Virtual Machine를 구매할 때의 작업과 유사합니다.

6. 사용자 이름, 비밀번호 및 보안 그룹을 설정하십시오.

7. [완료]를 클릭하십시오.

8. 작동 사양을 기반으로 스케일링 그룹을 생성합니다. 작동 사양은 용량 확장 시 어떤 기기를 생성할지를 결정하고 스케일링 그룹은 언제 용량을 확장할지를 결정합니다.
