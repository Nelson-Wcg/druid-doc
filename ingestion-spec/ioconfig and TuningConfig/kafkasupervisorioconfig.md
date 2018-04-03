##KafkaSupervisorIOConfig
例子：
```json
    "ioConfig": {
    "topic": "metrics",
    "consumerProperties": {
      "bootstrap.servers": "localhost:9092"
    },
    "taskCount": 1,
    "replicas": 1,
    "taskDuration": "PT1H"
  }
```

|Field|	Type|Description|Required|
|---|---:|---:|:----:|
|topic|string|读取的kafka的topic|yes|
|consumerProperties|Map|kafka消费者的配置信息，必须包含`bootstrap.servers`: `<BROKER_1>:<PORT_1>,<BROKER_2>:<PORT_2>,....`|yes|
|replicas|Integer|副本集的数量，其中1表示单个任务集（无复制）。复制任务总是分配给不同的工作人员，以提供针对节点故障的弹性。|no (default == 1)|
|taskCount|Integer|replica中的最大读取任务数|no (default == 1)|
|taskDuration|ISO8601 Period|任务停止读取并开始发布segment之前的时间长度|no (default == PT1H)|
|startDelay|ISO8601 Period|supervisor开始管理任务之前等待的时间|no (default == PT5S)|
|period|ISO8601 Period|supervisor多久会执行它的管理逻辑|no (default == PT30S)|
|useEarliestOffset|Boolean|如果一个supervisor第一次管理数据源，它将从kafka得到一组开始偏移|no(default == false)|
|completionTimeout|ISO8601 Period|在宣布发布任务失败并终止它之前等待的时间长度。|no(default==PT30M)|
|lateMessageRejectionPeriod|ISO8601 Period|配置task拒绝时间戳早于task创建之前的信息|no(default== none)|
|earlyMessageRejectionPeriod|ISO8601 Period|配置task拒绝时间戳晚于task创建之前的信息|no(default == none)|
|skipOffsetGaps|Boolean|是否允许卡夫卡流中缺少偏移量的间隙|no (default == false)|