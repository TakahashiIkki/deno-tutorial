## パーミッションシステム

- deno では `パーミッションシステム` というのが採用されており、特定の処理はデフォルトでは実行する事ができない
- 特定の処理、というには以下のもの
    - ファイルの読み書き
    - ネットワークアクセス
    - 環境変数の参照
    - サブプロセスの実行

```bash
$ deno run main.ts

⚠️  ┌ Deno requests net access to "0.0.0.0:8000".
   ├ Requested by `Deno.listenDatagram()` API
   ├ Run again with --allow-net to bypass this prompt.
   └ Allow? [y/n] (y = yes, allow; n = no, deny) > ^C
```

↑ こうなります。

このように指定が必要です

```bash
$ deno run --allow-net main.ts
```
