## 기능 설명

PUT Bucket website 요청은 버킷이 정적 웹사이트를 구성하는 데 사용됩니다. XML 형식의 구성 파일을 전달하여 구성합니다. 파일 크기는 64KB로 제한됩니다.

## 요청

### 요청 예제

```shell
PUT /?website HTTP/1.1
Host:<BucketName-APPID>.<Region>.myqcloud.com
Date: date
Content-Length: length
Content-Type:application/xml
Authorization: Auth String
<XML 파일>
```

> Authorization: Auth String(세부 정보는 [요청 서명](https://intl.cloud.tencent.com/document/product/436/7778) 문서를 참조).

### 요청 헤더

#### 공통 헤더

해당 요청 작업은 공통 요청 헤더를 사용하여 구현됩니다. 공통 요청 헤더에 대한 세부 정보는 [공통 요청 헤더](https://cloud.tencent.com/document/product/436/7728) 문서를 참조하십시오.

#### 비공통 헤더

해당 요청 작업은 특별한 요청 헤더 정보가 없습니다.

### 요청체

```shell
<WebsiteConfiguration>
	<IndexDocument>
		<Suffix>index.html</Suffix>
	</IndexDocument>
	<RedirectAllRequestsTo>
		<Protocol>https</Protocol>
	</RedirectAllRequestsTo>
	<ErrorDocument>
		<Key>Error.html</Key>
	</ErrorDocument>
	<RoutingRules>
		<RoutingRule>
			<Condition>
				<HttpErrorCodeReturnedEquals>404</HttpErrorCodeReturnedEquals>
			</Condition>
			<Redirect>
				<Protocol>https</Protocol>
				<ReplaceKeyWith>404.html</ReplaceKeyWith>
			</Redirect>
		</RoutingRule>
		<RoutingRule>
			<Condition>
				<KeyPrefixEquals>docs/</KeyPrefixEquals>
			</Condition>
			<Redirect>
				<Protocol>https</Protocol>
				<ReplaceKeyPrefixWith>documents/</ReplaceKeyPrefixWith>
			</Redirect>
		</RoutingRule>
		<RoutingRule>
			<Condition>
				<KeyPrefixEquals>img/</KeyPrefixEquals>
			</Condition>
			<Redirect>
				<Protocol>https</Protocol>
				<ReplaceKeyWith>demo.jpg</ReplaceKeyWith>
			</Redirect>
		</RoutingRule>
	</RoutingRules>
</WebsiteConfiguration>
```

구체적인 내용 설명은 다음과 같습니다.

| 이름                        | 부모 노드                | 설명                                                         | 유형      | 필수 선택 여부 |
| --------------------------- | --------------------- | ------------------------------------------------------------ | --------- | ---- |
| WebsiteConfiguration        | 없음                    | 정적 웹사이트 구성으로 인덱스 문서, 오류 문서, 프로토콜 전환과 리디렉션 규칙을 포함합니다. | Container | 예   |
| IndexDocument               | WebsiteConfiguration  | 인덱스 문서                                                     | Container | 예   |
| Suffix                      | IndexDocument         | 지정 인덱스 문서                                                 | String    | 예   |
| ErrorDocument               | WebsiteConfiguration  | 오류 문서                                                     | Container | 아니요   |
| Key                         | ErrorDocument         | 공용 오류 반환함을 지정합니다                                             | String    | 아니오   |
| RedirectAllRequestsTo       | WebsiteConfiguration  | 모든 요청 리디렉션                                               | Container | 아니요   |
| Protocol                    | RedirectAllRequestsTo | 전체 서버 리디렉션 프로토콜을 지정하며, https로만 설정할 수 있습니다.                        | String    | 아니요   |
| RoutingRules                | WebsiteConfiguration  | 라우팅 규칙을 설정하며, 최대 100개의 RoutingRule을 설정합니다.                     | Container | 아니요   |
| RoutingRule                 | RoutingRules          | 단일 라우팅 규칙을 설정하며 접두사 매칭 라우팅과 오류 코드 라우팅을 포함합니다.         | Container | 아니요   |
| Condition                   | RoutingRule           | 리디렉션 발생 조건을 지정합니다. 접두사 매칭 리디렉션과 오류 코드 리디렉션 중 1개만 지정할 수 있습니다. | Container | 아니요   |
| HttpErrorCodeReturnedEquals | Condition             | 리디렉션 오류 코드를 지정하고, 4XX 반환 코드만 지원하며, 우선 순위는 ErrorDocument보다 높습니다. | Interger  | 아니요   |
| KeyPrefixEquals             | Condition             | 라우팅해야 할 경로 접두사를 지정합니다                      | String    | 아니요   |
| Redirect                    | RoutingRule           | 리디렉션 conditon 만족 시 리디렉션의 구체적인 교체 규칙을 지정합니다.                 | Container | 아니요   |
| ReplaceKeyWith              | Redirect              | 전체 Key를 지정 내용으로 교체합니다.                                      | String    | 아니요   |
| ReplaceKeyPrefixWith        | Redirect              | 매칭한 접두사를 지정 내용으로 교체하고, Conditon이 KeyPrefixEquals여야 설정할 수 있습니다. | String    | 아니요   |

## 응답

### 응답 헤더

#### 공통 응답 헤더

해당 응답은 공통 응답 헤더를 포함합니다. 공통 응답 헤더에 대한 세부 정보는 [공통 응답 헤더](https://cloud.tencent.com/document/product/436/7729) 문서를 참조하십시오.

#### 고유의 응답 헤더

해당 응답은 특별한 응답 헤더가 없습니다.

### 응답 본문

해당 응답 본문은 비어 있습니다.

### 오류 코드

해당 요청 작업은 특별 오류 정보가 없습니다.일반적인 오류 정보는 [오류 코드](https://cloud.tencent.com/document/product/436/7730) 문서를 참조하십시오.

## 실제 사례

### 요청

```shell
PUT /?website HTTP/1.1
Host: examplebucket-1250000000.cos.ap-shanghai.myqcloud.com
Date:Thu, 21 Sep 2017 13:05:41 +0000
Content-Type: application/xml
Authorization:q-sign-algorithm=sha1&q-ak=AKIDWtTCBYjM5OwLB9CAwA1Qb2ThTSUjfGFO&q-sign-time=1484814927;32557710927&q-key-time=1484814927;32557710927&q-header-list=host&q-url-param-list=website&q-signature=8b9f05dabce2578f3a79d732386e7cbade9033e3
Content-Length: 646

<WebsiteConfiguration>
	<IndexDocument>
		<Suffix>index.html</Suffix>
	</IndexDocument>
	<RedirectAllRequestsTo>
		<Protocol>https</Protocol>
	</RedirectAllRequestsTo>
	<ErrorDocument>
		<Key>Error.html</Key>
	</ErrorDocument>
	<RoutingRules>
		<RoutingRule>
			<Condition>
				<HttpErrorCodeReturnedEquals>404</HttpErrorCodeReturnedEquals>
			</Condition>
			<Redirect>
				<Protocol>https</Protocol>
				<ReplaceKeyWith>404.html</ReplaceKeyWith>
			</Redirect>
		</RoutingRule>
		<RoutingRule>
			<Condition>
				<KeyPrefixEquals>docs/</KeyPrefixEquals>
			</Condition>
			<Redirect>
				<Protocol>https</Protocol>
				<ReplaceKeyPrefixWith>documents/</ReplaceKeyPrefixWith>
			</Redirect>
		</RoutingRule>
		<RoutingRule>
			<Condition>
				<KeyPrefixEquals>img/</KeyPrefixEquals>
			</Condition>
			<Redirect>
				<Protocol>https</Protocol>
				<ReplaceKeyWith>demo.jpg</ReplaceKeyWith>
			</Redirect>
		</RoutingRule>
	</RoutingRules>
</WebsiteConfiguration>
```

### 응답

```shell
HTTP/1.1 200 OK
Content-Type: application/xml
Content-Length: 0
Connection: keep-alive
Date: Thu, 21 Sep 2017 13:05:54 GMT
Server: tencent-cos
x-cos-request-id: NTljM2I5MzJfMjQ4OGY3MGFfNzk4OV83Zg==
```
