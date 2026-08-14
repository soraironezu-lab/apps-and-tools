# ChatSwitch 0.1.0-beta.1

ChatSwitchの最初の公開β版です。macOS上でCodexの複数チャットの状態を見渡し、次に戻るチャットへ切り替えられます。

## ダウンロードファイル

- ファイル名: `ChatSwitch-0.1.0-beta.1.zip`
- サイズ: `374,194 bytes`
- SHA-256: `056c08d9746f2e9befa82b94f5faf0219c88b8716c27b74ea18e424a16377247`
- VirusTotal: [検出なし（同じSHA-256）](https://www.virustotal.com/gui/file/056c08d9746f2e9befa82b94f5faf0219c88b8716c27b74ea18e424a16377247)

## 重要: Developer ID未署名・未公証のβ版です

このZIPに含まれるアプリは、アプリ識別のためのアドホック署名のみで、Developer ID署名・Appleの公証を行っていません。公式Releaseから入手した場合だけ利用してください。初回起動時にmacOSの警告が表示される場合があります。

起動を一度試した後、「システム設定 → プライバシーとセキュリティ → このまま開く」から起動できます。警告内容を理解できない場合は起動しないでください。

## 導入手順

1. `ChatSwitch-0.1.0-beta.1.zip`をダウンロードして展開する。
2. `ChatSwitch.app`を`Applications`へコピーする。
3. ChatSwitchを開く。
4. 初回起動時に通知許可ダイアログが出ない場合、または通知が届かない場合は、「システム設定 → 通知 → ChatSwitch」で「通知を許可」をオンにする。
5. 「設定 → Codex連携」で、自動設定または手動設定のどちらか一方を選ぶ。
6. 追加前に、対象の6イベントと完全な実行コマンドを確認する。
7. Codexで`/hooks`を開き、ChatSwitchの6項目を目視確認してから信頼する。
8. Codexで作業を開始し、ChatSwitchへの反映を確認する。

自動設定では、Hookの追加前に`~/.codex/hooks.json`のバックアップが作られます。手動設定では、同梱の`ChatSwitch-Hooks手動設定.md`とアプリ内に正確なJSON、確認、信頼、削除の手順を表示します。

## 主な機能

- Codexチャット一覧と状態表示
- 既存チャットの再開と、同じ作業フォルダでの新規チャット開始
- プロジェクト単位のチャット表示・検索
- macOS通知、メニューバー、Dockバッジ
- 任意のDiscord Webhook通知

## 既知の制約

- Apple Silicon搭載Mac、macOS 26.5以降とCodex環境が必要です。Intel Macは対象外です。
- 即時反映にはCodex Hooksの信頼が必要です。
- Claude Code連携、プロンプト送信、エージェント起動、自動更新は未実装です。
- 短時間の状態変化は反映できない場合があります。
- Hooksを設定していない場合でも、一覧画面に「Hooksで即時更新」と表示されます。Hooks未設定時は即時更新が有効になっていることを示す表示ではありません。
- 通知設定ウィンドウが、ほかのアプリのウィンドウの背面に開く場合があります。表示されないときは、Dockまたはアプリ切り替えでChatSwitchを選択してください。
- ChatSwitch内の通知設定とmacOSの通知許可は別です。初回起動時に許可ダイアログが表示されない場合があるため、通知が届かないときは「システム設定 → 通知 → ChatSwitch」を確認してください。許可がオフでもアプリ内の一覧と未確認状態は更新されます。
- VoiceOverでの主要操作はこのβ版では対応していません。VoiceOver利用が必要な方には、現時点では利用をおすすめしません。

このβ版には、配布リポジトリの[ChatSwitch β版利用条件](https://github.com/soraironezu-lab/apps-and-tools/blob/main/chatswitch/TERMS.md)に記載する個人利用・評価目的の利用条件が適用されます。

不具合や要望は[Issues](https://github.com/soraironezu-lab/apps-and-tools/issues)へお願いします。Webhook URL、チャット本文、作業パスなどの個人情報は投稿しないでください。
