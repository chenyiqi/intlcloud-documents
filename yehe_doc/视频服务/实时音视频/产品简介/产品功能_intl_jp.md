## 基本機能

<table>
<tr><th>機能</th><th width="50%">機能説明</th><th width="35%">一般的なユースケース</th>
</tr>
<tr>
<td>ビデオ通話</td>
<td><ul style="margin:0">
<li>1対1または多人数のビデオ通話。720P、1080PのHD画質をサポート。
<li>1つのルームで最大300人のオンライン同時接続、最大30人のカメラ同時起動をサポート。</li>
</ul></td>
<td>1対1のビデオ通話、300人まで同時に参加できるビデオ会議、オンライン診断、ビデオチャット、ビデオカスタマーサービス、ビデオインタビュー、ビデオダブルレコーディング、オンライン賠償請求、ビデオ人狼ゲームなど。</td>
</tr>
<tr>
<td>音声通話</td>
<td><ul style="margin:0">
<li>1対1または多人数の音声通話。48kHzのサンプルレート、デュアルサウンドチャネルをサポート。</li>
<li>1つのルームで最大300人のオンライン同時接続、最大30人のマイク同時起動をサポート。</li>
</ul></td>
<td>1対1の音声通話、多人数の音声通話、音声チャット、音声会議、音声カスタマーサービス、人狼ゲームなど。</td>
</tr><tr>
<td>ビデオインタラクティブストリーミング</td>
<td><ul style="margin:0">
<li>キャスターとオーディエンスの音声通話をサポート。</li>
<li>ライブストリーミングルーム間の キャスターPKをサポート。</li>
<li>スムーズなマイクのオン・オフをサポート。切り替えのプロセスを待つ必要がなく、キャスターの遅延は300ms未満です。</li>　
<li>1つのルームの音声通話の参加人数を無制限にでき、最大30人までの同時通話が可能です。</li>
<li>低遅延ライブストリーミングモードでは、視聴者10万人の同時再生をサポート。再生遅延を1000msまで低減させています。</li>
<li>CDN Relayed live streamingモードの場合は、視聴者数が無制限です。</li>
</ul></td>
<td>低遅延のビデオライブストリーミング、10万人規模のインタラクティブな授業、ビデオライブストリーミングのPK、ビデオお見合いルーム、双方向対話型授業、リモートトレーニング、大規模なミーティングなど。</td>
</tr><tr>
<td>音声インタラクティブストリーミング</td>
<td><ul style="margin:0">
<li>キャスターとオーディエンスの音声通話をサポート。</li>
<li>ライブストリーミングルーム間のキャスターPKをサポート。</li>
<li>スムーズなマイクのオン・オフをサポート。切り替えのプロセスを待つ必要がなく、キャスターの遅延は300ms未満です。</li>
<li>1つのルームの音声通話の参加人数を無制限にでき、最大30人までの同時通話が可能です。</li>
<li>低遅延ライブストリーミングモードでは、視聴者10万人の同時再生をサポート、再生の遅延を1000msまで低減させています。</li>
<li>CDN Relayed live streamingモードの場合は、視聴者数が無制限です。</li>
</ul></td>
<td>低遅延の音声ライブストリーミング、音声ライブストリーミングのPK、音声チャットルーム、音声お見合いルーム、カラオケルーム、FMラジオなど。</td>
</tr></table>

>? Web版は最大20人のカメラまたはマイク同時起動をサポートしています。

## 高度な機能

