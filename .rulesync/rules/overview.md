---
root: true
targets: ["*"]
description: "Project overview and general development guidelines"
globs: ["**/*"]
---

# Overview

## 基本方針

- 日本語で思考し、日本語でユーザーと対話する。
- すべてのテキスト、コメント、ドキュメントは日本語で記述する。
- クラス名、関数名、その他の識別子は英語で記述する。
- 明示されない限り、後方互換性は考慮しない。できるだけシンプルに保つ。
- 明示されない限り、フォールバックは実装しない。できるだけシンプルに保つ。
- KISS: Keep it simple, stupid
- YAGNI: You aren't gonna need it

## ユーザーとの対話

- 結論は最初に述べる。
- 列挙において、同じ属性値を比較する場合は、表形式で提示する。
- 簡潔に記載し、長文は避ける。

## drawio

drawio-desktopのCLIをラップした `drawio-export` を同梱している。役割はAIが作った `.drawio` をPNG/SVG/PDFにexportすること**に絞られる。図を新規作成する機能はほぼないため、作図はAIに `mxGraphModel` XMLを書かせて `.drawio` として保存させる前提で使う。

### 使い方

1. AIに `.drawio` ファイルを作らせる。
2. そのままAIに `drawio-export` を実行させる。
3. 必要なら生成されたPNG/SVG/PDFをdraw.ioで再編集する。

`-e` (`--embed-diagram`) を付けると元のXMLが出力ファイルに埋め込まれるので、特に理由がなければ常に付ける。ファイル名は `diagram.drawio.png` のような二重拡張子にしておくと再編集可能な成果物だと分かりやすい。

### 基本コマンド

```bash
# PNG
drawio-export -x -e -b 10 -f png -o diagram.drawio.png diagram.drawio

# SVG
drawio-export -x -e -f svg -o diagram.drawio.svg diagram.drawio

# PDF
drawio-export -x -e --crop -f pdf -o diagram.drawio.pdf diagram.drawio
```

よく使うオプション:

| オプション | 用途 |
| --- | --- |
| `-x, --export` | export 実行 |
| `-f, --format <fmt>` | `png` / `svg` / `pdf` などの出力形式 |
| `-o, --output <path>` | 出力先 |
| `-e, --embed-diagram` | 元のXMLを埋め込んで再編集可能にする |
| `-b, --border <n>` | PNG の余白 |
| `--crop` | PDF を図形サイズに合わせて切り詰める |
