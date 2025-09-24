# 学生生活効率化！課題・スケジュール管理ツール


## 💡 概要
大学生活における課題や予定の管理を効率化するために開発したPython製ツールです。タスクの登録・管理に加え、Googleカレンダー/ToDoリストとの連携、LINEによるリマインダー通知機能を備えています。

## 🏃‍♂️ 開発の背景・目的 
大学の授業や研究活動において、複数の課題や締め切りが並行して発生し、タスクの抜け漏れが頻発するという課題がありました。特に、異なるツール（手帳、カレンダーアプリなど）で管理していたため、情報が一元化されていないことが問題だと考えました。
そこで、プログラミング学習の一環として、これらの情報を一元管理し、普段利用しているGoogleサービスやLINEと自動で連携することで、自身の課題を解決する実用的なツールを開発することに挑戦しました。

## ✨ 機能一覧
- 対話型タスク管理: コンソール上でタスクの追加・一覧表示が可能
- 柔軟な日時入力: 「10/25 15:00」のような自然な形式で日時を登録可能
- Googleカレンダー連携:登録したタスクを開始・終了時刻付きでカレンダーに自動で予定として追加
- Google ToDoリスト連携: 登録したタスクを期日付きでToDoリストに自動で追加
- LINEリマインダー: 締め切りが24時間以内に迫ったタスクを、LINEで自動通知

## 🛠️ 使用技術
- 言語: Python 3
- 主要ライブラリ:
  - `google-api-python-client`, `google-auth-oauthlib`: Google API連携
  - `requests`: LINE Messaging API連携
- API:
  - Google Calendar API
  - Google Tasks API
  - LINE Messaging API
- 開発環境: Google Colaboratory

## 🚀 使い方
1.  APIキーの準備:
    - Google Cloud Platformにて、`Google Calendar API`と`Google Tasks API`を有効化し、認証情報（`client_secret.json`）をダウンロードします。
    - LINE DevelopersにてMessaging APIチャネルを作成し、`チャネルアクセストークン`とご自身の`ユーザーID`を取得します。
2.  Colabでの設定:
    - このノートブックを開き、Colabのシークレット機能（🔑）に以下の3つの情報を登録します。
      - `GOOGLE_CLIENT_SECRET_JSON`: `client_secret.json`の中身全体
      - `LINE_CHANNEL_ACCESS_TOKEN`: あなたのチャネルアクセストークン
      - `LINE_USER_ID`: あなたのユーザーID
3.  実行:
    - 上から順にセルを実行します。Google認証が求められた場合は、画面の指示に従い認証を完了させてください。
    - 対話型メニューが表示されたら、指示に従ってツールを操作します。

## 🔧 苦労した点・学んだこと
外部APIとの認証連携:GoogleのOAuth 2.0認証では、Colabのサーバー環境特有のエラーに何度も直面しました。`run_local_server`が使えない問題や、ライブラリのバージョンによる挙動の違いなどを、公式ドキュメントやエラーメッセージを読み解きながら、最終的に`run_console`を応用した手動の認証フローを実装することで解決しました。