# Cloud9ワークスペースの作成

ここでは、Cloud9ワークスペースを作成します。
以降の作業は全て東京リージョンで行います。

マネジメントコンソール上で、東京リージョンが選択されているか、確認ください。

![リージョン確認](./images/books/jawsug-niigata-aws-app-runner/check-tokyo-region.png "リージョン確認")

## Cloud9ワークスペースの作成

- AWSマネジメントコンソールから、Cloud9のページに遷移します。
    - https://ap-northeast-1.console.aws.amazon.com/cloud9/home?region=ap-northeast-1

![マネコントップCloud9](./images/books/jawsug-niigata-aws-app-runner/home_cloud9.png "マネコントップCloud9")

- 「環境を作成」をクリックします。

![トップCloud9](./images/books/jawsug-niigata-aws-app-runner/top_cloud9.png "トップCloud9")

- 以下適宜設定します。
    - 名前: 適宜設定します
    - 環境タイプ: 新しいEC2インスタンス (デフォルト)
        - インスタンスタイプ: t3.small
    - ネットワーク設定: デフォルトのまま
- 設定後「作成」をクリックします。

![Cloud9setting1](./images/books/jawsug-niigata-aws-app-runner/cloud9_setting1.png "Cloud9setting1")
![Cloud9setting2](./images/books/jawsug-niigata-aws-app-runner/cloud9_setting2.png "Cloud9setting2")
![Cloud9setting3](./images/books/jawsug-niigata-aws-app-runner/cloud9_setting3.png "Cloud9setting3")

- Cloud9ワークスペースの一覧画面に遷移します。
    - ワークスペース作成完了するまで、しばらくお待ちください。

![Cloud9creating1](./images/books/jawsug-niigata-aws-app-runner/cloud9_creating1.png "Cloud9creating1")

- 正常に作成されたら、Cloud9 IDEの「開く」をクリックします。

![Cloud9open1](./images/books/jawsug-niigata-aws-app-runner/cloud9_open1.png "Cloud9open1")

- しばらくすると、Cloud9のIDE画面が起動します。

![Cloud9open3](./images/books/jawsug-niigata-aws-app-runner/cloud9_open3.png "Cloud9open3")

## ディスクボリュームの拡張

デフォルトでは、Cloud9インスタンスのディスクボリュームサイズが10GiBです。
今回は30GiBまで拡張して使用したいと思います。

- Cloud9ワークスペース一覧画面から、作成済みのワークスペース環境の名前をクリックします。

![Cloud9open1](./images/books/jawsug-niigata-aws-app-runner/cloud9_open1.png "Cloud9open1")

- 「EC2インスタンスの管理」をクリックします。

![Cloud9volume1](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume1.png "Cloud9volume1")

- 表示されているEC2インスタンスの左側チェックボックスにチェックを入れ、下部の「ストレージ」タブをクリックした後、「ボリュームID」をクリックします。

![Cloud9volume2](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume2.png "Cloud9volume2")

- 表示されているボリュームの左側チェックボックスにチェックを入れ、「アクション」から「ボリュームの変更」をクリックします。

![Cloud9volume3](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume3.png "Cloud9volume3")

- サイズを「30」に変更して、「変更」ボタンをクリックします。

![Cloud9volume4](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume4.png "Cloud9volume4")

- 再度「変更」ボタンをクリックします。

![Cloud9volume5](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume5.png "Cloud9volume5")

- 変更リクエストが受付されました。Cloud9が起動するEC2インスタンスを再起動することで反映されます。

![Cloud9volume6](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume6.png "Cloud9volume6")

- 変更対象となるボリュームの左側チェックボックスにチェックを入れ、「詳細」タブの「アタッチされたインスタンス」をクリックします。

![Cloud9volume7](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume7.png "Cloud9volume7")

- 表示されているEC2インスタンスの左側チェックボックスにチェックを入れ、「インスタンスの状態」から「インスタンスを再起動」をクリックします。

![Cloud9volume8](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume8.png "Cloud9volume8")

- 「再起動」ボタンをクリックします。

![Cloud9volume9](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume9.png "Cloud9volume9")

- 再起動後、ストレージボリュームサイズが30GiBになっています。

![Cloud9volume10](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume10.png "Cloud9volume10")

- Cloud9ワークスペースに戻りましょう。もしワークスペースを開きっぱなしでボリュームサイズ変更している場合は、Webブラウザを再読み込みします。

![Cloud9volume11](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume11.png "Cloud9volume11")

- Cloud9からも、ルートディレクトリの容量が増えていることが確認できると思います。

![Cloud9volume12](./images/books/jawsug-niigata-aws-app-runner/cloud9_instance_volume12.png "Cloud9volume12")

次の章では、Cloud9ワークスペースに必要な権限を付与するために、
IAMロールの作成を行います。
