deno は TypeScriptファイルをスクリプトとして実行することが出来る

```bash
deno run main.ts
```

## 型チェックについて

- v1.23 以降では型チェックしないので型チェックする場合は 以下のように明示的に型チェックが必要

```bash
deno check main.ts
```