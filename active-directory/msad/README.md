# MSAD (AWS Directory Service)

このテンプレートを使用すると、Directory Service を使った Active Directory 環境(MSAD)を作成できます。

## デプロイする構成

![MSAD](https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/518b7a08-5d78-4522-b112-0951ffff231d)

## 前提条件

以下のURLからVPCのデプロイを行ってください。パラメータはデフォルトのままでOKです。デプロイ済みの場合は、そのまま流用できます。

- [VPCスタックのデプロイ](https://github.com/username/repo/tree/main/00_vpc)

## 利用方法

1. AWSアカウントにログインした状態で、以下の`スタックの作成`をクリックしてください。

2. CloudFormationの画面に遷移します。

3. 必要に応じてパラメータを変更して、スタックを作成してください。

[<img src="https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/c2d15fc9-8371-479b-94b0-4e433118e12e">](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create?stackName=MSADStack&templateURL=https://aws-deploy-factory-ap-northeast-1.s3.ap-northeast-1.amazonaws.com/active-directory/msad/msad.yml)

## パラメータ

### ADPassword  

- 説明: MSADの管理ユーザー admin のパスワード。8〜64文字で、数字、大文字、小文字、特殊文字のうち3つ以上を含む必要があります。

### DomainName

- 説明: Active Directory のドメイン名
- デフォルト値: example.com

## 削除方法

作成した CloudFormation スタックを削除してください。スタックを削除すると、関連するリソースも自動的に削除されます。

## トラブルシューティング 

- 作成中に CloudFormation で「No export named VPC1ID found. Rollback requested by user」というエラーが表示されて、作成が失敗した場合
  - 「前提条件」を確認して、VPC スタックのデプロイをまず行ってください。  
  - その後、ActiveDirectoryStack を一度削除して、もう一度、スタックの作成を行ってください。
- 「ValidationError: Parameter ADPassword failed to satisfy constraint: The password must be between 8 and 64 characters long and satisfy at least 3 of the following conditions contains a number, an uppercase letter, a lowercase letter, or a special character (non-alphanumeric).」と表示されてスタックが作成できない場合
  - ADPassword が 8〜64文字で、数字、大文字、小文字、特殊文字のうち3つ以上を含んでいることを確認してください。
