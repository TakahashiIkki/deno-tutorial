# deps

```typescript
import * as path from "https://deno.land/std@0.94.0/path/mod.ts";
```

- こういうのを複数ファイルで書いていると、バージョンアップの度に全ファイルをアップデートする必要がある
- 解決方法として2パターンある

## deps.ts を作る

- deps.ts っていうファイルを作ります。

```typscript
# deps.ts
export * as path from "https://deno.land/std@0.94.0/path/mod.ts";
export { ensureDir } from "https://deno.land/std@0.94.0/fs/ensure_dir.ts";
export { default as marked } from "https://cdn.skypack.dev/marked@1.2.7?dts";
```

- deps.ts 経由で全てのモジュールを使用する方法

```
import { ensureDir, path } from "./deps.ts";

await ensureDir(path.resolve("dist"));
```

なので、修正は deps.ts だけを修正すればOKとなる

## Import maps

- こんな感じでJSONファイルを用意して `imports` の key によって import する方針

```json
{
  "imports": {
    "std/colors": "https://deno.land/std@0.159.0/fmt/colors.ts"
  },
  "scopes": {}
}
```

- 以下のような使い方をします

```ts
import { bold, red } from "std/colors";

console.log(bold(red("Hello, Deno!")));
```

- `importmap` で指定する事で認識します

```bash
$ deno run --importmap import_maps.json 
```

ただし、 Import maps は denoプロセスにつき、1ファイルしか読み込めないとかの制約があるので、一旦、deps.ts に寄せても良いとの事
