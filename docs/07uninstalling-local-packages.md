# ローカルパッケージのアンインストール

`npm uninstall <package>`でnode_modulesディレクトリからパッケージを取り除くことが出来ます。  

```
npm uninstall lodash
```

`package.json`内の依存からも取り除くには、saveフラグを使います。  

```
npm uninstall --save lodash
```

NOTE:  
パッケージを`devDependency`としてインストールしていた場合(例えば`--save-dev`を使った場合)、`--save`では`package.json`の依存を取り除くことが出来ません。`--save-dev`を使ってください。