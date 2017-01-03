# npmパッケージの公開

[nodeモジュール](https://docs.npmjs.com/getting-started/creating-node-modules)のように、`package.json`ファイルを含むディレクトリならどれでも公開が可能です。  

## ユーザの作成

公開したい場合、npmレジストリのユーザが必要です。持っていない方は、`npm adduser`で作成しましょう。サイトの方で既に作成した方は、`npm login`を実行してクライアントに認証情報を保持して下さい。

テスト:  
`npm config ls`でクライアントが認証情報を持っていることを確認して下さい。また、レジストリに追加されたことは[https://npmjs.com/~](https://npmjs.com/~)でチェックして下さい。  

## パッケージの公開

`npm publish`を使ってパッケージを公開します。  

[npm-developers](https://docs.npmjs.com/misc/developers)にある通り、ローカルの`.gitignore`か`.npmignore`にない限りはディレクトリ内の全てが含まれることに注意しましょう。  

また、他の人が既に使っている名前と同名のパッケージが存在しないことを確認しておいて下さい。  

テスト:  
**https://npmjs.com/package/<package>**に、追加したパッケージの情報が存在することを見ましょう。  

## パッケージのアップデート

パッケージに変更を入れたときは、`npm version <update_type>`を使ってアップデートが可能です。`update_type`には、セマンティックバージョニングによるリリースの型、パッチ、マイナーバージョン、あるいはメジャーバージョンが入ります。このコマンドで、`package.json`内のバージョン番号も変更されます。Gitリポジトリをお持ちなら、そのリリース番号でタグが発行されることも覚えていて下さい。  

バージョン番号のアップデートが完了したら、`npm publish`を再度行います。  

テスト:  
**https://npmjs.com/package/<package>**で、パッケージ番号が更新されていることを確かめましょう。  

パッケージが公開されるまで、サイト上のREADMEは更新されません。`npm version patch`及び`npm publish`によって、サイトのドキュメントも合わせて修正して下さい。