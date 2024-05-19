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

[<img src="https://github.com/mirakuuu/aws-deploy-factory/assets/159740576/c2d15fc9-8371-479b-94b0-4e433118e12e">](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks/create?stackName=WordPressEC2Stack&templateURL=https://aws-deploy-factory-ap-northeast-1.s3.ap-northeast-1.amazonaws.com/wordpress/ec2-linux/ec2-linux.yml)

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

- [ここから](https://ap-northeast-1.console.aws.amazon.com/cloudformation/home?region=ap-northeast-1#/stacks?filteringStatus=active&filteringText=WordPressEC2Stack&viewNested=true)にアクセスして、表示される WordPressEC2Stackをクリックして、スタックの詳細を表示します。
- **出力** タブをクリックして、**WordPressURL** に表示されている URL をクリックします
- WordpPressの設定画面につながるので「さあ、はじめましょう！」をクリックします
- 以下の情報を入力して、「送信」をクリックします
  - データベース名: wordpress
  - ユーザー名: admin
  - パスワード: **MySQLAdminPassword** で入力したパスワード
  - データベースのホスト名: localhost
  - テーブル接頭辞: wp_ デフォルトのまま
- インストール実行をクリックします
- サイトのタイトルなどを入力して、「WordPress をインストール」をクリックします
  - （入力例）
  - サイトのタイトル： WordPress テスト
  - ユーザー名: admin
  - パスワード: (あとで使うのでメモする)
  - メールアドレス: 自分のメールアドレス（持っていない場合は test@example.com)
  - 検索エンジンでの表示: デフォルトのまま
- ログインをクリックして、さきほど入力したユーザ名とパスワードを入力
- WordPressの管理画面に遷移したことを確認
  

## 削除方法

作成したCloudFormationスタックを削除してください。スタックを削除すると、関連するリソースも自動的に削除されます。