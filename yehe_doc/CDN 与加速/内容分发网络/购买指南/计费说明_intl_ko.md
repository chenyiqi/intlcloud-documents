2020년 12월 7일 21:30부터 CDN 활성화 시 과금 방식은 [트래픽 시간에 따른 과금] 방식만 지원하며, 활성화 후에는 과금 방식을 변경할 수 없습니다.
트래픽 시간에 따른 과금에 대한 차등 금액은 [트래픽 종량제](https://intl.cloud.tencent.com/document/product/228/2949)와 동일하며 과금 주기만 시간별로 변경할 수 있습니다.

첫 적용 시에는 활성화 당일 00:00부터 적용되며, 이후에는 매월 1일 00:00부터 적용됩니다.

## 과금 개요

### 과금 지역

Tencent Cloud CDN은 **중국 내**와 **중국 외** 두 서비스 지역으로 나뉩니다.

- 중국 내 지역은 중국 대륙 전지역이 통합 과금됩니다.

- 중국 외 지역은 Tencent Cloud CDN 노드 서버 소재지에 따라 아태1존, 아태2존, 아태3존, 중동, 유럽, 북미, 남미, 아프리카 총 8개 과금 리전으로 나뉩니다.

  |  리전   |                        포함 국가                        |
  | :-----: | :----------------------------------------------------: |
  | 아태1존 |        중국홍콩, 중국마카오, 베트남, 싱가포르, 태국        |
  | 아태2존 |      중국대만, 일본, 한국, 말레이시아, 인도네시아      |
  | 아태3존 |      필리핀, 인도, 호주, 기타 아시아 태평양 국가 및 지역        |
  |  중동   |              사우디아라비아, 아랍에미리트, 터키               |
  |  유럽   | 영국, 러시아, 독일, 이탈리아, 아일랜드, 프랑스, 네덜란드, 스페인 |
  |  북미   |                      미국, 캐나다                      |
  |  남미   |                          브라질                          |
  |  아프리카   |                          남아프리카 공화국                          |

> 참고:
>
> 중국 내 지역과 중국 외 모든 리전의 CDN 소모 요금은 지역(리전) 단가와 용량에 따라 결산됩니다.

### 범용 과금 방식 설명

|     과금 방식      |                             설명                             |                           지불 방식                           |      과금 규정      |                           과금 상세 설명                           |
| :---------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------: | :----------------------------------------------------------: |
|     대역폭 과금      | 매월 피크 대역폭에 따른 과금 방식으로, 대역폭 데이터를 5분에 한 번 통계하여 매일 288개 값을 획득하고, 이 중 최대값으로 과금합니다.  | 후불 일 결산으로, 전날 00:00:00 ~ 23:59:59에 발생한 총 소모량이 다음날 18:00 이전에 계산되어 차감됩니다. |   차등 도달 방식   | [과금 상세 설명](https://intl.cloud.tencent.com/document/product/228/2949) 참조 |
| 트래픽 과금(기본) |         매월 Tencent Cloud CDN 노드에서 스트림되는 실제 트래픽에 따라 과금됩니다.          | 후불 일 결산으로, 전날 00:00:00 ~ 23:59:59에 발생한 총 소모량이 다음날 18:00 이전에 계산되어 차감됩니다. | 월간 차등 누적 방식 | [과금 상세 설명](https://intl.cloud.tencent.com/document/product/228/2949) 참조 |
| 트래픽 과금(기본) |         매월 Tencent Cloud CDN 노드에서 스트림되는 실제 트래픽에 따라 과금됩니다.          | 후불 시간당 결산으로, 1시간 전 발생한 소모량이 이후 2~4시간 내에 계산되어 차감됩니다. | 월간 차등 누적 방식 | [과금 상세 설명](https://intl.cloud.tencent.com/document/product/228/2949) 참조 |

### 대규모 고객 과금 방식 설명

귀하의 CDN 서비스 월간 요금이 USD 20,000달러 이상이거나 해당 금액 이상이 예상되는 경우, Tencent Cloud CDN은 더 많은 혜택의 월간 과금 방식을 제공합니다. Tencent Cloud 비즈니스팀으로 문의해 주십시오.

|    과금 방식    |                             설명                             |                           적용 시나리오                           |                           과금 상세 설명                           |
| :------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
| 일 피크 대역폭으로 월 평균 계산 | CDN에서 매일 총 288개의 대역폭 통계 포인트를 측정하며, 모든 유효 날짜의 피크치 평균으로 과금 대역폭을 계산한 후 체결한 비즈니스 계약 가격에 따라 비용을 계산합니다. | CDN 월간 과금 금액이 USD 20,000달러 이상이거나 해당 금액 이상이 예상되는 경우 비즈니스팀으로 문의해 주십시오. | [과금 상세 설명](https://intl.cloud.tencent.com/document/product/228/2949) 참조 |
|    월간 대역폭 95%    | CDN에서 매일 총 288개의 대역폭 통계 포인트를 측정하며, 당월 1일부터 모든 유효일(소모 발생)의 통계 포인트를 배열해 상위 5% 통계 포인트를 제외한 최대 통계 포인트를 과금 대역폭으로 하여 계약 가격에 따라 요금을 계산합니다. | CDN 월간 과금 금액이 USD 20,000달러 이상이거나 해당 금액 이상이 예상되는 경우 비즈니스팀으로 문의해 주십시오. | [과금 상세 설명](https://intl.cloud.tencent.com/document/product/228/2949) 참조 |
|     월간 트래픽     |       월간 누적 사용한 모드 트래픽의 합으로 계약 가격에 따라 요금을 계산합니다.       | CDN 월간 과금 금액이 USD 20,000달러 이상이거나 해당 금액 이상이 예상되는 경우 비즈니스팀으로 문의해 주십시오. |                              /                               |

> 설명:
>
> 
>
> - 각 CDN 노드는 실시간으로 트래픽 데이터를 기록하여 계산 센터에 보고해 도메인의 총 트래픽 데이터를 계산합니다. 대역폭 계산 시 5분마다 데이터 분할 정도를 계산하며, 즉 상응하는 대역폭 = 5분간 데이터 분할 정도 총 트래픽 / 300초가 됩니다. 예를 들어 5분 내에 발생한 총 트래픽 양이 30MB인 경우, 변환 규칙에 따라 1MB = 8Mb가 되며 상응하는 대역폭은 (30*8) / 300 = 0.8Mbps가 됩니다.
> - 단위 환산 규칙: 1GB = 1,000MB, 1MB = 1,000KB, 1Gbps = 1,000Mbps, 1Mbps = 1,000Kbps

## 과금 상세 설명



### 피크 대역폭 과금

CDN 대역폭 과금은 **차등 도달** 방식을 사용하며, 차등 가격은 다음과 같습니다.

| 대역폭 차등(USD/Mbps/일) | 중국대륙 - CN | 북미 - NA | 유럽 - EU | 아태1존 - AP1 | 아태2존 - AP2 | 아태3존 - AP3 | 중동 - ME | 아프리카 - AA | 남미 - SA |
| :----------------------- | ------------- | :-------- | :-------- | :------------ | :------------ | :------------ | :-------- | :-------- | :-------- |
| 0Mbps - 500Mbps          | 0.094         | 0.2941    | 0.2941    | 0.4412        | 0.5882        | 0.6471        | 0.8529    | 0.6471    | 0.6471    |
| 500Mbps - 5Gbps          | 0.092         | 0.2471    | 0.2471    | 0.3882        | 0.5294        | 0.5941        | 0.7824    | 0.5941    | 0.5941    |
| 5Gbps - 50Gbps           | 0.086         | 0.1824    | 0.1824    | 0.3412        | 0.4706        | 0.5471        | 0.7059    | 0.5471    | 0.5471    |
| ≥ 50Gbps                 | 0.084         | 0.1294    | 0.1294    | 0.2941        | 0.4118        | 0.5           | 0.6176    | 0.5       | 0.5       |

> 설명:
>
> ≥ 50Gbps인 경우, 오프라인 [고객센터](https://intl.cloud.tencent.com/contact-sales)를 통해 할인 여부를 문의해 주십시오.

#### 계산 방식

전날 CDN 중국대륙 지역의 대역폭 피크치가 X이고 중국 외 각 리전에서 소모가 발생하지 않은 경우, 차등 계산 방식은 다음과 같습니다.

1. X < 500Mbps인 경우, 청구서 요금은 X*0.094
2. 500Mbps ≤ X <5000Mbps인 경우, 청구서 요금은 X*0.092
3. 5000Mbps ≤ X <50000Mbps인 경우, 청구서 요금은 X*0.086
4. X ≥ 50000Mbps인 경우, 오프라인 계약으로 더 많은 혜택을 제공해드립니다.

[가격 계산기](https://buy.cloud.tencent.com/calculator/cdn)를 이용해 예상 비용을 계산해 볼 수 있습니다.



### 트래픽 종량제

CDN 트래픽 과금은 **월간 차등 누적** 방식을 사용하며, 차등 가격은 다음과 같습니다.

| 트래픽 차등(USD/GB) | 중국대륙 - CN | 북미 - NA | 유럽 - EU | 아태1존 - AP1 | 아태2존 - AP2 | 아태3존 - AP3 | 중동 - ME | 아프리카 - AA | 남미 - SA |
| :------------------ | ------------- | :-------- | :-------- | :------------ | :------------ | :------------ | :-------- | :-------- | :-------- |
| 0TB - 2TB           | 0.037         | 0.0547    | 0.0547    | 0.0812        | 0.1094        | 0.12          | 0.1588    | 0.12      | 0.12      |
| 2TB - 10TB          | 0.035         | 0.0459    | 0.0459    | 0.0724        | 0.1024        | 0.1129        | 0.1465    | 0.1129    | 0.1129    |
| 10TB - 50TB         | 0.032         | 0.0388    | 0.0388    | 0.0653        | 0.0935        | 0.1059        | 0.1359    | 0.1059    | 0.1059    |
| 50TB - 100TB        | 0.026         | 0.0318    | 0.0318    | 0.0582        | 0.0847        | 0.0988        | 0.1253    | 0.0988    | 0.0988    |
| ≥ 100TB             | 0.02          | 0.0247    | 0.0247    | 0.0547        | 0.0759        | 0.0918        | 0.1147    | 0.0918    | 0.0918    |

> 설명:
>
> ≥ 100TB인 경우, 오프라인 [고객센터](https://intl.cloud.tencent.com/contact-sales)를 통해 할인 여부를 문의해 주십시오.

#### 계산 방식

트래픽 과금은 대역폭 과금과 달리 월간 트래픽에 따라 차등 누적되며, 트래픽 일 결산 계산 방식은 다음과 같습니다.

- 사용자의 1월 1일 중국대륙 지역 트래픽 소모량이 3TB이고 중국 외 각 리전에서 소모가 발생하지 않은 경우, 다음 이미지와 같습니다. 이미지 중 회색 부분이 실제 과금되는 차등 구간이며 초록색 부분이 1월 1일 발생한 트래픽으로, 2TB는 0TB ~ 2TB 구간으로 과금되고 1TB는 2TB ~ 10TB 구간으로 과금됩니다. 따라서 1월 1일에 발생한 실제 요금은 2 * 1000 * 0.037 + 1 * 1000 * 0.035가 됩니다.
  ![img](https://mc.qcloudimg.com/static/img/bfdae242f6cca57421a65e46a96b0c67/image.png)
- 사용자의 1월 2일 중국대륙 지역 트래픽 소모량이 3TB이고 중국 외 각 리전에서 소모가 발생하지 않은 경우, 다음 이미지와 같습니다. 트래픽 과금은 월간 누적 방식을 사용하므로 1월 2일 발생한 트래픽은 2TB ~ 10TB 구간으로 과금되어, 1월 2일에 발생한 실제 요금은 3 * 1000 * 0.035가 됩니다.
  ![img](https://mc.qcloudimg.com/static/img/f62d1056c1c2cab249cec62ad6e74ddc/image.png)
- 사용자의 1월 3일 중국대륙 지역 트래픽 소모량이 7TB이고 중국 외 각 리전에서 소모가 발생하지 않은 경우, 다음 이미지와 같습니다. 해당일 7TB 중 4TB는 2TB ~ 10TB 구간으로 과금되고, 3TB는 10TB ~ 50TB 구간으로 과금됩니다. 따라서 1월 3일에 발생한 실제 요금은 4 * 1000 * 0.035 + 3 * 1000 * 0.032가 됩니다.
  ![img](https://mc.qcloudimg.com/static/img/954e2d483e31afd411f9a91ebd7f66c8/image.png)

이를 기반으로 당월 일일 요금을 계산할 수 있으며, 2월 1일부터는 다시 0부터 차등 누적되어 계산됩니다. [가격 계산기](https://buy.cloud.tencent.com/calculator/cdn)를 사용해 예상 금액을 계산해 볼 수 있습니다.



### 일 피크 대역폭으로 월 평균을 계산하여 과금

1. 1월 1일부터 정식으로 과금이 시작되었으며 계약 가격이 P USD/Mbps/월인 경우로 가정합니다.
2. 유효일: 소모량이 0보다 크면 유효일로 기록합니다.
3. 1월 유효일이 14일이고, 해당 14일의 하루 288개 통계 포인트 최대값이 Max_1, Max_2, Max_3… Max_14인 경우, 과금 대역폭은 Average(Max_1, Max_2, ..., Max_14)이 되며, 1월 요금은 Average(Max_1, Max_2, ..., Max_14) * P * 14 / 31이 됩니다.



### 월간 대역폭 95% 과금

1. 1월 1일부터 정식으로 과금이 시작되었으며 계약 가격이 P USD/Mbps/월인 경우로 가정합니다.
2. 유효일: 소모량이 0보다 크면 유효일로 기록합니다.
3. 1월 유효일이 14일이라고 가정할 경우, 해당 14일 동안의 모든 통계 포인트인 14 * 288개에서 상위 5%를 제외한 나머지 중 가장 높은 값인 Max95가 곧 과금 대역폭 기준이 됩니다. 따라서 1월 요금은 Max95 * P * 14 / 31이 됩니다.

## 과금 방식 선택

> 설명:
>
> 사용 중에 선택한 과금 방식이 실제 비즈니스 상태에 적합하지 않은 경우 과금 방식을 변경할 수 있으며, 자세한 내용은 [과금 방식 변경](https://intl.cloud.tencent.com/document/product/228/32326)을 참조하십시오.

**방식 선택:**
CDN은 트래픽 과금 방식과 대역폭 과금 방식을 제공하며, 비즈니스 상태에 따라 적합한 과금 방식을 선택할 수 있습니다.

**계산 예시:**
전날 00:00 ~ 23:59에 발생한 중국대륙 지역의 트래픽이 200GB이고, 대역폭 피크치가 40Mbps인 경우 그래프는 다음과 같습니다.
![img](https://mc.qcloudimg.com/static/img/3ecfe86a031782ebeaf0b1f7595cc69f/image.png)

트래픽 과금 방식인 경우 지불할 비용: 200 * 0.037 = 7.4USD

대역폭 과금 방식인 경우 지불할 비용: 40 * 0.094 = 3.76USD 

대역폭 과금 방식이 더 저렴하므로, 이 경우에는 대역폭 과금 방식 선택을 권장합니다.

## 연체 설명

Tencent Cloud 계정이 연체되면 SMS, 이메일 등 여러 방식으로 연체 상태를 고지하고 **24시간**의 충전 시간을 드리며, 24시간 후에는 시스템에서 CDN 서비스를 중지합니다. 계정이 정상으로 회복되면 CDN 콘솔을 통해 수동으로 가속 서비스를 활성화해야 합니다.

> 참고:
>
> 연체로 인해 가속 서비스가 중지되면 모든 도메인이 비활성화되고 액세스는 모두 Origin-pull로 처리됩니다. 또한 CDN 콘솔에서는 조회 작업만 지원하며 설정 수정 등의 작업은 할 수 없습니다. CDN 관련 도메인, 설정 정보는 12개월간 보관됩니다.

