# Braindump

[English version](README.md)

脳みそは覚えることより考えることに使おう。ここにぶち込めば、Claudeが整理してくれる。

[Obsidian](https://obsidian.md) + [Claude Code](https://docs.anthropic.com/en/docs/claude-code) で動くパーソナルナレッジベース。思いつき、リサーチ、深夜3時のアイデア——なんでも投げ込めば、整理された知識になって返ってくる。

**コンセプト：** Claudeには雑に短く話しかけるだけ。重い作業はClaudeがやる。時間があるときにObsidianを開いて、整理・リンクされたノートをじっくり読む。[Getting Things Done](https://en.wikipedia.org/wiki/Getting_Things_Done)の考え方——全部キャプチャして、あとで処理して、システムを信頼する。

## 何ができる？

### 1. 思考の垂れ流し

`Thoughts/` に何でも書き殴る。生煮えのアイデア、ふと思ったこと。そんな思いつきでもClaudeが咀嚼すれば宝になるかもしれない。

### 2. サクッとQ&A

「ベータマックスはなぜ負けた？」「Transformerって実際どう動くの？」——Claudeに聞くだけ。vault内の既存知識を確認し、必要ならWebも調べて、全部ファイリングしてくれる。今すぐ答えがもらえて、あとでObsidianにきれいなノートが待ってる。

### 3. ディープリサーチ

気になる単語を聞いた？「これメモしといて」とClaudeに言えば `Inbox.md` にストックされる。時間とコーヒーがある時にClaudeにリサーチを頼めば、計画・実行・整理まで全部やってくれる。Obsidianで結果を読むだけ。

### 4. Todo

「あの論文読まなきゃ」——Claudeにtodoに追加してと言うだけ。完了チェック、一覧表示、全部 `Todo.md` で管理。

すべてプレーンなMarkdown。ノートは自分のもの、どこかのアプリに囲い込まれない。

## 必要なもの

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) — CLIでも[Web版](https://claude.ai/code)でもOK
- [Obsidian](https://obsidian.md) — グラフビュー、wikilinks、Dataviewクエリを活かすならおすすめ。他のMarkdownエディタでも動くけど、もったいない
- Git

> **Git・Obsidian・Claude Codeが初めての人へ：** [非エンジニア向けセットアップガイド](docs/setup-guide-ja.md) にキャッチアップ資料とステップバイステップの手順をまとめています。

## セットアップ

1. **リポジトリをクローンまたはフォーク**

   ```sh
   git clone <this-repo-url> my-braindump
   cd my-braindump
   ```

2. **Obsidianで開く** — フォルダをvaultとして開く（詳しくは下の「Obsidianの使い方」を参照）。

3. **Claude Codeを起動** — ディレクトリで `claude` を実行。`CLAUDE.md` がClaudeに全部教えてくれるので、設定は不要。

## 使い方

Claudeに自然に話しかけるだけ。やりたいことを勝手に判断してくれる。挙動が安定しない場合は、スラッシュコマンドの直接使用を推奨：
デスクトップのClaude Code CLI、またはClaude Code on Web(モバイルアプリにもある)で実行可能

| Skills           | 内容                                                       | このskillsが選択されるプロンプトの例                 |
| ---------------- | ---------------------------------------------------------- | ---------------------------------------------------- |
| `dump`           | **思考整理** — タグとwikilinksで強化                       | 「これメモって：最近AIエージェントが〜」             |
|                  |                                                            |                                                      |
| `ask`            | **Q&A** — 何でも聞ける、回答と調査結果がvaultに保存        | 「なんでベータマックスは負けたの？」                 |
|                  |                                                            |                                                      |
| `deep-memo`      | **ディープリサーチ ステップ0** — 単語をInboxにメモ         | 「量子コンピュータ、あとで調べたいからメモしといて」 |
| `deep-plan`      | **ディープリサーチ ステップ1** — inboxからリサーチ計画作成 | 「Inboxのやつ、リサーチ計画作って」                  |
| `deep-research`  | **ディープリサーチ ステップ2** — 実際のリサーチを実行      | 「計画したトピック調べて」                           |
| `deep-suggest`   | **ディープリサーチ おまけ** — 追加の調査方向を提案         | 「他に調べるべきことある？」                         |
|                  |                                                            |                                                      |
| `/todo [タスク]` | **Todo** — タスクの追加・完了・一覧                        | 「あの論文読むのtodoに入れといて」                   |

`/ask` は単発の質問用。`/deep-memo` → `/deep-plan` → `/deep-research` はトピックを溜めておいて、まとめてリサーチしたいとき用。

### 典型的な使い方

1. **忙しいとき** — 気になったワードを `/deep-memo 量子コンピュータ` でInboxに投げておく。いつでも、何回でも。あとで調べたいものをとりあえずストックする
2. **ちょっと調べたいとき** — `/ask なぜ日本の金利は低い？` のようにClaude Codeに聞く。回答がその場で返ってきて、ノートとしてvaultに保存される
3. **まとまった時間があるとき** — `/deep-plan` でInboxのトピックをリサーチ計画に変換 → `/deep-research` で実行。Claude Codeが自動でWebを調べてノートを作成する
4. **あとで読む** — Obsidianを開いて、Claudeが作ったノートを読む。グラフビューで知識のつながりを眺める

## Vault構成

```
├── Inbox.md              # トピックを1行1語で書き込む
├── Home.md               # Dataviewクエリ付きダッシュボード
├── Thoughts/             # 自由な思考 — 何でも書く
├── Topics/               # リサーチ成果、トピックごとに1フォルダ
│   └── <topic-name>/
│       ├── _index.md     # 概要、ステータス、主要な問い
│       ├── notes/        # リサーチノート
│       └── references/   # ソース要約とリンク
├── Templates/            # トピック・ノート・リファレンスのテンプレート
├── Maps/                 # 関連トピックをつなぐMap of Content
├── Archive/              # 完了・休止中のリサーチ
├── CLAUDE.md             # Claude Codeへの指示（消さないで）
└── .claude/skills/       # スラッシュコマンドのスキル定義
```

## Obsidianの使い方

Obsidianは「閲覧・ブラウジング用」として使う。ノートの作成や整理はClaude Codeがやるので、Obsidianでは主に読む・眺める・つながりを発見する。

### 初回セットアップ

1. [Obsidian](https://obsidian.md/) をインストール
2. 「保管庫を開く」→ cloneしたフォルダを選択
3. 設定 → コミュニティプラグイン → 制限モードをオフ → 「閲覧」から以下をインストール・有効化：
   - **Dataview** — `Home.md` のダッシュボード表示に必要
   - **Obsidian Git** — Claude Codeがpushした変更を自動で取り込むために必要。インストール後、設定で「Auto pull interval」を有効にしておくと、Obsidianを開いているだけで最新のノートが反映される

### おすすめの使い方

- **Home.md を開く** — ダッシュボードになっていて、アクティブなトピック・最近の思考・最近のノートが自動で一覧表示される（Dataviewプラグインが必要）
- **グラフビュー** — 左サイドバーのグラフアイコン、またはCmd/Ctrl+Gで開く。ノート同士のつながりが可視化されて、思わぬ関連性が見つかる
- **wikilinks** — ノート内の `[[リンク]]` をクリックすると関連ノートに飛べる。Claude Codeが自動的にリンクを張ってくれる
- **タグで絞り込み** — 左サイドバーのタグペインで `#status/active` や `#topic/xxx` をクリックすると、関連ノートだけ表示できる
- **検索** — Cmd/Ctrl+Shift+F で全文検索。vault内のすべてのノートを横断検索できる

### Dataviewクエリについて

`Home.md` にはDataviewクエリが埋め込まれている。これはObsidianのDataviewプラグインがノートのメタデータ（フロントマターのタグやステータス）を読み取って、自動で一覧を生成する仕組み。プラグインを入れないと `\`\`\`dataview` のコードブロックがそのまま表示されるだけなので、Dataviewのインストールを推奨。

## カスタマイズ

- **テンプレート** — `Templates/` のファイルを編集して、トピック・ノート・リファレンスの形式を変更。
- **タグ** — デフォルト: `#topic/<name>`, `#status/planned|active|done`, `#thought`, `#reference`。`CLAUDE.md` で変更可能。
- **スキル** — `.claude/skills/<name>/SKILL.md` に定義。Claudeの動作を調整したり、独自スキルを追加できる。
- **CLAUDE.md** — 全体の司令塔。Claudeのルールはここで設定。

## ルール

- すべてのファイルはYAMLフロントマター付きMarkdown
- 内部リンクは `[[wikilinks]]` を使用
- フォルダ名・ファイル名は小文字・ハイフン区切り（`quantum-computing`, `error-correction.md`）
- Thoughtsは絶対に書き換えない——タグとリンクの追加のみ

## ブランチ運用

個人用ナレッジベースなので、**mainブランチ1本で運用**する。

- Claude Codeがリサーチや整理を実行すると、結果を自動的にmainにコミット＆プッシュする
- PRやブランチ分岐は使わない（個人vaultにレビューフローは不要）
- Obsidianで開いているときにClaudeが変更を加えた場合、Obsidian Gitプラグインが自動でpullして反映する
- もし手元の変更とClaude Codeの変更が衝突した場合は、`git pull` してからClaude Codeを再実行すればOK

## ライセンス

フォークして、好きにいじって、自分のものにしよう。
