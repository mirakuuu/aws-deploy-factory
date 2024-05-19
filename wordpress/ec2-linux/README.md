# WordPress on Sigle EC2

このテンプレートを使用すると、WordPress と MySQL がインストールされた WordPress を構築できます。

## デプロイする構成
![ec2-linux](https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/983c0d97-f029-4c6c-b45a-5a5953624929)

## 前提条件

以下のURLからVPCのデプロイを行ってください。パラメータはデフォルトのままでOKです。デプロイ済みの場合は、そのまま流用できます。
[VPCスタックのデプロイ](https://github.com/mirakuuu/aws-deploy-factory/tree/main/00_vpc)

## 利用方法

1. AWSアカウントにログインした状態で、以下の`スタックの作成`をクリックしてください。
2. CloudFormationの画面に遷移します。
3. 必要に応じてパラメータを変更して、スタックを作成してください。

[<img src="https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/c2d15fc9-8371-479b-94b0-4e433118e12e">](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create?stackName=VpcStack&templateURL=https://aws-deploy-factory-ap-northeast-1.s3.ap-northeast-1.amazonaws.com/00_vpc/vpc.yml)

## パラメータ

### YourIP

- 説明: WordPressへのアクセス制限（IP制限）をするアドレスを入力します。デフォルトは全IPに対して外部公開します。自分のIPが不明な場合は[こちら](https://www.cman.jp/network/support/go_access.cgi)から確認してください。/32 などのプレフィックスの入力を忘れないようにしてください。
- デフォルト値: 0.0.0.0/0

### MySQLAdminPassword

- 説明: WordPress用MySQLユーザーのパスワード

### InstanceType

- 説明: WordPress用ののEC2インスタンスタイプ
- デフォルト値: t2.micro

## WordPressのインストール方法



## 削除方法

作成したCloudFormationスタックを削除してください。スタックを削除すると、関連するリソースも自動的に削除されます。