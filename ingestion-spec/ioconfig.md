# 摄入规格 Ingestion Spec


Druid 摄入规格中包含三个元素：
```
{"dataSchema":{...},"ioConfig":{...},"tuningConfig":{...}}
```
## IOConfig
```
 "ioConfig" : {
      "type" : "realtime",
      "firehose": {
        "type": "kafka-0.8",
        "consumerProps": {
          "zookeeper.connect": "localhost:2181",
          "zookeeper.connection.timeout.ms" : "15000",
          "zookeeper.session.timeout.ms" : "15000",
          "zookeeper.sync.time.ms" : "5000",
          "group.id": "druid-example",
          "fetch.message.max.bytes" : "1048586",
          "auto.offset.reset": "largest",
          "auto.commit.enable": "false"
        },
        "feed": "wikipedia"
      },
      "plumber": {
        "type": "realtime"
      }
    },
```
指定数据来自何处以及数据将流向何处。该对象将随摄入方法而异。
type