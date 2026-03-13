# VRC Avatar Agent

AIチャットでVRChatアバター改変を自動化するUnity Editorツール  
An AI-powered Unity Editor tool for automating VRChat avatar customization

---

## 🔒 設計思想 / Design Philosophy

このツールは **完全オープンソース** です。ソースコードはすべてこのリポジトリで公開されています。

This tool is **fully open source**. All source code is available in this repository.

**なぜオープンソースにするのか？ / Why open source?**

類似ツールにはソースコードが非公開・DLLが難読化されているものがあります。そのようなツールをVRChatプロジェクト（有料アセットを含む場合もある）に導入することには、以下のリスクがあります：

Some similar tools ship with closed-source, obfuscated DLLs. Introducing such tools into a VRChat project — which may contain paid assets — carries the following risks:

- ツールが何をしているか検証できない / No way to verify what the tool is actually doing
- APIキーや作業内容が外部に送信されていても気づけない / API keys or work content could be exfiltrated without your knowledge
- Unityプロジェクト内のファイルが意図せず読み取られる可能性がある / Project files could be read without your awareness

このツールは **「信頼は検証から生まれる」** という考えに基づいて作られています。動作に不安があれば、コードを読んでください。

This tool is built on the principle that **trust comes from verification**. If you have any doubts about its behavior, read the code.

---

## 🛡️ プライバシーとAPIキーの取り扱い / Privacy & API Key Handling

### APIキーの保存場所 / Where API keys are stored

APIキーは **Unityの `EditorPrefs` またはローカル設定ファイル** にのみ保存されます。外部サーバーへの送信は一切行いません。コードで確認できます：[`Editor/Settings.cs`](./Editor/Settings.cs)

API keys are stored **only in Unity's `EditorPrefs` or a local config file**. They are never sent to any external server. Verify this yourself: [`Editor/Settings.cs`](./Editor/Settings.cs)

### 外部通信先 / External communications

このツールが行う外部通信は **あなたが選択したAIプロバイダーのAPIのみ** です。

The only external communication this tool performs is to **the AI provider API you configure**.

| 通信先 / Destination | 目的 / Purpose | 無効化 / Disable |
|---|---|---|
| 選択したAI API / Your chosen AI API | チャット送受信 / Chat requests | ツールを使わない / Don't use the tool |
| その他 / Other | **なし / None** | — |

開発者のサーバー、テレメトリ、アナリティクスへの送信は **実装していません**。

There is **no telemetry, no analytics, and no developer server** receiving your data.

### 送信されるデータ / What data is sent

AIにチャットを送信する際、以下の情報がAIプロバイダーに送られます：

When you send a chat message, the following is sent to your AI provider:

- あなたが入力したチャットメッセージ / Your chat message
- ツールのシステムプロンプト（操作指示） / The tool's system prompt (operation instructions)
- 直前の会話履歴（コンテキスト維持のため） / Recent conversation history (for context)
- Unityシーンの状態（操作対象の特定に必要な範囲） / Unity scene state (to identify operation targets)

これはAI APIを使う以上避けられない仕様です。各AIプロバイダーのプライバシーポリシーをご確認ください。

This is unavoidable when using any AI API. Please review each provider's privacy policy.

### チャット・操作履歴の保存 / Chat and operation history

チャット履歴は **ローカルの `UserSettings/` フォルダに保存** されます。外部には送信されません。

Chat history is saved **locally in the `UserSettings/` folder**. It is never sent externally.

保存先 / Save location: `[ProjectRoot]/UserSettings/AvatarAgent/history/`

---

## 🤖 対応AIプロバイダー / Supported AI Providers

どのプロバイダーも **同等に動作します**。特定のサービスへの誘導は行いません。

All providers work **equally well**. We do not steer you toward any particular service.

| プロバイダー / Provider | 取得先 / Get API key | 無料枠 / Free tier | ログ確認 / Log access |
|---|---|---|---|
| Claude (Anthropic) | [console.anthropic.com](https://console.anthropic.com) | あり / Yes | ✅ Consoleで確認可 |
| Gemini (Google) | [aistudio.google.com](https://aistudio.google.com/apikey) | あり / Yes | ⚠️ 有料プランのみ / Paid plan only |
| OpenAI | [platform.openai.com](https://platform.openai.com) | なし / No | ✅ Dashboardで確認可 |
| ローカルLLM (Ollama) | [ollama.com](https://ollama.com) | 完全無料 / Free | ✅ 完全ローカル / Fully local |

> ⚠️ **Gemini無料枠の注意点 / Note on Gemini free tier:**  
> Google AI Studioの無料プランではAPIリクエストのログを確認できません。送受信内容を自分で検証したい場合はGoogle Cloud Console（有料）またはFiddler等のプロキシツールをご使用ください。  
> The free tier of Google AI Studio does not provide request logs. To verify what is sent, use Google Cloud Console (paid) or a proxy tool such as Fiddler.

---

## ✨ 主な機能 / Features

- 日本語チャットでUnity Editorを操作 / Control Unity Editor via natural language chat
- 衣装の着せ替え（Modular Avatar対応） / Outfit swapping (Modular Avatar support)
- マテリアル・テクスチャの編集 / Material and texture editing
- PhysBone設定 / PhysBone configuration
- オブジェクトON/OFFトグル作成 / Object toggle creation
- 操作前の確認ダイアログ（破壊的操作） / Confirmation dialog before destructive operations
- セッション内Undo（一括元に戻す） / Session-wide undo
- チャット・操作履歴のローカル保存 / Local save of chat and operation history

---

## 📋 動作環境 / Requirements

- Unity 2022.3.22f1
- VRChat SDK 3.x
- Modular Avatar（衣装着せ替えに必要 / required for outfit swapping）
- liltoon（マテリアル編集に必要 / required for material editing）
- Windows 10 / 11

---

## 🚀 導入方法 / Installation

### VCC を使う場合（推奨）/ Using VCC (Recommended)

1. VCC（VRChat Creator Companion）を開く / Open VCC
2. Settings → Packages → Add Repository
3. 以下のURLを追加 / Add the following URL:
   ```
   https://[your-github-username].github.io/vrc-avatar-agent/index.json
   ```
4. プロジェクトに `VRC Avatar Agent` を追加 / Add `VRC Avatar Agent` to your project

### 手動インストール / Manual Installation

1. [Releases](../../releases) から最新の `.unitypackage` をダウンロード / Download the latest `.unitypackage`
2. Unityプロジェクトにインポート / Import into your Unity project
3. メニュー `Window > VRC Avatar Agent` を開く / Open via `Window > VRC Avatar Agent`
4. 設定画面でAIプロバイダーとAPIキーを入力 / Enter your AI provider and API key in Settings

---

## 🤝 コントリビューション / Contributing

バグ報告・機能要望は [Issues](../../issues) へ。プルリクエスト歓迎です。

Bug reports and feature requests go to [Issues](../../issues). Pull requests are welcome.

---

## 📄 ライセンス / License

MIT License — 自由に使用・改変・再配布できます / Free to use, modify, and redistribute.

---

## 💬 サポート / Support

- バグ報告 / Bug reports: [GitHub Issues](../../issues)
- 質問・雑談 / Questions: [Discussions](../../discussions)

---

*このツールはVRChatコミュニティのために、透明性を最優先に作られています。*  
*This tool is built for the VRChat community with transparency as the top priority.*
