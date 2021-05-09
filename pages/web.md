# Web技術入門

『Webを支える技術』から、Web開発をするに当たってひとまず必要になる情報をピックアップ。

## ハイパーメディア/分散システム

めちゃくちゃ簡単に言うと

- Web上にはさまざまなコンテンツが分散して存在している(分散システム)
- そういったコンテンツにアクセスするのに、「リンク」を用いる(ハイパーメディア)
- リンクをたどる通信において、通例うまくいくとされている考え方や取り決め(REST)

## REST

### Client - Serverモデル

- Client（利用者）とServer（提供者）に分けて考える

https://en.wikipedia.org/wiki/Client%E2%80%93server_model

### リソース

### 統一インターフェース

さまざまなクライアントが共通で使えるように、インターフェースを定義する。

#### 例

- LINE API
  - https://developers.line.biz/ja/reference/messaging-api/#send-reply-message
- Google Calendar
  - https://developers.google.com/calendar/v3/reference?hl=ja

### ステートレス

クライアントの状態をサーバーが持たない。

https://qiita.com/mtakehara21/items/efcbbc3ba58a62c10eb6

## URI

### 構文

https://developer.mozilla.org/ja/docs/Web/HTTP/Basics_of_HTTP/Identifying_resources_on_the_Web

## HTTP

### リクエスト

#### ヘッダ

- 開発者ツールでみてみる

#### メソッド

- GET: リソースの取得
  - 冪等性
  - 安全
- POST: リソースの作成
- PUT: リソースの更新・作成
  - 冪等性
- DELETE: リソースの削除
  - 冪等性

### レスポンス

#### ステータスコード

- 200
- 301
- 400
- 401
- 404
- 500

https://developer.mozilla.org/ja/docs/Web/HTTP/Status