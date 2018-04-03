\#\# DataSchema

指定传入数据的架构。所有摄入的规格可以共享相同的dataschema。

一个dataSchema的例子：

\`\`\`

"dataSchema":{

　　"dataSource":"wikipedia",

　　"parser":{

　　\|　　"type":"string",

　　\|　　"parseSpec":{

　　\|　　　　"format":"json",

　　\|　　　　"timestampSpec":{"column":"timestamp","format":"auto"},

　　\|　　　　"dimensionsSpec":{

　　\|　　　　\|　　"dimensions":\[

　　\|　　　　\|　　　　"page",

　　\|　　　　\|　　　　"language",

　　\|　　　　\|　　　　"user",

　　\|　　　　\|　　　　"unpatrolled",

　　\|　　　　\|　　　　"newPage",

　　\|　　　　\|　　　　"robot",

　　\|　　　　\|　　　　"anonymous",

　　\|　　　　\|　　　　"namespace",

　　\|　　　　\|　　　　"continent",

　　\|　　　　\|　　　　"country",

　　\|　　　　\|　　　　"region",

　　\|　　　　\|　　　　"city",

　　\|　　　　\|　　　　{"type":"long","name":"countryNum"},

　　\|　　　　\|　　　　{"type":"float","name":"userLatitude"},

　　\|　　　　\|　　　　{"type":"float","name":"userLongitude"}

　　\|　　　　\|　　\],

　　\|　　　　\|　　"dimensionExclusions":\[\],

　　\|　　　　\|　　"spatialDimensions":\[\]

　　\|　　　　}

　　\|　　}

　　},

　　"metricsSpec":\[

　　\|　　{"type":"count","name":"count"},

　　\|　　{"type":"doubleSum","name":"added","fieldName":"added"},

　　\|　　{"type":"doubleSum","name":"deleted","fieldName":"deleted"},

　　\|　　{"type":"doubleSum","name":"delta","fieldName":"delta"}

　　\],

　　"granularitySpec":{

　　　　"segmentGranularity":"DAY",

　　　　"queryGranularity":"NONE",

　　　　"intervals":\["2013-08-31/2013-09-01"\]

　　}

}

\`\`\`

\#\#\# DataSource

数据源名称，可以理解为数据库的表

\#\#\# Parser

指定如何解析摄入的数据。

\`\`\`

{"type":"string","parseSpec":"..."}

\`\`\`

type若没有指定，默认为==string==,当使用hadoop index时使用hadoopyString  



parseSpec 指定时间戳，格式，数据长度等

\#\#\# metricsSpec

聚合条件的集合，详见Aggregations

\#\#\# granularitySpec

指定如何创建segment和汇总数据

