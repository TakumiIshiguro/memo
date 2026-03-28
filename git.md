# Git メモ

## コミットメッセージの種類

- `🐛 fix`: バグ修正
- `🔧 modify`: 既存機能の改善
- `♻ refactor`: リファクタリング
- `📝 docs`: ドキュメントの変更
- `🎨 style`: フォーマットやコード構造の整理
- `🔥 remove`: 不要な機能・ファイルの削除
- `✨ feat`: 新機能の追加
- `🍰 chore`: 自動生成ファイルや雑務的な変更
- `🌱 init`: 初回コミット
- `🧪 test`: テストや CI の追加・修正
- `👕 lint`: Lint エラーやコードスタイルの修正
- `🚀 perf`: パフォーマンス改善
- `🆙 update`: 依存パッケージなどの更新
- `🚧 wip`: 作業途中

## GitHub の初期設定（SSH）

### ユーザー名とメールアドレスを設定する

```bash
git config --global user.name "YOUR_NAME"
git config --global user.email "YOUR_EMAIL"
```

### SSH キーを作成する

```bash
ssh-keygen
```

### 公開鍵を表示する

```bash
cat ~/.ssh/id_rsa.pub
```

表示された公開鍵を GitHub に登録する。

## `git add` を取り消す

```bash
git reset HEAD
```

ステージした変更を取り消し、作業内容はそのまま残す。

## 直前の `git commit` を取り消す

```bash
git reset --soft HEAD^
```

コミットだけを取り消し、変更内容はステージされたまま残す。

## 特定のコミット時点に戻す

```bash
git reset --hard <commit-hash>
```

作業内容も含めてそのコミット時点に戻る。破壊的なので注意。

## リモートブランチを削除する

```bash
git push <remote> --delete <branch>
```

例:

```bash
git push origin --delete feature/sample
```
