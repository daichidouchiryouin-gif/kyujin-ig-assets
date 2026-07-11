# kyujin-ig-assets（求人IGカルーセル画像 公開ホスティング）

求人Instagramアカウント向けカルーセル投稿画像の公開ホスティング用リポジトリ。
`kyujin-ig-cloud`（投稿ロジック本体・private）から参照される。

## 仕組み
- `feed/NN_slug/1.png, 2.png, ...` に画像を配置（`kyujin-ig-cloud` の `build_feed_manifest.py` が同期・push する）
- 画像は [jsDelivr](https://www.jsdelivr.com/) 経由でコミットSHA固定URLとして配信される
  - 例: `https://cdn.jsdelivr.net/gh/daichidouchiryouin-gif/kyujin-ig-assets@<commit-sha>/feed/01_xxx/1.png`
  - SHA固定なのでキャッシュ事故がなく、画像を差し替えても常に新しいURLになる
- このリポジトリを直接手編集する運用は想定していない。画像の追加・更新は `kyujin-ig-cloud` 側の `build_feed_manifest.py` から行う。

## 関連リポジトリ
- `daichidouchiryouin-gif/kyujin-ig-cloud`（private）… 投稿ロジック本体・manifest生成スクリプト
