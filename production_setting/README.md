# productionモードにする方法

1. reactコンテナでyarn run build
2. docker-compose.ymlでreactコンテナとnginxコンテナをvolumsで繋ぐ。
3. docker-compose.ymlでreactコンテナとnginxコンテナに依存性をもたせる
4. nginxの起動を遅らせるシェルスクリプトを使う。
5. nginx.confを切り替える