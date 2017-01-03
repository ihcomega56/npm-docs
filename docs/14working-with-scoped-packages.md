# スコープドパッケージ

スコープはnpmモジュールの名前空間のようなものです。パッケージ名が`@`で始まる場合、そのパッケージはスコープドパッケージです。`@`と`/`に囲まれたものは全てスコープとなります。  
```
@scope/project-name
```
npmユーザは皆それぞれスコープを持っています。  
```
@username/project-name
```
スコープについてより詳細な情報は[CLI documentation](https://docs.npmjs.com/misc/scope#publishing-public-scoped-packages-to-the-public-npm-registry)にあります。

## npmのアップデートとログイン

バージョン**2.7.0**以降のnpmが必要です。初めてスコープドモジュールを使う際は、コマンドライン上でnpmに再度ログインしなくてはなりません。  

```
sudo npm install -g npm
npm login
```

## スコープドパッケージの初期化

スコープドパッケージを作成するには、スコープで始まるパッケージ名を使いましょう。  
```
{
  "name": "@username/project-name"
}
```

`npm init`を使う場合、コマンドのオプションでスコープを追加出来ます。  
```
npm init --scope=username
```

毎度同じスコープを使うならば、上のオプションを[.npmrc](https://docs.npmjs.com/files/npmrc)に設定しておくのがよいでしょう。
```
npm config set scope username
```

## スコープドパッケージの公開

スコープドパッケージはデフォルトでプライベートとなります。プライベートモジュールを公開するには、課金して[プライベートモジュール](https://www.npmjs.com/private-modules)になる必要があります。

しかし、パブリックなスコープドモジュールは無料で使えますし、有料のサブスクリプションは不要です。パブリックなスコープドモジュールを公開するには、公開時にアクセスオプションを指定します。そのオプションは、その後公開する全てのバージョンに適用されます。  
```
npm publish --access=public
```

## スコープドパッケージの利用

スコープドパッケージを使うときは、スコープを含めたパッケージ名を用いるようにして下さい。  

`package.json`では:  
```
{
  "dependencies": {
    "@username/project-name": "^1.0.0"
  }
}
```

コマンドラインでは:  
```
npm install @username/project-name --save
```

`require`句では:  
```
var projectName = require("@username/project-name")
```

プライベートなスコープドモジュールについては[npmjs.com/private-modules](https://www.npmjs.com/private-modules)をご覧下さい。