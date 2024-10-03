# usecase1

## changesetsセットアップ(初回のみ)

1. パッケージインストール
```sh
$ npm install -D @changesets/changelog-github @changesets/cli
```

2. changesetsセットアップ
```sh
$ npx changeset init
```

3. config.json修正
```json
  "changelog": "@changesets/cli/changelog",
```

- ↑を↓に書き換えます。
- CHANGELOGに、対象のPRへのリンクと変更セットを追加したユーザーへの感謝メッセージを含むようchangelogを変更します。
```json
  "changelog": ["@changesets/changelog-github", { "repo": "kamaD-y/changesets_monorepo_test" }],
```

## 機能追加/修正時の対応手順
1. 機能開発を行い、commitを作成します
2. changesetファイルを生成します
```sh
$ cd usecases/usecase1
$ npx changeset
# バージョンアップを行いたくない場合は、上記コマンドは不要です。
# もしくは、npx changeset --emptyとすることで、空のchangesetファイルを生成することもできます。
# https://github.com/changesets/changesets/blob/main/packages/cli/README.md#add
```
3. changesetファイルをcommitします
4. リモートブランチへpushしPRを作成します
5. PRレビューを行います
6. リリースを行うまでにその他開発する機能がある場合は、引き続き開発を行います(1へ)
7. 開発を終え、リリースを行います
8. リリース後、蓄積されたchangesetファイルをもとにCHANGELOGを作成・更新します
```sh
$ npx changeset version
```