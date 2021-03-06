### 캐시 제거란 무엇인가요?
캐시 제거 방법에는 URL 퍼지, 디렉터리 새로고침 및 URL 프리패치 등이 있습니다. (자세한 내용은 [캐시 제거](https://intl.cloud.tencent.com/document/product/228/6299)를 참조 바랍니다)
- URL 퍼지는 파일 단위의 캐시 제거입니다.
- 디렉터리 새로고침을 하면 디렉터리를 단위로 디렉터리의 모든 파일에 대해 캐시 제거를 진행합니다.
- URL 프리패치는 파일을 단위로 리소스 프리패치를 진행합니다.

새로고침과 프리패치의 차이점:
- 새로고침 시 해당 리소스의 전체 네트워크 CDN 노드 상의 캐시를 제거합니다. 사용자의 요청이 노드에 도달하면 노드는 원본 서버로부터 해당하는 리소스를 불러온 다음, 사용자에게 리턴 및 노드에 캐싱함으로써 최신 리소스를 가져올 수 있도록 합니다.
- 프리패치 시 해당 리소스는 전체 네트워크 CDN 노드에 미리 캐시됩니다. 사용자의 요청이 노드에 도달하면 노드에서 리소스를 바로 가져올 수 있습니다.

### 캐시 제거에는 어떤 조건이 있나요? 캐시 제거 시 적용까지 얼마나 걸리나요?
캐시 제거 방식에는 URL 퍼지, 디렉터리 새로고침 및 URL 프리패치 등이 있습니다.
- URL 퍼지: 일일 URL 퍼지 수는 최대 10000개를 넘지 않습니다. 새로고침 시마다 제출하는 URL 수는 1000개를 넘지 않으며 새로고침 작업이 적용되는 데까지 약 5분 정도 소요됩니다. 파일에 설정한 캐시 만료 시간이 5분 미만이라면, 새로고침 툴을 사용하지 말고 타임아웃 업데이트까지 기다리시기를 권장합니다.
- 디렉터리 새로고침: 일일 디렉터리 새로고침 수는 최대 100개를 넘지 않습니다. 새로고침 시마다 제출하는 URL 디렉터리 수는 20개를 넘지 않으며 새로고침 작업이 적용되는 데까지 약 5분 정도 소요됩니다. 폴더에 설정한 캐시 만료 시간이 5분 미만이라면, 새로고침 툴을 사용하지 말고 타임아웃 업데이트까지 기다리시기를 권장합니다.
- URL 프리패치: URL 프리패치 기능은 현재 CDN의 대형 거래처에만 오픈되어 있습니다. 노드에 해당 리소스가 캐시되었고, 아직 만료되지 않은 상황이라면 최신 리소스로 업데이트되지 않습니다. 모든 CDN 노드에 있는 리소스를 최신으로 업데이트해야 한다면, 프리패치 전에 새로고침 작업을 진행할 수 있습니다. 일일 URL 프리패치 수는 최대 1000개를 넘지 않습니다. 프리패치 시마다 제출하는 URL 수는 20개를 넘지 않으며, 프리패치 작업이 적용되는 데까지 파일의 크기에 따라 5분에서 30분 정도 소요됩니다.

### CDN 가속 노드에 캐싱된 콘텐츠는 실시간으로 업데이트되나요?
현재 CDN 가속 노드에 캐싱된 콘텐츠는 실시간으로 업데이트되지 않습니다. CDN 노드는 콘솔에서 설정한 [캐시 만료 설정](https://intl.cloud.tencent.com/document/product/228/6290)을 토대로 캐시를 업데이트합니다. 특정 파일의 캐시를 실시간으로 업데이트해야 한다면 [캐시 제거](https://intl.cloud.tencent.com/document/product/228/6299)를 통해 진행할 수 있습니다.

### CDN 새로고침은 디렉터리 새로고침을 지원하나요?
CDN은 현재 URL 퍼지, 디렉터리 새로고침과 URL 프리패치를 지원합니다.
방법 1: Tencent Cloud CDN 콘솔에서 [디렉터리 새로고침](https://console.cloud.tencent.com/cdn/refresh)을 진행할 수 있습니다. 자세한 내용은 [캐시 제거](https://intl.cloud.tencent.com/document/product/228/6299)를 참조 바랍니다.
방법 2: API 호출 방식을 통하여 새로고침할 수 있습니다. 자세한 내용은 [목록 경신](https://intl.cloud.tencent.com/document/product/228/33602)를 참조 바랍니다.

### 캐시 제거 기록은 어떻게 조회할 수 있나요?
CDN 콘솔에서 캐시 제거 기록을 조회할 수 있습니다. 자세한 정보는 [작업 기록](https://intl.cloud.tencent.com/document/product/228/6299)을 참조 바랍니다.

### 디렉터리 프리패치 또는 새로고침이 왜 적용되지 않나요?
원본 서버 Last-Modified의 변경 여부를 확인하시기 바랍니다. Last-Modified가 변경되면 Origin-pull에 실패할 수 있습니다. 문제를 해결할 수 없다면 [티켓 제출](https://console.cloud.tencent.com/workorder/category)을 통해 유지보수 엔지니어에게 처리를 요청할 수 있습니다.
