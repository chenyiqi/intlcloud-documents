### 커널 마이너 버전 업그레이드는 어떻게 하나요?
TencentDB for MySQL은 커널 마이너 버전을 자동 및 수동으로 업그레이드하도록 지원합니다. 커널 마이너 버전의 업그레이드를 통해 문제 복구 등의 새로운 기능을 사용할 수 있으며 성능 또한 향상됩니다.
>?기본 버전 인스턴스는 현재 커널 마이너 버전 업그레이드를 지원하지 않습니다.
>
- **자동 업그레이드 트리거 시나리오**:
 - 시나리오1: TencentDB for MySQL에 심각한 버그나 보안 취약점이 발생했을 때, 시스템에서 점검 시간 안에 데이터베이스 커널 마이너 버전의 업그레이드를 진행하며, 사전에 내부 메시지, SMS 등의 방식으로 업그레이드 공지를 푸시합니다.
 - 시나리오2: TencentDB for MySQL에 인스턴스 마이그레이션을 트리거하는 작업(인스턴스 사양 업/다운그레이드, 디스크 용량 확장 및 축소, 데이터베이스 버전 업그레이드 등)이 발생했을 때, 시스템에서 인스턴스를 최신 커널 마이너 버전으로 업그레이드합니다.
- **수동 업그레이드 시나리오**:
자동 업그레이드 시나리오 외에도, 사용자는 콘솔에서 커널 마이너 버전을 수동으로 업그레이드할 수 있습니다. 자세한 내용은 [커널 마이너 버전 업그레이드](https://intl.cloud.tencent.com/document/product/236/36816)를 참조 바랍니다.

>!
>- 인스턴스를 최신 커널 마이너 버전으로 업그레이드하면 다시 다운그레이드할 수 없습니다.
>- 데이터베이스의 버전 업그레이드, 설정 변경 등의 작업으로 MySQL 인스턴스 연결이 몇 초간 끊길 수 있으니, 서비스의 재연결 메커니즘을 확보하시기 바랍니다.

### 커널 마이너 버전은 어떻게 조회하나요?
1. [CVM](https://intl.cloud.tencent.com/document/product/213/10517)에 로그인한 뒤, 다음 명령어를 실행하여 MySQL 인스턴스에 로그인합니다. 자세한 내용은 [Linux CVM에서 MySQL에 액세스](https://intl.cloud.tencent.com/document/product/236/3130)을 참조 바랍니다.
 내부 네트워크 액세스 시:
```
mysql -h hostname -u username -p
```
 외부 네트워크 액세스 시:
```
mysql -h [CDB IP] -P[CDB 포트 번호] -uroot -p
```
2. 다음 명령어를 실행하여 MySQL 인스턴스의 버전을 조회합니다.
```
show variables like 'version_comment';
```
![](https://main.qcloudimg.com/raw/abea801e026190a0cbfd763c5d4862bd.png)

