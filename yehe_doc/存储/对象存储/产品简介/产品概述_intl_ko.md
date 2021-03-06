Cloud Object Storage(COS)는 Tencent Cloud가 제공하는 대용량 파일을 저장하는 분산형 스토리지 서비스로, 사용자는 네트워크를 통해 수시로 데이터를 저장 및 조회할 수 있습니다. Tencent Cloud COS는 높은 확장성, 저렴한 가격, 높은 신뢰성 및 보안성을 겸비한 데이터 스토리지 서비스를 제공합니다.

콘솔, API, SDK, 툴 등 다양한 방법으로 간편하고 빠르게 액세스할 수 있으며, 대량의 데이터를 저장하고 관리할 수 있습니다. COS를 통해 모든 포맷의 파일을 업로드 및 다운로드하고 관리할 수 있으며, Tencent Cloud는 직관적인 Web 관리 인터페이스를 제공하고 동시에 전국에 분포되어 있는 CDN 노드에서 파일 다운로드를 가속할 수 있습니다.


## 제품 기능

COS는 대기업 및 개인 사용자에게 데이터 관리, 원격 재해 복구, 데이터 액세스 가속, 데이터 처리 등의 기능을 제공하며 다양한 시나리오가 포함되어 있습니다. 자세한 내용은 [기능 개요](https://intl.cloud.tencent.com/document/product/436/8186) 문서를 참조하십시오.

## 기본 개념

다음 몇 가지 용어 개념을 통해 Tencent Cloud COS를 더욱 명확하게 이해할 수 있습니다.

- [버킷(Bucket)](https://intl.cloud.tencent.com/document/product/436/13312): 객체 저장 수단으로 객체를 저장하는 ‘컨테이너’의 기능을 합니다.
- [객체(Object)](https://intl.cloud.tencent.com/document/product/436/13324): COS의 기본 단위로 이미지, 문서, 멀티미디어 파일 등 포맷의 데이터를 의미합니다.
- [리전(Region)](https://intl.cloud.tencent.com/document/product/436/6224): Tencent Cloud의 호스팅 데이터 센터가 분포된 지역으로 COS 데이터를 리전의 버킷에 저장합니다.
- [액세스 도메인(Endpoint)](https://intl.cloud.tencent.com/document/product/436/6224): 객체가 버킷에 저장되면 사용자가 액세스 도메인을 통해 객체에 액세스 및 다운로드할 수 있습니다.



## 스토리지 유형

스토리지 유형은 COS에서 객체의 스토리지 등급 및 활성화 정도를 나타냅니다. COS는 INTELLIGENT TIERING, 표준 스토리지, 표준IA 스토리지, CAS, DEEP ARCHIVE와 같은 다양한 객체 스토리지 유형을 제공합니다. 스토리지 종류별로 객체 액세스 빈도, 데이터 지속성, 데이터 가용성, 액세스 딜레이 시간 등 각각의 특성을 가지고 있으며 사용자 시나리오에 따라 데이터를 스토리지 유형을 선택하여 COS에 업로드할 수 있습니다.

> ?스토리지 유형에 대한 비교 설명은 [스토리지 유형 개요](https://intl.cloud.tencent.com/document/product/436/30925)를 참조하십시오.

### 표준 스토리지

표준 스토리지(STANDARD)는 핫 데이터 유형에 속하며 낮은 액세스 딜레이 시간, 높은 처리량의 성능을 가지고 있어 사용자에게 신뢰성이 높은 고가용성 및 고성능의 객체 스토리지 서비스를 제공할 수 있습니다.


**적용 시나리오**

표준 스토리지는 실시간 액세스가 많은 비디오, 소셜 이미지, 모바일 애플리케이션, 게임 프로그램, 정적 웹 사이트 등 실시간 액세스가 많은 파일, 빈번한 데이터 인터랙티브 등이 존재하는 비즈니스 시나리오에 적합합니다.


### 표준IA 스토리지

표준IA 스토리지(STANDARD_IA)는 사용자에게 높은 안정성, 저렴한 스토리지 비용 및 짧은 액세스 딜레이 시간을 자랑하는 COS 서비스를 제공합니다. 표준IA 스토리지는 스토리지 단가를 낮춰 첫 번째 바이트 액세스 시간을 ms 단위로 유지하고 데이터 검색 시나리오에서 대기 시간 없이 고속으로 데이터를 읽어옵니다. 사용자가 데이터에 액세스 시 데이터 검색 비용이 발생한다는 것이 표준 스토리지와의 가장 큰 차이점입니다.


**적용 시나리오**

표준IA 스토리지는 클라우드 데이터, 빅 데이터 분석, 정부와 기업 데이터, 저빈도 아카이브, 모니터링 데이터 등 액세스 빈도가 낮은(예: 월평균 액세스 빈도 1~2회) 비즈니스 시나리오에 적합합니다.

### INTELLIGENT TIERING

INTELLIGENT TIERING 유형의 객체는 표준 스토리지 레이어와 표준IA 스토리지 레이어에 저장할 수 있습니다. COS는 INTELLIGENT TIERING 유형 객체의 액세스 빈도 수에 따라 자동으로 두 개의 스토리지 레이어를 전환하며 데이터 검색 비용이 없어 스토리지 비용을 절감할 수 있습니다.

**적용 시나리오**

INTELLIGENT TIERING은 액세스 모델이 불규칙한 객체에 적합하며, 비용이 비교적 엄격하게 제한되고 파일 읽기 성능에 민감하지 않은 경우 이 유형을 선택하여 비용을 절감할 수 있습니다.

### CAS

CAS(ARCHIVE)는 콜드 데이터 유형에 속하며, 데이터 검색 시 사전에 복구(동결 해제)하여 사용자에게 신뢰성 높고 매우 저렴한 비용으로 장기간 저장을 제공하는 객체 스토리지 서비스입니다. CAS는 최소 90일 이상의 스토리지 시간이 요구되며 데이터를 읽기 전에 먼저 데이터를 복구(동결 해제)해야 합니다.

**적용 시나리오**

CAS는 아카이브 데이터, 의료 영상, 과학 자료 등 컴플라이언스 파일 보관, 라이프사이클 파일 보관, 작업 로그 보관, 원격 재해복구 등 데이터를 장기간 보관해야 하는 시나리오에 적합합니다.

### DEEP ARCHIVE

DEEP ARCHIVE는 신뢰성이 높고 다른 스토리지 유형에 비해 저렴한 비용으로 장기간 저장을 제공하는 COS 서비스입니다. DEEP ARCHIVE는 최소 180일 이상의 스토리지 시간이 요구되며 데이터를 읽기 전에 먼저 데이터를 복구해야 합니다.

**적용 시나리오**

DEEP ARCHIVE는 의료 영상 데이터, 보안 모니터링 데이터, 로그 데이터 등 데이터 장기 보관 비즈니스 시나리오에 적합합니다.

## COS는 어떻게 사용합니까?

COS는 사용자에게 다양한 사용 방식을 제공하며, 자세한 사항은 다음 표를 참조하십시오.

<table>
<thead>
<tr>
<th align="left" width="30%">시작 방법</th>
<th align="left" width="70%">기능 설명</th>
</tr>
</thead>
<tbody><tr>
<td align="left" width="30%"><a href="https://intl.cloud.tencent.com/document/product/436/32955">콘솔</a></td>
<td align="left" width="70%">COS 콘솔은 사용자의 편의를 위해 제공되는 간편하고 손쉬운 COS 사용 수단입니다. 코딩 또는 실행 프로그램이 없이도 COS 콘솔을 통해 COS 서비스를 바로 이용할 수 있습니다.</td>
</tr>
<tr>
<td align="left" width="30%"><a href="https://intl.cloud.tencent.com/document/product/436/11366">COSBrowser 툴</a></td>
<td align="left" width="70%">해당 툴은 데이터의 편리한 업로드, 다운로드, 액세스 링크 생성 등 작업을 위한 시각화 인터페이스를 제공합니다.</td>
</tr>
<tr>
<td align="left" width="30%"><a href="https://intl.cloud.tencent.com/document/product/436/10976">COSCMD 툴</a></td>
<td align="left" width="70%">해당 툴은 객체의 대량 업로드, 다운로드, 삭제 등 작업을 위한 간단한 명령 라인 명령을 제공합니다.</td>
</tr>
<tr>
<td align="left" width="30%"><a href="https://intl.cloud.tencent.com/document/product/436/7751">API 방식</a></td>
<td align="left" width="70%">COS는 단일 요청을 처리하는 경량의 인터페이스 XML API를 채택하고 있습니다. 이 인터페이스를 호출하여 HTTP/HTTPS의 요청 및 응답을 실행하고, Tencent Cloud COS의 백그라운드와 인터랙티브하게 연결할 수 있습니다.</td>
</tr>
<tr>
<td align="left" width="30%"><a href="https://intl.cloud.tencent.com/document/product/436/6474">SDK 방식</a></td>
<td align="left" width="70%">Android, C, C++, .NET, Go, iOS, Java, JavaScript, Node.js, PHP, Python, 미니프로그램 SDK 등 다양한 주요 개발 언어를 지원합니다.</td>
</tr>
</tbody></table>




## COS는 어떻게 과금됩니까?

COS는 기본적으로 종량제(후불)로 과금되며, 자세한 내용은 [과금 개요](https://intl.cloud.tencent.com/document/product/436/16871) 문서를 참조하십시오.


## 관련 문서

기타 소개 문서는 [개발자 가이드](https://intl.cloud.tencent.com/document/product/436/14102)를 참조하십시오.