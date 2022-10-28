# LINE Notify を動かしてみよう

## LINE Notify とは

![image](https://i.gyazo.com/5cf50e16f926ec4f0bdc17f76b5558e5.png)

LINE Notify の大まかな仕組みを把握します。

![image](https://i.gyazo.com/5ee7b4482f1b28caaf860e72744cd2f5.png)

LINE Notify https://notify-bot.line.me/ja/

> Webサービスと連携すると、LINEが提供する公式アカウント"LINE Notify"から通知が届きます。
> 複数のサービスと連携でき、グループでも通知を受信することが可能です。

![image](https://i.gyazo.com/8dddc3621b4a77af65be36d7907cd02a.png)

つまり「LINE Notifyと連携を行うことで、LINEユーザーが簡単にサービスの通知を受信できるようになります」

## 今回のプログラム

![5807b6ab26a7ca5de0947df6603af768](https://i.gyazo.com/5807b6ab26a7ca5de0947df6603af768.png)

inject ノードをクリックしてメッセージを送ると、タイムスタンプが LINE Notify に送られます。

## 以前作業していた柴犬 API のフローを編集しましょう

以前作業していた柴犬 API や LINE  BOT のフローをプロジェクトから選択してスタートしましょう。

### フローのタブを追加して今回のフローをはじめる

今回のフローは新しいタブで進めましょう。

![bfacbb2d76a7dd13d00cde6b970fb7d5](https://i.gyazo.com/bfacbb2d76a7dd13d00cde6b970fb7d5.png)

こちらの＋ボタンからフローのタブを作成します。新しくできたフローのタブで作業をはじめましょう。

## LINE Notify のアクセストークンを準備

![image](https://i.gyazo.com/abee7f38d2db6897c61cdb42fc29a83c.png)

LINE Notify のアクセストークンを準備します。

## LINE Notify のノードはこちらを使います

![b0d3b2e906021dd90898405676cde649](https://i.gyazo.com/b0d3b2e906021dd90898405676cde649.png)

以前インストールした node-red-contrib-line-messaging-api の Notify ノードを使います。

## inject ノードと Notify ノードを配置します

![b5462e9a6a60b9d07b6d421eafefd417](https://i.gyazo.com/b5462e9a6a60b9d07b6d421eafefd417.png)

このように inject ノードと Notify ノードを配置します。

## Notify ノードの設定

![d9f2ef790124007215da22d2a88c711e](https://i.gyazo.com/d9f2ef790124007215da22d2a88c711e.png)

Notify ノードをダブルクリックしてプロパティを表示します。

![7d67b1ffadd16f3a32b6198a3854addf](https://i.gyazo.com/7d67b1ffadd16f3a32b6198a3854addf.png)

プロパティが表示されたら、LINE Notify AccessToken に、自分の作成した LINE Notify のアクセストークン入力して、完了ボタンをクリックします。

## デプロイする

![20b1df2261adbfade8044ce441a30c35](https://i.gyazo.com/20b1df2261adbfade8044ce441a30c35.png)

保存ボタンをクリックしてデプロイします。

## 動かしてみる

![07430f24f9c6f870da7307c825f8d4ed](https://i.gyazo.com/07430f24f9c6f870da7307c825f8d4ed.png)

inject ノードをクリックしてメッセージを送ってみましょう。

![5807b6ab26a7ca5de0947df6603af768](https://i.gyazo.com/5807b6ab26a7ca5de0947df6603af768.png)

今回はタイムスタンプが LINE Notify に送られます。

## エクストラ

- inject ノードのメッセージを変更して自分なりにメッセージを変更してみましょう
    - データタイプを文字列にして「こんにちは！」をおくってみる
- LINE Notify API ドキュメント https://notify-bot.line.me/doc/ja/ を読んで理解を深めましょう

## 次は

左のメニューから、次に進みましょう。