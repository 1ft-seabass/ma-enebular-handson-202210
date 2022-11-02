# enebular と Metadata 感情解析 API をつないでみる

enebular と Metadata 感情解析 API をつないでみます。

## 試用 API キーの取得

![ea6bcbf79a9b1961c948b596c153a0c7](https://i.gyazo.com/ea6bcbf79a9b1961c948b596c153a0c7.png)

2022/10 時点での情報です。

<a href="https://metadata.co.jp/apis/emotion-analyzer.html" target="_blank">感情解析API</a> のページにある「API のご使用はこちら」ボタンをクリックして利用登録ページに移動します。

![48406c2d331d20268fbca27147c47a1d](https://i.gyazo.com/48406c2d331d20268fbca27147c47a1d.png)

利用登録ページで必要な情報を入力して API キーを受け取ります。

![b52cf990527952dda10db91b062587ae](https://i.gyazo.com/b52cf990527952dda10db91b062587ae.png)

メールから API キーをメモします。

![8db61fc06d5d4bdb0cb827a5c90c26bf](https://i.gyazo.com/8db61fc06d5d4bdb0cb827a5c90c26bf.png)

メールから感情解析 API の URL をメモします。

## API の仕様

<a href="https://metadata.co.jp/apis/emotion-analyzer/detail.html" target="_blank">感情解析APIご試用・技術仕様について | メタデータ株式会社</a>

こちらに詳細があります。 ※このバージョンは商用にご提供できません。

## Discover Flow

![12a6fec53998380d35ccd36904990eb6](https://i.gyazo.com/12a6fec53998380d35ccd36904990eb6.png)

<a href="https://enebular.com/discover/flow/b58c83e2-ef1c-4ec4-b930-e40ec46a1844" target="_blank">metadata-emotion-api-sample</a>

今回の Discover Flow です。

インポートボタンをクリックして、今回の作業するプロジェクトを選択してインポートします。

## フローの編集

![015404b841171403a58b728e4b808587](https://i.gyazo.com/015404b841171403a58b728e4b808587.png)

インポートしたらフローの編集をクリックしてフローを編集します。

![6bc643ae413ab8c873fc2fbe19715a93](https://i.gyazo.com/6bc643ae413ab8c873fc2fbe19715a93.png)

フローが表示されました。

## API キー の設定

![00824b137c6e19193a01d57c485456aa](https://i.gyazo.com/00824b137c6e19193a01d57c485456aa.png)

API 設定という名前の change ノードをクリックします。

![96c824862ebcab6237fd504f45c9b94b](https://i.gyazo.com/96c824862ebcab6237fd504f45c9b94b.png)

プロパティが表示されます。

`<API KEY>` をメールからメモした API キーで上書きして完了ボタンをクリックします。

## API URL の設定

![fd6d4bb1779db303e34ec3270957f94e](https://i.gyazo.com/fd6d4bb1779db303e34ec3270957f94e.png)

感情解析 API 接続という名前の http request ノードをクリックします。

![36804b9fe13860402ff339c7671b5da1](https://i.gyazo.com/36804b9fe13860402ff339c7671b5da1.png)

プロパティが表示されます。

`<API URL>` をメールからメモした 感情解析 API の URLで上書きして完了ボタンをクリックします。

## デプロイ

![e34ed707aa68e1381885d537487a81f3](https://i.gyazo.com/e34ed707aa68e1381885d537487a81f3.png)

保存ボタンをクリックしてフローをデプロイします。

## 動かしてみる

<img width="815" alt="image.png (16.1 kB)" src="https://img.esa.io/uploads/production/attachments/3062/2022/11/02/8131/cb437602-fb35-44ba-85c6-8a01739d16f6.png">

inject ノードのボタンをクリックして動かしてみましょう。

![b8b64f8c5acf14ff435a4bab978f05b1](https://i.gyazo.com/b8b64f8c5acf14ff435a4bab978f05b1.png)

クリックすると API にアクセスして「今日はいい天気！いい一日になりそうです！どんなランチ食べようかなあ～？」の解析結果がデバックタブに表示されます。

![6f38b3e2d880cb8dc0d3dc6a8879ff2a](https://i.gyazo.com/6f38b3e2d880cb8dc0d3dc6a8879ff2a.png)

取得した JSON データをデバッグタブで展開できます。like に 2 ポイント、joy に 2 ポイント入ってますね。

2022/10 時点で利用回数は 1 日あたり 100 回までなのでテスト回数は注意しましょう。