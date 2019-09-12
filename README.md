# WordPress + docker-compose + composer + Ansible

## やりたいこと
wordpreee を　*RDMS + Cloud Compute(debian環境)* で公開するとなった時に、
debian 環境を本番と開発どちらもAnsibleで作れるようにしたい。

## ディレクトリ構成
```
.
├── bedrock           wordpressのソースファイル群
├── ansible           wordpressインスタンスのansible構成ファイル群
├── docker                 docer-composeで使うfile
├── docker-compose.yml      docker-composeファイル
└── README.md            playbookファイル
```

## 開発環境構築
1. Dockerコンテナの起動
```
docker-compose build
docker-compose up

# ansible のコンテナに入る
docker-compose exec ansible bash

# ansibleを実行
ansible-playbook ansible/site.yml -i ansible/hosts.dev && tail -f /dev/null
```
