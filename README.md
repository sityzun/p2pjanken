# ローカルゲームPWA v1

## 仕組み

GitHub Pagesに置くのは「ゲームエンジン」です。

実際のゲームデータはユーザーのスマホ/PCのフォルダに置きます。

    janken/
    ├── game.json
    └── images/
        ├── rock.svg
        ├── paper.svg
        └── scissors.svg

PWAで「ゲームフォルダを選択」を押すとgame.jsonを読み込み、そこに書かれた画像をローカルフォルダから読み込んでゲームを構築します。

## サンプル

このZIPの `sample_game` フォルダをそのまま選択してください。

## GitHub Pages

ルートにある `index.html`, `manifest.json`, `sw.js` をGitHub Pagesへ置きます。

## 注意

フォルダはユーザーが明示的に選択した場合だけ読み込みます。
ブラウザが勝手にスマホのストレージ全体を読むことはできません。

このv1はCPU対戦です。次の段階で、このゲームデータをWebRTC経由で相手へ渡すことができます。
