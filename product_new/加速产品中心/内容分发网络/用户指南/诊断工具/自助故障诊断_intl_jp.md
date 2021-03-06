CDNサービスはセルフ障害診断ツールを提供しています。ユーザーがリソースURLへのアクセスが異常であると判断した場合、このツールによりセルフで問題を検出することができます。セルフ検出プロセスにはドメイン名のDNS解析、リンク品質、サーバーのユーザビリティ、データアクセスの一致性等の一連の診断項目の導入を含み、問題の特定に貢献し、解決案を提出することが可能です。

> **ご注意**：
> 診断するリソース URLは、ユーザーのアカウントに追加されているドメイン名の状態が **起動済み**にある必要があります。診断中に生成された帯域幅は課金帯域幅とされるため、診断するターゲットリソースが200MBytes以下であることをお勧めします。

## 使用説明
### 本機のアクセス診断
ユーザーはあるリソースのアクセスに異常があることを発見した場合は、 **本機のアクセス診断** により診断を行うことができます。下記のような手順となります。
1.  [CDN コンソール](https://console.cloud.tencent.com/cdn)にログインし、左側の【診断ツール】メニューから【セルフ障害診断】を選択します。
2. 【本機のアクセス診断】ページに入り、診断する必要のある異常なURLを入力します。URLは```http://``` プレフィックスを入力する必要があります。現在、HTTPSの診断はサポートされていません。
3. 正しいURLを入力してから、【検出アドレスの取得】をクリックすると、ページでは検出アドレスが生成されます。アドレスリンクをクリックして検出ページを開き、診断情報の収集を始めます。診断中に検出ページを閉じないでください。診断が終わると、当該ページが自動的に閉じます。
4. 検出が終わると、【診断報告】ページで今回の診断結果を確認することができます。

### ユーザーのアクセス診断 
ユーザーがリソースアクセスに異常があることを報告した場合は、 **ユーザーのアクセス診断**により問題を特定し、Tencent Cloudが提供する推薦操作に従って問題を解決することができます。手順は下記の通りです。
1.  [CDN コンソール](https://console.cloud.tencent.com/cdn)にログインし、左側の【診断ツール】メニューから【セルフ障害診断】を選択します。
2. 【ユーザーのアクセス診断】ページに入り、診断する必要のある異常 URLを入力します。URLは```http://``` プレフィックスを入力する必要があります。現在、HTTPSの診断はサポートされていません。
3. 正しいURLを入力してから、【検出アドレスの取得】をクリックすると、ページに検出アドレスが生成されます。当該検出アドレスをユーザーにに送信してください。診断情報は、ユーザーが検出アドレスを開く時に収集されますので、診断中に当該ページを閉じないことをユーザーに伝えてくだ


さい。
4. 検出が終わると、【診断報告】ページでユーザーから収集された診断結果を確認することができます。

### 診断報告の確認
 [CDN コンソール](https://console.cloud.tencent.com/cdn)にログインし、左側の【診断ツール】メニューから【セルフ障害診断】を選択します。【診断報告】ページに入ると、生成された診断報告は時刻順にテーブルで表示されています。

診断報告の右側にある【確認】をクリックすると、診断報告の詳細を確認することができます。 

報告の詳細ページは **診断対象** と **診断報告** の二つの部分に分けられています：
**診断対象：**診断 ID、異常なURL、異常なドメイン名、オリジンサーバーのタイプ、診断時間の情報が含まれています。
**診断報告：** CNAME、DNS 解析、各サーバーのユーザビリティ、リンクの品質、データアクセスの一致性の診断結果が含まれています。各診断項の可能な診断結果は下記の通りです。
**第一項：CNAME**

1. 正常：診断されるドメイン名の実際のCNAME解析は、解析を設定する必要のあるCNAMEと一致している場合は、診断結果が「正常」となります。
2. 異常：診断されるドメイン名の実際のCNAME解析は、解析を設定する必要のあるCNAMEと一致していない場合は、診断結果が「異常」となります。ユーザーは【詳細を見る】をクリックすると、実際に解析された CNAME 及び CDNサービスメーカー、解析を設定する必要のあるCNAME及びCDNサービスメーカーを確認することができます。診断されたドメイン名が実際に複数のCNAMEを解析する場合は、詳細には一つしか表示されません。この場合、DNSサービスプロバイダーでCNAMEの設定を変更することをお勧めします。CNAME設定が異常である場合は、ほかの項目の診断を続行できません。

**第二項：DNS解析**
1. 正常：診断されるドメイン名の実際にアクセスしているノードが最適ノードと一致している場合は、診断結果が「正常」となります。【詳細を見る】をクリックすると、クライアント IP、Local DNS、実際のノード及び最適ノードのIP、地域及びキャリア情報を確認することができます。
2. 現在の解析パスが最適パスではありません：診断されるドメイン名の実際にアクセスしているノードが最適ノードと一致していない場合は、診断結果が「現在の解析パスが最適パスではありません」となります。Tencent Cloudの技術者にお問い合わせの上、問題を特定してください。
3. ノードIPの取得は失敗した：診断されるドメイン名IPがハイジャックされた場合は、或いはアクセスしているノードの接続が失敗したなどの場合は、診断結果が「ノードIPの取得は失敗した」となります。この場合は、Tencent Cloudの技術者にお問い合わせの上、問題を特定してください。

**第三項：各サーバーのユーザビリティ**
1. 正常：ノードとオリジンサーバー間の接続が正常である場合は、診断結果が「ノードとオリジンサーバー間の接続が正常である」となります。
2. 異常：ノード又はオリジンサーバー間の接続が異常である場合は、診断結果が「ノードの接続が異常である」又は「オリジンサーバーの接続が異常である」又は「ノードもオリジンサーバーも接続が異常である」となります。この場合は、Tencent Cloudの技術者にお問い合わせの上、問題を特定してください。

**第四項：リンク品質**
1. 正常：診断されるドメイン名のアクセスが正常である場合は、診断結果が「正常」となり、リソースアクセスのトータルレイテンシーが表示されます。ユーザーは【詳細を見る】をクリックすることにより、リンクの各段階の所用時間を確認することもできます。
2. 異常：診断されるドメイン名のアクセスが失敗した場合は、診断結果が「異常」となります。この場合は、Tencent Cloudの技術者にお問い合わせの上、問題を特定してください。リンク品質が異常である場合は、データアクセスの一致性の診断を続行しません。

**第五項：データアクセスの一致性**
1. 正常：リソースがオリジンサーバーにもノードにも正常にアクセスされ、MD5が一致している場合は、診断結果が「正常」となります。【詳細を見る】をクリックすると、オリジンサーバーとノードにおけるリソース状況を確認することができます。
2. オリジンサーバーのリソース異常：オリジンサーバーリソースのリターンコードが 4XX 又は 5XXである場合は、或いは複数のオリジンサーバーにおけるリソース MD5 が一致していない場合は、診断結果が「オリジンサーバーのリソース異常」となります。この場合は、オリジンサーバーのリソースを検出することをお勧めします。【詳細を見る】をクリックすると、オリジンサーバーとノードにおけるリソース状況を確認することができます。
3. CDNリソースの異常：オリジンサーバーのリソースが正常であるが、ノードリソースのリターンコードが4XX又は5XXである場合は、またはノードのリソースがオリジンサーバーのリソース MD5と一致していない場合は、診断結果が「CDN リソースの異常」となります。この場合は、Tencent Cloudの技術者にお問い合わせの上、問題を特定してください。【詳細を見る】をクリックすると、オリジンサーバーとノードにおけるリソース状況を確認することができます。

診断報告で問題を解決できない場合は、[チケットを提出する](https://console.cloud.tencent.com/workorder/category)か、或いはTencent Cloudの技術者にお問い合わせの上、問題を特定することをお勧めします。
