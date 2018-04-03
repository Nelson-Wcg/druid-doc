##Avro Parser
```json
"parser" : {
  "type" : "avro_stream",
  "avroBytesDecoder" : {
    "type" : "schema_repo",
    "subjectAndIdConverter" : {
      "type" : "avro_1124",
      "topic" : "${YOUR_TOPIC}"
    },
    "schemaRepository" : {
      "type" : "avro_1124_rest_client",
      "url" : "${YOUR_SCHEMA_REPO_END_POINT}",
    }
  },
  "parseSpec" : {
    "format": "avro",
    "timestampSpec": <standard timestampSpec>,
    "dimensionsSpec": <standard dimensionsSpec>,
    "flattenSpec": <optional>
  }
}
```
|Field|Type|Description|Required|
|-----|-----:|-----:|:-----:|
|type|String|`avro_stream`|no|
|avroBytesDecoder|JSON Object|指定如何decode avro数据|yes|
|parseSpec|JSON Object|指定数据的时间戳和维度。|yes|
####type
> avro_stream

####avroBytesDecoder
|Field|Type|Description|Required|
|-----|-----:|-----:|:-----:|
|type|String|`schema_repo`|no|
|subjectAndIdConverter|JSON Object|指定如何从消息字节中提取主题和ID|yes|
|schemaRepository|JSON Object|指定如何查找Avro|yes|
__subjectAndIdConverter__
type: `avro_1124`
topic:指定kafka数据流的topic
__schemaRepository__
Schema Repository
 > type:`avro_1124_rest_client`
 > url:指定指定你的avro　schema仓库地址

Confluent's Schema Registry
 > type:schema_registry
 > url: Schema Registry地址
 >　capacity：缓存数最大值