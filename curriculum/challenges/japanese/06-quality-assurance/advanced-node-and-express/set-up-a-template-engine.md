---
id: 5895f700f9fc0f352b528e63
title: テンプレートエンジンを設定する
challengeType: 2
forumTopicId: 301564
dashedName: set-up-a-template-engine
---

# --description--

チャレンジに取り組むにあたり、以下の方法のうち 1 つを用いてコードを記述します。

- <a href="https://github.com/freeCodeCamp/boilerplate-advancednode/" target="_blank" rel="noopener noreferrer nofollow">GitHub リポジトリ</a>をクローンし、ローカル環境でプロジェクトを完了させる。
- <a href="https://replit.com/github/freeCodeCamp/boilerplate-advancednode" target="_blank" rel="noopener noreferrer nofollow">Replit スタータープロジェクト</a>を使用して、チャレンジを完了させる。
- 使い慣れたサイトビルダーを使用してプロジェクトを完了させる。 必ず GitHub リポジトリのすべてのファイルを取り込む。

完了したら、プロジェクトの動作デモをどこか公開の場にホストしてください。 そして、`Solution Link` フィールドでデモへの URL を送信してください。

テンプレートエンジンを使用すると、(*Pug* で記述するような) 静的なテンプレートファイルをアプリで使用できます。 実行時にテンプレートエンジンによって、テンプレートファイル内の変数がサーバーから提供される実際の値に置き換えられます。 そして、テンプレートが静的な HTML ファイルに変換され、クライアントへ送信されます。 このアプローチにより、HTML ページの設計が容易になり、クライアントから API 呼び出しを行うことなく、ページに変数を表示することができます。

すでに `pug@~3.0.0` がインストールされており、プロジェクトの `package.json` ファイルに依存関係としてリストされています。

どのテンプレートエンジンを使用しているかを Express に知らせる必要があります。 `set` メソッドを使用して、`view engine` プロパティの値として `pug` を割り当ててください (`app.set('view engine', 'pug')` と記述します)。

`views/pug` ディレクトリ内でインデックスファイルが正しくレンダーされるまで、ページは空です。

`pug` テンプレートをレンダーするには、`/` ルートで `res.render()` を使用する必要があります。 `views/pug` ディレクトリのファイルパスをメソッドの引数として渡します。 パスは相対パス (ビューを基準) または絶対パスで指定でき、ファイル拡張子を必要としません。

すべての処理に問題がなければ、アプリのホームページが空でなくなり、Pug テンプレートが正常にレンダーされたことを示すメッセージが表示されます。

正しいと思ったら、ページを送信してください。 エラーが発生している場合は、ここまでに完了したプロジェクトを<a href="https://gist.github.com/camperbot/3515cd676ea4dfceab4e322f59a37791" target="_blank" rel="noopener noreferrer nofollow">こちら</a>で確認できます。

# --hints--

Pug を依存関係にする必要があります。

```js
(getUserInput) =>
  $.get(getUserInput('url') + '/_api/package.json').then(
    (data) => {
      var packJson = JSON.parse(data);
      assert.property(
        packJson.dependencies,
        'pug',
        'Your project should list "pug" as a dependency'
      );
    },
    (xhr) => {
      throw new Error(xhr.statusText);
    }
  );
```

ビューエンジンを Pug にする必要があります。

```js
(getUserInput) =>
  $.get(getUserInput('url') + '/_api/server.js').then(
    (data) => {
      assert.match(
        data,
        /('|")view engine('|"),( |)('|")pug('|")/gi,
        'Your project should set Pug as a view engine'
      );
    },
    (xhr) => {
      throw new Error(xhr.statusText);
    }
  );
```

正しい ExpressJS メソッドを使用して、レスポンスからインデックスページをレンダーします。

```js
(getUserInput) =>
  $.get(getUserInput('url') + '/').then(
    (data) => {
      assert.match(
        data,
        /FCC Advanced Node and Express/gi,
        'You successfully rendered the Pug template!'
      );
    },
    (xhr) => {
      throw new Error(xhr.statusText);
    }
  );
```

Pug が正しく動作している必要があります。

```js
(getUserInput) =>
  $.get(getUserInput('url') + '/').then(
    (data) => {
      assert.match(
        data,
        /pug-success-message/gi,
        'Your projects home page should now be rendered by pug with the projects .pug file unaltered'
      );
    },
    (xhr) => {
      throw new Error(xhr.statusText);
    }
  );
```

# --solutions--

```js
/**
  Backend challenges don't need solutions, 
  because they would need to be tested against a full working project. 
  Please check our contributing guidelines to learn more.
*/
```
