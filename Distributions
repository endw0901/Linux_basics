# Linux Distributions

ポイント要約していく

* 統合的コード管理(GitHub)、GitLab Flow
* 課題とリリース追跡(Issue Board)
* コード品質向上(GitLab CI/CD)
* デプロイ管理
* モニタリング

## 無償プロダクト
* GitLab CE

## DevOpsに必要な開発ツール

* ツール群の検討にかかる時間を省略できる
* ツール間の連携機能がある
* 多くのプロセスを包括的に操作できる管理コマンドが提供されている
* セキュリティに厳格な環境でも、オンプレミスに展開できる

|カテゴリ|プロダクト|
|:------------:|:-----------|
|コミュニケーション|Slack、Mettermost|
|バージョン管理|GitHub|
|チケット管理|Redmine、Trac|
|CI|Jenkins、CircleCI、TravisCI|
|ビルド|Maven、Docker(Dockerfile)|
|テスト|Selenium、JUnit|
|成果物管理|Artifactory、Docker Registory|
|デプロイ|Ansible、Chef、Docker|
|監視|Prometheus|



## 管理コマンド

|コマンド|機能|
|:------------:|:-----------|
|gitlab-ctl|プロセス管理、設定の再構成、ログ管理|
|gitlab-psql|PostgreSQLに作成されたGitLabデータベースの参照・変更|
|gitlab-rake|バックアップ、キャッシュ削除など頻繁に利用される運用タスク|



## CI：継続的インテグレーション
* アーティファクト：動作が保証されたアプリケーションを実行形式のモジュールにした成果物
DockerイメージやBuildPackを指す

* CI = 安定的に動く結果をどこかに保存する仕組み

### GitLab CI/CD Jobs
* 一般的なのはJenkins、CircleCI、TravisCI
* ビルドツールやテストツールと連携したインテグレーションの自動化が可能

#### GitLab CI/CD Jobsの機能
* Merge Requestと連携できる
* 並列分散でビルド実行ができる
* ビルドのロギング機能がある
* ジョブにあわせてオートスケールが可能
* アーティファクトを動的にGitLabにアップロードし、ブラウザ上で利用可能


## CD：継続的デプロイ
* デプロイメントパイプライン＝アプリ開発やInfrastructure as Codeにおける、ビルド、テスト、デプロイ、リリースのプロセス

### GitLab CI/CD Pipeline
* デプロイメントパイプラインを自動化できる

### Review Apps
* GitLabのMerge Request(GitHubのPull Requestに相当)に対して、レビュー環境を動的に提供
