# LINE BOT ノードでオウム返し LINE BOT をつくってみる

![4d420ccaf6cad0706f056f177c3c86c6](https://i.gyazo.com/4d420ccaf6cad0706f056f177c3c86c6.png)

LINE BOT ノードでオウム返し LINE BOT をつくってみます。

![7dc340b3f7321e8dce59947cb3e82d50](https://i.gyazo.com/7dc340b3f7321e8dce59947cb3e82d50.png)

このようなフローを作ります。

## フローのタブを追加して今回のフローをはじめる

今回のフローは新しいタブで進めましょう。

![bfacbb2d76a7dd13d00cde6b970fb7d5](https://i.gyazo.com/bfacbb2d76a7dd13d00cde6b970fb7d5.png)

こちらの＋ボタンからフローのタブを作成します。新しくできたフローのタブで作業をはじめましょう。

## 作成したBOTのチャンネルシークレットとチャンネルアクセストークンを準備

![fec310ce30185a693f6e30be33779d79](https://i.gyazo.com/fec310ce30185a693f6e30be33779d79.png)

LINE Develipers https://developers.line.biz/console にログインして、作成したBOTのチャンネルシークレットとチャンネルアクセストークンを準備します。

- 作成した BOT にアクセス
- チャネル基本設定を選択してチャネルシークレットをコピーして準備
- Messaging API 設定を選択してチャンネルアクセストークンをコピーして準備

## node-red-contrib-line-messaging-api のインストール

LINE Messagin API を利用できる Node-RED のノード node-red-contrib-line-messaging-api を使います。

- 参考文献
  - Node-REDでLINE Bot作成が簡単になったよ / メッセージタイプほぼ全部解説
    - https://zenn.dev/ukkz/articles/a389105e400ea2

右のメニューから メニュー ＞ パレットの管理 を表示して、ノードの追加タブをクリックしてノード追加画面に移動します。

![0ce468bb98cf21d85df9b8ae915fabfd](https://i.gyazo.com/0ce468bb98cf21d85df9b8ae915fabfd.png)

node-red-contrib-line-messaging-api で検索してノードを追加ボタンをクリックしてノードをインストールします。

![c7e9b9e7151582019e51c8316cdef4d4](https://i.gyazo.com/c7e9b9e7151582019e51c8316cdef4d4.png)

パレットにノードが追加されました。

## フローを作る

![710bca68444a4b81197191017afe4c8d](https://i.gyazo.com/710bca68444a4b81197191017afe4c8d.png)

LINE ノードのカテゴリで Webhook ノードを配置します。これは Node.js のプログラムの時の、LINE Messaging のデータが入ってくる入り口の役割です。

![a6a64c590dc3dbdaecb2288e5d00a0ef](https://i.gyazo.com/a6a64c590dc3dbdaecb2288e5d00a0ef.png)

Reply ノードを Webhook ノードの横に配置します。

![aeb536a5fc5fc0be0346bee082dafd9a](https://i.gyazo.com/aeb536a5fc5fc0be0346bee082dafd9a.png)

Reply ノードと Webhook ノードをつなぎます。

## Webhook ノードの設定

![8161026e887bc2315168e07b06343a86](https://i.gyazo.com/8161026e887bc2315168e07b06343a86.png)

/webhook を窓口にするよう設定します。Webhook ノードをダブルクリックしてプロパティを表示します。

![615890f590aced84a1587e42388c47e9](https://i.gyazo.com/615890f590aced84a1587e42388c47e9.png)

/webhook と入力して完了ボタンをクリックします。

## Reply ノードの設定

作成したBOTのチャンネルシークレットとチャンネルアクセストークンを設定します。

![9f5c67592af9be3bd624480456fe8501](https://i.gyazo.com/9f5c67592af9be3bd624480456fe8501.png)

Reply ノードをダブルクリックしてプロパティを表示します。

<img width="575" alt="image.png (12.6 kB)" src="https://img.esa.io/uploads/production/attachments/3062/2022/09/28/8131/b9476e39-49fb-49d5-8745-d8d2a56f8811.png">

/webhook と入力して完了ボタンをクリックします。

![615890f590aced84a1587e42388c47e9](https://i.gyazo.com/615890f590aced84a1587e42388c47e9.png)

Sercret には チャンネルシークレット、AccessToken にはチャンネルアクセストークンを反映して完了ボタンをクリックします。

## デプロイ

![19e98ad3d0ad7297e36ad4c035cb36c4](https://i.gyazo.com/19e98ad3d0ad7297e36ad4c035cb36c4.png)

デプロイします。

## サーバー公開

これで enebular による LINE BOT サーバーができました。

今回は、この一時的に使っているエディタそのもののサーバー URL で試してみます。

![8355eb99ba9f5b82bf84301dbb7574ae](https://i.gyazo.com/8355eb99ba9f5b82bf84301dbb7574ae.png)

右上の i というアイコンをクリックします。

![31d22a4c38d78b46dc9d6623573f5136](https://i.gyazo.com/31d22a4c38d78b46dc9d6623573f5136.png)

URL をテキスト選択してコピーします。

## Webhook URL の更新

LINE Developers で、今回使っている BOT の Messaging API 設定に移動します。

![image](https://i.gyazo.com/c85ed28c0caa79951404327636ef1a44.png)

Webhook URL の項目に移動して以下の手順を行います。

## さきほどの URL に `/webhook` をつけて反映

![image](https://i.gyazo.com/3c32b8b9286ac4292628af21c546e08b.png)

さきほどコピーした URL `https://**********.herokuapp.com/` に `/webhook` をつけて Webhook URL の項目に入力して更新ボタンをクリックします。

![image](https://i.gyazo.com/3c32b8b9286ac4292628af21c546e08b.png)

Webhook の利用がオンになっていることも確認しましょう。

## 動かしてみる

![4d420ccaf6cad0706f056f177c3c86c6](https://i.gyazo.com/4d420ccaf6cad0706f056f177c3c86c6.png)

LINE BOT にメッセージを送ってオウム返しを試してみましょう。

## エクストラ

- このままの仕組みだとエディタが生きている時しか動かないので、ずっと動かしたいときは永続的な仕組み（クラウド実行環境）を導入します

## 次は

左のメニューから、次に進みましょう。