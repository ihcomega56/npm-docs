# dist-tagの利用

タグは、[semver](http://semver.org/)(例 v0.12)への補足情報で、パッケージの異なるバージョンの管理やラベリングに用いられます。人が読みやすくなるのに加え、パブリッシャーがパッケージの配布をより効果的に行うのに役立ちます。  

## タグの追加

パッケージの特定のバージョンにタグを追加するには、`npm dist-tag add <pkg>@<version> [<tag>]`を用います。もっと知りたい方は[the CLI docs](https://docs.npmjs.com/cli/dist-tag)をご覧下さい。  

## タグで指定したバージョンの公開

`npm publish`は、デフォルトだとパッケージに`latest`タグを打ちます。`--tag`フラグを使えば、それ以外のタグを指定出来ます。例えば、**beta**というタグと共にパッケージを公開する場合、以下のようになります。
```
npm publish --tag beta
```

## タグで指定したバージョンのインストール

`npm publish`と同様に、`npm install <pkg>`もデフォルトでは`latest`タグを使用します。それ以外は、`npm install <pkg>@<tag>`を使って下さい。次の例は、**somepkg**というパッケージを**beta**タグの付いたバージョンでインストールします。  
```
npm install somepkg@beta
```

## 警告

dist-tagはsemverと同じ名前空間を使うので、衝突するようなタグ名は避けましょう。そのためのベストプラクティスは、数字または**"v"**という文字で始まるタグを使うことです。