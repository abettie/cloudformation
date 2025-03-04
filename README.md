# CloudFormationソース

## InitialSet
- バージニア北部リージョンでInitialSet_us-east-1.ymlスタックを実行する。
- 実行中にホストゾーンが作成されたら、お名前ドットコムで該当ドメインのNSレコードを紐づける。
- InitialSet_us-east-1.ymlが正常完了するのを待つ。
- 作成されたホストゾーンのホストゾーンIDおよびバージニア北部リージョンで作成されたSSLのARNを控える。
- 東京リージョンでInitialSet_ap-northeast-1.ymlスタックを実行する。その際、控えていたホストゾーンIDとSSL ARNを入力する。
- InitialSet_ap-northeast-1.ymlが正常完了するのを待つ。
- EC2の秘密鍵はAWS System Managerのパラメータストアにある。
- なお、EC2へはInstance Connectで接続を行うため、RLoginのProxy Commandに以下を設定する。
C:\Programs\AWSCLIV2\aws.exe ec2-instance-connect open-tunnel --instance-id %S