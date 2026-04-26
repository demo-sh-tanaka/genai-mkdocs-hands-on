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