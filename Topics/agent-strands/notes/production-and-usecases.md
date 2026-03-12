---
title: "Strands Agents 本番運用とユースケース"
created: "2026-03-12"
status: active
tags:
  - topic/agent-strands
  - status/active
---

# Strands Agents 本番運用とユースケース

## 本番運用の成熟度

### オブザーバビリティ
- **OpenTelemetry** ビルトイン対応
- エージェントの実行トレース、ツール呼び出し、LLM インタラクションを追跡可能
- 既存の監視インフラ（CloudWatch, Datadog 等）と統合

### テスト・デバッグ
- エージェントの振る舞いを段階的にテスト可能
- ツール単体のユニットテスト
- エージェントループの統合テスト

### デプロイ環境
- AWS Lambda（サーバーレス）
- AWS Fargate（コンテナ）
- Amazon EKS（Kubernetes）
- Amazon Bedrock AgentCore（マネージド）
- Docker / Kubernetes（汎用）
- Terraform でのインフラコード化

## AWS 内部での採用実績

### Amazon Q Developer
- Strands を使って新エージェントの開発期間を **数ヶ月 → 数日〜数週間** に短縮
- AI コーディングアシスタントのバックエンド

### AWS Glue
- データ統合サービスのエージェント機能に採用

### Kiro（AI IDE）
- スペック駆動開発と組み合わせ
- 例: 3週間で本番品質の創薬ターゲット同定エージェントを構築
- マルチエージェント連携 + Bedrock AgentCore + Strands SDK

### VPC Reachability Analyzer
- ネットワーク分析機能にエージェントを活用

## 想定ユースケース

- **RAG（検索拡張生成）**: ナレッジベースからのドキュメント検索ツールと組み合わせ
- **コード生成・分析**: IDE 統合でのコーディング支援
- **データ分析**: 構造化データの分析・可視化
- **カスタマーサポート**: マルチエージェントで問い合わせをルーティング
- **ワークフロー自動化**: SOP（Standard Operating Procedures）機能で自然言語ワークフロー

## プロジェクト情報

- **ライセンス**: Apache 2.0
- **GitHub Stars**: 約 5,300
- **コミット数**: 604+
- **Python / TypeScript** の両 SDK
- **貢献企業**: Accenture, Anthropic, Meta, PwC 等
- **公開時期**: 2025年5月（初版）、2026年に 1.0 リリース

## 関連トピック
- [[architecture-and-core-concepts]]
- [[multi-agent-patterns]]
