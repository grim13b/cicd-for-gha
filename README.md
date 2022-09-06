# cicd-for-gha
GithubActionsでCI/CDを実現するサンプルです。

## 事前準備
このサンプルを実行するために事前準備として repository の Actions Secrets に設定が必要です。

| # | Param name | note                     |
|:-:|:-----------|:-------------------------|
| 1 | DEV-AWSARN | 開発環境用のRoleARN      |
| 2 | DEV-S3URI  | 開発環境用のデプロイ先S3 |
| 3 | STG-AWSARN | ステージング環境用       |
| 4 | STG-S3URI  | ステージング環境用       |
| 5 | PRD-AWSARN | プロダクション環境用     |
| 6 | PRD-S3URI  | プロダクション環境用     |
