# CLAUDE.md

このファイルはClaude Codeがこのプロジェクトで作業する際のガイドラインを定めます。

## Git 運用ルール

- **コードを変更するたびに必ずGitHubにプッシュすること**
- コミットメッセージは変更内容を簡潔に日本語で記述する
- コミット前に `git status` と `git diff` で変更内容を確認する
- プッシュは `git push origin <branch>` で行う
- mainブランチへの直接プッシュは避け、作業ブランチを使用することを推奨する

### 標準的なGitフロー

```bash
git add <変更ファイル>
git commit -m "変更内容の説明"
git push origin <ブランチ名>
```

## デプロイ先

- **本番URL:** https://karinozu.github.io/task-board/
- **ホスティング:** GitHub Pages
- **デプロイ方法:** `main` ブランチへのプッシュで GitHub Actions が自動ビルド＆デプロイ
- **ワークフロー:** `.github/workflows/deploy.yml`

## 技術スタック

| 種別 | 技術 |
|---|---|
| UIライブラリ | React 18 |
| ビルドツール | Vite 5 |
| 言語 | JavaScript (JSX) |
| スタイリング | CSS Modules (`.css` ファイルを直接 import) |
| 状態管理 | React `useState` / `useEffect`（外部ライブラリなし） |
| データ永続化 | `localStorage` |
| パッケージ管理 | npm |

## コンポーネント命名規約

- **ファイル名:** PascalCase（例: `TaskItem.jsx`, `TaskList.jsx`）
- **コンポーネント関数名:** ファイル名と一致させる（例: `export default function TaskItem()`）
- **CSSファイル名:** コンポーネントと同名（例: `TaskItem.css`）
- **コンポーネントは `src/` 直下に配置**（規模拡大時は `src/components/` に移動）
- **props の命名:** camelCase（例: `onDelete`, `isCompleted`）
- **イベントハンドラ:** `handle` プレフィックス（例: `handleKeyDown`, `handleSubmit`）
- **コールバック props:** `on` プレフィックス（例: `onToggle`, `onDelete`）

## 一般ルール

- 変更は最小限にとどめ、不要なリファクタリングは行わない
- コメントは「なぜそうするか」が自明でない場合のみ追加する
- セキュリティ上の問題（インジェクション、XSSなど）に注意する
