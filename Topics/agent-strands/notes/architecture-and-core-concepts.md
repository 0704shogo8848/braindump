---
title: "Strands Agents アーキテクチャとコア概念"
created: "2026-03-12"
status: active
tags:
  - topic/agent-strands
  - status/active
---

# Strands Agents アーキテクチャとコア概念

## モデル駆動型（Model-Driven）アプローチ

Strands Agents の最大の特徴は「モデル駆動型」設計思想。LLM 自身がどのツールをどの順序で呼び出すかを自律的に判断する。事前に定義されたワークフローに従うのではなく、モデルがコンテキストとタスクに基づいて最適なアクションを決定する。

これは LangGraph のようなグラフベースのワークフロー定義とは対照的なアプローチ。開発者はワークフローのロジックを書く代わりに、適切なツールとシステムプロンプトを用意するだけでよい。

## 3つのコアコンポーネント

### 1. Model Provider（推論エンジン）
LLM との通信を抽象化するレイヤー。対応プロバイダー:
- **Amazon Bedrock** — AWS ネイティブ統合
- **Anthropic** — Claude 直接利用
- **OpenAI** — GPT シリーズ
- **Google Gemini**
- **Ollama** — ローカル LLM
- **LiteLLM** — 統合プロキシ
- **llama.cpp** — ローカル推論
- **LlamaAPI, MistralAI, Cohere, SageMaker, Writer** 等
- **カスタム実装** も可能

### 2. System Prompt（指示）
エージェントの役割・制約・振る舞いを定義するプロンプト。

### 3. Tool / Toolbelt（ツール群）
エージェントが実行できるアクション。定義方法:
- **Python デコレータ**: `@tool` デコレータで関数をツール化。自動ドキュメンテーション付き
- **MCP (Model Context Protocol)**: MCP サーバーとのネイティブ統合で、外部ツールエコシステムにアクセス
- **ホットリロード**: `./tools/` ディレクトリからの自動読み込みで高速イテレーション

## エージェントループ

1. LLM にプロンプト・コンテキスト・ツール定義を送信
2. LLM が以下のいずれかを選択:
   - 自然言語で応答
   - ステップの計画を立てる
   - 前のステップを振り返る
   - 1つ以上のツールを使用
3. ツール選択時、Strands がツールを実行し結果を LLM に返却
4. ループを繰り返し、完了まで継続

## 最小コード例

```python
from strands import Agent
from strands_tools import calculator

agent = Agent(tools=[calculator])
agent("What is the square root of 1764")
```

たった3行でエージェントが動作する。これが Strands の「シンプルさ」の核心。

## デプロイメントパターン

- **モノリス**: エージェントループとツール実行が同一環境
- **マイクロサービス**: ループとツールを分離デプロイ
- 対応環境: AWS Lambda, Fargate, EKS, Bedrock AgentCore, Docker, Kubernetes, Terraform

## ストリーミング・イベントハンドリング

- ビルトインのストリーミングレスポンス対応
- 実行ライフサイクルイベントへの応答メカニズム
- v1.0 で非同期（async）操作をスタック全体でサポート

## 関連トピック
- [[agent-strands-multi-agent]]
- [[agent-strands-comparison]]
