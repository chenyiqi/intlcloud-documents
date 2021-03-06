
スポットインスタンスは、価格と在庫の理由によりインスタンスを自主的に回収し、インスタンスが回収される前にユーザーがカスタム操作を実行できるように、インスタンス内部から Metadata メカニズムを介して回収状態を取得するためのインターフェースが提供されています。詳細内容は下記の通りです。

## Metadata
インスタンスのメタデータはインスタンスに関連するデータであり、実行中のインスタンスの設定または管理するために使用できます。インスタンス内部を介してインスタンスのメタデータにアクセスして取得できます。詳細については、 [インスタンスメタデータ](http://intl.cloud.tencent.com/document/product/213/4934)をご参照ください。


##  Metadataを使用してスポットインスタンスの回収状態に関する情報を取得する
2. スポットインスタンスの回収状態に関する情報を取得するには、cURLツールまたはHTTP GETリクエストを使用してMetadataにアクセスできます。
```
curl metadata.tencentyun.com/latest/meta-data/spot/termination-time
```
- 下記のような情報が返された場合は、スポットインスタンスの回収時間を示しています。
```
2018-08-18 12:05:33
```
- エラーコード404が返された場合、インスタンスはスポットインスタンスではないか、回収がトリガーされていないことを示します。

詳細については、[インスタンスメタデータ](http://intl.cloud.tencent.com/document/product/213/4934)をご参照ください。
