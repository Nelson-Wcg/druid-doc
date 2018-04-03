# 摄入规格 Ingestion Spec
    curl -X 'POST' -H 'Content-Type:application/json' -d @ingestion.json localhost:8090/druid/indexer/v1/task
Druid 摄入规格中包含三个元素：
```json
{"dataSchema":{...},"ioConfig":{...},"tuningConfig":{...}}  ```   