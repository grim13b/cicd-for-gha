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

## かんたんな解説

### AWS の認証

Github Actions から接続する AWS への Credential は OIDC を利用しています。  
AWS の設定方法は公式の解説を確認してください。

ops/cfn/oidc.yml は CloudFormation で作成する場合の参考例です。  
IAM ROLE の必要な権限については適宜必要に応じて変更が必要です。

### location-deploy.yml について

特定の Branch に Push された場合に起動して S3 に Artifact を Sync する例です。
開発、ステージング、プロダクションとすべて AWS アカウントが異なる環境での利用を目的にしているため、一部ブランチの解釈やデプロイ先 AWS アカウント固有の情報を取得するために一部冗長な記述があります。
