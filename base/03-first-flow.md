# データの流れをつくってみる

![7fd43223dc843e6c9b32db02cf7a35ed](https://i.gyazo.com/7fd43223dc843e6c9b32db02cf7a35ed.png)

inject ノードと debug ノードをつないでデータを作り出す流れを作ってみましょう。

## inject ノードの配置

![3d92767dc815fe369ecb0738a7745ddf](https://i.gyazo.com/3d92767dc815fe369ecb0738a7745ddf.png)

パレットから inject ノードを探し、ワークスペースにドラックアンドドロップします。

## debug ノードの配置

![712bb1daa91c9ba270b5498204db9236](https://i.gyazo.com/712bb1daa91c9ba270b5498204db9236.png)

パレットから debug ノードを探し、inject ノードの横に debug ノードをドラックアンドドロップします。

## ノードとノードをつなぐ

inject ノードと debug ノードをつなぎます。

赤い枠にある丸いパーツを「ポート」といいます。

![7aee834e6c04e489a5495e9e3d0e5fbf](https://i.gyazo.com/7aee834e6c04e489a5495e9e3d0e5fbf.png)

このポートでマウスをドラッグしてつまむと、つなぐもの「ワイヤー」が出てます。

![feb949072dd368ca1f76e49786f0232f](https://i.gyazo.com/feb949072dd368ca1f76e49786f0232f.png)

debug ノードにある「ポート」にマウスを離してドロップします。これでノードとノードをつなぐのが完了です。

## いま作ったものを反映する「デプロイ」

保存ボタンをクリックして、いま作ったものが反映します。これがデプロイです。

![76b181398bee6a4d0aee2e76ba0b0a50](https://i.gyazo.com/76b181398bee6a4d0aee2e76ba0b0a50.png)

保存ボタンはエディタの右上にあります。

![b7d2256f345e6c3a23cfcbc3707cc738](https://i.gyazo.com/b7d2256f345e6c3a23cfcbc3707cc738.png)

保存ボタンをクリックすると、押せなくなり、デプロイが完了したことが分かります。また何かを変更すると緑色に戻り押せるようになります。

## 動かしてみる

動かしてみましょう。inject ノードでデータが作られてｍ、debugノードでデータが到着するか確認します。

![ed83f066a42bb1053d2e89aff9366df7](https://i.gyazo.com/ed83f066a42bb1053d2e89aff9366df7.png)

debugノードのデータはサイドバーにあります。

![b662ebd39f08a1c9f6dcf266531b35bb](https://i.gyazo.com/b662ebd39f08a1c9f6dcf266531b35bb.png)

デバッグタブはこちらの虫マークのタブをクリックすると見れます。

![7fd43223dc843e6c9b32db02cf7a35ed](https://i.gyazo.com/7fd43223dc843e6c9b32db02cf7a35ed.png)

injectノードの横のボタンを押すとdebugノードにデータが送られます。今回はinjectノードは日付（タイムスタンプ）を送っています。さきほどのデバッグタブでdebugノードが受け付けたデータを確認できます。

## injectノードで送るデータを変更してみる

![97fb1764dafb280128fec11c99287b17](https://i.gyazo.com/97fb1764dafb280128fec11c99287b17.png)

injectノードをダブルクリックしてデータを変更しましょう。

![1a0b9075bf71ae3c94e2543172a7877a](https://i.gyazo.com/1a0b9075bf71ae3c94e2543172a7877a.png)

ノードはダブルクリックすると細かな設定ができます。今回は inject ノードでは、何も設定をしていない場合は「日時」という 1970 年から現在までのミリ秒が発行されます。

![ba68577c988748ff75aba5cf3a021fb6](https://i.gyazo.com/ba68577c988748ff75aba5cf3a021fb6.png)

msg.payload が今回送るデータの内容です。数値に変更しましょう。

![f93af9d39beedc4b09f2735f9ba93a36](https://i.gyazo.com/f93af9d39beedc4b09f2735f9ba93a36.png)

50に設定します。

![022752c67c664e1a4a6a326dc0d55aa3](https://i.gyazo.com/022752c67c664e1a4a6a326dc0d55aa3.png)

完了ボタンをクリックします。

![19e98ad3d0ad7297e36ad4c035cb36c4](https://i.gyazo.com/19e98ad3d0ad7297e36ad4c035cb36c4.png)

保存ボタンをクリックすると今作ったものが反映されます。

![413619cbf2800595d21cde664c1c26b3](https://i.gyazo.com/413619cbf2800595d21cde664c1c26b3.png)

inject ノードのボタンをクリックして動かしてみます。

![72ecb786ab5ceac00b7e6cb93c387f2b](https://i.gyazo.com/72ecb786ab5ceac00b7e6cb93c387f2b.png)

inject ノードから送られるデータが 50 の数値になっているかをデバッグタブで確認します。

## 次は

左のメニューから、次に進みましょう。