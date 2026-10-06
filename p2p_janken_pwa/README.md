# P2Pじゃんけん PWA

## 構成
- PWA: HTML/CSS/JavaScript
- ローカル大容量データ: File System Access API
- P2P通信: WebRTC RTCDataChannel
- シグナリング: Offer/Answerを手動コピーしてLINE等で交換
- サーバー側DB: なし

## 起動
PWA / Service Worker / File System Access API は安全なコンテキスト(HTTPS)が必要です。
GitHub Pages / Cloudflare Pages等のHTTPS静的ホスティングで配信してください。

## 接続
1. Aで「Offerを作る」
2. 表示されたJSONをLINE等でBへ送る
3. BでJSONを貼って「B: Offerを読み込む」
4. Bに生成されたAnswer JSONをAへ送る
5. AでAnswerを貼って「A: Answerを読み込む」
6. 接続後、じゃんけん開始

## ローカルフォルダ
「フォルダを選択」で、ユーザーが明示的に選んだゲームデータフォルダを読み取ります。
ブラウザは端末内の任意フォルダを勝手には読みません。

## 注意
この試作は `iceServers: []` なので、NAT越えが必要なインターネット環境では接続できない場合があります。
STUN/TURNを使えば接続成功率を上げられますが、その場合は外部サーバーを利用します。
