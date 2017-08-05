# Euphoria blog
プログラミング言語 Euphoria で作ったブログシステムです。

## 使い方
1. Euphoriaをインストールしてください。[openeuphoria.org](http://openeuphoria.org/)からダウンロードできます。
2. `index.cgi`の一行目をEuphoriaの実行ファイル`eui`に書き換えてください。
3. Apache2をインストールして，`sample.conf`を参考に，`/static/`以下はそのまま表示させるように・それ以外は全てindex.cgiに向けるように設定し，起動します。
4. 記事管理者のアカウント情報は`lib/blog/web/auth.exu`のプライベート変数`account`としてベタ書きされているので適宜変更してください。

## ライブラリについて
### template.exu
`lib/blog/template.exu`

テンプレートエンジンです。関数`process(sequence filepath, map:map params)`で実行します。TTerseに似た以下の記法が使えます。
- [% variable_name %]
- [% FOREACH value IN values %]~[% value %]~[% END %]
- [% INCLUDE filename %]

### dispatch.exu
`lib/blog/web/dispatch.exu`

ルーティング表は`dispatch.exu`内の手続き`dispatch`内の変数`route`にあります。

URLクエリパラメータとメッセージボディのパラメータを一つのmapに纏めます。

### response.exu
`lib/blog/web/response.exu`

レスポンスを作ります。これと`dispatch.exu`を使うことでCGIについてあまり意識することなくコントローラを記述できます。
