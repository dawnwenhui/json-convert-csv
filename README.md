# json-convert-csv

json 数据转换为csv表格。

### Usage

```bash
npm install -S json-convert-csv
```

```javascript
const fs = require('fs')
const Csv = require('json-convert-csv')
const convert = new Csv()

const json = fs.createReadStream('path-to-json-file')
const csv = fs.createWriteStream('path-to-csv-file')

json.pipe(convert).pipe(csv)
```

### Options

##### new Csv([options])

##### options 参数

| 名称 | 类型 | 描述 | 示例 |
| --- | --- | --- | --- |
| header | Array | 数据的字段名 | `['name', 'age', 'tel']`
| headerDisplay | Array | 数据的显示名称 | `['姓名', '年龄', '电话']` |

### Event

- [parse](#parse)
- [convert](#convert)
- [error](#error)

### parse

##### 参数

| 名称 | 类型 | 描述 |
| --- | --- | --- |
| obj | Object | 解析的每个对象 |
| index | Number | 第几个解析的对象 |

### convert

##### 参数

| 名称 | 类型 | 描述 |
| --- | --- | --- |
| convertStr | String | 格式化的字符串。 |
| index | Number | 第几个解析的对象 |

### error

##### 参数

| 名称 | 类型 | 描述 |
| --- | --- | --- |
| error | Error | 转换过程出现的错误。 |

### Simple

```javascript
const convert = new Csv({
  header: ['name', 'age', 'tel'],
  headerDisplay: ['姓名', '年龄', '电话']
})
/*
<<< Input JSON
[
  {
    "name": "小白",
    "age": "18",
    "tel": "1383794XXXX"
  },
  {
    "name": "小红",
    "age": "14",
    "tel": "1337893XXXX"
  }
]
>>> Output CSV
*/
```

| 姓名 | 年龄 | 电话 |
| --- | --- | --- |
| 小白 | 18 | 1383794XXXX |
| 小红 | 14 | 1337893XXXX |