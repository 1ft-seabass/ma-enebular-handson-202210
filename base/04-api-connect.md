# 柴犬画像 API につないでみよう

![8b3562b82fc4b2f8ff213966c1fd3f3a](https://i.gyazo.com/8b3562b82fc4b2f8ff213966c1fd3f3a.png)

Node-RED パレットにはじめから多彩な接続ノードがあります。 WEB まわりで使われる HTTP / WebSocket など揃えています。

![4a5f646eda6c88a6d5303ad7938e5a9c](https://i.gyazo.com/4a5f646eda6c88a6d5303ad7938e5a9c.png)

API は HTTP でつなぐことが多いですが Node-RED にも HTTP 関連ノードあります。

![c35f519b28bb8f47fbde1e9bfc1d0158](https://i.gyazo.com/c35f519b28bb8f47fbde1e9bfc1d0158.jpg)

さまざまな API につなぐ例として、柴犬画像を取得してみることも試してみます。

Node-RED で public-apis の柴犬画像 API につないで表示させるメモ – 1ft-seabass.jp.MEMO
https://www.1ft-seabass.jp/memo/2020/09/04/nodered-connect-shibainu/

こちらを元に進めてみます。

## フローのタブを追加して今回のフローをはじめる

Node-RED ではフローをタブで分けて作業できます。今回のフローは新しいタブで進めましょう。処理としては同じ enebular 内の処理です。

![bfacbb2d76a7dd13d00cde6b970fb7d5](https://i.gyazo.com/bfacbb2d76a7dd13d00cde6b970fb7d5.png)

こちらの＋ボタンからフローのタブを作成します。

![e01a18b769c2495de48a79a925ac8be8](https://i.gyazo.com/e01a18b769c2495de48a79a925ac8be8.png)

新しい名前のフローができるので、こちらで進めます。

### inject ノードを配置

![af09116801b29c392cbe03090907c5ad](https://i.gyazo.com/af09116801b29c392cbe03090907c5ad.png)

パレットから inject ノードを配置します。

### http request ノードを配置

![908ca750fd2e9f804b4e787bef1cc211](https://i.gyazo.com/908ca750fd2e9f804b4e787bef1cc211.png)

パレットから http resuest ノードを探します。このノードは、HTTPリクエストを送信し、レスポンスを返します。

![c5624380278275141618e2cfa9298c79](https://i.gyazo.com/c5624380278275141618e2cfa9298c79.png)

inject ノードの横に配置します。

![16defaa77097163827df6c653e56f57a](https://i.gyazo.com/16defaa77097163827df6c653e56f57a.png)

inject ノードとつなぎます。

### http request ノードの設定

![8704383322f88fc626764382e85f1479](https://i.gyazo.com/8704383322f88fc626764382e85f1479.png)

さきほど配置した http resuest ノードをダブルクリックしてプロパティを表示します。

![e6537e382b2b2271dd9635b74668a2ee](https://i.gyazo.com/e6537e382b2b2271dd9635b74668a2ee.png)

shibe.online https://shibe.online/ の仕様は、GETリクエストでURL http://shibe.online/api/shibes とつなぎに行くと、柴犬画像が取得できますので、それに合わせてプロパティを以下に設定します。

- メソッド
  - GET
- URL
  - http://shibe.online/api/shibes
- 名前
  - shibe.online
- 出力形式
    - JSON オブジェクト

出力形式を JSON オブジェクトに変更するのは、すでにリクエストが JSON で来ることでが分かっているので、この後 JSON として扱うことで、今後のデータを扱いやすくします。

完了ボタンをクリックしてワークスペースに戻りましょう。

### 一度デバッグをしてみる

![c2458e1064e33a389b8f9981727c05d2](https://i.gyazo.com/c2458e1064e33a389b8f9981727c05d2.png)

ここまで出来たら、名前を変更することで shibe.online となった 先ほどの http request ノードのあとに debug ノードを配置してつなげましょう。

![19e98ad3d0ad7297e36ad4c035cb36c4](https://i.gyazo.com/19e98ad3d0ad7297e36ad4c035cb36c4.png)

デプロイします。

![7b9d45f2d8a6c709d749bd529937a111](https://i.gyazo.com/7b9d45f2d8a6c709d749bd529937a111.png)

inject ノードのボタンをクリックして、inject ノードからデータを発生させて、http request ノードが shibe.online にアクセスしてデータを受信して debug ノードにデータが届くか試してみましょう。

![ed86a999c23ff154a9f27a3ba6bc0462](https://i.gyazo.com/ed86a999c23ff154a9f27a3ba6bc0462.png)

デバッグタブにデータが来るか確認しましょう。

![5e5a37b9c45313b8e6e0e266bb372771](https://i.gyazo.com/5e5a37b9c45313b8e6e0e266bb372771.png)

JSON であればこちらの三角ボタンをクリックすることで、中のデータ構造を確認できます。

```
["https://cdn.shibe.online/shibes/ee05ff710dc406157fa3fbca514b132c95d555dd.jpg"]
```

今回の場合は、配列のデータで 1 つだけ柴犬画像 URL が入っています。

## データの流れを変更できる change ノードを配置

![66ad3dd31e4294b0ef99df1afbafe408](https://i.gyazo.com/66ad3dd31e4294b0ef99df1afbafe408.png)

http request ノードに change ノードをつなぎます。change ノードはデータの流れを変更できます。

![c3fed19e6bc45cd8a487d261eae58ee4](https://i.gyazo.com/c3fed19e6bc45cd8a487d261eae58ee4.png)

パレットでは近くに似ている switch ノードがあるので、間違えないように配置してください。

![94896647c194d66bf969c9a6a9095424](https://i.gyazo.com/94896647c194d66bf969c9a6a9095424.png)

http request ノードに change ノードをつなぎます。

### change ノードの設定

![baae9c45e87d6af2dab7704d870ed14b](https://i.gyazo.com/baae9c45e87d6af2dab7704d870ed14b.png)

change ノードをノードをダブルクリックしてプロパティを表示します。

![d5a524587bf1fec1978fade1b5023bcb](https://i.gyazo.com/d5a524587bf1fec1978fade1b5023bcb.png)

msg.payload に変更する対象の値を、まず、msg にします。

![28c023e3263ad87f4a60aac9fb07bbf7](https://i.gyazo.com/28c023e3263ad87f4a60aac9fb07bbf7.png)

対象の値は payload[0] にします。

```
["https://cdn.shibe.online/shibes/ee05ff710dc406157fa3fbca514b132c95d555dd.jpg"]
```

先ほどの柴犬画像 URLが配列がきていて URL が一つだけ入っているものを指定するために、payload の 0 番目の値ということで payload[0] にしています。

完了ボタンをクリックしてワークスペースに戻りましょう。

### 画像を表示する node-red-contrib-image-output ノードを追加する

ここまでで、柴犬画像の画像URLを 1つ表示することができます。

画像 URL が入ってくると画像を表示する node-red-contrib-image-output ノードをインストールします。

![0ec652ef6896a2a0908d1ad09f39e283](https://i.gyazo.com/0ec652ef6896a2a0908d1ad09f39e283.png)

右のメニューから メニュー ＞ パレットの管理 と移動します。

![f02564a9503a2f7e4ae5d98da90e4db1](https://i.gyazo.com/f02564a9503a2f7e4ae5d98da90e4db1.png)

ノードの追加タブをクリックしてノード追加画面に移動します。

![c308d89f6e09f9fc2714964a2950a282](https://i.gyazo.com/c308d89f6e09f9fc2714964a2950a282.png)

ノードを検索するテキストエリアに node-red-contrib-image-output を入力してノードを検索して ノードを追加 ボタンをクリックします。

![777ebc61dd824a863752a4378056ee96](https://i.gyazo.com/777ebc61dd824a863752a4378056ee96.png)

追加 ボタンをクリックします。

![66cd153be70bdf92248a338b3451fc9b](https://i.gyazo.com/66cd153be70bdf92248a338b3451fc9b.png)

インストールされました。

### node-red-contrib-image-output ノードをつなげる

![ba210040447d60d145a031978e2e7b93](https://i.gyazo.com/ba210040447d60d145a031978e2e7b93.png)

node-red-contrib-image-output ノードをパレットから探します。

![2e1c34c3247fd109d724f2d0373dc21f](https://i.gyazo.com/2e1c34c3247fd109d724f2d0373dc21f.png)

node-red-contrib-image-output ノードをパレットからワークスペースに配置します。

![8e9635e4788fd83e3cfe97b85415fd52](https://i.gyazo.com/8e9635e4788fd83e3cfe97b85415fd52.png)

change ノードと node-red-contrib-image-output ノードのフローをつなぎます。

![19e98ad3d0ad7297e36ad4c035cb36c4](https://i.gyazo.com/19e98ad3d0ad7297e36ad4c035cb36c4.png)

デプロイします。

### 動かしてみる

![7b9d45f2d8a6c709d749bd529937a111](https://i.gyazo.com/7b9d45f2d8a6c709d749bd529937a111.png)

inject ノードのボタンをクリックして、動作確認してみましょう。

![c35f519b28bb8f47fbde1e9bfc1d0158](https://i.gyazo.com/c35f519b28bb8f47fbde1e9bfc1d0158.jpg)

このように、柴犬 API からデータが取得でき、node-red-contrib-image-output ノードで画像が表示されます。

### エクストラ

![49f835fa9e85339a5bc223ddd85ff0d6](https://i.gyazo.com/49f835fa9e85339a5bc223ddd85ff0d6.png)

- node-red-contrib-image-output ノードのプロパティに Width 160 という画像の横幅を指定する値があるので 320 にして大きく画像を表示してみましょう。
- 柴犬画像 API 、実は他の動物も行けます。http request ノードのプロパティの URL を変更して、鳥 https://shibe.online/api/birds や、猫 https://shibe.online/api/cats を試してみましょう。
- 余裕があれば、柴犬画像 API などがあつまる public-apis https://github.com/public-apis/public-apis の紹介

## 次は

左のメニューから、次に進みましょう。