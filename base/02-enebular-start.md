# enebular の準備

enebular の準備をしていきます。

## 注意 : enebular には最新の Chrome ブラウザでアクセスしましょう

![image](https://i.gyazo.com/5e1ec175cac8cc7db65c7ce4c04f2bae.png)

enebular には最新の Chrome ブラウザでアクセスしましょう。

## enebular へログイン

![image](https://i.gyazo.com/7f6553a1ad9aaf68d497a8cc6c3805f4.jpg)

[https://www.enebular.com/ja/](https://www.enebular.com/ja/) にアクセスします。

![image](https://i.gyazo.com/aea8ffa24d015ec37c14c444c12a68e8.png)

右上のサインインをクリックしてサインインページを表示します。

![image](https://i.gyazo.com/58fb509fc97d9fd22fa200211f0e4483.png)

事前準備でつくった自分の enebular アカウントでサインインします。

![image](https://i.gyazo.com/1eed04bef6c4d23c34d89f50eee0dc0c.png)

サインイン後の画面、ダッシュボードが表示されました。

## プロジェクト の作成（今回は作成済みなのでスキップ）

こちらの [Introduction](https://docs.enebular.com/ja/GetStarted/Introduction.html) を参考に進めていきます。

![image](https://i.gyazo.com/b40f201363ea704a542c325a31188d86.png)

enebular を始めるには、まずプロジェクトを作成します。サインイン後の画面にあるプロジェクトを作成ボタンからプロジェクトを作成します。

![image](https://i.gyazo.com/1bd4954dfc734a4ffb96aa9d385f3d67.png)

プロジェクトを作成ウィンドウが表示されるのでプロジェクト名を入力して送信ボタンをクリックします。

![image](https://i.gyazo.com/1ea2bca7c56fcef35df83f2e1ef25126.png)

入力したプロジェクトでプロジェクトが作成されたことがダッシュボードの一覧で確認できます。

## プロジェクトの選択

![image](https://i.gyazo.com/1ea2bca7c56fcef35df83f2e1ef25126.png)

ダッシュボードの一覧から、今回のプロジェクトを選択します。

## アセット の作成

プロジェクトを作成できたら enebular のアセットの 1 つであるフローを作成しましょう。

![image](https://i.gyazo.com/22b67a6d78f02a7f24f1224621b108f9.png)

作成したプロジェクトをクリックします。

![image](https://i.gyazo.com/ba4b258701393a3e4f62583e367e539b.png)

プロジェクトの管理画面に移動します。

![image](https://i.gyazo.com/857cc00d69ceccb3a2ae578edbdcd004.png)

右下の + ボタンをクリックするとアセットを作成するウィンドウが表示されます。

![image](https://i.gyazo.com/52bbf8c583892aee9edb065d8ea318d4.png)

アセット種別はフローを選択して、フローのタイトル `flow-first-step` とつけます。

フローへのデフォルトのアクセス権は閲覧に設定してください。

続けるボタンをクリックします。

![image](https://i.gyazo.com/56405a922d23e4612caa8b3e0f1312f7.png)

作成が完了し、フローの詳細ページに移動します。

![image](https://i.gyazo.com/8c9620f93a15b939c166bfcf7e5a5138.png)

編集ボタンをクリックします。

![image](https://i.gyazo.com/98736f6f6724b9e6caf6faee92380646.png)

左上に Loading がでたら、しばらく待ちます。

![image](https://i.gyazo.com/24326a0a917c45ac033ca382b83e1b9a.png)

フローを編集する画面が立ち上がります。こちらが、先ほどふれた Node-RED というローコードツールで出来ているところです。

## 注意：enebular の活動限界について

![image](https://i.gyazo.com/f28676b44f73532243a626cc1e0dd412.png)

WEBブラウザで enebular のフローエディタを使っている際には、1セッションは「60分まで」となっています。ここでいう「1セッション」は、ダッシュボードから編集するフローを選択し、「Edit」ボタンを押してフローエディタが起動してから始まります。

このあたりの詳細について、以下のページを元に説明します。

[enebularの活動限界について \| enebular blog](https://blog.enebular.com/enebular/session-time/)

## ノードについて

![58951f750453c84b44d8b941bb901b8d](https://i.gyazo.com/58951f750453c84b44d8b941bb901b8d.png)

ノード（Node）はNode-REDを構成する基本的な構成要素です。処理をする機能のかたまりです。

![1025e100d9711a31b8aaac687861012d](https://i.gyazo.com/1025e100d9711a31b8aaac687861012d.png)

ノードはフロー中の前方のノードからメッセージを受け取るか、外部イベントを受け取ることで動き出します。ノードはメッセージまたはイベントを処理し、 フロー中の次のノードにメッセージを送ります。左から右に処理されていきます。

![21250655fb324c0bc0b3a87a17f17182](https://i.gyazo.com/21250655fb324c0bc0b3a87a17f17182.png)

メッセージはJSONデータで構成され、msg という一番上のオブジェクトにぶら下がっている payload というオブジェクトの中で、各ノードで処理された内容がバケツリレーのようにやり取りされていきます。

![a77ad581f63cea641a56f74e0ea77f61](https://i.gyazo.com/a77ad581f63cea641a56f74e0ea77f61.png)

こんな感じです。

![59cae4a9db2befa3d0d1408a5b73a817](https://i.gyazo.com/59cae4a9db2befa3d0d1408a5b73a817.png)

今回は inject というノードでボタンクリックをきっかけにメッセージを送り、 debug ノードという送られてきたメッセージをサイドバーのデバッグタブに表示するノードに送ります。

## 画面紹介

![a536a5b1ac2e532debfea2f5c44e0127](https://i.gyazo.com/a536a5b1ac2e532debfea2f5c44e0127.png)

パレットはインストール済みで利用可能なすべてのノードが含まれます。ノードが置かれているエリアです。

![bb782eeca7b05ef91f63d3c659c5bfab](https://i.gyazo.com/bb782eeca7b05ef91f63d3c659c5bfab.png)

ワークスペースはパレットからノードを配置してフロー（データの流れ）を作るエリアです。

![dabb58dd475e44daae3ace0760347e7c](https://i.gyazo.com/dabb58dd475e44daae3ace0760347e7c.png)

サイドバーは、エディタ内に多くの便利なツールを提供するエリアです。

- ノードについてのさらなる情報
- ヘルプを確認するパネル
- デバッグメッセージを確認するパネル
- フローの設定ノードを確認するパネル

などがあります。

## 次は

左のメニューから、次に進みましょう。