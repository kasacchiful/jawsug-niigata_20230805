# Dockerを使ってWebサイトをApp Runnerにデプロイしよう

この章では、AWS App Runnerにアプリケーションをデプロイする方法の1つである、
Dockerコンテナを利用してデプロイする方法を行います。

## ソースコードをCloud9へコピー

Cloud9のIDEを起動しましょう。

以下のGitHubリポジトリにソースコードがありますので、このソースをCloneします。

https://github.com/kasacchiful/app-runner-handson-docker-app

```bash
git clone https://github.com/kasacchiful/app-runner-handson-docker-app
```

![docker1](./images/books/jawsug-niigata-aws-app-runner/app_runner_docker1.png "docker1")

クローンしたら、該当ディレクトリに移動しておきましょう。

```bash
cd app-runner-handson-docker-app
```

## ECRの設定

App RunnerにDockerコンテナを利用してデプロイする場合、コンテナイメージをAmazon ECRに登録する必要があります。

https://ap-northeast-1.console.aws.amazon.com/ecr/get-started?region=ap-northeast-1

![ecr0](./images/books/jawsug-niigata-aws-app-runner/app_runner_ecr0.png "ecr0")

- 「リポジトリの作成」の「使用方法」をクリックします。

![ecr1](./images/books/jawsug-niigata-aws-app-runner/app_runner_ecr1.png "ecr1")

- 以下の設定を行います。
    - 可視性設定: プライベート (デフォルト)
    - リポジトリ名: `app-runner-handson-docker-app` とします。
- 「リポジトリを作成」をクリックします。

![ecr2](./images/books/jawsug-niigata-aws-app-runner/app_runner_ecr2.png "ecr2")

- リポジトリが作成されたら、「プッシュコマンドの表示」ボタンをクリックします。

![ecr3](./images/books/jawsug-niigata-aws-app-runner/app_runner_ecr3.png "ecr3")

- CLIでリポジトリにプッシュするコマンド一覧が表示されます。このコマンドを使ってコンテナイメージを登録します。

![ecr4](./images/books/jawsug-niigata-aws-app-runner/app_runner_ecr4.png "ecr4")



## ECRにコンテナイメージを登録

Cloud9のIDEに戻り、Dockerfileがあるディレクトリ上で、以下のコマンドを実行します。

```bash
aws ecr get-login-password --region ap-northeast-1 | docker login --username AWS --password-stdin ＜AWSアカウントID＞.dkr.ecr.ap-northeast-1.amazonaws.com
```

![ecr5](./images/books/jawsug-niigata-aws-app-runner/app_runner_ecr5.png "ecr5")

```bash
docker build -t app-runner-handson-docker-app .
```

![ecr6](./images/books/jawsug-niigata-aws-app-runner/app_runner_ecr6.png "ecr6")

```bash
docker tag app-runner-handson-docker-app:latest ＜AWSアカウントID＞.dkr.ecr.ap-northeast-1.amazonaws.com/app-runner-handson-docker-app:latest
```

![ecr7](./images/books/jawsug-niigata-aws-app-runner/app_runner_ecr7.png "ecr7")

```bash
docker push ＜AWSアカウントID＞.dkr.ecr.ap-northeast-1.amazonaws.com/app-runner-handson-docker-app:latest
```

![ecr8](./images/books/jawsug-niigata-aws-app-runner/app_runner_ecr8.png "ecr8")

ECRにコンテナイメージが登録できたら、作成したリポジトリ名をクリックし、「イメージのURI」の「URIのコピー」アイコンをクリックしましょう。

![ecr10](./images/books/jawsug-niigata-aws-app-runner/app_runner_ecr10.png "ecr10")

以下のようなURI文字列がコピーされます。App Runnerの設定で使いますので、コピーを取っておきましょう。

![ecr11](./images/books/jawsug-niigata-aws-app-runner/app_runner_ecr11.png "ecr11")

```txt
＜AWSアカウントID＞.dkr.ecr.ap-northeast-1.amazonaws.com/app-runner-handson-docker-app:latest
```

## App Runnerの設定

では、App Runnerの設定を行って、Webアプリケーションを起動しましょう。

https://ap-northeast-1.console.aws.amazon.com/apprunner/home?region=ap-northeast-1

- App Runnerの画面から、「サービスの作成」をクリックします。

![apprunner_docker2](./images/books/jawsug-niigata-aws-app-runner/app_runner_docker2.png "apprunner_docker2")

- 以下の設定を行います。
    - リポジトリタイプ: コンテナレジストリ
    - プロバイダー: Amazon ECR
    - コンテナのイメージURI: 先ほどコピーを取得したイメージURI文字列
        ```txt
        ＜AWSアカウントID＞.dkr.ecr.ap-northeast-1.amazonaws.com/app-runner-handson-docker-app:latest
        ```
    - デプロイトリガー: 手動
    - ECRアクセスロール: 「新しいサービスロールの作成」を選択
        - サービスロール名はデフォルトのままでOK

![apprunner_docker3](./images/books/jawsug-niigata-aws-app-runner/app_runner_docker3.png "apprunner_docker3")

- サービス設定は以下の通りにします。
    - サービス名: 適宜設定します
    - ポート: `3000` を入力します。
    - その他デフォルト設定でそのまま「次へ」をクリックします。

![apprunner_docker4](./images/books/jawsug-niigata-aws-app-runner/app_runner_docker4.png "apprunner_docker4")

- 設定内容を確認して、「作成とデプロイ」をクリックします。

![apprunner_docker6](./images/books/jawsug-niigata-aws-app-runner/app_runner_docker6.png "apprunner_docker6")

- デプロイが完了するまで、しばらく待ちます

![apprunner_docker7](./images/books/jawsug-niigata-aws-app-runner/app_runner_docker7.png "apprunner_docker7")

- ステータスが「Running」になったら、デフォルトドメインのURLをクリックします。

![apprunner_docker8](./images/books/jawsug-niigata-aws-app-runner/app_runner_docker8.png "apprunner_docker8")

- ブラウザに「Hello World」が表示されればOKです。

![apprunner_docker9](./images/books/jawsug-niigata-aws-app-runner/app_runner_docker9.png "apprunner_docker9")
