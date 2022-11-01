# フロー JSON のインポート

enebular および Node-RED には、インポートというフローの JSON データをワークスペースに読み込む機能があります。

似た機能に Discover Flow がありますが Discover Flow の場合はフローアセットを新しく作る形になるので、新規に仕組みを作るときに向いています。

作業中のフローアセットには Discover Flow で追加で読み込めないので、フローのインポートを使うと、現状のフローにフローを加えることができます。

## フロー JSON ファイルをコピー

![b0b9a7d3aeaf0472b1cb4eb37fef7fc3](https://i.gyazo.com/b0b9a7d3aeaf0472b1cb4eb37fef7fc3.png)

たとえばこのようなフローファイルを読み込みましょう。

フローの JSON データはこちらです。

```js
[{"id":"a369a3f0682a5fda","type":"inject","z":"a08580516b70e626","name":"","props":[{"p":"payload"},{"p":"topic","vt":"str"}],"repeat":"","crontab":"","once":false,"onceDelay":0.1,"topic":"","payload":"Hello!","payloadType":"str","x":270,"y":180,"wires":[["fda10a5f6510e765"]]},{"id":"fda10a5f6510e765","type":"debug","z":"a08580516b70e626","name":"","active":true,"tosidebar":true,"console":false,"tostatus":false,"complete":"payload","targetType":"msg","statusVal":"","statusType":"auto","x":450,"y":180,"wires":[]},{"id":"2a3e220cb729cbfc","type":"comment","z":"a08580516b70e626","name":"サンプルフロー","info":"","x":280,"y":140,"wires":[]}]
```

こちらをコピーします。これでクリップボードにコピーされました。

## インポート

![3573ebed7a63db3d7a20f6e995536b67](https://i.gyazo.com/3573ebed7a63db3d7a20f6e995536b67.png)

enebular で今回インポートで追加するフローアセットを表示します。

![3c21d38a8e39568639962fb7ebf4fcf6](https://i.gyazo.com/3c21d38a8e39568639962fb7ebf4fcf6.png)

右上のメニューボタンから読み込みをクリックします。

![df8d954d7d495abaa7fb823ec4b1ca25](https://i.gyazo.com/df8d954d7d495abaa7fb823ec4b1ca25.png)

インポート画面が表示されました。

![a0d3f6b361a2092f53be4a9cc7e70c0b](https://i.gyazo.com/a0d3f6b361a2092f53be4a9cc7e70c0b.png)

テキスト入力エリアに、さきほどコピーしたフロー JSON をコピーします。

コピーできたら読み込みボタンをクリックします。

![af431d6a1b1fc5f7cfee47aedc81663f](https://i.gyazo.com/af431d6a1b1fc5f7cfee47aedc81663f.png)

マウスに追従する形で今回のフローが読み込まれます。クリックして配置しましょう。

![8aaffa53e39a07d6d5f109e131f8be63](https://i.gyazo.com/8aaffa53e39a07d6d5f109e131f8be63.png)

これでフローがインポートできました。フローをデプロイして反映します。

## 注意点

- インポート元のフローで使われていたノードが、インポート先のフローでインストールされていないとフローがないエラーが出てしまうので事前にインストールしておきましょう。