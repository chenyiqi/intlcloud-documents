

## サーバーフリート 

複数のCVMインスタンスから1個のサーバーフリートが構築されています。1個のCVMが複数のゲームサーバーセッションを実行します。GSEのゲームサーバーセッションの管理とアサインについて、通常、1個のゲームサーバーセッションは1個のプロセスです。

![](https://main.qcloudimg.com/raw/9539e4c5e762feadcf331ac3ca15b2ac.png)




### CVM Auto Scaling

- ゲームサーバーセッションバッファーに基づきAuto Scalingを実行します。   
クライアントが構成するゲームサーバーセッションバッファーは、残っているアイドル状態のサーバープロセスの割合を意味します。アイドル不足時はスケールイン、アイドルが十分であるときはスケールアウトが実行されます。

- ステートフルなスケールイン・アウト  
GSEは実行中のゲームサーバーセッションのインスタンスを減らしません。スケールイン時には、GSEがゲームサーバーセッションに通知するため、ゲームサーバーセッションはすぐにスケールインを実行するどうかを決定できます。開発者が製品構成ページで完全保護を選択し、ゲームサーバーセッションがずっと実行状態でスケールインに同意しない場合、スケールインは永遠に実行されません。





## ゲームサーバーキュー

ゲームサーバーキューとは、1セットの優先順位のあるサーバーフリートのキューです。このキューは、世界各地のサーバーフリートを含んでいるため、最寄りのスケジューリングと災害復帰を可能とする条件を有しています。

![](https://main.qcloudimg.com/raw/ec7a6961656f315de95a1c10d981de37.png)



#### 災害復帰の原理 
GSEはマルチリージョンへのデプロイをサポートし、複数エリアでサービスフリートを構築し、それらで1個のサーバーフリートのキューを構成しています。ある地域で不具合が発生した場合、クライアントからサーバーまでのディレーが非常に大きくとなると、システムはディレーが小さいエリアに自動で切り換え、災害復帰を実現します。同時に開発者は手動でフリートの優先順位を調整し、キューから不具合のエリアを除外できます。

#### 最寄りアサインの原理 
GSEの速度測定ツールは、クライアントからサーバーまでのディレーを測定できます。対戦系のシナリオでは、GSEは総合的にすべてのルームのプレイヤーに近いエリアのサーバーをクライアントにアサインします。



## エイリアス 

クライアントはエイリアス（alias）からサーバーフリート（fleet）のサーバーをリクエストをします。バージョンをアップデートする場合、サーバーフリート（fleet）を新規作成し、新規作成したフリートを指定してエイリアス（alias）を構成します。クライアントは依然として同一のエイリアスを呼び出せるため、ノンストップのアップデートが可能となります。
![](https://main.qcloudimg.com/raw/84df25b4e1609cafb0cf7271e7a0aaf4.png)





