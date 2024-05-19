# WordPress on EC2 and RDS MySql

このテンプレートを使用すると、EC2 インスタンスと RDS MySQL で構成された環境をデプロイできます。

## デプロイする構成
![ec2-linux-with-rds](https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/bddc433c-de4a-4cee-b64b-eb72fd375f0a)

## 前提条件

以下のURLからVPCのデプロイを行ってください。パラメータはデフォルトのままでOKです。デプロイ済みの場合は、そのまま流用できます。

- [VPCスタックのデプロイ](https://github.com/mirakuuu/aws-deploy-factory/tree/main/00_vpc)

## 利用方法

1. AWSアカウントにログインした状態で、以下の`スタックの作成`をクリックしてください。
2. CloudFormationの画面に遷移します。
3. 必要に応じてパラメータを変更して、スタックを作成してください。

[<img src="https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/c2d15fc9-8371-479b-94b0-4e433118e12e">](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create?stackName=WordPressEC2RDSStack&templateURL=https://aws-deploy-factory-ap-northeast-1.s3.ap-northeast-1.amazonaws.com/wordpress/ec2-linux-with-rds/ec2-linux-with-rds.yml)

## パラメータ

### YourIP

- 説明: WordPressへのアクセス制限（IP制限）をするアドレスを入力します。デフォルトは全IPに対して外部公開します。自分のIPが不明な場合は[こちら](https://www.cman.jp/network/support/go_access.cgi)から確認してください。/32 などのプレフィックスの入力を忘れないようにしてください。
- デフォルト値: 0.0.0.0/0

### MySQLAdminPassword

- 説明: RDS MySQL admin ユーザーのパスワード
- 制約: 8～41 文字

### DBInstanceClass

- 説明: WordPress用のRDS DBインスタンスクラス
- デフォルト値: db.t3.micro

### InstanceType

- 説明: WordPress用のEC2インスタンスタイプ
- デフォルト値: t2.micro

## WordPressのインストール方法

- [スタック一覧](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks)にアクセスして、表示される WordPressEC2RDSStackをクリックして、スタックの詳細を表示します。
- **出力** タブをクリックします
  - **DBHostname** に記載している、値をメモします
  - **WordPressURL** に表示されている URL をクリックします
- WordpPressの設定画面につながるので「さあ、はじめましょう！」をクリックします
- 以下の情報を入力して、「送信」をクリックします
  - データベース名: wordpress
  - ユーザー名: admin
  - パスワード: **MySQLAdminPassword** で入力したパスワード
  - データベースのホスト名: さきほどメモした **DBHostname** の値を入力します
  - テーブル接頭辞: wp_ (デフォルトのまま)
- インストール実行をクリックします
- サイトのタイトルなどを入力して、「WordPress をインストール」をクリックします
  - （入力例）
  - サイトのタイトル： WordPress テスト
  - ユーザー名: admin
  - パスワード: (あとで使うのでメモする)
  - メールアドレス: 自分のメールアドレス（持っていない場合は test@example.com)
  - 検索エンジンでの表示: デフォルトのまま
- ログインをクリックして、さきほど入力したユーザ名とパスワードを入力
- WordPressの管理画面に遷移したことを確認します

## 削除方法

作成したCloudFormationスタックを削除してください。スタックを削除すると、関連するリソースも自動的に削除されます。


## トラブルシューティング
- 作成中に CloudFormationで「No export named VPC1ID found. Rollback requested by user」というエラーが表示されて、作成が失敗した場合
  - 「前提条件」を確認して、VPCスタックのデプロイをまず行ってください。
  - その後、WordPressEC2Stack を一度削除して、もう一度、スタックの削除を行ってください。