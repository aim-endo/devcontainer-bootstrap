# devcontainer-bootstrap (aim-endo fork)

[skipbit/devcontainer-bootstrap](https://github.com/skipbit/devcontainer-bootstrap) を fork し、aim-endo 用の設定を追加したリポジトリです。

## Fork 運用戦略

### ブランチ方針

- **origin/main** にすべての変更を直接コミットする（aim-endo の「完成形」）
- 本家への PR 用ブランチは `upstream/main` から都度切る

### 変更の分類

| 種類 | 置き場 | 本家への還元 |
|---|---|---|
| aim-endo 固有の設定 | origin/main に直接コミット | しない |
| 本家にも入れたい改善 | origin/main にコミット後、cherry-pick で本家に PR | する |

### 本家の変更を取り込む

```bash
git fetch upstream
git merge upstream/main
```

### 本家に変更を提案する

```bash
git fetch upstream
git switch -c proposal/xxx upstream/main
git cherry-pick <commit>
git push origin proposal/xxx
# GitHub 上で skipbit/devcontainer-bootstrap に PR を作成
```

### カスタマイズ用フック

`install.local.sh` を作成すると、`install.sh` の最後に自動で読み込まれます。
fork 固有のツール追加などに使えます。
