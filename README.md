# efak(Eagle for Apache Kafka)

## 对别人的dockerfile进行了优化，删除cluster2，否则日志一直在报错

## 1. 官网

<https://www.kafka-eagle.org/>

## 2. 编译

```sh
docker build -t jiangxuhui/efak:2.0.8 --build-arg VERSION=2.0.8 .
```

- 升级版本时注意
  - 解压升级版本后，注意修改 `conf/system-config.properties` 文件的内容

## 3. 上传镜像

```sh
docker push jiangxuhui/efak:2.0.8
```

## 4. 创建并启动容器

```sh
docker run --name efak \
    -d -p1048:8048 \
    -e TZ=CST-8 \
    -e ZK_HOSTS=172.17.0.1:2181 \
    --restart always \
    jiangxuhui/efak:2.0.8
```

- ZK_HOSTS
  ZooKeeper的连接地址
