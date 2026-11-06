# Prometheus 项目分析

## 项目名称
**Prometheus** — 开源监控系统与时序数据库，云原生监控事实标准
- **GitHub**: [prometheus/prometheus](https://github.com/prometheus/prometheus)
- **许可证**: Apache-2.0
- **主要语言**: Go
- **官网**: [prometheus.io](https://prometheus.io)

---

## 项目概述
Prometheus 起源于 SoundCloud 的监控项目，2016 年加入 CNCF，如今已是云原生领域监控与告警的事实标准。它采用拉取（pull）模型周期性抓取目标暴露的 HTTP 指标端点，将数据存入自带的高性能时序数据库（TSDB），并通过功能强大的 PromQL 查询语言支持多维度的实时聚合分析。

Prometheus 的数据模型（指标名 + 键值对标签）天然适配动态的容器化环境：服务发现机制可与 Kubernetes、Consul 等无缝集成，自动发现并监控新实例。围绕它形成了完整的生态——Alertmanager（告警）、Grafana（可视化）、各类 exporter（Node、blackbox、数据库等）。

当前已演进到 v3 系列，2026-11-06 登上 Trending（当日 +140 Stars），作为基础设施老牌项目仍保持高热度。

---

## 核心功能
| 功能 | 描述 |
|------|------|
| 多维数据模型 | 指标名 + 标签键值对，支持任意维度切片聚合 |
| PromQL | 强大的时序查询语言，速率、直方图、预测一应俱全 |
| 拉取式采集 | HTTP pull 模型 + 多种服务发现（K8s/Consul/DNS 等） |
| TSDB 存储 | 自研时序数据库，高效压缩与 retention 管理 |
| 告警规则 | 基于 PromQL 的告警规则 + Alertmanager 路由/去重/静默 |
| Remote Write | 标准化远程写入协议，对接长期存储（Thanos/Mimir 等） |

---

## 技术栈
| 组件 | 技术 |
|------|------|
| 语言 | Go |
| 存储 | 自研 TSDB（write-ahead log + 分块压缩） |
| 查询 | PromQL 引擎 |
| UI | 内置 React Web UI |
| 部署 | 单二进制 + Docker/distroless 镜像 |

---

## 项目亮点
### 云原生监控标准
CNCF 毕业项目，Kubernetes 生态指标格式的定义者，几乎所有云原生组件原生暴露 Prometheus 指标。

### PromQL 的表达力
一条查询即可完成「过去 5 分钟错误率的 P99」这类复杂计算，告警规则与查询语言同源，可观测性体验一致。

### 活跃的 v3 演进
18,800+ 提交，v3 系列在存储、查询性能与 OpenTelemetry 兼容上持续投入，与老牌告警体系（SECURITY-INSIGHTS 等安全流程）并重。

---

## 应用场景
### Kubernetes 集群监控
配合 kube-prometheus-stack 是 K8s 可观测性默认方案。

### 微服务指标监控
服务指标、RED/USE 方法论、SLO 告警的标准实现路径。

### 基础设施与业务指标
配合 Grafana 构建从主机层到业务层的完整监控大盘。

---

## Star 数据
| 指标 | 数值 |
|------|------|
| 总 Stars | 66,997 |
| 总 Forks | 10,979 |
| 今日新增 | +140 |
| Open Issues | 1,065 |

---

## 总结
Prometheus 用 pull 模型 + 多维标签 + PromQL 定义了云原生时代的监控范式，是可观测性领域无可争议的基石项目。

---

*数据来源：GitHub 仓库 (prometheus/prometheus)，2026 年 11 月访问*
