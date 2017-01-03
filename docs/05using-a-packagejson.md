# package.jsonの使用

ローカルインストールされたnpmパッケージを管理するには、`package.json`使うのが良いでしょう。  

`package.json`でこんなことが出来ます。  
1. プロジェクトがどんなパッケージに依存するかを示すドキュメントの役割を果たします。
1. [semantic versioning rules](https://docs.npmjs.com/getting-started/semantic-versioning)に基づき、プロジェクトで使えるパッケージのバージョンを明確にします。
1. 組み立てたものをコピー可能にします。他の開発者とのシェアを容易にする手段です。  

## 必要なもの

最低限、`package.json`は次のものを含む必要があります。  

* "name"
    * すべて小文字
    * 一単語のみ、スペースなし
    * ダッシュとアンダースコアは許容
* "version"
    * **x.x.x**の形式
    * [semver spec](https://docs.npmjs.com/getting-started/semantic-versioning)に準拠

例:  
```json
{
  "name": "my-awesome-package",
  "version": "1.0.0"
}
```

## package.jsonの作成

`package.json`を作成するには、以下を実行します。  

```
> npm init
```

対話式のコマンドラインが立ち上がり、上記のコマンドラインを実行したディレクトリに`package.json`が作成されるまで続きます。  

### 初期化フラグ --yes

コマンドラインを拡張した対話式の操作はすべてのユーザ向けではありまえせん。`package.json`を使うほうが快適だという人もいるでしょう。  
`npm init`に`--yes`または`-y`というフラグを付けることでデフォルトの`package.json`を取得できます。  

```
> npm init --yes
```

これを使うと、コマンドラインでは`author`のみ確認され、その他の項目にはデフォルト値が設定されます。  

```
> npm init --yes
```

`/home/ag_dubs/my_package/package.json`に次の内容が書き出されます。  
 
```
{
  "name": "my_package",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "ag_dubs",
  "license": "ISC",
  "repository": {
    "type": "git",
    "url": "https://github.com/ashleygwilliams/my_package.git"
  },
  "bugs": {
    "url": "https://github.com/ashleygwilliams/my_package/issues"
  },
  "homepage": "https://github.com/ashleygwilliams/my_package"
}
```

* name: Gitディレクトリの中にない場合、authorの名前(その場合、それがnpmリポジトリの名前となる)
* version: 常に `1.0.0`
* main: 常に `index.js`
* scripts: デフォルトでは、空のテストスクリプト
* keywords: 空
* author: コマンドラインで入力した値
* license: ISC
* repository: カレントディレクトりより取得(あれば)
* bugs: カレントディレクトりより取得(あれば)
* homepage: カレントディレクトりより取得(あれば)
`init`コマンドでは、他にもいくつかの設定が可能です。便利な例を挙げます: 

```
> npm set init.author.email "wombat@npmjs.com"
> npm set init.author.name "ag_dubs"
> npm set init.license "MIT"
```

NOTE:  
`package.json`に`description`フィールドがない場合、npmは`README.md`あるいは`README`の先頭行を`description`として使います。`description`は`npm search`でパッケージを探すときに有用なので、用意しておくときっとパッケージが見つかりやすくなります。  

### init処理の拡張

init処理で作る情報や、対話式に質問する内容は、`.npm-init.js`を作ることでカスタマイズが可能です。デフォルトでは、ホームディレクトリに`~/.npm-init.js`があります。  

シンプルな`.npm-init.js`はこのようになります:  
```
module.exports = {
  customField: 'Custom Field',
  otherCustomField: 'This field is really cool'
}
```

ホームディレクトリで`npm init`を実行すると、`package.json`が次のように出力されます:  
```
{
  customField: 'Custom Field',
  otherCustomField: 'This field is really cool'
}
```

また、`prompt`関数を使うと質問を拡張出来ます。  

```
module.exports = prompt("what's your favorite flavor of ice cream buddy?", "I LIKE THEM ALL");
```

拡張機能の応用編はこちらのドキュメント([init-package-json](https://github.com/npm/init-package-json))を参照してください。  

## パッケージの特定

プロジェクトの依存するパッケージを特定するには、使いたいパッケージを`package.json`にリストアップします。リスト化出来るパッケージには2種類あります:  
* "dependencies": プロダクションコードで必要なパッケージ
* "devDependencies": 開発およびテストで必要なパッケージ  

### package.jsonのマニュアル編集

`package.json`は手で書き換えることが出来ます。オブジェクトを値に持つ、`dependencies`という属性をパッケージオブジェクトの中に作って下さい。このオブジェクトは、使いたいパッケージから名前をとった属性を持ち、その値は[semver](https://docs.npmjs.com/getting-started/semantic-versioning)形式を取ります。semver形式は、依存するプロジェクトのどのバージョンが自分のプロジェクトと互換性を持つか表すものです。  

ローカル環境でのみ必要な依存は、`devDependencies`プロパティで同じように定義します。  

```
{
  "name": "my_package",
  "version": "1.0.0",
  "dependencies": {
    "my_dep": "^1.0.0"
  },
  "devDependencies" : {
    "my_test_framework": "^3.1.0"
  }
}
```

### インストールフラグ --save, --save-dev

`package.json`への依存の追加は、コマンドラインから行う方法がより簡単で、そしてより優れていると言えます。環境に応じて`npm install`コマンドに`--save`または`--save-dev`フラグをつけるのです。  

`package.json`の`dependencies`への追加:  
```
npm install <package_name> --save
```
`package.json`の`devDependencies`への追加は:  
```
npm install <package_name> --save-dev
```

## 依存のバージョン管理

npmは、パッケージのバージョン及びバージョンの範囲を管理するのに、セマンティックバージョニング(Semantic Versioning、よくSemVerと呼ばれます)を使っています。  

ディレクトリに`package.json`ファイルが存在する状態で`npm install`を実行すると、npmはファイル内にリスト化された依存関係を見ます。そして、全パッケージの[semver rules](https://docs.npmjs.com/getting-started/semantic-versioning)を満たす最新バージョンをダウンロードします。  

セマンティックバージョニングについて詳しく知りたい方は["Semver" page](https://docs.npmjs.com/getting-started/semantic-versioning)をご覧ください。