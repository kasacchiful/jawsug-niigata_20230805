# IAMロールの作成

ここでは、Cloud9ワークスペースの作業に必要な権限を付与するために、IAMロールの作成とアタッチを行います。

https://us-east-1.console.aws.amazon.com/iamv2/home?region=ap-northeast-1#/home

## IAMロールの作成

- AWSマネジメントコンソールから、Cloud9のページに遷移します。
    - https://us-east-1.console.aws.amazon.com/iamv2/home?region=ap-northeast-1
- 左側メニューの「ロール」をクリックし、「ロールの作成」をクリックします。

![トップIamRole](./images/books/jawsug-niigata-aws-app-runner/iam_role1.png "トップIamRole")

- 信頼されたエンティティタイプは「AWSのサービス」、ユースケースは「EC2」が選択されていることを確認し、「次へ」をクリックします。

![CreateIamRole2](./images/books/jawsug-niigata-aws-app-runner/iam_role2.png "CreateIamRole2")

- 今回は「AdministratorAccess」にチェックを入れ、「次へ」をクリックします。

![CreateIamRole3](./images/books/jawsug-niigata-aws-app-runner/iam_role3.png "CreateIamRole3")

- ロール名を適宜入力したら、「ロールの作成」をクリックします。

![CreateIamRole4](./images/books/jawsug-niigata-aws-app-runner/iam_role4.png "CreateIamRole4")

- ロールが作成されたことを確認します。

![CreateIamRole5](./images/books/jawsug-niigata-aws-app-runner/iam_role6.png "CreateIamRole6")

## Cloud9ワークスペースEC2インスタンスにアタッチ

- Cloud9ワークスペース右上の丸い灰色ボタンをクリックし、「Manage EC2 Instance」をクリックします。
    - それ以外にも、マネジメントコンソール上からEC2インスタンス管理を辿ってもOKです。

![AttachIamRole1](./images/books/jawsug-niigata-aws-app-runner/iam_role7.png "AttachIamRole1")

- 表示されているEC2インスタンスの左側チェックボックスにチェックを入れ、「アクション」「セキュリティ」「IAMロールを変更」の順でクリックします。

![AttachIamRole2](./images/books/jawsug-niigata-aws-app-runner/iam_role8.png "AttachIamRole2")

- 先ほど作成したIAMロールを選択して、「IAMロールの更新」をクリックします。

![AttachIamRole3](./images/books/jawsug-niigata-aws-app-runner/iam_role9.png "AttachIamRole3")

これで事前の準備は整いました。

次の章で、実際にAWS App Runnerを使っていきましょう。
