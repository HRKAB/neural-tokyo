# NEURAL TOKYO — X投稿キット（2026-07-05）

投稿前チェック: 本キットの全文言はArgus観点で自己監査済（機密なし・未公開IRなし・実写映像なし＝L2表記ルール対象外・他社言及なし）。「Turingの技術の再現」とは一切主張しない文言に統一。

---

## 1. メイン投稿（EN — グローバル狙い）

> I asked Claude to build something that would normally take a year.
>
> One HTML file. No server. No ML library.
>
> 1,200 cars self-organize with real traffic physics — and one car learns to drive from raw pixels, with a neural network training live in your browser.
>
> NEURAL TOKYO 🌃
> [URL]

（動画添付：下記構成案A）

## 2. メイン投稿（JA）

> Claudeに「普通なら開発に1年かかるもの」を頼んだら、これが返ってきた。
>
> HTMLファイル1枚。サーバーなし。MLライブラリなし。
>
> 1,200台が本物の交通物理で自己組織化する夜の東京で、1台だけ、生のカメラピクセルからニューラルネットが運転を学んでいく。
>
> NEURAL TOKYO
> [URL]

## 3. スレッド構成（EN、リプライツリー）

1. **(動画: BRAINモード30秒)** "The red car is not scripted. A 38,186-parameter MLP — written from scratch in plain JS — reads 48×16 grayscale pixels from its front camera and outputs steering + throttle. You watch the loss fall and the autonomy meter climb, live."
2. **(動画: スライダー操作15秒)** "Drag one slider and phantom traffic jams condense out of nothing. That's not animation — it's the Intelligent Driver Model (the standard model in traffic science). Human drivers = longer headways + 0.7s reaction delay. That's all it takes."
3. **(スクショ: 学習ループ図/コード)** "The trick is 4 steps: render the car's POV to a tiny texture → read pixels → hand-rolled backprop → imitate a classical controller, with DAgger-style takeovers when the student drifts. ALVINN did this in 1989 with 30×32 pixels. Your browser can do it today."
4. **(スクショ: CITY俯瞰)** "Everything is generated: the city, the window lights, the neon, the rain. Seeded RNG — everyone sees the same Tokyo. 6 draw calls for all 1,200 cars."
5. "Why this shape? @Turing_inc is building camera-first end-to-end autonomy in Tokyo — the bet that driving intelligence lives in the brain, not the sensor stack. This is that idea at 1:1,000,000 scale. Code: [GitHub URL]"
6. "Built in one session with Claude. Prompting approach + full write-up: [記事URL]"

## 4. 動画構成案A（メイン添付・45秒・16:9）

| 秒 | 画 | 意図 |
|---|---|---|
| 0-3 | タイトルカード→空撮落下（イントロそのまま） | 3秒Wow・スケール提示 |
| 3-12 | CITY俯瞰オービット、光の川 | 「生きている都市」 |
| 12-20 | HUMAN DRIVERSスライダー 0→70%、渋滞が生まれる（JAM INDEX上昇を画面内で見せる） | 科学の驚き・参加可能性 |
| 20-24 | CHASE：クリムゾンの1台に急降下 | 主役の提示 |
| 24-38 | BRAIN：カメラ入力→発火→LOSS低下→AUTONOMY上昇、介入→復帰 | 核心。「学んでいる」 |
| 38-45 | 引きの俯瞰＋コピー「one HTML file / no server / no ML library」→URL | 再現性の一撃・CTA |

撮影: 実機Chrome最大化、`?shot=` パラメータでカメラ固定可。QuickTime画面収録→1080p書き出し。

## 5. スクリーンショット案（静止画4枚）

1. CITY俯瞰（og.png と同構図・光の川）
2. BRAINモード全景（右パネル込み＝「中身が見える」ことが伝わる）
3. カメラ入力 48×16 の拡大（"これが車が見ている全て"）
4. スライダー0%と70%の比較2連結（渋滞の発生）

## 6. 再現記事の構成案（note / Zenn / X長文）

1. 掴み：完成動画
2. なぜ作ったか：Genie 3時代に「学習過程そのもの」を見せたい／Turingの頭脳優位思想
3. アイデア発散20案→評価表→NEURAL TOKYO決定の思考過程（DEVLOG転載）
4. 技術解説：都市生成／IDM／無信号交差点／純JSバックプロパゲーション／DAggerループ（コード断片付き）
5. Claudeへのディレクション術：QAループ（スクショ自己検証）、車線が逆になったバグと座標系検証、視覚品質の反復
6. 最小再現（4ステップ）と拡張アイデア
7. 締め：カメラと脳だけで運転は学べるか → Turingの現実のチャレンジへ接続

## 7. 拡張アイデア（バズ第2波用）

- 「あなたのブラウザで学習したネットの重みをURLに埋めて共有」→ #MyNeuralDriver
- 学習済み vs 未学習のレース動画
- WebGPU化で10,000台
- ハンドトラッキングで人間介入（案Bの吸収）
- 実在の東京の道路グラフ（OSM）読み込み

## 8. 投稿タイミング推奨

火〜木の日本時間22-24時（US西海岸朝・欧州夕方の重複帯）。メインはENを@AbeHirakuから、JA引用RTで日本語圏を回収。
