---
title: "Agent Strands (エージェントのStrands)"
created: "2026-03-12"
status: active
tags:
  - topic/agent-strands
  - status/active
---

# Agent Strands (エージェントのStrands)

## Overview
AWS が公開した AI エージェント構築のためのオープンソース SDK「Strands Agents」について調査する。Strands Agents は、モデル駆動型のアプローチでエージェントを構築するフレームワークであり、ツール利用・マルチエージェント連携・メモリ管理などを統合的に提供する。LangChain や CrewAI など既存のエージェントフレームワークとの比較、アーキテクチャ設計思想、実用性を明らかにする。

## Key Questions

### 基本概念・アーキテクチャ
- [x] Strands Agents のコアアーキテクチャ（Agent Loop, Tool, Model Provider）はどう設計されているか？
- [x] 「モデル駆動型（model-driven）」アプローチとは何か？他のフレームワークとどう異なるか？
- [x] 対応している LLM プロバイダー（Amazon Bedrock, OpenAI, Anthropic 等）は何か？

### 機能・API
- [x] ツール定義の仕組みはどうなっているか？（Python デコレータ、MCP サーバー対応等）
- [x] マルチエージェント連携（Swarm パターン、グラフベース等）はどのように実装されているか？
- [x] メモリ・セッション管理はどう行うか？長期記憶の仕組みはあるか？
- [x] ストリーミング応答やイベントハンドリングの仕組みは？

### エコシステム・比較
- [x] LangChain / LangGraph / CrewAI / AutoGen など既存フレームワークと比較した際の強み・弱みは？
- [x] AWS サービス（Bedrock, Lambda, S3 等）との統合はどの程度深いか？
- [x] ライセンス形態、コミュニティの活発さ、ドキュメント充実度は？

### 実用性・ユースケース
- [x] 本番運用に耐えうる成熟度か？（テスト・デバッグ・オブザーバビリティ機能）
- [x] 実際のユースケース事例は？（RAG、コード生成、データ分析等）

## Findings

### コアアーキテクチャ
Strands は **Model Provider + System Prompt + Tool** の3コンポーネントで構成。LLM 自身がツール選択・実行順序を自律判断する「モデル駆動型」設計で、たった3行のコードでエージェントを構築可能。13以上の LLM プロバイダー（Bedrock, Anthropic, OpenAI, Gemini, Ollama 等）に対応。

### ツールシステム
Python `@tool` デコレータによるツール定義と **MCP（Model Context Protocol）ネイティブ統合**が特徴。`./tools/` ディレクトリからのホットリロードで高速開発が可能。

### マルチエージェント（v1.0）
4つのプリミティブ: **Agents-as-Tools**（階層的委任）、**Swarm**（集合知）、**Graph**（明示的ワークフロー）、そしてこれらの**自由な組み合わせ**。段階的に採用可能。

### メモリ・セッション
セッション管理（DAO パターン、S3/ローカルバックエンド）、AgentCore Memory 連携による短期/長期メモリ、エージェント間コンテキスト共有をサポート。

### 本番実績
AWS 内部で **Amazon Q Developer, AWS Glue, Kiro, VPC Reachability Analyzer** に採用。OpenTelemetry ビルトイン。Lambda/Fargate/EKS/Bedrock AgentCore 等にデプロイ可能。

### 他フレームワーク比較
最もシンプルなAPI（学習曲線が最低）。LangGraph は細かいワークフロー制御に強く、CrewAI はエンタープライズ機能が充実。Strands は AWS 統合と MCP エコシステムが差別化要因。

### プロジェクト情報
Apache 2.0、GitHub Stars ~5,300、Python/TypeScript 両対応。Accenture, Anthropic, Meta, PwC 等が貢献。

## Notes
- [[architecture-and-core-concepts|アーキテクチャとコア概念]]
- [[multi-agent-patterns|マルチエージェントパターン]]
- [[framework-comparison|フレームワーク比較]]
- [[production-and-usecases|本番運用とユースケース]]

## Related Topics
<!-- [[wikilinks]] to related topics -->

## Resources
- [Strands Agents 公式サイト](https://strandsagents.com/)
- [GitHub: strands-agents/sdk-python](https://github.com/strands-agents/sdk-python)
- [AWS Blog: Introducing Strands Agents](https://aws.amazon.com/blogs/opensource/introducing-strands-agents-an-open-source-ai-agents-sdk/)
- [AWS Blog: Strands 1.0](https://aws.amazon.com/blogs/opensource/introducing-strands-agents-1-0-production-ready-multi-agent-orchestration-made-simple/)
- [AWS Blog: Technical Deep Dive](https://aws.amazon.com/blogs/machine-learning/strands-agents-sdk-a-technical-deep-dive-into-agent-architectures-and-observability/)
- [AWS Prescriptive Guidance: Framework Comparison](https://docs.aws.amazon.com/prescriptive-guidance/latest/agentic-ai-frameworks/comparing-agentic-ai-frameworks.html)
