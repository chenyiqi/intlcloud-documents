## 同期遅延の影響
TencentDB for MySQLのデフォルトのスレーブデータベース、ディザスタリカバリインスタンス、読み取り専用インスタンスはいずれもMySQLのネイティブbinlogレプリケーションテクノロジーを使用しており、データのレプリケーション方式が非同期または準同期レプリケーションの時、いずれも遅延が発生する恐れがあります。

- [スレーブデータベース](https://intl.cloud.tencent.com/document/product/236/38328) に遅延が存在する場合、マスター／スレーブインスタンスが短時間で切り替えを完了できなくなり、これにより業務にも影響が出て、短時間で正常にリストアできなくなります。

## よくある原因とその対処方法
[監視機能](https://intl.cloud.tencent.com/document/product/236/8455) により、【マスター／スレーブの遅延時間】を確認することができます。マスター/スレーブの遅延時間が0より大きい場合、そのインスタンスにデータ遅延が存在することを表します。一般的な原因は以下のとおりです。

### 非プライマリキーまたはセカンダリインデックス
**原因**
binlogがrow形式でかつテーブルが非プライマリキーまたはセカンダリインデックスの場合、ビッグテーブルに対してDML操作（例：delete、update、insert）を行い、スレーブデータベースでbinlogアプリケーションを行う時、プライマリキーまたはセカンダリインデックスに基づき変更する必要のある行を検索します。対応するテーブルがプライマリキーまたはセカンダリインデックスを作成していない場合、大量の全テーブルスキャンが発生することによりログ応用の速度が低下し、その結果、データ遅延が発生します。

**対処方法**
- すべてのテーブルにプライマリキーを作成します。テーブルにプライマリキーを作成できない場合、基数が高い列を選択してセカンダリインデックスを作成することをお勧めします。
- truncateコマンドを使用してテーブルのすべての記録を削除することをお勧めします。

### 大規模トランザクション
**原因**
マスターインスタンスが大量のデータを含むDML操作を実行し、大量のbinlogがスレーブデータベースに送信される時、スレーブデータベースはマスターインスタンスと同じ時間を費やして対応するトランザクションを完了する必要があり、それによりスレーブデータベースにデータ遅延が発生します。

**対処方法**
大規模トランザクションを小規模トランザクションに分割し、where条件により毎回処理するデータ量を制限することをお勧めします。これにより、スレーブデータベースの迅速なトランザクション実行完了に役立ち、スレーブデータベースの遅延発生が避けられます。

### DDL操作
**原因**
大規模トランザクションの原理と似ており、マスターインスタンスでのDDL操作の実行時間が長い場合、スレーブデータベースで同じかそれ以上の時間を費やしてこの操作を実行するため、DDL操作が妨害される可能性があります。

**対処方法**
ビジネスのオフピーク期間にDDL操作を実行することをお勧めします。ディザスタリカバリインスタンス、読み取り専用インスタンスのクエリービジネスによりDDL操作がブロックされた場合、ブロックされたセッションを直接強制終了して、マスター／スレーブデータの同期をリカバーすることをお勧めします。

### インスタンスの規格が小さすぎる
**原因**
ディザスタリカバリインスタンス、読み取り専用インスタンスの規格がマスターインスタンスよりも小さく、かつ負荷が高いと、ディザスタリカバリインスタンス、読み取り専用インスタンスのデータ遅延が発生します。

**対処方法**
ディザスタリカバリインスタンス、読み取り専用インスタンスの規格をマスターインスタンス以上にすることをお勧めします。ディザスタリカバリインスタンス、読み取り専用インスタンスが大量の分析類ビジネスをホストすることによりインスタンスの負荷が過剰に高くなった場合、そのインスタンスの規格を適切な構成にアップグレードするか、低パフォーマンスのSQLステートメントを最適化する必要があります。


## Waiting for table metadata lock のエラー
**原因**
長時間のトランザクションを実行すると、DDLがブロックされ、これが続くと同一テーブルの全ての後続の操作に支障がでます。またトランザクションを送信しない場合も、DDLがブロックされ、これが続くと同一テーブルの全ての後続の操作に支障がでます。この場合は、以下の対処方法をお勧めします。

**対処方法**
 [TencentDB for DBbrain](https://intl.cloud.tencent.com/document/product/1035/36036) を使用して実際の業務およびインスタンスに対する診断を行い、スローログなどの指標を調査して、時間を消費するトランザクションを特定することをお勧めします。
- DBbrainの診断結果にもとづき、DDL関連の構文を最適化します。
- 読取専用ノード上でユーザーのクエリーが上層で実行されるため、読み取り専用ノード上で実行時間が非常に長いクエリーが行われると、このクエリーが、実行が完了するまで、マスターデータベースからのDDLを堰き止め、これにより読み取り専用ノードのデータ遅延が発生します。
DBbrainによって時間を消費する大きなクエリーを特定して、読み取り専用ノード上の大量のクエリーをkill（強制終了）すれば、読み取り専用ノードとマスターノードのデータの同期を回復できます。
- DBbrainによって時間の長いトランザクションを特定し、長時間のトランザクションを小さく分割して実行すれば、読み取り専用ノードが迅速にトランザクションを完了でき、データ遅延が発生することはありません。
