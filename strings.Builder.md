## strings.Builder
<mark>strings.Builder</mark> 是高效构建字符串的类型
- 它避免了重复创建和销毁字符串所带来的性能开销
- strings.Builder 在内部使用一个可增长的字节切片（byte slice）来存储数据
- 只在最后调用 String()会一次性生成一个字符串
### 基本用法
- 1.创建实例： 声明一个 strings.Builder 类型的变量，无需初始化。
- 2.写入内容： 使用 Write、WriteString、WriteByte、WriteRune 等方法向 Builder 中添加内容。
- 3.生成字符串： 调用 String() 方法获取最终拼接好的字符串。
- 4.重置（可选）： 如果需要复用 Builder，可以使用 Reset() 方法清空其内容

```go
var sb strings.Builder
sb.WriteString("Hello, ")
sb.WriteByte(' ')
sb.WriteRune('A')
finalString := sb.String()
```
### 常用方法
- Len() int：返回当前 Builder 中已写入内容的字节数。
- Cap() int：返回 Builder 内部字节切片的容量。
- Grow(n int)：预留 n 个字节的容量，可以减少内部的内存重新分配，进一步提升性能。
- Reset()：清空 Builder，使其可以被重复使用
