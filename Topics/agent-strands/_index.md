---
title: "Agent Strands (エージェントのStrands)"
created: "2026-03-12"
status: planned
tags:
  - topic/agent-strands
  - status/planned
---

# Agent Strands (エージェントのStrands)

## Overview
AWS が公開した AI エージェント構築のためのオープンソース SDK「Strands Agents」について調査する。Strands Agents は、モデル駆動型のアプローチでエージェントを構築するフレームワークであり、ツール利用・マルチエージェント連携・メモリ管理などを統合的に提供する。LangChain や CrewAI など既存のエージェントフレームワークとの比較、アーキテクチャ設計思想、実用性を明らかにする。

## Key Questions

### 基本概念・アーキテクチャ
- [ ] Strands Agents のコアアーキテクチャ（Agent Loop, Tool, Model Provider）はどう設計されているか？
- [ ] 「モデル駆動型（model-driven）」アプローチとは何か？他のフレームワークとどう異なるか？
- [ ] 対応している LLM プロバイダー（Amazon Bedrock, OpenAI, Anthropic 等）は何か？

### 機能・API
- [ ] ツール定義の仕組みはどうなっているか？（Python デコレータ、MCP サーバー対応等）
- [ ] マルチエージェント連携（Swarm パターン、グラフベース等）はどのように実装されているか？
- [ ] メモリ・セッション管理はどう行うか？長期記憶の仕組みはあるか？
- [ ] ストリーミング応答やイベントハンドリングの仕組みは？

### エコシステム・比較
- [ ] LangChain / LangGraph / CrewAI / AutoGen など既存フレームワークと比較した際の強み・弱みは？
- [ ] AWS サービス（Bedrock, Lambda, S3 等）との統合はどの程度深いか？
- [ ] ライセンス形態、コミュニティの活発さ、ドキュメント充実度は？

### 実用性・ユースケース
- [ ] 本番運用に耐えうる成熟度か？（テスト・デバッグ・オブザーバビリティ機能）
- [ ] 実際のユースケース事例は？（RAG、コード生成、データ分析等）

## Findings
<!-- Summary of key findings so far -->

## Related Topics
<!-- [[wikilinks]] to related topics -->

## Resources
<!-- Key resources, links, papers -->
