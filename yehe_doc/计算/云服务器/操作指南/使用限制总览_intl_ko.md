## CVM 인스턴스 구매 시의 계정 제한

- 사용자는 Tencent Cloud 계정을 등록해야 하며, 등록은 [Tencent Cloud 등록](https://intl.cloud.tencent.com/document/product/378/17985)을 참조할 수 있습니다.
- 사용자는 실명 인증을 진행해야 하며, 인증 자격은 [실명 인증 가이드](https://intl.cloud.tencent.com/document/product/378/3629)를 참조할 수 있습니다.
- 종량제 CVM을 생성할 때 시스템은 1시간 동안의 호스트 비용을 동결하므로, 결제를 위해 충분한 계정 잔액을 확보해야 합니다.

## CVM 인스턴스의 사용 제한

- 버츄얼 소프트웨어 설치와 버츄얼 재실행(VMware 또는 Hyper-V를 설치하여 사용하는 경우)은 지원하지 않습니다.
- 사운드 카드 애플리케이션을 지원하지 않으며, 외장 하드웨어 장치(USB, 외장 디스크, 은행 USB-KEY 등에 마운트하는 경우)를 직접 탑재할 수 없습니다.
- 공용망 게이트웨이는 현재 Linux 시스템만 지원합니다.

## CVM 인스턴스의 구매 제한

- 사용자당 각 가용존에서 구매 가능한 종량제 CVM 인스턴스의 **총 수량**은 30개입니다.
- 자세한 내용은 [CVM 인스턴스 구매 제한](https://intl.cloud.tencent.com/document/product/213/2664)을 참조 바랍니다.


## 이미지 관련 제한

- 공용 이미지는 현재 사용 제한이 없습니다.
- 사용자 정의 이미지: 리전마다 최대 10개의 사용자 정의 이미지를 지원합니다.
- 공유 이미지: 각 사용자 정의 이미지는 최대 50명의 Tencent Cloud 사용자에게 공유될 수 있으며, 상대방 계정의 동일 리전 내에서만 공유할 수 있습니다.
- 자세한 내용은 [이미지 유형 제한](https://intl.cloud.tencent.com/document/product/213/4941)을 참조 바랍니다.

## EIP 관련 제한

#### 할당 제한

| 리소스 | 제한 |
|---------|:---------:|
| 각 Tencent Cloud 계정별 리전(Region)에 할당된 EIP 개수 | 20개 |
| 각 Tencent Cloud 계정별 리전의 일일 주문 횟수	 | 쿼터수 \* 2회 |
| EIP 바인딩 해제 시 계정당 일일 무료 공인 IP를 재할당 가능 횟수 | 10회 |

#### CVM의 공인 IP 바인딩 제한

2019년 9월 18일(포함)부터 CPU 구성의 차이에 따라, 단일 CVM의 공인 IP 바인딩 수량 최댓값이 아래 표와 같이 변경되었습니다.
> 2019년 9월 18일 0시 전에 구매한 CVM은 이 제한을 받지 않으며 해당 CVM이 지원하는 공인 IP 바인딩 수량은 사용자의 서버가 지원하는 [개인 IP 수량](https://intl.cloud.tencent.com/document/product/576/18527)과 동일합니다.
>

| CVM의 CPU 수 | 바인딩 가능한 공인 IP 수량 최댓값(일반 공인 IP와 EIP 포함) |
|---------|---------|
| CPU：1 - 5 | 2 |
| CPU：6 - 11 | 3 |
| CPU：12 - 17 | 4 |
| CPU：18 - 23 | 5 |
| CPU：24 - 29 | 6 |
| CPU：30 - 35 | 7 |
| CPU：36 - 41 | 8 |
| CPU：42 - 47 | 9 |
| CPU：≥ 48 | 10 |

## ENI 관련 제한

CPU와 메모리 구성에 따라 CVM이 바인딩할 수 있는 ENI 수와 단일 ENI가 바인딩할 수 있는 개인 IP 수가 크게 다르며, ENI 및 단일 ENI IP 할당 수는 아래 표와 같습니다.
> 단일 ENI의 IP 바인딩 수량은 ENI가 바인딩할 수 있는 IP 수의 최댓값만을 의미합니다. 최댓값에 따라 EIP 할당을 제공한다고 보장할 수 없으며, 계정의 EIP 할당은 [EIP 사용 제한](https://intl.cloud.tencent.com/document/product/213/5733) 에 따라 제공됩니다.

| CVM 구성              | ENI 수| 단일 ENI의 개인 IP 바인딩 수 |
| ------------------- | :---- | :------ |
| CPU: 싱글코어   </br>메모리: 1GB    | 2     | 2       |
| CPU: 싱글코어   </br>메모리: > 1GB   | 2     | 6       |
| CPU: 듀얼코어             | 2     | 10      |
| CPU: 쿼드코어   </br>메모리: < 16GB | 4     | 10      |
| CPU: 쿼드코어   </br>메모리: > 16GB | 4     | 20      |
| CPU: 옥타코어 - 도데카코어          | 6     | 20      |
| CPU: > 도데카코어           | 8     | 30      |


## 대역폭 관련 제한

- Outbound 대역폭 최댓값(다운스트림 대역폭):
<table>
    <tr>
       <th rowspan="2"><b>네트워크 과금 방식</b></th> 
       <th colspan="2" ><b>인스턴스</b></th>
       <th rowspan="2"><b>대역폭 최댓값의 설정 가능 범위(Mbps)</b></th>	
   </tr>
    <tr>
       <th><b>인스턴스 과금 방식</b></th> 
       <th><b>인스턴스 구성</b></th> 
    </tr>
	<tr>
	      <td>트래픽 과금</td> 
        <td >종량제 인스턴스</td> 
        <td >ALL</td> 
				<td>0 - 100</td>    
   </tr>
	 <tr>
		    <td>대역폭 과금</td> 
        <td >종량제 인스턴스</td> 
        <td >ALL</td> 
				<td>0 - 100</td>      
   </tr>
    <tr>
		    <td>공유 대역폭</td> 
        <td colspan="2">ALL</td> 
        <td>0 - 200 또는 속도 제한 없음</td>    
    </tr>
</table>

- 가입 대역폭 최댓값(업스트림 대역폭):
	- 사용자가 구매한 고정 대역폭이 10Mbps보다 높은 경우, Tencent Cloud는 구매한 대역폭과 동일한 외부 네트워크 인바운드 대역폭을 할당합니다.
	- 사용자가 구매한 고정 대역폭이 10Mbps보다 낮은 경우, Tencent Cloud는 10Mbps의 외부 네트워크 인바운드 대역폭을 할당합니다.

## 디스크 관련 제한

<table>
	<tr><th>제한 유형</th><th>제한 설명</th></tr>
	<tr><td>CBS 능력</td><td>2018년 5월부터 CVM과 함께 구매하는 데이터 디스크는 모두 탄력적인 CBS이며 CVM에서 언마운트한 후 다시 마운트할 수 있습니다. 본 기능은 모든 <a href="https://intl.cloud.tencent.com/document/product/213/35071">가용존</a>에서 사용할 수 있습니다. </td></tr>
	<tr><td>CBS 성능 제한</td><td> I/O 성능이 동시에 적용됩니다. <br/>예를 들어 1TB의 SSD CBS가 최대 랜덤 IOPS 26,000에 도달한다면 읽기 IOPS와 쓰기 IOPS 모두 해당 값에 도달할 수 있음을 의미합니다. 동시에 여러 성능 제한으로 인하여 해당 예시에서 block size가 4KB/8KB인 I/O를 사용하면 IOPS 최대치에 도달할 수 있지만, block size가 16KB인 I/O를 사용하면 IOPS 최대치에 도달할 수 없습니다(처리량은 260MB/s의 제한에 도달함).</td></tr>
	<tr><td>단일 CVM이 마운트할 수 있는 탄력적인 CBS 수량</td><td>는 최대 20블록입니다.</td></tr>
	<tr><td>단일 리전의 스냅샷 할당</td><td>64 + 리전 내 CBS 수량 * 64(개).</td></tr>
	<tr><td>CBS이 마운트할 수 있는 CVM 제한</td><td>CVM과 CBS는 반드시 동일 가용존에 있어야 합니다.</td></tr>
	<tr><td>스냅샷 롤백 제한</td><td>스냅샷 데이터는 스냅샷을 생성한 소스 CBS로만 롤백할 수 있습니다.</td></tr>
	<tr><td>스냅샷 생성 CBS 유형 제한</td><td>데이터 디스크 스냅샷으로만 새로운 탄력적인 CBS를 생성할 수 있습니다.</td></tr>
	<tr><td>스냅샷이 생성하는 CBS 크기 제한</td><td>스냅샷으로 생성한 새로운 CBS의 용량은 반드시 스냅샷 소스 CBS의 용량과 같거나 커야 합니다.</td></tr>
</table>


## 보안 그룹 관련 제한

- 보안 그룹은 리전별로 구분하므로, 한 CVM은 동일 리전의 보안 그룹에만 바인딩할 수 있습니다.
- 보안 그룹은 [네트워크 시나리오](https://intl.cloud.tencent.com/document/product/213/5227)의 모든 CVM 인스턴스에 적용됩니다.
- 각 사용자는 리전별, 항목별로 최대 50개의 보안 그룹을 설정할 수 있습니다.
- 한 보안 그룹의 인바운드 또는 아웃바운드 액세스 정책으로 각각 최대 100건까지 설정할 수 있습니다.
- 하나의 CVM을 여러 보안 그룹에 추가할 수 있으며, 하나의 보안 그룹을 여러 CVM에 동시에 연결할 수 있습니다.
- **기본 네트워크**의 CVM이 바인딩한 보안 그룹은 Tencent Cloud의 인/아웃 관계형 데이터베이스(TencentDB) , 탄력적 캐시(Redis와 Memcached)의 데이터 패키지를 **필터링할 수 없습니다.** 이러한 인스턴스의 트래픽을 필터링해야 한다면 iptables 사용하여 구현할 수 있습니다.
- 관련 할당 제한 다음과 같습니다.
<table>
<tr><th>기능 설명</th><th>제한</th></tr>
<tr><td>보안 그룹 개수</td><td>50개/리전</td></tr>
<tr><td>보안 그룹 규칙 수</td><td>100건/인바운드, 100건/아웃바운드</td></tr>
<tr><td>단일 보안 그룹에 연결된 CVM 인스턴스 수</td><td>100개</td></tr>
<tr><td>각 CVM 인스턴스가 연결할 수 있는 보안 그룹 수</td><td>5개</td></tr>
<tr><td>각 보안 그룹의 보안 그룹 ID 참조 테이블 규칙 조항 수</td><td>10조</td></tr>
</table>

## VPC 관련 제한

| 리소스| 제한(개) |
|---------|---------|
| 각 계정, 각 리전 내의 VPC 수 | 5	 |
| 각 VPC 내의 서브넷 수 | 10 |
| 각 VPC가 지원하는 기본 네트워크 호스트 연결 수| 100 |
| 각 VPC 내의 라우팅 테이블 수 | 10 |
| 각 서브넷의 라우팅 테이블 연결 수 | 1 |
| 각 라우팅 테이블의 라우팅 정책 수 | 100 |
| 각 VPC의 HAVIP 기본 쿼터수 | 10 |

