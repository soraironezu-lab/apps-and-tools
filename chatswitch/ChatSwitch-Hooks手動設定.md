# ChatSwitch Codex Hooks 手動設定

この手順は、ChatSwitchに設定ファイルを変更させず、自分で追加内容を確認してから`~/.codex/hooks.json`へ設定したい人向けです。Hooksは任意機能であり、設定しなくてもチャット一覧とチャットへの復帰は利用できます。

## 事前確認

1. `ChatSwitch.app`を`Applications`フォルダへコピーしてから起動します。
2. ChatSwitchの「設定 → Codex連携 → 手動設定の手順を見る…」を開きます。
3. 自動設定が有効なら、先に「Hooksを削除…」で自動設定分を削除します。自動設定と手動設定は同時に使いません。
4. `~/.codex/hooks.json`が存在する場合は、編集前に別名でコピーして保管します。

## 変更せずに設定内容を表示する

アプリ内の手動設定画面でJSONを確認できます。ターミナルから確認する場合は、次のコマンドを実行します。

```sh
'/Applications/ChatSwitch.app/Contents/MacOS/ChatSwitch' --print-codex-hooks
```

このコマンドはJSONを標準出力へ表示するだけで、`hooks.json`やChatSwitchの保存データを変更しません。

## 追加する設定

ChatSwitchを標準の`/Applications`へ置いた場合、追加内容は次のとおりです。アプリを別の場所へ置いた場合は、アプリ内または上記の表示コマンドで実際のパスを確認してください。

```json
{
  "hooks" : {
    "PermissionRequest" : [
      {
        "hooks" : [
          {
            "command" : "'/Applications/ChatSwitch.app/Contents/MacOS/ChatSwitch' --receive-codex-hook",
            "timeout" : 5,
            "type" : "command"
          }
        ]
      }
    ],
    "PostToolUse" : [
      {
        "hooks" : [
          {
            "command" : "'/Applications/ChatSwitch.app/Contents/MacOS/ChatSwitch' --receive-codex-hook",
            "timeout" : 5,
            "type" : "command"
          }
        ]
      }
    ],
    "PreToolUse" : [
      {
        "hooks" : [
          {
            "command" : "'/Applications/ChatSwitch.app/Contents/MacOS/ChatSwitch' --receive-codex-hook",
            "timeout" : 5,
            "type" : "command"
          }
        ]
      }
    ],
    "SessionStart" : [
      {
        "hooks" : [
          {
            "command" : "'/Applications/ChatSwitch.app/Contents/MacOS/ChatSwitch' --receive-codex-hook",
            "timeout" : 5,
            "type" : "command"
          }
        ]
      }
    ],
    "Stop" : [
      {
        "hooks" : [
          {
            "command" : "'/Applications/ChatSwitch.app/Contents/MacOS/ChatSwitch' --receive-codex-hook",
            "timeout" : 5,
            "type" : "command"
          }
        ]
      }
    ],
    "UserPromptSubmit" : [
      {
        "hooks" : [
          {
            "command" : "'/Applications/ChatSwitch.app/Contents/MacOS/ChatSwitch' --receive-codex-hook",
            "timeout" : 5,
            "type" : "command"
          }
        ]
      }
    ]
  }
}
```

上のJSONで`hooks.json`全体を置き換えないでください。既存のトップレベル設定と`hooks`内のイベントを残し、6イベントの配列へChatSwitchのグループを追加します。同じコマンドがすでにある場合は重複して追加しません。

## Codexで確認して有効にする

1. Codexで`/hooks`を開きます。
2. 6イベントすべてについて、イベント名と実行コマンドが上記と一致することを目視確認します。
3. 内容に納得した項目だけを信頼します。
4. Codexで新しい作業を1件開始し、ChatSwitchで作業中・確認待ち・完了が反映されることを確認します。

Hook受信時にChatSwitchが一時保存するのは`session_id`、`turn_id`、`hook_event_name`、`tool_name`だけです。プロンプト本文、ツール入力・出力、作業フォルダはHookイベントとして保存しません。

## 手動で削除する

手動追加した項目は、ChatSwitchの「Hooksを削除…」では削除されません。`~/.codex/hooks.json`を開き、上記の`--receive-codex-hook`コマンドを持つ6イベントのハンドラーだけを削除します。ほかのコマンドを含むグループや、ChatSwitch以外のHooksは残してください。空になったChatSwitch用グループは削除できます。

削除後にCodexで`/hooks`を開き、ChatSwitchの6項目がなく、ほかのHooksが残っていることを確認します。

## 注意

- `ChatSwitch.app`を移動・改名するとコマンドのパスが無効になります。移動後は新しい表示内容に合わせて6項目を更新し、Codexで再確認してください。
- JSONとして読み取れない状態になった場合は保存せず、事前バックアップへ戻してからやり直してください。
- 手動設定ではChatSwitchによる自動バックアップは作成されません。
