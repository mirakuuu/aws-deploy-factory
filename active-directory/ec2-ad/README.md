# Active Directory on EC2

このテンプレートを使用すると、Windows Server 2022 上に Active Directory をインストールした EC2 インスタンスを構築できます。

## デプロイする構成

![active-directory](https://github.com/username/repo/assets/active-directory.png)

## 前提条件

以下のURLからVPCのデプロイを行ってください。パラメータはデフォルトのままでOKです。デプロイ済みの場合は、そのまま流用できます。

- [VPCスタックのデプロイ](https://github.com/username/repo/tree/main/00_vpc)

## 利用方法

1. AWSアカウントにログインした状態で、以下の`スタックの作成`をクリックしてください。

2. CloudFormationの画面に遷移します。

3. 必要に応じてパラメータを変更して、スタックを作成してください。

[<img src="https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/c2d15fc9-8371-479b-94b0-4e433118e12e">](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create?stackName=ADStack&templateURL=https://aws-deploy-factory-ap-northeast-1.s3.ap-northeast-1.amazonaws.com/active-directory/ec2-ad/ec2-ad.yml)

## パラメータ

### YourIP

- 説明: Active Directory EC2 インスタンスへの RDP アクセス制限（IP制限）をするアドレスを入力します。デフォルトは全IPに対して外部公開します。自分のIPが不明な場合は[こちら](https://www.cman.jp/network/support/go_access.cgi)から確認してください。/32 などのプレフィックスの入力を忘れないようにしてください。
- デフォルト値: 0.0.0.0/0

### InstanceType

- 説明: Active Directory 用の EC2 インスタンスタイプ
- デフォルト値: t2.micro

### WindowsAdministratorPassword  

- 説明: EC2 Administrator ユーザーのパスワード。8〜64文字で、数字、大文字、小文字、特殊文字のうち3つ以上を含む必要があります。

### DomainName

- 説明: Active Directory のドメイン名（FQDN）
- デフォルト値: example.com

## Active Directory への接続方法

- [スタック一覧](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks)にアクセスして、表示される ActiveDirectoryStack をクリックして、スタックの詳細を表示します。  

- **出力** タブをクリックして、**ADEIP** に表示されているパブリック IP アドレスをコピーします。

- Remote Desktop などの RDP クライアントを使用して、コピーした IP アドレスに接続します。  

- ユーザー名に `Administrator`、パスワードに **WindowsAdministratorPassword** で入力したパスワードを使用してログインします。

## 削除方法

作成した CloudFormation スタックを削除してください。スタックを削除すると、関連するリソースも自動的に削除されます。

## トラブルシューティング 

- 作成中に CloudFormation で「No export named VPC1ID found. Rollback requested by user」というエラーが表示されて、作成が失敗した場合
  - 「前提条件」を確認して、VPC スタックのデプロイをまず行ってください。  
  - その後、ActiveDirectoryStack を一度削除して、もう一度、スタックの作成を行ってください。