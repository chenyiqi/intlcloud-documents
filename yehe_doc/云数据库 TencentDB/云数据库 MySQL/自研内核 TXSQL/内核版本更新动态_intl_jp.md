このドキュメントでは、MySQLカーネルのバージョンに関する更新情報について説明します。アップグレードが必要な場合は、[カーネルマイナーバージョンのアップグレード](https://intl.cloud.tencent.com/document/product/236/36816)をご参照ください。

## MySQL 8.0
### 20200630
#### 新機能：
- 大きなテーブルの非同期削除が可能：ファイルを非同期かつゆっくりとクリーンアップすることで、大きなテーブルの削除によるビジネスパフォーマンスの変動を回避します。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。
- リソースの競合を減らすために、アイドルタスクの自動強制終了をサポートします。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。　　
- 透過的データ暗号化（TDE）をサポートします。


#### 公式バグの修正：
- relay_log_posとmaster_log_posの間のチェックポイントに一貫性がないために切り替えが失敗するエラーを修正しました。
- 非同期でディスクにデータを保存することにより発生するデータファイルエラーを修正しました。
- fsyncがEIOを返すことを繰り返してデッドループに陥ってしまうという不具合を修正しました。
- フルテキストインデックスにおけるマルチバイト文字セットでのフレーズ検索（phrase search）に発生したクラッシュ問題を修正しました。

## MySQL 5.7
### 20200701
#### 公式バグの修正：
- INNOBASE_SHARE index mapping のエラーの不具合を修正しました。

### 20200630
#### 新機能：
- SELECT FOR UPDATE/SHARE のステートメントに NOWAITとSKIP LOCKED の選択項目の使用をサポートしました。
- 大量のトランザクションを最適化する機能をサポートし、大量のトランザクションによるマスターに対するスレーブの遅延、バックアップ失敗等の不具合を修正しました。
- 監査機能を最適化し、非同期監査機能をサポートしました。

#### 公式バグの修正：
-  digest_add_token 関数のオーバーフローの不具合を修正しました。
- insert blob によるインスタンス crash の不具合を修正しました。
- hash scanでevent中に同じ行に対する更新が発生してレコードが見つからず、マスター／スレーブのレプリケーション中断が起きる不具合を修正しました。
- performance_schema のクエリー時にハングする不具合を修正しました。

### 20200331
#### 新機能：
- 公式のMySQL 5.7.22 JSONシリーズ関数が追加されました。
- 電子商取引のフラッシュセール（seckill）ケースに基づく[ホットスポットの更新](https://intl.cloud.tencent.com/document/product/1035/36037)機能をサポートしています。
- [SQLトラフィック制限](https://intl.cloud.tencent.com/document/product/1035/36037)をサポートしています。
- データ暗号化機能は、KMSカスタムキーの暗号化をサポートしています。

#### 公式バグの修正：
- フルテキストインデックスにおけるマルチバイト文字セットでのフレーズ検索（phrase search）に発生したクラッシュ問題を修正しました。
- 同時実行数が多い場合、CATSロックスケジューリングモジュールに発生したクラッシュ問題を修正しました。

### 20190830
#### 新機能：
- binlogファイルが破損した場合にスキップして解析を続ける機能をサポートします。マスターインスタンスとbinlogの両方が破損した場合に、最大限にスレーブデータベースからデータを復元して利用します。
- 非GTIDモードからGTIDモードへのデータ同期をサポートします。
- ユーザーがshow full processlistステートメントを使用して「ユーザースレッドのメモリ使用状況」を確認することをサポートします。
- テーブルの[高速列作成機能](https://intl.cloud.tencent.com/document/product/236/35990)をサポートし、データをコピーせず、ディスク領域やディスクI/Oを消費せず、サービスのピーク時にもリアルタイムで変更できます。
- 永続的な自動インクリメント値をサポートします。

#### 公式バグの修正：
- GRANTステートメントの列名に予約語がある場合にレプリケーションが中断するという不具合を修正しました。
- パーティションテーブルで逆方向スキャンを実行するとSQLの実行効率が低下するという不具合を修正しました。
- プライマリキーを含むテーブルの仮想インデックスのデータ不整合によって、クエリー結果の異常が発生するという不具合を修正しました。
- InnoDBでプライマリキーを範囲検索するとデータが欠落するという不具合を修正しました。
- スペースインデックスを持つテーブルでDDLを実行するによって引き起こされるクラッシュを修正しました。
- binlogのサイズが大きすぎると、ハートビート情報内のファイルの長さがオーバーフローし、マスター／スレーブが中断するという不具合を修正しました。
- eventを削除すると他のeventが時間通りに実行されなくなるという不具合を修正しました。
- 検索結果をまとめるとエラーが発生するという不具合を修正しました。

### 20190615
#### 新機能：
- 透過的データ暗号化（TDE）をサポートします。

### 20190430
#### 公式バグの修正：
- サブクエリーで長いテキスト機能を使用した場合のNULLポインタ参照の不具合を修正しました。
- Hash Scanを実行するとマスター／スレーブが中断するという不具合を修正しました。
- マスターデータベースのbinlogのスイッチによってslaveノードのI/Oスレッドが中断するという不具合を修正しました。
- NAME_CONSTによって引き起こされるクラッシュを修正しました。
- 文字セットによる「不正な照合順序の混在」エラーを修正しました。


### 20190203
#### 新機能：
- 大きなテーブルの非同期削除が可能：ファイルを非同期かつゆっくりとクリーンアップすることで、大きなテーブルの削除によるビジネスパフォーマンスの変動を回避します。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。
- CATSのスケジューラをロックする方式をサポートします。
- GTIDを有効にすると、トランザクション内の一時テーブルおよびCTS構文を作成・削除することができます。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。
- 暗黙的なプライマリキーをサポートします。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。
- super権限以外のユーザーが他のユーザーのセッションを強制終了する機能をサポートします。cdb_kill_user_extraパラメータを使用して設定します。デフォルト値はroot@%です。
- エンタープライズクラスの暗号化関数をサポートします。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。

#### 公式バグの修正：
- binlogキャッシュファイルの容量が不足している場合にレプリケーションが中断されるという不具合を修正しました。
- fsyncがEIOを返すことを繰り返してデッドループに陥ってしまうという不具合を修正しました。
- GTIDの欠番によってレプリケーションが中断され、再開できないという不具合を修正しました。
  

### 20180918
#### 新機能：
- アイドル状態のトランザクションを強制終了してリソースの競合を減らすことをサポートします。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。
- MemoryエンジンからInnoDBエンジンへの自動切り替え：グローバル変数cdb_convert_memory_to_innodbがONの場合、テーブルエンジンはテーブルの作成/変更時にMemoryからInnoDBに変換されます。
- インデックスの非表示機能をサポートします。
- Jemallocによるメモリ管理をサポートします。これにより、jlibcメモリ管理モジュールを置き換え、メモリ使用量を削減し、メモリ割り当て効率を向上させることができます。
  
#### パフォーマンスの最適化：
- binlogのスイッチを最適化し、rotateのホールドロック時間を短縮させることで、システムパフォーマンスを向上させます。
- クラッシュの回復速度を向上させます。
  
#### 公式バグの修正：
-  マスター／スレーブの切り替えによるeventの無効化の不具合を修正しました。
- REPLAY LOG RECORDによって引き起こされるクラッシュを修正しました。
- Lose index scansによってクエリー結果にエラーが発生するという不具合を修正しました。


### 20180530
#### 新機能：
- SQL監査機能をサポートします。
- テーブルレベルの並列レプリケーションをサポートします。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。
  
#### パフォーマンスの最適化：
- slaveインスタンスのロックを最適化し、slaveインスタンスの同期パフォーマンスを向上させます。   
- select ... limitステートメントのプッシュダウンを最適化します。
  
#### 公式バグの修正：
- relay_log_posとmaster_log_posの間のチェックポイントに一貫性がないために切り替えが失敗するエラーを修正しました。
- Crash on UPDATE ON DUPLICATE KEYによるCrashの不具合を修正しました。
-JSONカラムのインポートによる「Invalid escape character in string.」のエラーを修正しました。
  
### 20171130
#### 新機能：
- information_schema.metadata_locksビューをサポートし、現在のインスタンスにおけるMDLの付与及び待機ステータスを確認します。
- ALTER TABLE NO_WAIT | TIMEOUT構文をサポートし、DDL操作に待機タイムアウトを与えます。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。
- スレッドプール機能をサポートします。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。

#### 公式バグの修正：
- bytes_dataに基づいてinnodb_buffer_pool_pages_dataを計算し、このパラメータのオーバーフローを回避します。
- 非同期モードで速度制限プラグインが使用できないという不具合を修正しました。

   
## MySQL 5.6
### 20200915
#### 新機能：
- [SQLトラフィック制限](https://intl.cloud.tencent.com/document/product/1035/36037) 機能をサポートしています。

#### パフォーマンスの最適化：   
- buffer pool の初期化アクセラレーションを最適化します

#### 公式バグの修正：
- マスター／スレーブのrename tableがハングする不具合を修正しました。 
- event_schedulerの設定をdisableにした場合、cdb_skip_event_schedulerをon からoffに変更した際に、crashが発生する不具合を修正しました。 
- tencentroot 最大リンク数に srv_max_n_threadsがカウントされず、sync_wait_array関連のアサーションが失敗する不具合を修正しました。 
- 他のクラウド製品のMySQL 5.6 とTencent MySQL 5.6 のシステムデータベース中のテーブル構造の一部が異なるため、マスター／スレーブの並列レプリケーションを行った際に、crashが発生する不具合を修正しました。 
- INSERT ON DUPLICATE KEY UPDATE THE WRONG ROW の不具合を修正しました。 
- index_mappingにエラーが起きる不具合を修正しました。 
- mtr 失敗のbugの問題を修正しました。 
- hash scanでevent 中に、同じ行に対する更新が発生した時にレコードが見つからなくなり、マスター／スレーブのレプリケーション中断が起きる不具合を修正しました。 

### 20190930
#### 新機能：
- ユーザーがshow full processlistステートメントを使用して「ユーザースレッドのメモリ使用状況」を確認できます。  

#### 公式バグの修正：
- スレーブデータベースのレプリケーションフィルターによるgtid欠番の不具合を修正しました。
- Binlogのサイズが大きすぎると、ハートビート情報内のファイルの長さが制限を超えた、マスター／スレーブが中断するという不具合を修正しました。
- 文字セットによる「不正な照合順序の混在」エラーを修正しました。
- Hash Scanを実行するとマスター／スレーブが中断するという不具合を修正しました。
- NAME_CONSTの使用によって引き起こされるクラッシュを修正しました。
- マスターデータベースのbinlogのスイッチによってslaveノードのI/Oスレッドが中断するという不具合を修正しました。
- innodb_log_checusumによるバックアップに互換性がないという不具合を修正しました。

### 20190530
#### 公式バグの修正：
- RCモードでダーティデータが読み込まれるという不具合を修正しました。
- 一時テーブルを削除するとスレーブインスタンスの再生に失敗するという不具合を修正しました。
- 高並列処理でのデッドロックの不具合を修正しました。
  

### 20190203
#### 新機能：
- 大きなテーブルの非同期削除が可能：ファイルを非同期かつゆっくりとクリーンアップすることで、大きなテーブルの削除によるビジネスパフォーマンスの変動を回避します。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。
- super権限以外のユーザーが他のユーザーのセッションを強制終了する機能をサポートします。cdb_kill_user_extraパラメータを使用して設定します。デフォルト値はroot@%です。
- GTIDを有効にすると、トランザクション内の一時テーブルおよびCTS構文を作成・削除することができます。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。
  
#### パフォーマンスの最適化：   
- パーティションテーブルのレプリケーションと再生を最適化することで、パーティションテーブルの再生速度を向上させます。
  
#### 公式バグの修正：
- 一時的な空き容量が不足しているため、マスター／スレーブ間でデータが一致しないという不具合を修正しました。
- ホットログレコードを更新するとハングアップするという不具合を修正しました。
- 並列レプリケーションでのSeconds_Behind_Master値に異常が発生するという不具合を修正しました。

### 20180915
#### 新機能：
- MEMORYエンジンからInnoDBエンジンへの自動切り替え：グローバル変数cdb_convert_memory_to_innodbがONの場合、テーブルエンジンはテーブルの作成/変更時にMEMORYからInnoDBに変換されます。
- アイドル状態のトランザクションを強制終了してリソースの競合を減らすことをサポートします。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。
  
#### 公式バグの修正：
- REPLAY LOG RECORDによって引き起こされるクラッシュを修正しました。
- decimalの精度によるマスター／スレーブ間の時間データに不整合が生じる不具合を修正しました。


### 20180130
#### 新機能：
- スレッドプール機能をサポートします。この機能を有効化するには、[チケットを提出](https://console.cloud.tencent.com/workorder/category)して申請する必要があります。
- slaveノードはレプリケーションフィルタリングルールの動的な変更をサポートします。

#### パフォーマンスの最適化：
- drop tableによるパフォーマンスの変動。
  
#### 公式バグの修正：
- パスワード文字列の認証によるデータベースのcrashの不具合を修正しました。
  
### 20180122
#### 新機能：
- SQL監査機能をサポートします。

#### 公式バグの修正：
- 整数オーバーフローのエラーを修正しました。
- フルテキストインデックスにおけるクエリーにエラーが発生するという不具合を修正しました。
- レプリケーション中にslaveがcrashするという不具合を修正しました。
	
### 20170830
#### 公式バグの修正：
- 非同期モードでbinlog速度制限が無効化になるという不具合を修正しました。
- buffer_poolステータスに異常が発生するという不具合を修正しました。
- SEQUENCEと暗黙的なプライマリキーの競合を修正しました。
  
### 20170228
#### 公式バグの修正：
- drop tableの文字コードのバグを修正しました。
- replicate-wild-do-tableが小数点などの特殊文字を含むデータベース又はテーブルを正しくフィルタリングできない不具合を修正しました。
- スレーブデータベースからrotateイベントが発生した後にSQLスレッドが早く終了するという不具合を修正しました。
  
### 20161130
#### パフォーマンスの最適化：
- lock_logロックを分割し、lock logにかかる時間を短縮させ、並列処理のパフォーマンスを向上させます。
- マスターデータベースのACKスレッドが独立して動作するようにして、応答時間が向上します。
- ファントムリードを防ぐために、ACKを待機している間、ユーザースレッドが強制終了されることを禁止します。
- sync_binlog !=1の場合に、不要なlock_syncロックになることを修正しました。

