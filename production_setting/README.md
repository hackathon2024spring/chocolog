# productionモードにする方法・・・間に合わず

1. reactコンテナでyarn run build
2. docker-compose.ymlでreactコンテナとnginxコンテナをvolumsで繋ぐ。
3. docker-compose.ymlでreactコンテナとnginxコンテナに依存性をもたせる
4. nginxの起動を遅らせるシェルスクリプトを使う。
5. nginx.confを切り替える

# ルートの.envの修正
- MYSQL_HOSTをDockerコンテナ名からRDSインスタンスのエンドポイントに書き換える。
    MYSQL_HOST=aws-and-infra-rdsa.・・・
- MYSQL_PORTをRDSインスタンスに書き換える。3306はMySQLのデフォルト値
    PORT_MYSQL_FAST=・・・
- MYSQL_USERをCDFTKの.env　RDS_USERと一致させる。
- MYSQL_PASSWORDをCDFTKの.env　RRDS_PASSWORDと一致させる。

# バックエンドの.envは削除すること
- Dockerfileは自分のフォルダから上方に.envを探していき、該当する環境変数が最初に見つかれば採用する。つまり、バックエンドのMYSQL_HOSTがDockerコンテナのままなので、RDSに接続できない。

# docker-compose.ymlの修正
- MySQLコンテナの箇所を消去

# docker_softclear.shの修正
- docker composeをdocker-composeに変更




