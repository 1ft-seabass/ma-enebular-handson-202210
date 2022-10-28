# プロジェクトにクラウド環境の作成

プロジェクトにクラウド環境の作成を行います。

enebular のクラウド環境には以下の参考文献があります。

- [新リリースのenebularクラウド実行環境の使い方 | enebular blog](https://blog.enebular.com/enebular/how-to-use-enebular-cloud-exec-environment/)
- [クラウド実行環境とは · enebular](https://docs.enebular.com/ja/executionenvironment/overview)
- [クラウド実行環境でのスケジュールトリガーによるフローの実行 · enebular](https://docs.enebular.com/ja/getstarted/CloudEEScheduleTrigger.html)
- [クラウド実行環境でのHTTPトリガーによるフローの実行 · enebular](https://docs.enebular.com/ja/getstarted/CloudEEHTTPTrigger.html)
- [クラウド実行環境の準備 · enebular](https://docs.enebular.com/ja/getstarted/cloudeeprepareenvironment)
- [クラウド実行環境の管理 · enebular](https://docs.enebular.com/ja/executionenvironment/manageexecutionenvironment)

## クラウド実行環境の準備

![6692cdf781b7a65707ac51925347925d](https://i.gyazo.com/6692cdf781b7a65707ac51925347925d.png)

[クラウド実行環境の準備 · enebular](https://docs.enebular.com/ja/getstarted/cloudeeprepareenvironment) 

こちらの記事を参考に、クラウド実行環境の作成とLCDPノードのインポートを行います。

## 新しいフローを作りましょう

![8d22f28117008204f57bcb688f23bb24](https://i.gyazo.com/8d22f28117008204f57bcb688f23bb24.png)

プロジェクトで、新しく flow-http-handson-sample フローを作ります。

## クラウド実行環境のフローの作成

![fdc01ba043368f62c7b2cce069fcaa76](https://i.gyazo.com/fdc01ba043368f62c7b2cce069fcaa76.png)

[クラウド実行環境でのスケジュールトリガーによるフローの実行 · enebular](https://docs.enebular.com/ja/getstarted/CloudEEScheduleTrigger.html)

こちらの記事を参考に、

- LCDPノードの利用
- ノードのインストール
- タイムスタンプの取得と表示
- クラウド実行環境へのフローのデプロイ

まで、進めます。

## 事前に HTTP トリガーの URL を考えておきます

HTTP トリガーの URL は enebular の他のユーザーやプロジェクトも含めて共有して使っています。

もし使いたい URL が他のユーザーやプロジェクトが、すでに取得していた場合に、設定することができずエラーになります。

![837d56ba51a68dbb5c7129b209ff8b0d](https://i.gyazo.com/837d56ba51a68dbb5c7129b209ff8b0d.png)

すでに取得されていた場合は、この後の作業で、このようなエラーが起きます。

ですので、なるべく重複しない URL を決めておきましょう。

`（自分の名前の英語名）-（今回のプロジェクト名）-（今日の日付）-（ランダム値）-linebot` と決めておきましょう。

たとえば、

- 自分の名前の英語名
    - 山田太郎でしたら yamada-taro
- 今回のプロジェクト名
    - たとえば myproject
- 今日の日付
    - 2022 年 10 月 21 なら 20221021
- ランダム値
    - 3 桁以上のランダム値　例：2736
    - やり方は後述します

でしたら、`yamada-taro-myproject-20221021-2736-linebot` のようになります。

とくにランダム値をつけないと推測されやすくなり、他との重複もしやすくなるので、必ずつけるようにしましょう。

### ランダム値の作り方

なお、ランダム値を手軽にやれるおススメは、[Google 検索で「乱数」を検索](https://www.google.com/search?q=%E4%B9%B1%E6%95%B0)して上部に乱数ジェネレータが出てくるので、これを使うことです。

[Google 検索で「乱数」を検索](https://www.google.com/search?q=%E4%B9%B1%E6%95%B0)

![d939bfd4e2ff24ae75256186b51153c9](https://i.gyazo.com/d939bfd4e2ff24ae75256186b51153c9.png)

右側の設定を最小を 1 で最大を 100000 にします。生成ボタンをクリックして3 桁以上のランダム値がでたら採用します。

## クラウド実行環境でのHTTPトリガーによるフローの実行

![756b5862faab1e4fb1403bec4ac8b1fd](https://i.gyazo.com/756b5862faab1e4fb1403bec4ac8b1fd.png)

[クラウド実行環境でのHTTPトリガーによるフローの実行 · enebular](https://docs.enebular.com/ja/getstarted/CloudEEHTTPTrigger.html)

こちらの記事を参考に、クラウド実行環境でのHTTPトリガーによるフローの実行を行います。

## エクストラ

- クラウド実行環境後のデバッグ
  - debug ノードでシステムコンソールをチェックすると、クラウド実行環境側のログでメッセージが出るのでデバッグしやすくなります
- クラウド実行環境の更新
  - フローを更新したら今回のクラウド実行環境の詳細から、更新したフローをデプロイしましょう

## 作業が終わったら

クラウド開発環境の削除をしましょう。

![486c24d12c469b2e62949cc6cbaba28b](https://i.gyazo.com/486c24d12c469b2e62949cc6cbaba28b.png)

今回のクラウド実行環境の詳細から設定をクリックします。

![cf00f58d1efdc2c47c0532cf049fedbd](https://i.gyazo.com/cf00f58d1efdc2c47c0532cf049fedbd.png)

設定ページに移動したら、設定を編集クリックします。

![1e8f695ea85b249508a6cb007681859f](https://i.gyazo.com/1e8f695ea85b249508a6cb007681859f.png)

下までスクロールし削除ボタンがあるのでクリックし、本当にこの実行環境を削除しますか？と聞かれるので「はい」をクリックして削除しましょう。

## 次は

左のメニューから、次に進みましょう。