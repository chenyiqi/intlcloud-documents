##　概要
バックアップスペースはあるリージョンにおけるすべてのMySQL インスタンスのバックアップファイルを保存することに使われています。バックアップファイルは自動的データバックアップ、手動データバックアップ及びログバックアップから構成されています。

MySQLはリージョンにより一定の無料バックアップスペースを贈与します。無料バックアップスペースの容量は顧客の対応するリージョンにおけるすべての高可用性インスタンス（マスターインスタンス、災害復帰インスタンスを含む）の合計ストレージスペースです。
>
>- 読取専用インスタンスROを購入する場合は、バックアップスペースの贈与をもらうことができません。マスターインスタンス及び災害復帰インスタンスを購入する場合のみ、贈与をもらうことが可能です。
>- バックアップスペースの容量は [MySQL コンソール](https://console.cloud.tencent.com/cdb/backup) のデータベースバックアップページで表示できます。

## バックアップの価格
無料限度を超えたバックアップスペースについて、中国大陸部では0.000127米ドル/GB/時間で課金されます。
課金スペースが1GB以下の場合は、実際の課金が発生しません。1時間以下の場合は、1時間として課金されます。MySQLの贈与ポリシーは柔軟的であり、圧倒的多数のインスタンスはバックアップスペースのためにお金を支払う必要がありません。

## バックアップの課金日程
- 2019年12月02日0時から、中国香港・中国マカオ・中国台湾地域及びほかの海外地域は正式に課金を行います。
- 2019年12月02日0時から、西南地域（成都、重慶）は正式に課金を行います。
- 2019年12月05日0時から、華南地域（広州）は正式に課金を行います。
- 2019年12月09日0時から、華北地域（北京）は正式に課金を行います。
- 2019年12月10日0時から、華東地域（上海）は正式に課金を行います。


## 計算式

**無料バックアップスペース（単一地域）= 当該地域で購入されたMySQL高可用性インスタンスの合計ストレージスペース**

**課金部分（単一地域）= データのバックアップ容量（当該地域）+ ログのバックアップ容量（当該地域）- 無料バックアップスペース（当該地域）**

>ゴミ箱におけるMySQLインスタンスバックアップはバックアップスペースにカウントされ、合計スペースに算入されます。

**計算例**
例えば、顧客は広州三区に実行中のMySQL高可用性インスタンス（購入されたデータベースストレージスペースが每月500GBである）が一つあり、広州四区に実行中のMySQL高可用性インスタンス（購入されたデータベースストレージスペースが每月200GBである）が一つある場合、広州地域には每月700GBの無料バックアップスペースがあります。

ユーザーは広州地域での合計バックアップストレージスペースが700Gを超えた場合（例えばデータバックアップは800G、ログバックアップは100Gである）、1時間当りの課金スペース = 800 + 100 - 700 = 200GBとなります。ユーザーは余分な200GBのためにバックアップスペース費用を支払う必要があります。これによって類推します。

## バックアップのライフサイクル

<span id = "anliang_zhouqi"></span>
### 従量課金インスタンス
- バックアップはインスタンスのライフサイクルに応じて変わっています。
- インスタンス満期後の2時間以内は、正常にバックアップを行えます。
- インスタンス満期後の2時間後、インスタンスはごみ箱に隔離されます。この場合は、自動バックアップは停止され、ロールバックや手動バックアップは禁止されますが、バックアップのダウンロードは許可されます（[バックアップリスト](https://console.cloud.tencent.com/cdb/backup)ページからダウンロードできます）。また無料のバックアップスペースを超えたバックアップは課金されます。ユーザーがコンソールのごみ箱から更新操作を実行してインスタンスの復元とバックアップを実行することができます。
- インスタンスは1日隔離されたら正式にオフラインになります。この時にインスタンスは確実に廃棄され、関連するデータバックアップも一緒に廃棄されますので、ユーザーの必要となるバックアップを適時に保存してください。

## アカウントの支払い延滞に関する説明

### 従量課金インスタンス
アカウントに支払い延滞があった場合は、バックアップがユーザーのインスタンスのライフサイクルとともに変わります。上述の従量課金バックアップのライフサイクルに関する説明をご参照ください。


## 事業者向けのバックアップサービスの向上
>下表記載の数値は一つのTencent Cloudアカウントが同じ地域で対応できる各項目の最大値です。

| 利用内容             | アップグレード前         | アップグレード後          |
| ------------------ | -------------- | --------------- |
| データバックアップの保留時間   | 30日             | 732日             |
| ログバックアップの保留時間 | 5日              | 732日             |
| バックアップの圧縮率         | 一般圧縮率              | 極めて高い圧縮率               |
| binlog 集中化         | ローカルストレージ | 集中化ストレージ |

## バックアップ支出削減に関するアドバイス
- これから使わない手動バックアップデータを削除します。（手動バックアップはコンソールで削除できます） 
- 中核でないサービスの自動的バックアップ頻度を下げます。（毎週のバックアップ日数を調整できます。週に少なくとも2日分をバックアップします）
>[ロールバック機能](https://intl.cloud.tencent.com/document/product/236/7276) バックアップ間隔とバックアップの保持日数以内のデータバックアップ + ログバックアップ(binlog)に基づき、自動バックアップ頻度と保持日数を減らすとインスタンスデータのロールバック機能に影響を与えるため、バックアップのコンフィグレーションをよく考慮してください。
>
- 中核でないサービスのデータバックアップ及びログバックアップの保存時間を短縮します。（7日間のバックアップ保留時間は大部分のサービスケースのニーズを満たしています）

| サービスケース             | バックアップ保留時間                                                 |
| -------------------- | ------------------------------------------------------------ |
| 中核サービス             | 7日 - 732日をお薦めします                                              |                               　
| 中核でない、データ類でないサービス | 7日をお薦めします                                                       |                                                  
| アーカイブ類サービス             | バックアップの保留時間を7日間とし、実際のサービスニーズにより手動でデータをバックアップし、使い終わったら適時に削除することをお薦めします |
| テスト類サービス             | バックアップの保留時間を7日間とし、実際のサービスニーズにより手動でデータをバックアップし、使い終わったら適時に削除することをお薦めします |

