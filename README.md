# chat-log-plugin

Claude Code とのセッション会話をMarkdownファイルに保存するプラグイン。

## インストール

```bash
/plugins install github:kmmm99/chat-log-plugin
```

または、ローカルインストール:

```bash
# ~/.claude/plugins/local/ にクローン
git clone https://github.com/kmmm99/chat-log-plugin ~/.claude/plugins/local/chat-log-plugin
```

## 使用方法

Claude Codeで以下のコマンドを実行します。

```
/chat-log
```

## 機能

- セッション会話の完全な記録
- タイムスタンプ付きファイル名（`chat_yyyymmdd_HHmm.md`）
- セッションサマリーの自動生成
- 機密情報（APIキー、パスワード等）の自動マスキング
- 月次アーカイブ（過去月のログを `old/` フォルダに自動退避）

## 月次アーカイブ機能について

コマンド実行時に、過去月のチャットログを自動的に `old/` フォルダに退避します。

- **保存先**: `~/Documents/claude-outputs/chat-logs/`
- **過去月退避先**: `~/Documents/claude-outputs/chat-logs/old/`

### 動作

1. 当月（`yyyymm`）を算出
2. ベースディレクトリ直下の `chat_*.md` ファイルを確認
3. 当月以外のファイルが存在する場合、`old/` フォルダに移動

これにより、ベースディレクトリには常に当月分のログのみが保持されます。

## 保存形式

```markdown
# チャットログ

- 日時: yyyy-mm-dd HH:mm
- セッション概要: （会話の主題を1行で要約）

---

## 会話内容

### ユーザー
（ユーザーの発言）

### Claude
（Claudeの応答）

---

## セッションサマリー

### 主なトピック
- トピック1

### 実行されたアクション
- アクション1

### 未解決事項・次回への申し送り
- 事項1
```

## セキュリティ

- 機密情報（APIキー、パスワード等）が含まれる場合は `[REDACTED]` に自動置換
- 保存先ディレクトリへのアクセス権限を適切に設定することを推奨


## カスタマイズ

保存先ディレクトリを変更する場合は、`commands/chat-log.md` 内の以下の行を編集:

```markdown
- **ベースディレクトリ**: `~/Documents/claude-outputs/chat-logs/`
- **チャットログ**: `~/Documents/claude-outputs/chat-logs/chat_yyyymmdd_HHmm.md`
- **過去月退避先**: `~/Documents/claude-outputs/chat-logs/old`
```

## ファイル構造

```
chat-log-plugin/
├── .claude-plugin/
│   └── plugin.json
├── commands/
│   └── chat-log.md
└── README.md
```

## ライセンス

MIT License

## 注意事項

### 手動実行について

本プラグインは自動更新機能を持ちません。チャットログを保存する際は、セッション終了前に毎回 `/chat-log` コマンドを実行してください。

### 機密情報のマスキングについて

本プラグインは機密情報（APIキー、パスワード等）の自動マスキング機能を備えていますが、すべての機密情報が確実にマスキングされることを保証するものではありません。保存されたログファイルに機密情報が含まれていないか、ご自身で確認することを強く推奨します。

### 免責事項

本プラグインの使用によって生じたデータの損失、システムの障害、その他いかなる損害についても、作者は一切の責任を負いません。使用は自己責任でお願いいたします。

---

作成日: 2025-01-25  
最終更新日: 2025-01-25  
