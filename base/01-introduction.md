# はじめに

## enebular とは

> ![image](https://i.gyazo.com/627c47635133e03b57279d3292cdbf29.png)
> 
> enebular  
> https://www.enebular.com/ja/

あらゆるデバイスとクラウドサービスを「つなぐ」、IoT のためのデータ連携プラットフォームです。アカウント登録をすることで無料で始められます。

HTTP でつながる様々な API サービスとつながります。今回のハッカソンで扱う LINE やメタデータの API へも、もちろんつながります。

enebular のドキュメントはこちらです。

![image](https://i.gyazo.com/e6044a271c9e7913c5a34a378a8ed48b.png)

> Introduction · enebular  
> https://docs.enebular.com/ja/

## enebular は Node-RED というローコードツールがベース

enebular は Node-RED というローコードツールがベースにあります。

ローコードツールとは、あまりプログラムを書かずに、目で見て機能をポチポチつなぐ操作で、仕組みが作れるツールの総称です。そのうちのひとつが Node-RED です。

![image](https://i.gyazo.com/a93a65feb868db86c580e9f495d8a9e0.png)

enebular ではノードという機能のかたまりをつないで、フローというデータの流れを作り、データや IoT につながります。

![image](https://i.gyazo.com/82277372eeca4580a378bbc8bcc97769.jpg)

たとえば、このようなフローで柴犬画像を返してくれる API に HTTP でつないで画像を表示する仕組みがすぐに作れます。

プログラムを書いた経験があまりなくてもノードの機能を試して理解しながらつなげば、仕組みがつくれます。

![image](https://i.gyazo.com/0f0d8330e70baee4b216f55c51881f0b.png)

Node-RED の詳しい使い方は Node-RED の日本のコミュニティページを見てみると良いでしょう。

> ドキュメント : Node-RED日本ユーザ会  
> https://nodered.jp/docs/

## 次は

左のメニューから、次に進みましょう。