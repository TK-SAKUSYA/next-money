NEXT MONEY — Web公開用パッケージ
=================================

このパッケージは、既存のNEXT MONEY HTMLをFirebase Hostingで公開するための準備済みフォルダです。
公開作業自体は、あなたのFirebaseアカウントで実行する必要があります。このZIPだけで公開済みにはなりません。

公開手順（Windows）
-------------------

1. ZIPを展開します。
2. Firebase ConsoleでFirebaseプロジェクトを作成します:
   https://console.firebase.google.com/
3. Node.jsをインストールします（未導入の場合）:
   https://nodejs.org/
4. コマンドプロンプトを開き、このフォルダ（firebase.jsonがあるフォルダ）へ移動します。
5. 次を順に実行します。

   npm install -g firebase-tools
   firebase login
   firebase init hosting

6. 初期設定では:
   - 既存のFirebaseプロジェクトを選ぶ
   - 公開ディレクトリは「public」
   - 既存のpublic/index.htmlを上書きするか聞かれたら「No」
   - GitHub自動デプロイは必要なければ「No」
   - SPA設定は、この単一HTMLアプリでは通常「No」でOK

   注意: firebase initが既存ファイルを上書きしそうな場合は、上書きしないでください。
   必ず public/index.html がNEXT MONEY本体のまま残っていることを確認してください。

7. 次を実行して公開します。

   firebase deploy --only hosting

8. 表示された https://<プロジェクトID>.web.app のURLをPCやスマホで開きます。

データ保存について
------------------
NEXT MONEYは現状、ブラウザのlocalStorageに設定を保存します。
そのため同じURLを複数端末で開けますが、残高や設定は端末・ブラウザごとに別々です。
端末間同期をするには、別途クラウドデータベースとログイン機能の実装が必要です。

重要
----
- 公開URLはFirebaseのデプロイ完了後に発行されます。
- Firebaseアカウントでの操作は利用者自身が行う必要があります。
- 公開前に、public/index.htmlを開いて既存機能が残っていることを確認してください。
