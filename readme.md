# elastic 5をコンテナで作りたい

+ memo

```
$ cd .
$ docker-compose build 
```

+ まずはきれいにする

```
for i in `docker ps -a  | awk 'NR > 1 {print $1}'` ; do docker rm  -f ${i} ; done && docker ps -a
for i in `docker images | awk 'NR > 1 {print $3}'` ; do docker rmi -f ${i} ; done && docker images
```


```
# YAMLに「build:」があれば、そのイメージをまとめてビルド
docker-compose build
# YAMLに「image:」があれば、そのイメージをまとめてプル
docker-compose pull
# docker-compose build, docker-compose pullをした後にdocker run
docker-compose up -d
# 個別のサービスを指定することもできる。依存関係がある場合は関係するコンテナすべてが起動するので、この場合は redmine と mysql が両方起動する
docker-compose up -d redmine
# 関係するコンテナすべての出力を表示
docker-compose logs
# 関係するコンテナをまとめて終了
docker-compose stop
# 関係するコンテナをまとめて削除
docker-compose rm
```
