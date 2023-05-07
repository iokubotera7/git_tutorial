## SAMとは
サーバレスアプリケーション開発において必要なLambda構築・設定・イベントソースマッピングなどなどの  
AWSリソースの作成・管理をソースコードで管理する機能  

## SAMの初期設定
1. sam initでSAMの初期設定を行う
  * sam initでSAMで管理するプロジェクトを作成する
  * 上記コマンドで作成されるフォルダ内にapp.pyとtemplate.yamlという重要なファイルがある
    * app.py：Lambdaのソースプログラムが記載されているファイル
    * template.yaml：Lambdaの設定が記載されているファイル
3. SAMビルド
  * samのファイルが存在するディレクトリに移動する
  * sam build --use-containerを実行する
5. SAMデプロイ
  * 以下のコマンドでSAMをデプロイします。デプロイ時のガイド付き、ロール等は自動で作成するオプションを付けている  
  * sam deploy --guided --capabilities CAPABILITY_IAM CAPABILITY_AUTO_EXPAND


## template.yaml

template.yamlのResourcesには、リソースの情報が記載されている。例えば、  
* Type: AWS::Serverless::Function
  * Lambda関数であることを示しています
* Type: Api
  * APIGatewayであることを示しています  

