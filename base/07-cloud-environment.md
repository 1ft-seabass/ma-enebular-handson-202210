# プロジェクトにクラウド環境の作成

プロジェクトにクラウド環境の作成を行います。

enebular のクラウド環境には以下の参考文献があります。

- [新リリースのenebularクラウド実行環境の使い方 | enebular blog](https://blog.enebular.com/enebular/how-to-use-enebular-cloud-exec-environment/)
- [クラウド実行環境とは · enebular](https://docs.enebular.com/ja/executionenvironment/overview)
- [クラウド実行環境でのスケジュールトリガーによるフローの実行 · enebular](https://docs.enebular.com/ja/getstarted/CloudEEScheduleTrigger.html)
- [クラウド実行環境でのHTTPトリガーによるフローの実行 · enebular](https://docs.enebular.com/ja/getstarted/CloudEEHTTPTrigger.html)
- [クラウド実行環境の準備 · enebular](https://docs.enebular.com/ja/getstarted/cloudeeprepareenvironment)
- [クラウド実行環境の管理 · enebular](https://docs.enebular.com/ja/executionenvironment/manageexecutionenvironment)

## 月当たりの利用上限

<a href="https://docs.enebular.com/ja/executionenvironment/overview" target="_blank">クラウド実行環境とは · enebular</a>

こちらに、月当たりの利用上限があります。ハッカソンやハンズオンで使うぶんには問題なく使えます。

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

![890cda4d2bf112becc98bafe03027e72](https://i.gyazo.com/890cda4d2bf112becc98bafe03027e72.png)

LCDP in ノードと LCDP out ノードをパレットから探します。これが、クラウド実行環境での起点と終点になります。LCDP in ノードで来た値が enebular のフローで処理されて、その結果が LCDP out ノードに渡されます。

LCDP in ノードと LCDP out ノードの詳しい挙動はこちらを参考ください。 → <a href="https://docs.enebular.com/ja/executionenvironment/createflow" target="_blank">クラウド実行環境向けフローの作成 · enebular</a>

![b99380d5aca334342d4d976a45de097d](https://i.gyazo.com/b99380d5aca334342d4d976a45de097d.png)

LCDP in ノードと LCDP out ノードをこのように配置します。

![e75d348b8e18182bccc3e8c8f94375b9](https://i.gyazo.com/e75d348b8e18182bccc3e8c8f94375b9.png)

つづいて、LCDP in ノードの横に change ノードを配置します。

![1774eda3fb51ec7277bc99288efd8421](https://i.gyazo.com/1774eda3fb51ec7277bc99288efd8421.png)

change ノードをダブルクリックしてプロパティを開き、対象の値のデータタイプを日時にします。変更出来たら完了ボタンをクリックします。

![2593ed8ee79ef4f0a1afc7c8c18204dd](https://i.gyazo.com/2593ed8ee79ef4f0a1afc7c8c18204dd.png)

change ノードの横に template ノードをつなぎます。template は来たペイロードをテンプレートに従って変更します。

![6207b635774f84fb91638c290718dd4a](https://i.gyazo.com/6207b635774f84fb91638c290718dd4a.png)

template ノードをダブルクリックしてプロパティを開きます。

```
Hello! timestamp : {{payload}}
```

テンプレートの内容を上記で変更します。

![724fae0f563f9cdd7860355b4454bc83](https://i.gyazo.com/724fae0f563f9cdd7860355b4454bc83.png)

このようになります。変更出来たら完了ボタンをクリックします。

![59c4d1f86fcd9a194f3c06a006cdf75c](https://i.gyazo.com/59c4d1f86fcd9a194f3c06a006cdf75c.png)

template ノードを LCDP out ノードとつなげます。

![3f0f6dd51a51490175347dd58f2ccdb7](https://i.gyazo.com/3f0f6dd51a51490175347dd58f2ccdb7.png)

クラウド実行環境の動作を確認するため debug ノードを template ノードにつなぎます。

![5170a66242a10aa3410cdb08920868a1](https://i.gyazo.com/5170a66242a10aa3410cdb08920868a1.png)

debug ノードをダブルクリックしてプロパティを開き、クラウド実行環境を実行時のしたときのログ機能でも確認できるようにシステムコンソールをチェックします。変更出来たら完了ボタンをクリックします。

## デプロイする

![20b1df2261adbfade8044ce441a30c35](https://i.gyazo.com/20b1df2261adbfade8044ce441a30c35.png)

保存ボタンをクリックしてデプロイします。

## クラウド実行環境でのHTTPトリガーによるフローの実行

![756b5862faab1e4fb1403bec4ac8b1fd](https://i.gyazo.com/756b5862faab1e4fb1403bec4ac8b1fd.png)

[クラウド実行環境でのHTTPトリガーによるフローの実行 · enebular](https://docs.enebular.com/ja/getstarted/CloudEEHTTPTrigger.html)

こちらの記事を参考に、クラウド実行環境でのHTTPトリガーによるフローの実行を行います。

![44f78bf6278cb6c8ebebbf2745f87389](https://i.gyazo.com/44f78bf6278cb6c8ebebbf2745f87389.png)

さきほどのフローの template ノードをダブルクリックしてプロパティを表示します。

```
<!DOCTYPE html>
<head>
    <title>Hello World !</title>
</head>
<body>
    <center>
        <h1>Hello World ! {{payload}}</h1>
    </center>
</body>
```

テンプレート内容をこちらに変更します。

さきほどのフローの change ノードをダブルクリックしてプロパティを表示します。変更出来たら完了ボタンをクリックします。

![7b5eb574e2fa84701e449d977f62c285](https://i.gyazo.com/7b5eb574e2fa84701e449d977f62c285.png)

ひとつルールを下部の＋ボタンから加えます。値の代入を `msg.headers.Content-Type` としするので入力するのは `headers.Content-Type` です。

対象の値を文字列のまま `text/html;charset=UTF-8` にします。

変更出来たら完了ボタンをクリックします。

## デプロイする

![20b1df2261adbfade8044ce441a30c35](https://i.gyazo.com/20b1df2261adbfade8044ce441a30c35.png)

保存ボタンをクリックしてデプロイします。

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

![5f6b3bff40ec29bd5f21e2840aeb7fc9](https://i.gyazo.com/5f6b3bff40ec29bd5f21e2840aeb7fc9.png)

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

`（自分の名前の英語名）-（今回のプロジェクト名）-（今日の日付）-（ランダム値）` と決めておきましょう。

たとえば、

- 自分の名前の英語名
    - 山田太郎でしたら yamada-taro
- 今回のプロジェクト名
    - たとえば httpsample
- 今日の日付
    - 2022 年 10 月 21 なら 20221021
- ランダム値
    - 3 桁以上のランダム値　例：2736
    - やり方は後述します

でしたら、`yamada-taro-httpsample-20221021-2736` のようになります。

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

## アクセスしてみる

![04298ba33fbaaeafd65b7031ea22f403](https://i.gyazo.com/04298ba33fbaaeafd65b7031ea22f403.png)

設定画面で、HTTP トリガーの URL ができるので、右のコピーボタンをクリックして URL を取得します。

![c2e45eb04e10e3243ef1eeaf43e1926e](https://i.gyazo.com/c2e45eb04e10e3243ef1eeaf43e1926e.png)

この URL でブラウザアクセスしてみると、このような画面が表示されます。

## 次は

左のメニューから、次に進みましょう。