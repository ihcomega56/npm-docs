# セマンティックバージョニングとnpm

セマンティックバージョニングは、そのリリースにどのような変更が含まれるかを伝えるのに多くのプロジェクトにおいて標準で採用されています。リリースに含まれる変更は、依存するパッケージのコードを壊しかねないためとても重要な情報です。

## パブリッシャーにとってのsemver

プロジェクトをほかの人と共有する場合、**1.0.0**から始めるのがルールです。npmのプロジェクトには、これに則っていないものもありますが。  

After this, changes should be handled as follows:
その後は、次のように変更を扱います。  

* バグフィックスやマイナーな変更: パッチリリース。1.0.1のように、最後の数字をインクリメントします。
* 既存の機能や仕様に影響のない新規機能追加: マイナーリリース。1.1.0のように、真ん中の数字をインクリメントします。
* 後方互換生を持たない変更: メジャーリリース。2.0.0のように、最初の数字をインクリメントします。

## 利用者にとってのsemver

利用者目線では、自分のアプリの`package.json`ファイルでどのアップデートまで適用可能か特定するのに使えます。  

例えば1.0.4から始めていた場合、使えるバージョンの幅は次のようになります。

* パッチリリース: 1.0 or 1.0.x or ~1.0.4
* マイナーリリース: 1 or 1.x or ^1.0.4
* メジャーリリース: * or x

より詳しい情報は[granular semver ranges](https://docs.npmjs.com/misc/semver)にあります。