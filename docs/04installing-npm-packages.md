# npmパッケージをローカルインストール

npmパッケージのインストールには2つの方法があります。ローカルとグローバルです。どちらを使うかは、パッケージをどのように使いたいかに合わせて選んで下さい。  

例えばNode.jsの`require`を使うような、モジュール独自のパッケージを使いたい場合はローカルインストールをしましょう。ローカルインストールは、`npm install`のデフォルトの挙動です。一方で、grunt CLIのようなコマンドラインツールが欲しいときはグローバルインストールが良いでしょう。  

`install`コマンドの挙動について詳しく知りたい方は、[CLI doc page](https://docs.npmjs.com/cli/install)をご確認ください。  

## インストール

パッケージは次のコマンドでダウンロード出来ます。  

```
> npm install <package_name>
```

実行すると、カレントディレクトリに`node_modules`ディレクトリが作成され(まだ存在しない場合のみ)、その中にパッケージがダウンロードされます。  

テスト:  
`npm install`が正しく動作したことを確認するために、`node_modules`ディレクトリが存在することと、インストールしたパッケージのディレクトリが含まれていることを確認してください。UNIXシステム(OSX, Debianなど)をお使いの場合は`ls node_modules`で、Windowsの場合は`dir node_modules`で確認出来ます。  

例:  
`lodash`というパッケージをインストールしてみましょう。`node_modules`の中身に`lodash`というディレクトリがあるかどうかチェックして、実行が成功したことを確認してください。  

```
> npm install lodash
> ls node_modules #Windowsなら`dir`コマンドを使います

#=> lodash
```

## どのバージョンのパッケージがインストールされたか？

`package.json`というファイルがローカルディレクトリに存在しなければ、最新バージョンのパッケージがインストールされています。  

`package.json`が存在する場合、該当パッケージの[semver rule](https://docs.npmjs.com/getting-started/semantic-versioning)を満たす最新のバージョンが`package.json`に宣言されています。  

## インストールしたパッケージの使用

パッケージが`node_modules`に入ったら、それを自分の書くコード内で使うことが出来ます。例えばNode.jsのモジュールを作ったならば、`require`が可能です。  

例:  
`index.js`という名前のファイルを作り、以下のコードを書いてみてください。  

```javascript
// index.js
var lodash = require('lodash');

var output = lodash.without([1, 2, 3], 1);
console.log(output);
```

`node index.js`コマンドで実行してみます。`[2, 3]`と出力されるはずです。  

`lodash`がうまくインストール出来ていなかったら、次のようなエラーに出くわすでしょう。  

```
module.js:340
    throw err;
          ^
Error: Cannot find module 'lodash'
```

修正するには、`index.js`と同じディレクトリで`npm install lodash`を実行してください。