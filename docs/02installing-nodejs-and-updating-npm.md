# Node.jsのインストールとnpmのアップデート

## Node.jsのインストール

OS XかWindowsの場合、[Node.jsダウンロードページ](https://nodejs.org/en/download/)よりインストーラを取得し使うのがよいでしょう。Linuxの場合、インストーラも使えますし、[NodeSourceバイナリディストリビューション](https://github.com/nodesource/distributions)でお使いのシステムに対応したより新しいバージョンがないか確認するのも手です。  

テスト: `node -v` を実行してみましょう。バージョンはv0.10.32より新しい必要があります。  

## npmのアップデート

Nodeはnpmがインストールされた状態で取得されるので、何らかのバージョンのnpmが使えるようになります。しかし、npmはNodeより頻繁に更新されるので、最新であることを確認して下さい。  

```
npm install@latest -g
```  

テスト: `npm -v` を実行してみましょう。バージョンは2.1.8より新しい必要があります。  

## npmの手動インストール

上級者向け。  

npmのモジュールはこちらでダウンロードできます。  
https://registry.npmjs.org/npm/-/npm-{VERSION}.tgz