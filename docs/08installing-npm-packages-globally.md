# npmパッケージのグローバルインストール

npmパッケージのインストールには2つの方法があります。ローカルとグローバルです。どちらを使うかは、パッケージをどのように使いたいかに合わせて選んで下さい。  

grunt CLIのようなコマンドラインツールが欲しいときはグローバルインストールが便利です。一方で、例えばNode.jsの`require`を使うような、モジュール独自のパッケージを使いたい場合はローカルインストールが良いでしょう。  

グローバルインストールをするには、`npm install -g <package>`というコマンドを使うだけです。  
例:  
```
npm install -g jshint
```

EACCESエラーが起きたら、[パーミッションを修正してください](https://docs.npmjs.com/getting-started/fixing-npm-permissions)。`sudo`を使うことも出来ますが、次のようなコマンドは避けた方がよいです。  
```
sudo npm install -g jshint
```