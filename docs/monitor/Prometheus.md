# Windows配置Prometheus 教程

## prometheus

### 下载Prometheus安装包
  下载 [prometheus-2.37.9-LTS]

[prometheus-2.37.9-LTS]: https://github.com/prometheus/prometheus/releases/download/v2.37.9/prometheus-2.37.9.windows-amd64.zip
### 启动Prometheus
  解压安装包到指定目录

![prometheus.exe](https://raw.githubusercontent.com/HT-MA/Blog/main/docs/images/Prometheus-exe.png)

  启动prometheus.exe程序

![set up prometheus](https://raw.githubusercontent.com/HT-MA/Blog/main/docs/images/Prometheus-setup.png)

## export 
### widows_export

## grafana
### 下载Grafana安装包
  下载[grafana]
[grafana]: https://dl.grafana.com/enterprise/release/grafana-enterprise-10.0.0.windows-amd64.zip
### 启动Grafana
### 配置 Prometheus数据源

## alter
### 下载altermanager安装包
下载[altermanager]
[altermanager]: https://github.com/prometheus/alertmanager/releases/download/v0.26.0/alertmanager-0.26.0.windows-amd64.zip
### 启动altermanager



# Linux配置Prometheus教程
## prometheus
### 下载Prometheus安装包
### 启动Prometheus

## export 
### widows_export

## grafana
### 下载Grafana安装包
### 启动Grafana
### 配置 Prometheus数据源

## alter

# prometheus 查询语法
Prometheus 使用 PromQL（Prometheus Query Language）作为其查询语言，它提供了丰富的功能来从 Prometheus 中检索和分析时间序列数据。以下是一些常用的 PromQL 查询语法和功能介绍：

1. **基本查询**：基本查询用于检索时间序列数据。例如，`cpu_usage` 可以表示一个 CPU 使用率的时间序列。
   
   ```promql
   cpu_usage
   ```

2. **标签过滤**：可以使用标签过滤器来过滤时间序列。例如，使用 `{job="node-exporter"}` 来获取具有特定 job 标签的时间序列。

   ```promql
   cpu_usage{job="node-exporter"}
   ```

3. **聚合操作**：PromQL 提供了各种聚合函数来汇总时间序列数据。例如，`avg` 计算时间序列的平均值，`sum` 计算时间序列值的总和。

   ```promql
   avg(cpu_usage)
   sum(memory_usage)
   ```

4. **向量操作**：PromQL 支持向量操作，可以对多个时间序列进行数学运算。例如，两个向量相加或相减。

   ```promql
   cpu_usage + memory_usage
   cpu_usage - memory_usage
   ```

5. **内置函数**：PromQL 提供了许多内置函数来对时间序列进行操作和转换。例如，`rate` 计算时间序列的速率，`increase` 计算时间序列的增量。

   ```promql
   rate(http_requests_total[5m])
   increase(cpu_usage{instance="server1"}[1h])
   ```

6. **逻辑运算符**：PromQL 支持逻辑运算符，例如 `and`、`or` 和 `unless`，用于组合表达式。

   ```promql
   cpu_usage > 0 and memory_usage > 0
   cpu_usage > 0 or memory_usage > 0
   ```

7. **聚合操作符**：PromQL 还提供了聚合操作符，例如 `by` 和 `without`，用于对标签进行聚合或排除。

   ```promql
   sum(cpu_usage) by (job)
   sum(cpu_usage) without (instance)
   ```

8. **向后聚合**：通过使用 `offset` 关键字，可以在时间序列上向后进行聚合操作。

   ```promql
   rate(http_requests_total[5m] offset 1h)
   ```

这只是一些 PromQL 中常用的功能和语法。Prometheus 提供了丰富的查询语言和功能，可以灵活地满足不同的监控和分析需求。