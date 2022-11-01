# LCDP ノードを使ったフローのデバッグ方法

LCDP ノードを使ってクラウド開発環境へデプロイしたフローは、クラウド開発環境のログ機能を使ってデバッグします。

![e48075e0e15bcbe721a6623f940359c6](https://i.gyazo.com/e48075e0e15bcbe721a6623f940359c6.png)

たとえばこのようなシンプルな LCDP in と out で出来たフローがあります。

![43b5cd24c092060c69a3a453e1224731](https://i.gyazo.com/43b5cd24c092060c69a3a453e1224731.png)

LCDP in ノードで外部からデータが送られてきたときのデータを見たい場合は、LCDP in ノードに debug ノードをつけます。

![db371b6a9768a5ed353e1cb948e5bb0e](https://i.gyazo.com/db371b6a9768a5ed353e1cb948e5bb0e.png)

debug ノードをダブルクリックしてプロパティを表示します。

出力先がデフォルトだとデバッグウィンドウのみです。このままだと、debug ノードは、表示している Web エディタの中でフローを動かしたときのデータしか見れません。

## システムコンソールをチェック

![484d9532aa619d3f7d4f2eef0476a0fc](https://i.gyazo.com/484d9532aa619d3f7d4f2eef0476a0fc.png)

システムコンソールすると、ここに到着したデータがクラウド開発環境のログにも出力されます。設定したら完了ボタンをクリックします。

![88b47e0e0a4126e8ae097033396c1ffc](https://i.gyazo.com/88b47e0e0a4126e8ae097033396c1ffc.png)

フローを保存します。

## フローをクラウド開発環境にデプロイ

![3986eacb92c88bb8fe02aefd0fc9e094](https://i.gyazo.com/3986eacb92c88bb8fe02aefd0fc9e094.png)

フローを閉じてクラウド開発環境画面で今回のフローをデプロイします。

![92f32a8ba3884083ffec91ce8e02ee38](https://i.gyazo.com/92f32a8ba3884083ffec91ce8e02ee38.png)

HTTP トリガーで設定した URL にブラウザにアクセスして動かしてみましょう。

![21be7a7b449803eb85c84d2d85a36ce9](https://i.gyazo.com/21be7a7b449803eb85c84d2d85a36ce9.png)

たとえば、HTTP トリガーで設定した URL に `?message=hello!enebular!` をつけて GET リクエストでパラメータをつけたアクセスをします。

## ログを確認

HTTP トリガーで設定した URL にアクセスできたら、さきほどの LCDP in ノードの先の debug ノードが反応したはずです。

![d777e5f9ec1e051f1581a4c0fcc716da](https://i.gyazo.com/d777e5f9ec1e051f1581a4c0fcc716da.png)

クラウド開発環境 > 今回のクラウド開発環境をクリック > 上部のメニュー > ログ をクリックします。

![24059c628c2be692e03c004a90e4f9d5](https://i.gyazo.com/24059c628c2be692e03c004a90e4f9d5.png)

このようにログが表示されるので、今回実行した日時のログのグループを右側のログリストから選択します。

![d71e7834e9a08f6cb0ab3810d7f95e73](https://i.gyazo.com/d71e7834e9a08f6cb0ab3810d7f95e73.png)

たとえば、HTTP トリガーで設定した URL に `?message=hello!enebular!` をつけて GET リクエストでパラメータをつけたアクセスの場合は、さきほどの debug ノードが反応して、このようなデータが表示されます。

## TIPS: よくあるデータの追い方

- GET リクエストでパラメータをつけた場合
  - `?message=hello!enebular!` のように URL のあとにつけたパラメータは `msg.payload` に入っています。
- POST リクエストでJSON データを送った場合
  - ヘッダーで `Content-Type:application/json` を指定して JSON データを送った場合は `msg.payload` に送った JSON データが入っています。

## TIPS: アクセスしたパス

`msg.req` に Node.js に準拠した Express リクエストオブジェクトの内容で入っています。

Express リクエストオブジェクト → https://expressjs.com/ja/4x/api.html#req 

たとえば、アクセスしたパスは `msg.req.url` に入っていています。HTTP トリガーで設定した URL そのままでアクセスすると `/HTTPトリガーのID/` となります。

この HTTP トリガーの ID は今回のクラウド開発環境の設定で HTTP トリガーを設定した時のパスそのものです。

![f93f0bbe56a8e7a8322403819acf7bd6](https://i.gyazo.com/f93f0bbe56a8e7a8322403819acf7bd6.png)

パスは今回のクラウド開発環境の設定のこの部分です。

`https://lcdp003.enebular.com/hogehoge-project-202211-384764` であれば `/hogehoge-project-202211-384764/` となります。

HTTP トリガーで設定した URL に `/hello/world` とつけた場合は `/HTTP トリガーのID/hello/world` となります。

`https://lcdp003.enebular.com/hogehoge-project-202211-384764/hello/world` であれば `/hogehoge-project-202211-384764/hello/world` となります。