# aws-deploy-factory

このリポジトリは、AWSを使ったインフラ構成やソリューションを簡単にデプロイできるためのリソースを提供しています。CloudFormationやCDKを使って、紹介している構成を簡単にデプロイできるようにしています。

## 目的

- AWSの勉強目的で、まずは形を作ってそこから学ぶことができます。
- テンプレートやソースコードも公開しているので、要件に似たソリューションがあれば、カスタマイズして利用することも可能です。

## 作成できる構成例
- ![ec2-linux-with-rds-alb-public-subnet](https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/a5dad8e3-4381-4f03-bf64-d656ac9fcc94)
- ![fsx-windows-single-ssd](https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/70b51632-ef79-4018-b480-0c6b9fa84f11)

## 利用方法

各ソリューションのディレクトリに移動し、README.mdの手順に従ってデプロイしてください。

## 前提条件

- AWSアカウントにログインできること。そして、Administrator権限（もしくはそれに近い権限）を持っていること。
- 必要なツールやソフトウェア: なし

## 注意事項

- 無料枠を超えた場合、無料枠外の場合のAWS利用料は利用者負担となります。不要な環境は必ず削除してください（削除手順は別途記載しています）。
- デプロイされた環境のセキュリティは利用者の責任で管理してください。
- 本番環境へのデプロイは、十分なテストと検証の後に行ってください。

## トラブルシューティング

- デプロイ時にエラーが発生した場合は、CloudFormationのスタックイベントやログを確認して原因を特定してください。
- 作成されたリソースが意図した通りに動作しない場合は、各サービスのドキュメントを参照して設定を見直してください。

## ライセンス

このリポジトリ内のテンプレートは、非商用・商用利用を問わず自由に使用できます。カスタマイズして公開することも可能です。

## バグ報告、機能要求

バグ報告、機能要求、プルリクエストなどでご連絡ください。

## 免責事項

このリポジトリで提供されるテンプレートやソースコードは、現状のまま提供されます。使用によって生じたいかなる損害に対しても、作者は責任を負いません。

## 連絡先

ご質問やご意見がある場合は、Issueを作成してください。

## 一覧
- [VPC](https://github.com/mirakuuu/aws-deploy-factory/tree/main/00_vpc)
- [WordPress](https://github.com/mirakuuu/aws-deploy-factory/tree/main/wordpress)
- [Active Directory](https://github.com/mirakuuu/aws-deploy-factory/tree/main/active-directory)
- [FSx for Windows File Server](https://github.com/mirakuuu/aws-deploy-factory/tree/main/fsx-windows)