| 機能           | 機能説明                                                     | 一般的なユースケース                                               |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| キャスターとオーディエンスの音声通話       | キャスターとオーディエンスの音声通話をサポート、視聴者は自由かつスムーズにマイクをオン・オフでき、切り替えのプロセスも待つ必要がありません。     | インタラクティブライブストリーミング、オンライン授業、チャットルームなど。                               |
| ルーム間 PK        | 別名、「ライブストリーミングルーム間のPK」。複数のキャスターがルームを跨いでPKを行い、視聴者がこれを鑑賞します。       | ショーのライブストリーミング、PKのマイク同時トーク、ルームを跨ぐ授業など。                              |
| 画面共有       | 別名、「スクリーンシェア」。ローカルPCのデスクトップ、ウィンドウ、画面等の領域を他人と共有する機能をサポート（例：Microsoft PowerPointのPPT再生のウィンドウ）。 | オンライン授業、PPT共有、リモートアシスタントなど。                               |
| クラウドレコーディング       | Relayed Pushの方式を採用し、 [LVB](https://intl.cloud.tencent.com/document/product/267) の機能を利用して、全プロセスにおけるクラウドレコーディング（録音/録画）を提供します。さらにレコーディングしたファイルは [VOD](https://intl.cloud.tencent.com/document/product/266) プラットフォームに保存し、レコーディングプロセスの信頼性とリアルタイム性を保証します。 | ダブルレコーディング、アーカイブ、コンプライアンスなど。                                         |
|ローカルレコーディング | ローカルサーバーでのレコーディング（録音/録画）をサポート。ご利用を希望される場合は、 [弊社営業担当に連絡](https://intl.cloud.tencent.com/support)して、SDKおよび関連ガイドを入手できます。 | ダブルレコーディング、ファイル保存、コンプライアンスなど。                                         |
| 高音質         | <li>48kHzのサンプルレートをサポート。</li><li>真左/右サウンドトラックによるステレオ音声をサポート、その音質は純正の CD効果に匹敵します。</li> | 音声通話、ビデオ通話、インタラクティブライブストリーミング、音声チャットルーム、高音質 FMラジオ、音楽教室、カラオケルーム、オンライン授業など。 |　　　
| 高画質         | 720P、1080PのHD画質ビデオをサポート。                              | ビデオ通話、インタラクティブライブストリーミング、オンライン授業など。                             |
| 3A 処理        | 業界をリードするTRAEオーディオエンジンで3A処理を実施。ダブルトーク、騒音低減等の場面においてより良い音質を提供します。3Aとは、AEC（エコーキャンセル）、ANS（バックグラウンドノイズ除去）、AGC（音声自動調整）を指します。 | 全ての音声シーン。                                               |
| 基本美顔機能       | ベーシックな美顔機能をサポート。美白、肌質アップ、明るい艶感等の設定、そして基本的なフィルタ効果が含まれます。 | ビデオ通話、インタラクティブストリーミング、オンライン授業など。                             |
| BGM            | ローカルのmp3、aac、wav形式等の音声ファイルを人の声のBGMにする機能をサポート。 | 音声通話、ビデオ通話、インタラクティブストリーミング、オンライン授業、音声チャットルーム、カラオケルーム、FMラジオなど。 |
| 効果音         | 通話のプロセスで効果音を追加します。例：手拍子、歓声、口笛、掛け声など。     | 音声通話、ビデオ通話、インタラクティブストリーミング、音声チャットルーム、カラオケルーム、FMラジオなど。    |
| ハーモニーと伴奏づけ       | QQ Musicの曲など、ローカルで再生される音楽は、他のユーザーと共有できます。 | インタラクティブストリーミング、オンライン授業、音声チャットルーム、FMラジオなど。                      |
| ボイスチェンジャー           | ボイスチェンジャー の特殊効果を提供します。例：ロリータ、オジサン、ヘビメタ等の声の特殊効果。             | 音声通話、ビデオ通話、インタラクティブストリーミング、チャットルーム、カラオケ、FMラジオなど。    |
| ボイスリバーブ           | リバーブ効果を提供します。例：カラオケ、小部屋、音楽ホール、浴室等のリバーブ効果。     | 音声通話、ビデオ通話、インタラクティブストリーミング、音声チャットルーム、カラオケルーム、FMラジオなど。    |
| ボリュームの調整   | ボリュームの値を提供し、波形の形でボリュームを表示できます。        | 音声通話、ビデオ通話、音声チャットルーム、FMラジオ、カラオケルーム、人の声の検出など。    |
| インイヤ・モニタリング           | ローカルでレコーディングした音声をローカルのイヤホンで再生できるため、自分で自分が発した声を聴くことが可能。一般的に話した内容の訂正やイントネーションのチェックに利用します。 | インタラクティブストリーミング、ショーのライブストリーミング、カラオケルームなど。                               |
| カスタムオーディオデータ | 自分でキャプチャした音声データのコールバック処理をサポート。開発者はネイティブデータに対する処理を行い、カスタマイズした操作を実施することが可能です（例：非標準装置への接続、音声ファイルなど）。 | 非標準装置の接続、カスタムのオーディオ効果、音声処理、音声識別など。         |
|カスタムビデオデータ | カスタムビデオソースとレンダリングエンジンをサポート。動画ファイル、外部デバイス、サードパーティのカスタムデータソースなどのカメラ以外のビデオソースを利用できます。 | カスタムの美顔、カスタムデータソース、マルチデバイス管理、ビデオ認識、画像処理など。   |
| SEI 情報       | 　SEIフレームを通じてビデオストリームに歌詞、問題などのカスタム情報を埋め込み、他のユーザーと共有できます。| カラオケルーム、クイズのライブストリーミング、インタラクティブストリーミングなど。                               |


## 拡張機能

>?拡張機能は、TRTCとTencent Cloudの他のクラウドサービスをドッキングさせることで、お客様にご提供する付加価値サービスです。その他クラウドサービスについては、各々の課金ルールに基づき、関連費用がそれぞれ徴収されます。


| 機能         | 機能説明                                                     | 一般的なユースケース                                       | 課金説明                                                     |
| ------------ | ------------------------------------------------------------ | -------------------------------------------------- | ------------------------------------------------------------ |
| バイパスプッシュ | TRTCはクラウド上でバイパストランスコーディングクラスターを活用し、TRTCで使用する UDP プロトコルを標準のライブストリーミングRTMPプロトコルに変換して、TRTCの音声ビデオデータを標準のLVBシステムにプッシュします。さらに CDNを介して視聴者に配信されます。これにより CDN ライブウォッチを実現します。 | インタラクティブストリーミング、ライブ共有、大型ミーティング、リモート視聴など。 | Relayed Live Streamingは付加価値サービスに属し、**[LVB](https://intl.cloud.tencent.com/document/product/267)** 経由で関連費用が徴収されます。詳細は [CDN relayed live streaming > 関連費用](https://intl.cloud.tencent.com/document/product/647/35242)をご参照ください。 |
| IMインスタントメッセージング  | <li>IMのシングルチャット、グループチャット、人数制限なしのチャットルームによって、チャットメッセージ、コメント、弾幕、プレゼント、「いいね！」等の機能が実現できます。</li><li>IM経由でシグナリングインタラクションを実行し、通話呼び出し、ルームユーザー数統計などの機能が実現可能です。</li> | オンラインカスタマーサービス、インタラクティブストリーミング、双方向対話型授業、リモートトレーニングなど。         | IMは付加価値サービスに属し、**[Instant Messaging](https://intl.cloud.tencent.com/document/product/1047)**経由で関連費用が徴収されます。詳細は、[料金](https://intl.cloud.tencent.com/document/product/1047/34350)をご参照ください。 |
