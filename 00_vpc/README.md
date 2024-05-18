# VPC deploy

このテンプレートを使用すると、VPCの基本構成をデプロイできます。

## 利用方法

1.  AWSアカウントにログインした状態で、以下の`スタックの作成`をクリックしてください。
2. CloudFormationの画面に遷移します。
3. 必要に応じてパラメータを変更して、スタックを作成してください。

[<img src="https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/c2d15fc9-8371-479b-94b0-4e433118e12e">](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create?stackName=VpcStack&templateURL=https%3A%2F%2Faws-deploy-factory-ap-northeast-1.s3.ap-northeast-1.amazonaws.com%2F00_vpc%2Fvpc.yml)

## パラメータ

### VPC1Name

- 説明: 作成するVPCの名前
- デフォルト値: vpc1

### VPC1Cidr

- 説明: 作成するVPCのIPv4 CIDR
- デフォルト値: 10.0.0.0/16
- 注意事項:
  - IPv6は未対応です。
  - カスタマイズする場合は、/16から/20の間で指定してください。

### VPC1AZOption

- 説明: VPCで利用するAZの数
- デフォルト値: 2（az-aとaz-cを使用）
- 選択肢:
  - 2: az-aとaz-cを使用
  - 3: az-a、az-c、az-dを使用

### VPC1NatGatewayOption

- 説明: PublicサブネットにNAT Gatewayを作成するかどうかのオプション
- デフォルト値: false（作成しない）
- 選択肢:
  - false: NAT Gatewayを作成しない
  - true: 全てのPublicサブネットにNAT Gatewayを作成

## 注意事項

- NAT Gatewayを作成した場合、NAT Gatewayの料金が発生します。
- NAT Gatewayを作成しない場合、料金は発生しません。

## 削除方法

作成したCloudFormationスタックを削除してください。スタックを削除すると、関連するリソースも自動的に削除されます。