# はじめてのひとへ：セットアップガイド

エンジニアじゃなくても使えます。以下の3つのツールを順番にセットアップすれば大丈夫です。

## 1. Git & GitHub（コードのバージョン管理・共有ツール）

- [サル先生のGit入門](https://backlog.com/ja/git-tutorial/) — 図解でわかりやすい定番チュートリアル
- [GitHub公式：GitHubを使ってみよう](https://docs.github.com/ja/get-started/start-your-journey/hello-world) — アカウント作成〜forkまで
- やることは「GitHubアカウント作成 → リポジトリをfork → 自分のPCにclone」だけ

## 2. Obsidian（Markdownノートアプリ）

- [Obsidian公式サイト](https://obsidian.md/) — ダウンロードはここから（無料）
- [Obsidian入門ガイド（日本語）](https://publish.obsidian.md/help-ja/) — 公式ヘルプの日本語版
- cloneしたフォルダをObsidianで「保管庫として開く」だけでOK
- コミュニティプラグインを2つ入れる（設定 → コミュニティプラグイン → 制限モードをオフ → 「閲覧」から検索）：
  - **Dataview** — ダッシュボード（Home.md）の自動一覧表示に必要
  - **Obsidian Git** — Claude Codeが更新した内容をObsidianに自動反映するために必要。インストール後、設定で「Auto pull interval」を有効にしておく

## 3. Claude Code

- [Claude Code公式ドキュメント](https://docs.anthropic.com/ja/docs/claude-code/overview) — インストール手順はここ
- [Claude Code Web版](https://claude.ai/code) — ターミナルに不慣れならWeb版もあり、ブラウザだけで使える
- cloneしたフォルダで `claude` と打つだけで、あとはClaude Codeが全部わかってくれます

## セットアップの流れ（5ステップ）

1. GitHubアカウントを作る
2. リポジトリページで「Fork」ボタンを押す
3. 自分のPCにcloneする（`git clone <自分のforkのURL>`）
4. Obsidianで開く（「保管庫として開く」→ cloneしたフォルダを選択）
5. ターミナルでそのフォルダに移動して `claude` と打つ
