## 操作シナリオ

セキュリティグループは、インスタンスの仮想ファイアウォールとして機能し、1つまたは複数のCVMのネットワークアクセス制御を設定するために使用され、Tencent Cloudが提供する重要なネットワークセキュリティ分離方法です。CVMインスタンスを作成する際に、そのインスタンスのセキュリティグループを設定する必要があります。Tencent CloudはユーザーがCVMインスタンスを作成した後にインスタンスが属するセキュリティグループを変更することをサポートしています。
> インスタンスの新しいセキュリティグループを設定したい場合は、先にセキュリティグループを新規作成してください。詳細については、 [セキュリティグループの作成](https://intl.cloud.tencent.com/document/product/213/34271)をご参照ください。

## 前提条件

[CVMコンソール](https://console.cloud.tencent.com/cvm/index)にログインします。

## 操作手順

### 設定されたセキュリティグループの変更

CVMコンソールでのユーザーエクスペリエンスを向上させるために、インスタンス管理ページまたはインスタンス詳細ページでセキュリティグループを設定できます。

#### インスタンス管理ページでのセキュリティグループの設定

1. 次の図に示すように、インスタンス管理ページで新しいセキュリティグループに再割り当てするCVMを選択し、【その他】>【セキュリティグループ】>【セキュリティグループの設定】をクリックします。　　　
![](https://main.qcloudimg.com/raw/68a30faac347446e57d87e8a1c30ef11.png)
2. 表示されるポップアップウィンドウで、新しいセキュリティグループの名前（複数選択可能）をチェックし、【OK】をクリックすると、セキュリティグループの変更操作が完了します。
 
####  インスタンスの詳細ページでのセキュリティグループの設定
 
1. インスタンス管理ページで、セキュリティグループを変更する必要のあるCVMインスタンスID/インスタンス名をクリックし、このインスタンス詳細ページに進みます。
2. 次の図に示すように、インスタンス詳細ページの右上隅にある【その他】>【セキュリティグループの設定】をクリックします。
![](https://main.qcloudimg.com/raw/c7a1d76159feaa66f52eb16c7787432d.png)
3.  表示されるポップアップウィンドウで、新しいセキュリティグループの名前（複数選択可能）をチェックし、【OK】をクリックします。

### バインドされたセキュリティグループの変更

1. インスタンス管理ページで、セキュリティグループをバインドする必要のあるCVMインスタンスID/インスタンス名をクリックし、このインスタンスの詳細ページに進みます。
2. 次の図に示すように、インスタンス詳細ページで【セキュリティグループ】タブを選択し、「バインドされたセキュリティグループ」欄で、【バインド】をクリックします。
![](https://main.qcloudimg.com/raw/2ea553a1f2f589c6202245addfd62523.png)
3. 次の図に示すように、表示されるポップアップウィンドウで、実際のニーズに応じて、バインドする必要のあるセキュリティグループをチェックし、【OK】をクリックしてセキュリティグループをバインドします。
![](https://main.qcloudimg.com/raw/ac58322e8b11db8497d79eb54ecc67f6.png)
