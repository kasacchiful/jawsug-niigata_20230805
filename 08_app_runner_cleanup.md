# リソースを削除する

最後に、各種AWSリソースを削除して後片付けをしましょう。

## App Runner サービスの削除

今回作成したApp Runnerサービスを1つずつ削除します。

![cleanup_apprunner1](./images/books/jawsug-niigata-aws-app-runner/cleanup_app_runner1.png "cleanup_apprunner1")

![cleanup_apprunner2](./images/books/jawsug-niigata-aws-app-runner/cleanup_app_runner2.png "cleanup_apprunner2")

## ECRリポジトリの削除

今回作成したECRリポジトリを削除します。
左側のチェックボックスにチェックを入れ、「削除」ボタンをクリックします。

![cleanup_ecr1](./images/books/jawsug-niigata-aws-app-runner/cleanup_ecr1.png "cleanup_ecr1")

![cleanup_ecr2](./images/books/jawsug-niigata-aws-app-runner/cleanup_ecr2.png "cleanup_ecr2")

## Cloud9環境の削除

IDEはブラウザを閉じても大丈夫です。

今回作成したCloud9環境を削除します。
左側のラジオボタンを選択し、「削除」ボタンをクリックします。

![cleanup_cloud9_1](./images/books/jawsug-niigata-aws-app-runner/cleanup_cloud9_1.png "cleanup_cloud9_1")

![cleanup_cloud9_2](./images/books/jawsug-niigata-aws-app-runner/cleanup_cloud9_2.png "cleanup_cloud9_2")

## IAMロールの削除

最初に作成したIAMロールと、ECRでデプロイした際に作成したIAMロールを削除します。

![cleanup_iamrole1](./images/books/jawsug-niigata-aws-app-runner/cleanup_iamrole1.png "cleanup_iamrole1")

![cleanup_iamrole2](./images/books/jawsug-niigata-aws-app-runner/cleanup_iamrole2.png "cleanup_iamrole2")

![cleanup_iamrole3](./images/books/jawsug-niigata-aws-app-runner/cleanup_iamrole3.png "cleanup_iamrole3")

![cleanup_iamrole4](./images/books/jawsug-niigata-aws-app-runner/cleanup_iamrole4.png "cleanup_iamrole4")

## GitHubリポジトリの削除

フォークしたGitHubリポジトリは、削除してもかまいません。

「Settings」から「Delete this Repository」をクリックすると、リポジトリを削除できます。

![cleanup_github1](./images/books/jawsug-niigata-aws-app-runner/cleanup_github1.png "cleanup_github1")

![cleanup_github2](./images/books/jawsug-niigata-aws-app-runner/cleanup_github2.png "cleanup_github2")

以上です。
お疲れ様でした。
