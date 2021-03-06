云函数日志检索支持关键词搜索，您可以使用查询语法组合关键词进行检索。

## 查询语法

检索支持以下查询语法：

| 语法      | 语义                                                         |
| --------- | ------------------------------------------------------------ |
| key:value | 键值搜索格式。其中 value 支持`?`、`*`模糊搜索，若 key 或 value 中包含空格、冒号等关键字符，则需用引号包括。目前已支持的 key 列表请参见 [预置 key](#key)。 |
| A and B   | “与”逻辑，返回 A 与 B 的交集结果，若检索多个关键词，使用空格分割则默认为 and。 |
| A or B    | “或”逻辑，返回 A 或 B 的并集结果。                             |
| not B     | “非”逻辑，返回不包含 B 的结果。                                |
| A not B   | “减”逻辑，返回符合 A 但不符合 B 的结果，即 A - B。               |
| 'a'       | 字符 a 将被视为普通字符，不会作为语法关键词处理。              |
| "A"       | A 中的所有关键词都将被视为普通字符，不会作为语法关键词处理。   |
| \         | 转义字符，转义后的字符表示符号本身，例如转义引号`\"`，转义冒号`\:`等。 |
| *         | 模糊查询关键字，匹配零个、单个或多个任意字符，不支持以`*`开头。例如，输入`abc*`，会返回以 `abc` 开头的所有命中日志。 |
| ?         | 模糊查询关键字，特定位置匹配单个字符。例如，输入`ab?c`，会返回以 `ab` 为开头，以 `c` 为结尾字符，且两者之间仅有一个字符的所有命中日志。 |
| >         | 大于，针对数值类型的字段。                                     |
| >=        | 大于等于，针对数值类型的字段。                                 |
| <         | 小于，针对数值类型的字段。                                     |
| <=        | 小于等于，针对数值类型的字段。                                 |
| =         | 等于，可以是数值类型的字段，也可以是文本类型（不支持模糊搜索，若需使用模糊搜索，请参考键值搜索 key:value）。 |
| in        | 数值范围查询，中括号 `[]` 表示闭区间，`()` 表示开区间。例如，`(0 100]` 表示大于0且小于等于100。 |


>
>- 运算符的优先级由高到低排序为`:` > `"` > `()` > `and` > `not` > `or`。
>- 若 b 为文本，则 `a=b` 与 `a：b` 的区别在于前者是 a 全等于 b，后者是 a 包含 b（按分词逻辑处理，支持模糊搜索）。
>- 语法关键词不区分大小写。
>- 检索内容区分大小写，如果无检索结果，请检查是否为大小写或拼写错误。



## 预置 key<span id="key"></span>

| Key           | 类型   | 含义         | 查询示例          |
| ------------- | ------ | ------------ | ----------------- |
| SCF_RequestId | text   | 请求 ID      | SCF_RequestId:123 |
| SCF_Duration  | double | 运行时间（ms） | SCF_Duration>20   |



## 示例

- 查询包含关键词 error 或者 fail 的日志：
```
error or fail
```
- 查询指定请求里包含 error 关键词的日志：
```
SCF_RequestId:123 and error
```
- 查询运行时间大于 20 ms 且包含 error 关键词的日志：
```
SCF_Duration>20 and error
```
>如果需要对请求日志进行去重，可以检索 "Report RequestId"。例如，想查看运行时间大于 20 ms 的请求有哪些，则可以使用：
`"Report RequestId" and SCF_Duration>20`。


## 常见问题

#### 1. 为什么页面提示“检索语法不合法”？
请注意检索时不能以 `*` 或 `？`作为开头。

#### 2. 为什么日志里有匹配的关键词，但检索不到？
- 请注意大小写是否匹配。
- 请确认检索内容和语法关键词之间是否有空格。正确示例 `SCF_Duration>20` ，错误示例`SCF_Duration > 20`。
