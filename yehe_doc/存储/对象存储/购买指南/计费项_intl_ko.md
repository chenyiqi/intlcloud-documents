COS의 과금 항목은 [스토리지 용량 과금](#jf1), [요청 과금](#jf2), [데이터 검색 과금](#jf3), [트래픽 과금](#jf4), [관리 기능 과금](#jf5)이 있습니다. 각 과금 항목의 자세한 설명은 다음과 같습니다.


> ?COS는 액세스 빈도 수와 재해 복구 수준에 따라 INTELLIGENT TIERING, 표준 스토리지, 표준IA 스토리지, CAS, DEEP ARCHIVE와 같이 다양한 객체에 맞는 스토리지 유형을 제공합니다. 자세한 사항은 [COS 유형](https://intl.cloud.tencent.com/document/product/436/30925)의 소개를 참조하시기 바랍니다.

## 제품 가격

과금 항목에 대한 설명과 [제품 가격](https://intl.cloud.tencent.com/document/product/436/6239)을 숙지한 뒤 과금액을 직접 추산할 수 있으며, [COS 가격 계산기](https://buy.cloud.tencent.com/price/cos/calculator)로 필요에 따른 과금액을 계산해 볼 수 있습니다.



<span id="jf1"></span>

## 스토리지 용량 과금

| 과금 항목   | 적용 스토리지 유형&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     | 과금 항목 정의                                                   | 과금 관련 설명                                                     |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 스토리지 용량 | INTELLIGENT TIERING<br>표준 스토리지<br>표준IA 스토리지<br>CAS<br>DEEP ARCHIVE | 스토리지 용량은 사용자의 데이터가 점유하는 실제 스토리지 용량으로 사용자 데이터가 실제로 점유하는 스토리지 용량에 근거해 과금액을 계산함 | <li>월 결산<br><li>스토리지 용량 과금액 = 스토리지 용량 단가 x 월 스토리지 용량<br><li>월 스토리지 용량 = 당월 ‘일일 스토리지 용량’ 총합 / 당월 일수<br><li>일일 스토리지 용량 = 당일 ‘5분당 스토리지 용량’ 총합 / 288(샘플 카운팅) |



#### 과금 유의 사항

1. 표준IA 스토리지 유형: 스토리지 기간이 30일 미만이면 30일로 계산합니다. 개별 스토리지 파일이 64KB 미만이면 64KB로 계산하며, 64KB 이상이면 실제 크기에 근거해 계산합니다.
2. CAS 유형: 공유 클라우드 리전에 한해 지원합니다. 스토리지 기간이 90일 미만이면 90일로 계산합니다. 개별 스토리지 파일이 64KB 미만이면 64KB로 계산하며, 64KB 이상이면 실제 크기에 근거해 계산합니다.
3. DEEP ARCHIVE 유형: 베이징, 상하이, 광저우, 청두 리전에 한해 지원합니다. 스토리지 기간이 180일 미만이면 180일로 계산합니다. 개별 스토리지 파일이 64KB 미만이면 64KB로 계산하며, 64KB 이상이면 실제 크기에 근거해 계산합니다.
4. 버전 컨트롤 기능의 비활성화 상태에서 **동일 명칭**의 표준IA 스토리지 또는 CAS 유형의 객체를 업로드할 경우, 업로드 완료 뒤 COS가 기존의 동일 명칭 객체를 삭제합니다. 이때도 **객체 사전 삭제**로 인해 발생한 스토리지 과금이 있습니다.
5. INTELLIGENT TIERING 유형은 데이터 레이어에 따라 스토리지 용량 과금액이 달라집니다. 고빈도 액세스 레이어의 스토리지 용량 과금 관련 사항은 표준 스토리지를 참조하고, 저빈도 액세스 레이어의 스토리지 용량 과금 관련 사항은 표준IA 스토리지를 참조하십시오.

<span id="jf2"></span>

## 요청 과금

요청 과금은 **사용자 요청 횟수**와 사용자의 기능 설정 후 발생한 **백그라운드 요청 횟수**로 인한 금액이 포함됩니다.

- 사용자 요청 횟수: 사용자가 API, SDK 또는 콘솔 등을 이용해 데이터를 업로드, 다운로드, 조회, 삭제하는 행위는 사실 Tencent Cloud의 COS로 요청 명령을 보내 실행되는 것입니다.
- 백그라운드 요청 횟수: 라이프사이클 전환, 보관 기간 만료 후 표준 스토리지 사본의 삭제, 리전 간 복제 시 읽기 및 쓰기 요청, 인벤토리 보고서 제출 등 요청 횟수입니다.

| 과금 항목                   | 적용 스토리지 유형&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;     | 과금 항목 정의                                                 | 과금 관련 설명                                                     |
| ------------------------ | ------------------------------------------------------------ | ---------------------------------------------------------- | ------------------------------------------------------------ |
| 요청 횟수                 | INTELLIGENT TIERING<br>표준 스토리지<br>표준IA 스토리지<br>CAS<br>DEEP ARCHIVE | 요청 명령 발송 횟수에 근거해 요청 횟수 계산                       | <li>월 결산<br><li>월간 누적 요청 횟수가 1만 번 미만이면 1만 번으로 계산<br><li>요청 과금액 = 요청 1만 회당 단가 x 월간 누적 요청 횟수 / 10000 |
| 스마트 티어링 모니터링 횟수         | INTELLIGENT TIERING                                                 | INTELLIGENT TIERING 유형 데이터의 객체 모니터링 요금으로 데이터 액세스 현황 모니터링시 발생 | <li>월 결산<br><li>월 평균 모니터링 횟수가 1만 번 미만이면 1만 번으로 계산<br><li>객체 모니터링 과금액 = 모니터링 만 회당 단가 x 월간 누적 모니터링 횟수 / 10000 |
| 고급 보관 데이터 검색 요청 횟수 | DEEP ARCHIVE                                                | DEEP ARCHIVE 유형의 파일이 복구 실행시 발생하는 요청 횟수       | <li>월 결산<br><li>월간 누적 복구 요청 횟수가 1만 번 미만이면 1만 번으로 계산<br><li>데이터 검색 요청 과금액 = 요청 1만 회당 단가 x 월간 누적 요청 횟수 / 10000 |

#### 과금 유의 사항

1. 요청 성공 여부에 관계없이 모두 요청이 발생한 것으로 간주합니다.
2. 요청 과금은 1만 회가 최소 단위입니다. 따라서 요청의 성공 여부에 관계없이 월간 누적 요청 횟수가 1만 번 미만이면 1만 번으로 계산합니다.
3. CAS와 DEEP ARCHIVE 유형 데이터는 읽기와 다운로드 기능을 지원하지 않습니다. CAS 유형 데이터를 표준 스토리지 유형으로 복구(또는 활성화)할 경우, 해당 표준 스토리지 유형의 데이터에 대해 과금이 발생합니다. DEEP ARCHIVE 유형 데이터를 복구(또는 활성화)할 경우, 고급 보관 요청 단가에 따라 과금됩니다.
4. DEEP ARCHIVE 유형 데이터를 복구할 경우, 별도의 데이터 검색 요청 비용이 발생합니다. 복구 모드별로 요청 비용은 상이합니다.


<span id="jf3"></span>

## 데이터 검색 과금

<table>
   <tr>
      <th>과금 항목</td>
      <th>적용 스토리지 유형</td>
      <th>과금 항목 정의</td>
      <th>과금 관련 설명</td>
   </tr>
   <tr>
      <td rowspan=2>데이터 검색량</td>
      <td>표준IA 스토리지<br>CAS</td>
      <td rowspan=2>읽는 데이터 크기에 근거해 데이터 검색량 계산</td>
      <td><li>월 결산<br><li>데이터 검색 과금액 = GB당 단가 x 월간 데이터 검색량</td>
   </tr>
   <tr>
      <td>DEEP ARCHIVE</td>
      <td><li>일 결산<br><li>데이터 검색 과금 = GB당 단가 x 일일 데이터 검색량</td>
   </tr>
</table>


#### 과금 유의 사항

**표준IA 스토리지**, **CAS** 및 **DEEP ARCHIVE** 유형은 콜드 데이터 스토리지 유형입니다. 표준IA 스토리지 데이터의 경우 데이터를 읽기 또는 다운로드하려면 백그라운드에서 우선 데이터를 검색해야 합니다. 보관 유형의 데이터는 읽기와 다운로드가 불가능하며, 이 경우 데이터 검색을 데이터 활성화(보관 데이터를 표준 데이터로 복구하는 과정)라고도 합니다.


<span id="jf4"></span>

## 트래픽 과금

트래픽은 사용자가 스토리지 데이터를 읽을 때 발생하는 데이터 플로의 누적 값으로 트래픽 누적 값에 따라 과금합니다.

<table>
   <tr>
      <th>과금 항목</th>
      <th>적용 스토리지 유형</th>
      <th>과금 항목 정의</th>
      <th>과금 관련 설명</th>
   </tr>
   <tr>
      <td>외부 네트워크 업스트림 트래픽</td>
      <td rowspan="7" nowrap="nowrap">INTELLIGENT TIERING<br>표준 스토리지<br>표준IA 스토리지<br>CAS<br>DEEP ARCHIVE</td>
      <td>인터넷으로 데이터를 클라이언트에서 COS로 전송할 때 발생하는 트래픽</td>
      <td>무료</td>
   </tr>
   <tr>
      <td>내부 네트워크 업스트림 트래픽</td>
      <td>Tencent Cloud 내부 네트워크로 데이터를 클라이언트에서 COS로 전송할 때 발생하는 트래픽</td>
      <td>무료</td>
   </tr>
   <tr>
      <td>외부 네트워크 다운스트림 트래픽</td>
      <td>인터넷으로 데이터를 COS에서 클라이언트로 전송할 때 발생하는 트래픽</td>
      <td><li>일 결산<br><li>외부 네트워크 다운스트림 트래픽 = GB당 단가 x 일일 누적 외부 네트워크 다운스트림 트래픽</td>
   </tr>
   <tr>
      <td>내부 네트워크 다운스트림 트래픽</td>
      <td>Tencent Cloud 내부 네트워크로 데이터를 COS에서 클라이언트로 전송할 때 발생하는 트래픽</td>
      <td>무료</td>
   </tr>
   <tr>
      <td>CDN Origin-pull 트래픽</td>
      <td>데이터를 COS에서 Tencent Cloud CDN의 엣지 노드로 전송할 때 발생하는 트래픽</td>
      <td><li>일 결산<br><li>CDN Origin-pull 트래픽 과금액 = GB당 단가 x 일일 누적 CDN Origin-pull 트래픽</td>
   </tr>
   <tr>
      <td>리전 간 트래픽 복제</td>
      <td>데이터를 한 리전의 버킷에서 다른 리전의 버킷으로 전송할 때 발생하는 트래픽</td>
      <td><li>일 결산<br><li>리전 간 복제 트래픽 과금액 = GB당 단가 x 일일 누적 리전 간 복제 트래픽</td>
   </tr>
   <tr>
      <td>글로벌 가속 트래픽</td>
      <td>사용자가 글로벌 가속 기능을 활성화한 뒤 전송 가속 도메인으로 데이터를 전송할 때 발생하는 트래픽입니다. 전송 가속 도메인은 업스트림 트래픽과 다운스트림 트래픽으로 나뉩니다. <br><li>업스트림 트래픽: 사용자가 전송 가속 도메인으로 로컬 데이터를 COS에 전송할 때 발생하는 트래픽<br><li>다운스트림 트래픽: 사용자가 전송 가속 도메인으로 데이터를 조회하거나 로컬로 다운로드할 때 발생하는 트래픽</td>
      <td><li>일 결산<br><li>글로벌 가속 트래픽 과금액 = GB당 단가 x 일일 누적 글로벌 가속 트래픽 </td>
   </tr> 
</table>

#### 과금 유의 사항

1. 보관 유형 데이터는 읽기와 다운로드가 불가능합니다. 하지만 데이터를 표준 스토리지 유형으로 복구(또는 활성화)한 뒤 읽을 때 발생하는 트래픽은 표준 스토리지에 포함됩니다.
2. 3rd party CDN을 사용해 Tencent Cloud COS로 Origin-pull할 경우, **외부 네트워크 다운스트림 트래픽**이 발생합니다.
3. Tencent Cloud의 CDN 가속 활성화 이후 **Tencent Cloud CDN 가속 도메인**으로 클라이언트로부터 COS 데이터를 열람하거나 다운로드할 때 발생하는 트래픽은 CDN Origin-pull 트래픽에 속합니다.
4. 사용자가 **객체 링크**로 객체를 직접 다운로드하거나 **정적 웹 사이트 원본 서버**로 객체를 열람할 때 발생하는 트래픽은 외부 네트워크 다운스트림 트래픽에 속합니다. 
5. 인터페이스 복사 또는 리전 간 복제 기능으로 데이터를 한 리전 버킷에서 다른 리전 버킷으로 전송할 때 발생하는 트래픽은 리전 간 복제 트래픽입니다. 리전 간 복제 트래픽은 소스 버킷이 속한 리전의 단가를 기준으로 과금됩니다.
6. INTELLIGENT TIERING 유형의 데이터로 인해 발생한 트래픽 과금은 전환 이후의 스토리지 유형과 동일합니다.

> ?동일 리전 내의 Tencent Cloud 제품은 자동으로 내부 네트워크 액세스가 실행되므로 트래픽에 대한 과금이 발생하지 않습니다. 클라우드 서비스 내부 네트워크 액세스 판별 방법은 [내부 네트워크 및 외부 네트워크 액세스](https://intl.cloud.tencent.com/document/product/436/30613)를 참조하십시오.


#### 트래픽 방향

다음은 사용자가 Tencent Cloud의 CDN 가속 도메인을 활성화하거나 비활성화한 경우 데이터를 COS에서 사용자에게 전송 시 발생하는 트래픽 과금에 관한 사항입니다.
![](https://main.qcloudimg.com/raw/a7e5562e9404ba265cb4797a59521d28.png)

<span id="jf5"></span>

## 관리 기능 과금

관리 기능 과금이란 사용자가 관리 기능(인벤토리 또는 인덱스 기능)을 활성화한 후 사용하면서 발생한 금액입니다.



<table>
<thead>
<tr>
<th>과금 항목</th>
<th>적용 스토리지 유형</th>
<th>과금 항목 정의</th>
<th>과금 관련 설명</th>
</tr>
</thead>
<tbody><tr>
<td>인벤토리 기능 과금</td>
<td nowrap="nowrap">스토리지 유형과 별개</td>
<td>사용자가 인벤토리 기능을 활성화한 뒤 버킷 객체 목록을 나열할 때 발생하는 금액</td>
<td><li>일 결산<br></li><li>객체 1백만 개 나열 시마다 과금</li></td>
</tr>
<tr>
<td >인덱스 기능 과금</td>
<td>표준 스토리지<br>표준IA 스토리지</td>
<td>사용자가 인덱스 기능을 활성화한 뒤 객체를 스캔할 때 발생하는 금액</td>
<td><li>일 결산<br></li><li>스캔한 데이터 크기에 따라 계산</li></td>
</tr>
<tr>
<td>배치 과금</td>
<td nowrap="nowrap">스토리지 유형과 별개</td>
<td>사용자가 배치 기능을 활성화하면 COS가 생성된 작업 수와 객체 처리량에 따라 과금</td>
<td><li>일 결산<br></li><li>생성된 작업 수와 객체 처리량에 따라 계산</li></td>
</tr>
<tr>
<td>객체 태그 과금</td>
<td nowrap="nowrap">스토리지 유형과 별개</td>
<td>사용자가 객체 태그 기능을 활성화하면 COS가 객체 태그 양에 따라 과금</td>
<td><li>일 결산<br></li><li>설정한 객체 태그 양에 따라 계산</li></td>
</tr>
</tbody></table>

#### 과금 유의 사항

INTELLIGENT TIERING 유형의 데이터는 인덱스 및 배치 기능을 현재 지원하지 않습니다.

