# Roadmap / ロードマップ

開発の方向性と優先順位を示すドキュメントです。変更される場合があります。  
This document outlines the development direction and priorities. Subject to change.

---

## ✅ v0.1.0 — 基盤構築 / Foundation
*目標: 動くものを最速で作る / Goal: Get something working as fast as possible*

- [ ] Unity Editor拡張の基本構造 / Basic Unity Editor extension structure
- [ ] MCPサーバー（localhost）の実装 / MCP server (localhost) implementation
- [ ] AIプロバイダー接続（Claude / Gemini / OpenAI / Ollama） / AI provider connection
- [ ] チャットUIの実装 / Chat UI implementation
- [ ] APIキーのローカル保存 / Local API key storage
- [ ] ヒエラルキーの基本操作（選択・移動・削除） / Basic hierarchy operations (select, move, delete)
- [ ] チャット・操作履歴のローカル保存 / Local save of chat and operation history

---

## 🔧 v0.2.0 — VRC改変コア機能 / VRC Customization Core
*目標: 衣装着せ替えを自動化する / Goal: Automate outfit swapping*

- [ ] Modular Avatar対応の衣装着せ替え / Outfit swapping with Modular Avatar
- [ ] 素体プレファブのバリエーション作成 / Base prefab variation creation
- [ ] PhysBone設定の自動化 / PhysBone configuration automation
- [ ] オブジェクトON/OFFトグル作成 / Object ON/OFF toggle creation
- [ ] 破壊的操作前の確認ダイアログ / Confirmation dialog before destructive operations
- [ ] セッション内一括Undo / Session-wide undo

---

## 🎨 v0.3.0 — マテリアル・テクスチャ編集 / Material & Texture Editing
*目標: 色変更・テクスチャ編集を自然言語で / Goal: Color and texture editing via natural language*

- [ ] liltoonマテリアルの色変更（HSV調整） / liltoon material color change (HSV)
- [ ] テクスチャの差し替え / Texture replacement
- [ ] マテリアルのコピー・適用 / Material copy and apply
- [ ] 複数オブジェクトへの一括適用 / Batch apply to multiple objects

---

## 😊 v0.4.0 — 表情・アニメーション / Expressions & Animations
*目標: 表情セットアップを自動化する / Goal: Automate expression setup*

- [ ] FaceEmo連携 / FaceEmo integration
- [ ] 表情セットの自動生成 / Auto-generate expression sets
- [ ] アニメーターへの基本操作 / Basic Animator operations
- [ ] VRCExpressionsMenuへの項目追加 / Add items to VRCExpressionsMenu

---

## 🔁 v0.5.0 — 繰り返し作業の自動化 / Repetitive Task Automation
*目標: 毎回やる作業をワンコマンドで / Goal: One command for recurring tasks*

- [ ] 作業レシピの保存・再実行 / Save and replay operation recipes
- [ ] 「前回と同じ衣装を別の素体に着せる」などのテンプレート化 / Templates like "apply the same outfit to a different base"
- [ ] バッチ処理（複数バリエーションを一括生成） / Batch processing (generate multiple variations at once)

---

## 🌐 v1.0.0 — 安定版リリース / Stable Release
*目標: 広く使えるツールにする / Goal: Make it broadly usable*

- [ ] ドキュメントの整備 / Documentation
- [ ] エラーハンドリングの強化 / Improved error handling
- [ ] Unity 2022.3 LTS での動作保証 / Guaranteed compatibility with Unity 2022.3 LTS
- [ ] VCC / ALCOM対応パッケージの公開 / VCC / ALCOM compatible package release
- [ ] 日英ローカライズの完成 / Complete Japanese/English localization

---

## 💡 検討中 / Under Consideration
*優先度未定 / Priority not yet determined*

- Windows以外のサポート（Mac / Linux） / Non-Windows support (Mac / Linux)
- Web監視ダッシュボード / Web monitoring dashboard
- VRChatアバターのアップロード自動化 / VRChat avatar upload automation
- AI画像生成によるテクスチャ作成 / Texture generation via AI image generation
- Discordへの作業ログ送信（ユーザー自身のWebhook） / Operation log to Discord (user's own Webhook)

---

## ❌ 実装しない方針のもの / Out of Scope

| 項目 / Item | 理由 / Reason |
|---|---|
| テレメトリ・使用状況の収集 / Telemetry or usage analytics | ユーザーの同意なくデータを収集しない / No data collection without explicit consent |
| 特定AIプロバイダーへの誘導 / Steering users to a specific AI provider | ユーザーが自由に選択できるべき / Users should choose freely |
| 難読化されたDLLの配布 / Distributing obfuscated DLLs | 検証可能性を損なうため / Undermines verifiability |

---

*フィードバックは [Issues](../../issues) または [Discussions](../../discussions) へ。*  
*Send feedback to [Issues](../../issues) or [Discussions](../../discussions).*
