# Google Guava 项目分析

## 项目名称

**Google Guava** — Google 官方出品的 Java 核心库集合，Java 生态中使用最广泛的第三方库之一。

- **GitHub**: [google/guava](https://github.com/google/guava)
- **许可证**: Apache-2.0

---

## 项目概述

Guava 是 Google 从内部代码库中提取并开源的 Java 基础库，2014 年 5 月在 GitHub 公开，至今已累计 51.6K+ Stars、11.1K+ Forks，被 39.9 万个下游项目依赖——这一数字使其成为 Java 生态中无可争议的「基础设施级」项目。它的定位是补全 JDK 标准库的不足，为开发者提供更强大、更安全的集合、并发、I/O、哈希等工具。

项目包含 Google 内部几乎所有 Java 项目都在使用的基础组件：新的集合类型（如 Multimap、Multiset、BiMap）、不可变集合（Immutable* 系列）、图论库（Graph/ValueGraph/Network）、以及并发、I/O、缓存、字符串处理等领域的实用工具。它分为两个发行版本：面向 JRE 的标准版和面向 Android 的兼容版。

Guava 的独特价值在于「经过 Google 大规模生产环境验证」——它的每一个 API 都经过 Google 内部数万级服务的高并发考验，API 设计严谨、文档完善、废弃策略保守（提供 3 年以上的兼容窗口），这些特质让它成为企业级 Java 项目的默认选择。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **新集合类型** | Multimap（多值映射）、Multiset（多重集）、BiMap（双向映射）、Table（二维表）等 JDK 缺失的集合 |
| **不可变集合** | ImmutableList/Set/Map 系列，线程安全、内存高效、防御性编程利器 |
| **图论库** | Graph、ValueGraph、Network 三种抽象，支持遍历、最短路径等算法 |
| **并发工具** | ListenableFuture、RateLimiter（限流器）、Monitor、并发哈希等高级并发原语 |
| **缓存框架** | Guava Cache 本地缓存，支持过期策略、引用回收、统计指标 |
| **基础工具** | Preconditions 前置校验、Strings、MoreObjects、哈希（Hashing）、IO（ByteSource 等）、事件总线 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **主要语言** | Java（100%） |
| **构建工具** | Maven + Gradle（Android 变体） |
| **最低版本** | Java 8+（JRE 版） |
| **发布节奏** | 每月发布小版本，遵循语义化版本 |
| **许可证** | Apache-2.0 |

---

## 项目亮点

### Google 生产级质量背书
每一个 API 都来自 Google 内部真实业务的高并发场景，经过数十亿次调用验证。开箱即用的稳定性是它区别于普通开源库的最大优势。

### 不可变集合的工程价值
Immutable 系列集合天然线程安全且不可被外部修改，是编写健壮并发代码和防御性编程的基石，Java 开发中「能用不可变就不用可变」的实践离不开 Guava。

### 极致的兼容性承诺
Guava 对废弃 API 提供极长的兼容期，升级几乎无痛；同时维护 JRE 与 Android 双版本，覆盖服务端与移动端开发场景。

### 教科书级的 API 设计
Guava 的文档和 API 设计被视为 Java 库开发的典范，读 Guava 源码与文档本身就是提升 Java 功底的高效途径，影响了 JDK 本身的发展。

---

## 应用场景

### 企业级 Java 服务端开发
几乎所有大型 Java 微服务项目都会引入 Guava：用 ImmutableMap 构建配置、用 RateLimiter 保护下游、用 Cache 缓存热点数据。

### Android 应用开发
Guava Android 版为移动端提供去重、集合、字符串处理等工具，减少样板代码，提升代码质量。

### 数据处理与算法实现
图论库适用于依赖关系分析、路由计算等场景；Hashing 工具支持一致性哈希、布隆过滤器等分布式算法的实现。

### 单元测试与代码审查
Preconditions 与 MoreObjects 帮助编写防御性代码，使故障在最早的位置暴露；清晰的 API 让团队代码风格更统一、更易审查。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 51,560 |
| **总 Forks** | 11,155 |
| **今日新增 Stars** | 9 |
| **许可证** | Apache-2.0 |
| **主要语言** | Java |

---

## 总结

Google Guava 是 **Java 生态的基础设施级核心库**，51.6K Stars。它用经过 Google 大规模生产验证的集合、并发、缓存与工具类补全 JDK 短板，被 39.9 万项目依赖，是企业级 Java 开发事实上不可绕过的标准依赖。

---

*数据来源：GitHub 仓库 (google/guava)，2026 年 8 月访问*
