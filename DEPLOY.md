# デプロイ手順（5分・Hiraku実行用）

前提: HRKAB アカウント / Vercel（hiraku-abes-projects）接続済み。1リポ=1クローン原則に従い新規リポとして作成。

```bash
cd ~/Documents/Claude/Projects/Claude司令塔/neural-tokyo

git init
git add index.html og.png README.md DEVLOG.md POST_KIT.md SPEC.md
git commit -m "NEURAL TOKYO v1.0 — a city that drives itself, and one car that learns to"

# GitHub CLI（推奨）
gh repo create HRKAB/neural-tokyo --public --source=. --push

# Vercel（どちらか）
# A) ダッシュボード: vercel.com/new → Import HRKAB/neural-tokyo → Deploy（設定不要・静的）
# B) CLI:
npx vercel --prod
```

デプロイ後:
1. 本番URLを確認（推奨カスタム: neural-tokyo.vercel.app — og:image のURLと一致させること。別名になった場合は index.html 内の `https://neural-tokyo.vercel.app/og.png` を2箇所書き換えて再push）
2. **公開設定注意**: company-deck無認証公開の前例（台帳P1）があるため、このリポは意図的にpublic。機密ゼロ確認済（Argus観点自己監査: コード・文言に社内情報なし）
3. X投稿は POST_KIT.md 参照
