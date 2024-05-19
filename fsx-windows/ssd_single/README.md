# Amazon FSx for Windows File Server (Single AZ, SSD)

このテンプレートを使用すると、Amazon FSx for Windows File Server を Single AZ 構成で SSD ストレージを使用して構築できます。

## デプロイする構成

![fsx-windows-single-ssd](https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/70b51632-ef79-4018-b480-0c6b9fa84f11)

## 前提条件

以下のスタックを事前にデプロイしておく必要があります。

- [VPCスタックのデプロイ](https://github.com/mirakuuu/aws-deploy-factory/tree/main/00_vpc)
- [Active Directory スタックのデプロイ](https://github.com/mirakuuu/aws-deploy-factory/tree/main/active-directory/ec2-ad)

## 利用方法

1. AWSアカウントにログインした状態で、以下の`スタックの作成`をクリックしてください。

2. CloudFormationの画面に遷移します。

3. 必要に応じてパラメータを変更して、スタックを作成してください。

[<img src="https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/c2d15fc9-8371-479b-94b0-4e433118e12e">](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create?stackName=FSxWinSSDSingleStack&templateURL=https://aws-deploy-factory-ap-northeast-1.s3.ap-northeast-1.amazonaws.com/fsx-windows/ssd_single/ssd_single.yml)


## パラメータ

### StorageCapacity

- 説明: FSx for Windows のストレージ容量（GB）。32GB 以上である必要があります。
- デフォルト値: 32

### ThroughputCapacity

- 説明: FSx for Windows のスループット容量（MB/s）
- 許容値: 8, 16, 32, 64, 128  
- デフォルト値: 8

## FSx for Windows へのアクセス方法

(作成中)

## 削除方法

作成した CloudFormation スタックを削除してください。スタックを削除すると、関連するリソースも自動的に削除されます。

## トラブルシューティング

- 作成中に CloudFormation で「No export named VPC1ID found. Rollback requested by user」というエラーが表示されて、作成が失敗した場合
  - 「前提条件」を確認して、VPC スタックのデプロイを行ってください。
  - その後、FSxWindowsStack を一度削除して、もう一度、スタックの作成を行ってください。
- 作成中に CloudFormation で「No export named ADPrivateIP found. Rollback requested by user」というエラーが表示されて、作成が失敗した場合
  - 「前提条件」を確認して、Active Directory スタックのデプロイを行ってください。
  - その後、FSxWindowsStack を一度削除して、もう一度、スタックの作成を行ってください。