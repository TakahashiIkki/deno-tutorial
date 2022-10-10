# モジュールの仕組み

- DenoはES Modulesを前提としている
- ライブラリを利用したいときは、以下のようにimport文のURLでダウンロード先を指定する。
    - こういう感じですかね。 `deno colors.ts` とかでググると出てきます
    - https://deno.land/std@0.159.0/fmt/colors.ts

```bash
$ deno run main.ts

Hello, Deno!
```

ちなみに、 ローカルのキャッシュの場所は `deno info` で取得できるらしい. `DENO_DIR` がそれ。

```bash
$ deno info

DENO_DIR location: /Users/~~~/Library/Caches/deno
```
