## 設定シナリオ
Tencent Cloud CDNサービスは、ビジネスリソースのアクセスソース元を制御するためのIPブラックリスト・ホワイトリスト設定機能を提供します。

ユーザーリクエスト側IPに対してアクセス制御ポリシーを設定することにより、アクセスのソース元を効果的に制御し、悪意のあるIPの盗用や攻撃を防ぐことができます。

## 設定ガイド

### 設定の確認
[CDNコンソール](https://console.cloud.tencent.com/cdn)にログインし、メニューバーで【ドメイン名管理】を選択して、ドメイン名の右側にある【管理】をクリックすると、ドメイン名設定画面に入ります。第2欄の【アクセス制御】でIPブラックリスト/ホワイトリスト設定を確認できます。デフォルトで無効になっています。
![](https://main.qcloudimg.com/raw/f151317bd14f053a125bf0c3841da033.png)

### 設定を有効にする

スイッチをクリックし、ブラックリスト/ホワイトリストを選択して、IPまたはIPセグメントリストに入力し、【保存】をクリックして、IPブラックリスト/ホワイトリスト設定を有効にします。
![](https://main.qcloudimg.com/raw/0b278589542a7022b3525f80ecadd2e3.png)
**IP ブラックリスト**
クライアントIPがブラックリストのIPまたはIPセグメントに該当する場合、CDNノードにアクセスすると、403ステータスコードを直接返します。
**IP ホワイトリスト**
クライアントIPがホワイトリストのIPまたはIPセグメントに該当しない場合、CDNノードにアクセスすると、403ステータスコードを直接返します。
**設定の制約**

- IPブラックリストまたはIPホワイトリストのいずれかを選択します。両方を同時に設定することはできません。
- IPブラックリスト/ホワイトリストはそれぞれ200個入力可能です。
- IPセグメントは /8、/16、/24 のIPレンジのみをサポートし、他のIPレンジはサポートしません。
- `IP：port`形式のブラックリスト/ホワイトリストはサポートされていません。

### 設定を無効にする
IPブラックリスト/ホワイトリスト設定スイッチでワンクリックでオフにすることができます。スイッチがオフの場合、既存の設定があっても、この機能は実稼働環境では有効になりません。スイッチがオンになると、ネットワーク全体で設定が有効になる前に、この機能を有効にするかどうかを確認するメッセージが表示されます。
![](https://main.qcloudimg.com/raw/24a3de16131fd945c05307493eb768f0.png)

>!ご利用のアクセラレーションドメイン名のサービスエリアがグローバルアクセラレーションの場合、設定されたIPブラックリスト/ホワイトリストはグローバルに有効になります。中国本土と中国本土以外で個別に設定することはサポートされていません

## 設定サンプル

アクセラレーションドメイン名`www.test.com`のIPブラックリスト/ホワイトリストの設定が下記の通りです。
![](https://main.qcloudimg.com/raw/29a9307902d03f686345eef2964c5ec2.png)
実際のアクセス状況は次のとおりです。
1. クライアントIP が`1.1.1.1`であるユーザーがリソース`http://www.test.com/test.txt`にアクセスし、IPがホワイトリストのIPと一致するため、正常にコンテンツを戻します。
2. クライアントIP が`2.1.1.1`であるユーザーがリソース`http://www.test.com/test.txt`にアクセスし、IPがホワイトリストのどのIPとも一致しないため、403ステータスコードが返されます。

