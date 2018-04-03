#parseSpec
parseSpec的作用：
* 字符串解析器使用它们来确定格式（例如JSON、CSV、TSV）对传入行进行格式化操作。
* 所有解析器都使用它们来确定传入行的时间戳和维度。
```json
"parseSpec" : {
      "format" : "json",
      "timestampSpec" : {
      |  "column" : "timestamp",
      |  "format" : "auto"
      },
      "dimensionsSpec" : {
      |  "dimensions": [
      |    "page",
      |    "language",
      |    "user",
      |    "country",
      |    "region",
      |    "city",
      |    {"type": "long","name": "countryNum"},
      |    {"type": "float","name": "userLatitude"},
      |    {"type": "float","name": "userLongitude"}
      |  ],
      |  "dimensionExclusions" : [],
      |  "spatialDimensions" : []
      }
    }
```
|字段|类型|描述|Required|
| --------   | -----:  | ----:  |:----: |
| format | string | `json jsonLowercase csv tsv timeAndDims` |no|
|timestampSpec| JSONObject|指定时间戳的列和格式|yes|
|dimensionsSpec|JSONObject|指定维度数据|yes|
|flattenSpec|JSONObject| 指定嵌套JSON数据的扁平化配置。|no|
