ストレージエンジンはテーブルのタイプであり、データベースのストレージエンジンはテーブルをコンピュータにどのように格納するかを決定します。MySQLデータベースは機能の異なる複数のストレージエンジンをサポートしていますが、すべてのエンジンがリカバリ及びデータ耐久性のために最適化されているわけではありません。ポイント・イン・タイム・リカバリやスナップショットリストアなどのTencent MySQL機能には、リカバリ可能なストレージエンジンが必要であり、これらの機能はInnoDBストレージエンジンのみがサポートしています。

Tencent MySQLはInnoDBストレージエンジンをデフォルトでサポートしますが、バージョン5.6以降ではMyISAMエンジン及びMemoryエンジンがサポートされていません。主な理由は以下の通りです。
- 現在のMySQLバージョンでは、TencentDBはInnoDBに対して多くのカーネル最適化を行っており、パフォーマンス上の大きな利点を持っています。
- MyISAMはテーブルレベルのロック機構を使用していますが、InnoDBは行レベルのロック機構を使用しています。通常、InnoDBはより高い書込効率があります。
>?
>- テーブルレベルロックは、MySQLでロックの粒度が一番大きなロックであり、現在操作の対象となるテーブル全体をロックすることを示します。
>- 行レベルロックは、MySQLでロックの粒度が一番小さなロックであり、現在操作の対象となる行のみをロックすることを示します。
- MyISAMによるデータの完全性保護に欠陥があり、それらの欠陥はデータベースデータの破損又は紛失の原因となります。また、これらの欠陥の多くは設計上の問題であり、互換性を損なわずに修正することはできません。
- MyISAM及びMemoryをInnoDBに移行するコストは低く、ほとんどのアプリケーションではテーブルを作成するためのコードを変更するだけで移行できます。
- MyISAMはInnoDBに移行しています。最新の公式MySQLバージョン8.0では、システムテーブルにすべてInnoDBが採用されています。
- Memoryではデータの完全性が保証されていません。インスタンスのリスタート又は マスター・スレーブの切替が発生すると、テーブル内のすべてのデータが失われます。できるだけ早くInnoDBに移行することを推奨します。

詳細については、[InnoDBの概要](https://dev.mysql.com/doc/refman/5.7/en/innodb-introduction.html)及び[MyISAMの概要](https://dev.mysql.com/doc/refman/5.7/en/myisam-storage-engine.html)をご参照ください。

