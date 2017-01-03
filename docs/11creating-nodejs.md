# Node.jsモジュールの作成

Node.jsモジュールは、npmに公開できるパッケージの一種です。`package.json`ファイルを用意することで、新しいモジュールの作成を開始出来ます。  

`npm init`で`package.json`を作成出来ます。このコマンドは、`package.json`の各フィールドに必要な値の入力を求めます。`name`と`version`の2つは、必須のフィールドです。また、`main`の値も必要でしょう。`index.js`をデフォルトで使うことが出来ます。  

`author`フィールドに情報を追加したい場合、次のフォーマットを使うとよいでしょう(`email`と`web site`はいずれも任意項目です)。  

```
Your Name <email@example.com> (http://example.com)
```

一度`package.json`を作ったら、作ったモジュールが呼ばれたときに読み込まれるファイルが必要となるはずです。デフォルトでは、それが`index.js`となります。  

その中に、エクスポートオブジェクトのプロパティとして関数を追加します。これにより、外部のコードから使える関数が提供出来ます。  

```
exports.printMsg = function() {
  console.log("This is a message from the demo package");
}
```

テスト:  
1. パッケージをnpmに公開します
1. プロジェクトの外に新しいディレクトリを作り、`cd`でその中に入ります
1. `npm install <package>`を実行します
1. 作成したパッケージに依存し、メソッドを呼び出す`test.js`ファイルを作成します
1. `node test.js`を実行し、メッセージの出力を確認します
