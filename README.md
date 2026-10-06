# P2Pじゃんけん v2.1

GitHub Pages + スマホ2台 + LINE等でOffer/Answerを手動交換して接続する診断版です。

## 今回の修正

- Google / Cloudflare のSTUNサーバーを追加
- Offer/Answerを作る前にICE候補を収集
- ICE gathering / ICE connection / Peer connection / DataChannelの状態を画面表示
- Offer/Answerの種類をチェック
- 接続失敗時に原因の手掛かりを診断欄へ表示
- DataChannel接続後に `hello` を送って相互接続を確認
- v2のじゃんけん・フォルダ選択・ファイル転送機能は維持

## GitHub Pages

1. ZIPを展開
2. 中身の `index.html`, `manifest.json`, `sw.js`, `README.md` をGitHubリポジトリのルートへ置く
3. GitHubの Settings → Pages
4. Deploy from a branch
5. Branch: `main` / Folder: `/ (root)`
6. 発行された `https://ユーザー名.github.io/リポジトリ名/` をスマホ2台で開く

## 接続手順

### A側
1. 「A: Offer作成」
2. JSONを全部コピーしてBへLINE等で送る

### B側
1. Aから受け取ったJSONを貼る
2. 「B: Offer読み込み」
3. 表示されたAnswer JSONを全部コピーしてAへ送る

### A側
1. Bから受け取ったAnswer JSONを貼る
2. 「A: Answer読み込み」
3. 数秒待つ
4. `接続済み（P2P）` になれば成功

## 接続診断

- `ICE gathering: complete`
  - Offer/AnswerへICE候補が入り終わった状態
- `ICE connection: checking`
  - 接続経路を確認中
- `ICE connection: connected` / `completed`
  - ICE経路が成立
- `DataChannel OPEN`
  - 実際のP2Pデータ通信が開始
- `ICE FAILED`
  - 直接P2P経路を作れなかった可能性あり

## 重要

STUNを使っても、すべてのネットワークで直接P2P接続できるわけではありません。
特に携帯キャリア網や厳しいNATではTURNリレーが必要になることがあります。

この版は「アプリデータをサーバーへ保存しない」ことを優先しており、TURNサーバーは使っていません。

また、ファイル転送は試作版なので100MB以下を推奨します。受信側はメモリ上でBlobを組み立ててダウンロードリンクを作ります。
