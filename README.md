# WebRTC P2P 接続テスト

## 目的
WebRTCの接続部分だけを確認する最小テストです。

## GitHub Pages
index.html / manifest.json / sw.js をリポジトリのルートに置いてGitHub Pagesで公開してください。

## 手順
### A
1. 「Offerを作成」
2. Offer全文をBへ送る

### B
1. Offerを貼る
2. 「Offerを読み込んでAnswerを作る」
3. Answer全文をAへ送る

### A
1. Answerを貼る
2. 「Answerを設定」
3. `P2P接続成功！` になるか確認

成功後はPing送信を押して、相手側に受信が表示されればDataChannelも成功です。

## 注意
STUNだけを使っています。STUNで直接経路を作れないネットワークではICE FAILEDになります。
