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

対話式のコマンドラインが立ち上がり、上記のコマンドラインを実行したディレクトリに`package.json`するまで続きます。  

### 初期化フラグ --yes

