# NEURAL TOKYO — X投稿キット v3（実写版・2026-07-05）

投稿前チェック: 全文言Argus観点で自己監査済（機密/未公開IRなし・実写=Google 3D Tiles＝L2走行映像ではないため footage 表記規則対象外・他社中傷なし）。「Turingの技術の再現」とは主張しない。事実のみ。

**ライブURL（本番）**: `https://raw.githack.com/HRKAB/neural-tokyo/main/tokyo-live.html?key=<KEY>`
※ 公開時は自ドメイン（vercel）へ載せ替え、APIキーはHTTPリファラ制限をかける（拡散時のキー抜き取り防止）。動画ファースト戦略で体験版は限定公開。

---

## 1. メイン投稿（EN）

> This is the real Shibuya. Not a model — Google's photorealistic 3D tiles.
>
> I put 1,000 cars on the real roads with real traffic physics, and let one neural network teach itself to drive from the pixels. Live. In a browser tab.
>
> NEURAL TOKYO 🌃
> [動画]

## 2. メイン投稿（JA）

> これは本物の渋谷。モデルじゃなくて、Googleの実写3Dタイル。
>
> その実際の道路に1,000台を走らせて本物の交通物理で動かし、1台のニューラルネットに「映像だけ」で運転を学ばせた。ブラウザのタブの中で、リアルタイムに。
>
> NEURAL TOKYO
> [動画]

## 3. スレッド（EN）

1. **(BRAINショット動画)** "The crimson car isn't scripted. A 38,186-parameter neural net — written from scratch in plain JS — reads 48×16 pixels from its front camera and outputs steering + throttle. Watch the loss fall and autonomy climb, over the real Shibuya."
2. **(THE CROSSING動画)** "1,000 cars, real Shibuya road network from OpenStreetMap, real traffic physics (the Intelligent Driver Model). Cars sit on the actual photogrammetry — ground height comes from raycasting Google's 3D tiles."
3. **(コード/学習ループ図)** "The stack: 3d-tiles-renderer streams Google's tiles → three-mesh-bvh raycasts the ground → the car's POV renders to a tiny texture → a hand-rolled MLP imitates a pure-pursuit teacher with DAgger takeovers. ALVINN did this in 1989 at 30×32. Your browser does it on Google Earth."
4. **(DESCENT静止画)** "No game engine. No server. One HTML file + a Map Tiles key. It runs the real city."
5. "Why? @Turing_inc builds camera-first end-to-end autonomy in Tokyo — intelligence in the brain, not the sensor stack. This is that idea at 1:1,000,000, on the real streets of Shibuya. Code: github.com/HRKAB/neural-tokyo"
6. "Built in one session with Claude. Full write-up + how to reproduce: [記事URL]"

## 4. 動画構成（45秒・本体`?record=45`で自動収録）

本体の6ショット自動ツアーがそのまま尺になる。実機Chromeで `?record=45` を付けて開く → 45秒後に `neural-tokyo-live.webm` が自動ダウンロード → 必要なら冒頭3秒をサムネ映えするDESCENT頂点にトリム。

| 秒 | ショット | 狙い |
|---|---|---|
| 0-3 | DESCENT頂点（実写渋谷が視界に開ける） | 3秒Wow・「これ実写？」 |
| 3-12 | THE CROSSING（1,000台の光の流れ） | スケールと生命感 |
| 12-22 | STREET LEVEL（ビルの谷、交差点） | 実在感の接写 |
| 22-30 | FOLLOW（クリムゾンを追走） | 主役提示 |
| 30-40 | BRAIN（学習パネル・LOSS低下・介入→復帰） | 核心「学んでいる」 |
| 40-45 | ASCEND＋コピー「the real city, in a browser tab」 | CTA |

## 5. スクリーンショット案（4枚）

1. DESCENT頂点（実写渋谷スクランブル俯瞰）＝og.png候補
2. FOLLOW（実写ビル群を背にクリムゾン走行）
3. BRAINパネル全景（実写背景×学習可視化＝「中身が見える」）
4. カメラ入力48×16の拡大（"これが車の見ている全て"）

## 6. 再現記事の構成

1. 完成動画
2. なぜ実写路線に転換したか（手書きポリゴンの限界→実写データが唯一の正答）
3. スタック解説（3d-tiles-renderer / setLatLonToYUp の罠 / BVHレイキャストで路面高 / POVピクセル→純JSバックプロパゲーション / DAgger）
4. Claude活用（Chrome経由でGCP APIキー発行・GitHub運用・隠れタブでも streaming を回すスケジューラ差し替え・スクショ自己検証）
5. 最小再現4ステップ＋拡張（夜化不可の制約・WebGPU・複数都市）
6. 締め：カメラと脳だけで運転は学べるか → Turingの現実へ

## 7. 拡張アイデア（第2波）

- 学習済み重みをURLに埋めて共有 #MyNeuralDriver
- 世界の他都市（NYC/SF/パリ）ワンパラメータ切替
- ドローンFPVショット追加
- Genie系World Modelとの対比記事

## 8. コスト注意（重要）

Photorealistic 3D Tilesは従量課金。日次クォータ13,000req・予算¥30,000アラート設定済（2026-07-05）。**拡散＝閲覧増＝課金増**なので、Xには動画を貼り、ライブ体験版は「触りたい人向け」に限定的に案内する。バズ規模次第でキーのリファラ制限・上限引き下げを即応する。
