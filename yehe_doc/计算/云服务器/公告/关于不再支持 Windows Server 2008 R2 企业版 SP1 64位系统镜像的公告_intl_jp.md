## ご利用説明
Microsoftは2020年1月14日をもって「Windows Server 2008」関連のオペレーティングシステムのメンテナンスサポートが正式に終了しました。Tencent Cloudは2020年3月16日にWindowsServer 2008 R2 Enterprise Edition SP1 64ビットパブリックイメージも非アクティブ化しました。同時に、Tencent CloudでWindows Server 2008 R2 Enterprise Edition SP1 64ビットシステムのCVMを実行する場合、この日付以降にはMicrosoftからセキュリティ更新プログラムとパッチを取得できません。また、プログラムの互換性、不安定性、セキュリティなどの問題及びリスクに直面します。

現在、このイメージを使用してCVMインスタンスを作成または再インストールすることはできなくなりましたが、カスタムイメージ、マーケットプレイスイメージ、またはイメージのインポートの使用には影響を受けません。ビジネスのセキュリティと安定性を確保するために、既存のWindows Server 2008 R2 Enterprise Edition SP1 64ビット CVMインスタンスをWindows Server2012以降のバージョンに移行することをお勧めします。

## リスク通知
MicrosoftからWindows Server 2008のセキュリティ更新プログラムとパッチを取得できないため、Tencent CloudはOSに関連する問題を解決できません。Windows Server 2008 R2 Enterprise Edition SP1 64ビットシステムを継続利用する場合、下記のリスクを充分ご了承ください。
1. Windows Server 2008 R2 Enterprise Edition SP1 64ビット OSのCVMを継続利用する場合、2020年3月16日以降、Microsoftが提供する更新プログラムとパッチを継続取得することはできなくなります。同時に、お客様のアプリケーションと業務はさまさまなリスクに直面します。セキュリティ問題、アプリケーションの非互換性 、コンプライアンス要件、および他の非機能問題によって引き起こされる未知のセキュリティリスクを含み、それに限定されません。
2. 2020年3月16日以降、Windows Server 2008のCVMを継続利用する場合、このOSに対するMicrosoftのサポートの欠如により、故障、セキュリティ問題、非互換性、又はより高い未知のリストを引き起こす場合、Tencent Cloudは責任を負いかねますのでご了承ください。お客様が該当するリスク、結果、責任を負う必要があります。

## サービスを利用する前に知っておくべき
MicrosoftからWindows Server 2008 のセキュリティ更新プログラムとパッチを取得できないため、Tencent CloudはOSに関連する問題を解決できません。下記状況はTencent Cloudのサービス品質不良、故障又は責任に属しません。
1. Windows Server 2008 R2 Enterprise Edition SP1 64ビット OSを実行しているインスタンスは、障害のリスクが高くなる可能性があります。さまざまなセキュリティ問題、非互換性、または適切に動作できないことが発生し、完全にフリーズする場合もあります。
2. Windows Server 2008 R2 Enterprise Edition SP1 64ビット OSのインスタンスで実行されているアプリケーションに障害が発生し、Microsoftパッチをインストールするか、又はMicrosoftがOSレベルのトラブルシューティングサポートを提供する必要がある場合は、我々は経験豊富なサービス技術者がトラブルシューティングをお手伝いしますが、完全な問題解決策を提供できない場合があります。
3. ハードウェアの互換性とドライバー関連の制限により、将来新しいTencent Cloud CVM はWindows Server 2008イメージの実行をサポートできなくなる可能性があります。

