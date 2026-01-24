# claude-chat-log

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

Claude Codeで以下のコマンドを実行:

```
/chat-log
```

## 機能

- セッション会話の完全な記録
- タイムスタンプ付きファイル名（`chat_yyyymmdd_HHmm.md`）
- セッションサマリーの自動生成
- 機密情報（APIキー、パスワード等）の自動マスキング

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
```

## ファイル構造

```
claude-chat-log/
├── .claude-plugin/
│   └── plugin.json
├── commands/
│   └── chat-log.md
└── README.md
```

## ライセンス

MIT License
