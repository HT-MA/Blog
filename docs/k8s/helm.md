# HELM

## install

## helm cli

## charts

## go templates
Go 模板（Go templates）是 Go 语言中的一个强大工具，用于生成文本（如 HTML、邮件、配置文件等）。在 Helm 模板、Kubernetes YAML 模板等领域，Go 模板被广泛应用。以下是对 Go 模板的深入介绍，包括基础知识、常用函数和高级用法。

### 基础知识

#### 语法结构

1. **变量声明和使用**：
   ```go
   {{ $var := "value" }}   // 声明变量
   {{ $var }}              // 使用变量
   ```

2. **条件判断**：
   ```go
   {{ if condition }}
     // 当 condition 为 true 时执行
   {{ else }}
     // 当 condition 为 false 时执行
   {{ end }}
   ```

3. **循环**：
   ```go
   {{ range $index, $element := .Array }}
     {{ $index }}: {{ $element }}
   {{ end }}
   ```

4. **模板包含**：
   ```go
   {{ template "templateName" . }}
   ```

### 常用函数

1. **字符串函数**：
   - `len`: 获取长度
     ```go
     {{ len .String }}
     ```
   - `upper`: 转换为大写
     ```go
     {{ upper .String }}
     ```
   - `lower`: 转换为小写
     ```go
     {{ lower .String }}
     ```

2. **比较函数**：
   - `eq`: 等于
     ```go
     {{ if eq .Value "expected" }} Equal {{ end }}
     ```
   - `ne`: 不等于
     ```go
     {{ if ne .Value "unexpected" }} Not Equal {{ end }}
     ```

3. **逻辑运算**：
   - `and`: 逻辑与
     ```go
     {{ if and .Cond1 .Cond2 }} Both True {{ end }}
     ```
   - `or`: 逻辑或
     ```go
     {{ if or .Cond1 .Cond2 }} One or Both True {{ end }}
     ```
   - `not`: 逻辑非
     ```go
     {{ if not .Cond }} Not True {{ end }}
     ```

4. **字典相关函数**：
   - `hasKey`: 检查键是否存在
     ```go
     {{ if hasKey .Map "key" }} Key exists {{ end }}
     ```

### 示例

#### 配置文件生成

假设我们有一个 YAML 配置模板，用于生成应用的配置文件：

```yaml
apiVersion: v1
kind: Config
metadata:
  name: {{ .Name }}
spec:
  replicas: {{ .Replicas }}
  containers:
  {{- range .Containers }}
    - name: {{ .Name }}
      image: {{ .Image }}
      ports:
      {{- range .Ports }}
        - containerPort: {{ . }}
      {{- end }}
  {{- end }}
```

如果提供的数据结构如下：

```go
data := map[string]interface{}{
  "Name": "my-app",
  "Replicas": 3,
  "Containers": []map[string]interface{}{
    {
      "Name": "app-container",
      "Image": "my-app:latest",
      "Ports": []int{80, 443},
    },
  },
}
```

渲染后的输出将是：

```yaml
apiVersion: v1
kind: Config
metadata:
  name: my-app
spec:
  replicas: 3
  containers:
    - name: app-container
      image: my-app:latest
      ports:
        - containerPort: 80
        - containerPort: 443
```

### 高级用法

#### 自定义函数

你可以在 Go 模板中定义和使用自定义函数：

```go
import (
  "text/template"
  "strings"
)

func main() {
  tmpl := `{{ title .Name }}`
  funcMap := template.FuncMap{
    "title": strings.Title,
  }
  t := template.Must(template.New("example").Funcs(funcMap).Parse(tmpl))
  t.Execute(os.Stdout, map[string]string{"Name": "go templates"})
}
```

这个示例中，自定义了一个 `title` 函数，用于将字符串的首字母大写。

#### 嵌套模板

你可以将一个模板嵌套在另一个模板中：

```go
{{ define "header" }}
  <h1>{{ .Title }}</h1>
{{ end }}

{{ define "content" }}
  <p>{{ .Content }}</p>
{{ end }}

{{ template "header" . }}
{{ template "content" . }}
```

这个示例将 `header` 和 `content` 模板分开定义，然后在主模板中调用它们。

### 调试

在编写和调试 Go 模板时，调试信息非常重要。你可以使用 `printf` 函数输出调试信息：

```go
{{ printf "Value of .Name: %s" .Name }}
```

### 总结

Go 模板是一种非常灵活和强大的工具，适用于生成各种文本内容。通过掌握基本语法、常用函数和高级用法，你可以创建高效且可维护的模板系统。在实际应用中，结合自定义函数和调试技巧，可以进一步增强模板的功能和可读性。