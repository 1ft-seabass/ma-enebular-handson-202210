# クラウド実行環境 LINE BOT 作成

![66faa3725ee4bffbcf17cee5b31fdb51](https://i.gyazo.com/66faa3725ee4bffbcf17cee5b31fdb51.png)

このページでは、クラウド実行環境 LINE BOT 作成してみます。

クラウド実行環境 LINE BOT 作成を作成して、LINE BOT にメッセージを送ってみると、オウム返しが返ってきます！

## 今回の Discover Flow

[lcdp-linebot-simple](https://enebular.com/discover/flow/67a6ffb1-a6e6-4b18-86dc-afe807f5ef97)

![b114bae7b730650f53fc3672a01018a9](https://i.gyazo.com/b114bae7b730650f53fc3672a01018a9.png)

今回使う Discover Flow はこちらです。

[クラウド実行環境の準備](https://docs.enebular.com/ja/getstarted/CloudEEPrepareEnvironment.html) の手順が完了したプロジェクトにインポートボタンをクリックしてインポートしましょう。

## フローを編集する

![3ff60d45dd48d014f0cf98f76a8f3836](https://i.gyazo.com/3ff60d45dd48d014f0cf98f76a8f3836.png)

インポートして読み込めたら編集ボタンをクリックしてフローを編集しましょう。

![0e244ea9d593535ab9a9fbf2e8e4ab18](https://i.gyazo.com/0e244ea9d593535ab9a9fbf2e8e4ab18.png)

このようなフローが表示されます。

## LINE BOT 設定 change ノードの設定

LINE BOT 設定という名前の change ノードの設定をします。今回使う LINE BOT のチャネルシークレット・
チャネルアクセストークンをせていします。

![88b6b3e8a37ddef4100ee52f9777c6da](https://i.gyazo.com/88b6b3e8a37ddef4100ee52f9777c6da.png)

ノードをダブルクリックしてプロパティ設定を表示しましょう。

![7225862d363ff6f25dc45a924c95cbb8](https://i.gyazo.com/7225862d363ff6f25dc45a924c95cbb8.png)

プロパティ設定です。

![0df8cc921ae11e2a8403ce3ffbcb04a6](https://i.gyazo.com/0df8cc921ae11e2a8403ce3ffbcb04a6.png)

対象の値の `<ChannelSecret>` を今回使う LINE BOT のチャネルシークレットに置き換えます。

![fe122212a517e87736a3ffaaeadf9655](https://i.gyazo.com/fe122212a517e87736a3ffaaeadf9655.png)

対象の値の `<ChannelAccessToken>` を今回使う LINE BOT のチャネルアクセストークンに置き換えます。

![93e77f8a577df58051b9bd2737ec0b63](https://i.gyazo.com/93e77f8a577df58051b9bd2737ec0b63.png)

設定できたら完了ボタンをクリックします。

![19e98ad3d0ad7297e36ad4c035cb36c4](https://i.gyazo.com/19e98ad3d0ad7297e36ad4c035cb36c4.png)

保存ボタンをクリックしてデプロイします。

## クラウド実行環境へのフローの反映

![f856bd74daef5e8f1e65ec05c00c9789](https://i.gyazo.com/f856bd74daef5e8f1e65ec05c00c9789.png)

ブラウザでエディタのタブを閉じて、以前のタブのフロー詳細画面に戻ります。

![fd45a8a5a4a3590b0f22dbe54384e682](https://i.gyazo.com/fd45a8a5a4a3590b0f22dbe54384e682.png)

上部のプロジェクト名をクリックしてプロジェクト詳細画面に戻ります。

![4fb0ceae14076142819a0b448f9f24f1](https://i.gyazo.com/4fb0ceae14076142819a0b448f9f24f1.png)

プロジェクト詳細画面で右メニューのクラウド実行環境をクリックします。

![7e47a0dbf363c44b6f1e139742543ec0](https://i.gyazo.com/7e47a0dbf363c44b6f1e139742543ec0.png)

クラウド実行環境の一覧が表示されたので、一覧から今回設定するクラウド実行環境をクリックします。

<img width="803.25" alt="2022-10-21 11.51.09.png (28.2 kB)" src="https://img.esa.io/uploads/production/attachments/3062/2022/10/21/8131/2a0993b5-add1-4307-8a29-321079ed188e.png">

クラウド実行環境の詳細が表示されたので、デプロイボタンをクリックします。

![f520cd9d3ebf6d95d236e77d6d8987a1](https://i.gyazo.com/f520cd9d3ebf6d95d236e77d6d8987a1.png)

今回作成したフローをクリックしてデプロイボタンをクリックします。

![51690929924f0721a89a00ecdd6df249](https://i.gyazo.com/51690929924f0721a89a00ecdd6df249.png)

デプロイ中となります。

![7d60f476884cdd39a40f1dfcb4fe03bb](https://i.gyazo.com/7d60f476884cdd39a40f1dfcb4fe03bb.png)

デプロイ済みになりました。

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

## クラウド実行環境の設定

![178efb4b8d9a49aa07ab2161ec1ab596](https://i.gyazo.com/178efb4b8d9a49aa07ab2161ec1ab596.png)

上部のメニューから設定をクリックします。このままだと設定は入力できずロックされています。

![55ff13c76fb9c6f9ee37ea92bcc89fef](https://i.gyazo.com/55ff13c76fb9c6f9ee37ea92bcc89fef.png)

設定を編集をクリックします。クリックすると設定が編集できるようになります。

![548f4229cc8a661582b4ed1771f07eae](https://i.gyazo.com/548f4229cc8a661582b4ed1771f07eae.png)

HTTP トリガーの項目に注目します。

![49688e8f71bcec31eea9a11af151c3fc](https://i.gyazo.com/49688e8f71bcec31eea9a11af151c3fc.png)

スイッチをクリックして ON にします。

![334cb392bfab62ebe99aabd15b06359d](https://i.gyazo.com/334cb392bfab62ebe99aabd15b06359d.png)

HTTP トリガーのパスを linebot と入力します。

![05896f03e963601634695b02263cea88](https://i.gyazo.com/05896f03e963601634695b02263cea88.png)

下までスクロールして保存ボタンをクリックします。

![cbb4b4d1fef8e22ad3fbc99b4b8a5af0](https://i.gyazo.com/cbb4b4d1fef8e22ad3fbc99b4b8a5af0.png)

しばらく待つと画面左下に更新に成功しましたとメッセージが出ます。他にエラーメッセージがでなければ成功です。

![55bd6317e3fa50bd9a246042b4bcf59b](https://i.gyazo.com/55bd6317e3fa50bd9a246042b4bcf59b.png)

このようにまた編集できないようなり、設定が完了します。

## HTTP トリガー URL の確認

![fbbbb720ef8b6304f1ff98d664d17717](https://i.gyazo.com/fbbbb720ef8b6304f1ff98d664d17717.png)

HTTP トリガーの項目を確認します。

![df338f511531ab6435ea2c3ba0175330](https://i.gyazo.com/df338f511531ab6435ea2c3ba0175330.png)

このボタンをクリックしてクリップボードにHTTP トリガー URL をコピーします。

![88d466a827bb7d34a757a320f292bd18](https://i.gyazo.com/88d466a827bb7d34a757a320f292bd18.png)

コピーができると、このようにコピーしました。と出ます。

この設定を LINE BOT の Webhook 設定に使用します。

## LINE Developers で Webhook の設定をする

![457de21c86739267afefb13436823a3f](https://i.gyazo.com/457de21c86739267afefb13436823a3f.png)

[LINE Developers](https://developers.line.biz/console/) を、ブラウザの別のタブで開きます。このように今回使う LINE BOT の Messaging API 設定に移動します。

![22a1db1b9049a7cc5187de9489062c7b](https://i.gyazo.com/22a1db1b9049a7cc5187de9489062c7b.png)

スクロールして Webhook 設定の項目を見つけて、編集ボタンをクリックします。

![90667fd5ab304648436d1e84ed94f9d0](https://i.gyazo.com/90667fd5ab304648436d1e84ed94f9d0.png)

さきほどコピーした URL を Webhook URL の欄にペーストして更新ボタンをクリックします。

また、Webhook の利用がオンになっていることも確認してきましょう。まれにオフになっているので、その時はオンにしましょう。

これで LINE BOT の設定は完了です。

## 動かしてみる

![66faa3725ee4bffbcf17cee5b31fdb51](https://i.gyazo.com/66faa3725ee4bffbcf17cee5b31fdb51.png)

今回動かす LINE BOT でメッセージを送ってみると、オウム返しが返ってきます！

サーバレスな AWS Lambda の挙動になるので、最初の 1 回のアクセスは、コールドスタートというサーバーの起動込みの動作が行われるので 5 ～ 10 秒程度の間があります。

そのあと、直後に続けてメッセージするのは素早く帰ってきます。しばらくアクセスしていないと、またコールドスタートがはじまります。

参考文献 : [Lambdaの実行環境について(コールドスタートとウォームスタート)](https://zenn.dev/yoshii0110/articles/0d50e872b64f59)

## エクストラ

- フローでオウム返しの近くにある change ノード 固定の返信内容や画像返信をつないでフロー更新後クラウド環境も更新してみて体験してみましょう

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