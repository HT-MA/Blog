下面是一个简单的 Go 语言脚本示例，它用于读取一个文本文件的内容并输出到标准输出：

```go
package main

import (
    "fmt"
    "io/ioutil"
    "os"
)

func main() {
    // 检查是否提供了文件名作为命令行参数
    if len(os.Args) < 2 {
        fmt.Println("Usage: go run script.go <filename>")
        os.Exit(1)
    }

    // 获取文件名
    filename := os.Args[1]

    // 读取文件内容
    content, err := ioutil.ReadFile(filename)
    if err != nil {
        fmt.Printf("Error reading file: %v\n", err)
        os.Exit(1)
    }

    // 输出文件内容到标准输出
    fmt.Println("File content:")
    fmt.Println(string(content))
}
```

这个脚本接受一个文件名作为命令行参数，并读取该文件的内容，然后将内容输出到标准输出。你可以将上面的代码保存到一个名为 `script.go` 的文件中，并使用 `go run script.go <filename>` 命令来执行，其中 `<filename>` 是你要读取的文本文件的路径。

请注意，这只是一个简单的示例，展示了如何使用 Go 语言编写一个脚本来处理文件。在实际应用中，你可能需要处理更多的边界情况和错误，以及更复杂的逻辑。