#Aggregations
作为摄取规范的一部分，可以在摄取时提供聚合作为在进入德鲁伊之前汇总数据的一种方式。 聚合也可以在查询时被指定为许多查询的一部分。
###1. Count aggregator
```json
{ "type" : "count", "name" : <output_name> }
```
###2. Sum aggregators

```json
{ "type" : "type", "name" : <output_name>, "fieldName" : <metric_name> }
```
type:`longSum` `doubleSum` `floatSum`

###3. Min / Max aggregators
```json
{ "type" : "type", "name" : <output_name>, "fieldName" : <metric_name> }
```
type: `doubleMin` `doubleMax` `floatMin` `floatMax` `longMin` `longMax`
###4. First / Last aggregator
`doubleFirst` `doubleLast` `floatFirst` `floatLast` `longFirst` `longLast`
###5. JavaScript aggregator
```json
{ "type": "javascript",
  "name": "<output_name>",
  "fieldNames"  : [ <column1>, <column2>, ... ],
  "fnAggregate" : "function(current, column1, column2, ...) {
                     <updates partial aggregate (current) based on the current row values>
                     return <updated partial aggregate>
                   }",
  "fnCombine"   : "function(partialA, partialB) { return <combined partial results>; }",
  "fnReset"     : "function()                   { return <initial value>; }"
}
```