# RustFS 项目分析

## 1. 项目名称与地址

**RustFS** -- 高性能分布式对象存储系统

**项目地址**：https://github.com/rustfs/rustfs

## 2. 项目概述

RustFS 是一个使用 Rust 语言从零构建的高性能分布式对象存储系统，完全兼容 Amazon S3 API。项目由 RustFS Inc. 团队开发和维护，于 2025 年正式开源，定位为 MinIO 的下一代替代方案。RustFS 将 MinIO 的简洁易用性与 Rust 语言的内存安全和原生性能深度结合，专为数据湖、AI 训练和大数据工作负载场景优化。

根据官方基准测试，在 4KB 小对象载荷场景下，RustFS 的吞吐量达到 MinIO 的 2.3 倍。与 MinIO 采用的 AGPL v3 许可证不同，RustFS 选择宽松的 Apache 2.0 许可证，消除了企业在商业使用中的许可证合规风险。项目同时支持从 MinIO 和 Ceph 平滑迁移，并为 OpenStack 用户提供原生 Swift API 支持。

RustFS 已入选 Runa Capital 发布的 ROSS Index（2025 Q4 最快增长开源初创项目），并获 HelloGitHub 中文开源推荐平台收录。项目支持中文、英语、日语、韩语、德语、法语、西班牙语、葡萄牙语、俄语等九种语言的文档。

## 3. 核心功能

- **S3 完全兼容**：100% 兼容 S3 API，可无缝替换任何使用 S3 协议的应用程序和工具。现有基于 AWS SDK 的代码无需修改即可对接 RustFS。
- **高性能对象存储**：Rust 语言原生实现，无垃圾回收（GC）暂停，内存安全由编译器保证。在 4KB 对象载荷场景下比 MinIO 快 2.3 倍。
- **分布式架构**：可扩展的容错设计，支持大规模集群部署。分布式模式目前处于测试阶段（Under Testing），单体模式已稳定可用。
- **OpenStack Swift API 支持**：原生支持 OpenStack Swift 协议，集成 Keystone 身份认证（X-Auth-Token），Swift 元数据操作部分支持。
- **多租户隔离**：支持多租户环境下的资源隔离和配额管理，适合企业级共享存储平台。
- **数据完整性保护（Bitrot Protection）**：通过校验和机制检测和防止静默数据损坏，确保存储数据的长期完整性。
- **版本控制与跨区域复制**：支持对象版本管理（Versioning）和跨区域的桶复制（Bucket Replication），满足数据保护和灾备需求。
- **生命周期管理**：支持对象生命周期策略配置（Under Testing），可自动迁移或过期删除数据。
- **事件通知**：支持存储事件的实时通知机制，可与消息队列和 Serverless 函数集成。
- **KMS 密钥管理**：内置密钥管理服务（RustFS KMS，Under Testing），支持服务端加密。
- **数据主权合规**：零遥测设计，不收集任何使用数据。符合 GDPR（欧盟/英国）、CCPA（美国）、APPI（日本）等数据保护法规。
- **Web 管理控制台**：内置功能完善的管理界面，支持可视化的桶管理、对象上传下载、策略配置等操作。
- **K8s 原生部署**：提供 Helm Chart，一键部署到 Kubernetes 集群。

## 4. 技术栈

- **核心语言**：Rust（100%）
- **部署方式**：
  - Docker（官方镜像 `rustfs/rustfs`，支持 amd64/arm64）
  - Podman
  - Kubernetes（Helm Chart）
  - Nix Flake
  - X-CMD
  - 一键安装脚本
- **构建工具**：cargo、Makefile、docker-buildx（多架构：linux/amd64、linux/arm64）
- **可观测性集成**：Grafana（仪表盘）、Prometheus（指标采集）、Jaeger（分布式追踪）、Redis、Nginx
- **API 端口**：S3 API（端口 9000）、Web 控制台（端口 9001）
- **容器运行**：以非 root 用户 `rustfs`（UID 10001）运行
- **许可证**：Apache 2.0
- **CI/CD**：GitHub Actions（CI 构建与测试、Docker 镜像自动构建推送）

### 压力测试环境

| 类型 | 参数 | 备注 |
|------|------|------|
| CPU | 2 核 | Intel Xeon (Sapphire Rapids) Platinum 8475B, 2.7/3.2 GHz |
| 内存 | 4GB | |
| 网络 | 15Gbps | |
| 磁盘 | 40GB x 4 | IOPS 3800 / Drive |

### 安装部署方法

**方式一：一键安装脚本**
```bash
curl -O https://rustfs.com/install_rustfs.sh && bash install_rustfs.sh
```

**方式二：Docker 快速启动**
```bash
# 创建数据和日志目录
mkdir -p data logs

# 修改目录权限（容器以 UID 10001 运行）
chown -R 10001:10001 data logs

# 启动最新版本
docker run -d -p 9000:9000 -p 9001:9001 \
  -v $(pwd)/data:/data \
  -v $(pwd)/logs:/logs \
  rustfs/rustfs:latest
```

**方式三：Docker Compose（含可观测性栈）**
```bash
docker compose --profile observability up -d
```
注意：docker-compose.yml 包含 Grafana、Prometheus、Jaeger 等服务，建议先查看配置。

**方式四：Kubernetes Helm Chart**
```bash
# 按照 Helm Chart README 中的说明在 K8s 集群中安装
```

**方式五：源码编译（高级用户）**
```bash
# 多架构本地构建
./docker-buildx.sh --build-arg RELEASE=latest

# 构建并推送到镜像仓库
./docker-buildx.sh --push

# 构建指定版本
./docker-buildx.sh --release v1.0.0 --push

# 或使用 Make 命令
make docker-buildx
make docker-buildx-push
```
注意：macOS 交叉编译时需先执行 `ulimit -n 4096` 以避免文件描述符限制。

**方式六：Nix Flake**
```bash
nix run github:rustfs/rustfs
# 或构建二进制
nix build github:rustfs/rustfs
./result/bin/rustfs --help
```

**方式七：X-CMD**
```bash
x rustfs                    # 直接运行
x env use rustfs            # 安装到全局环境
```

**访问控制台**：浏览器打开 `http://localhost:9001`，默认凭据 `rustfsadmin` / `rustfsadmin`。

## 5. 项目亮点

### 性能对比：RustFS vs MinIO

在 4KB 小对象载荷场景下，RustFS 的吞吐量是 MinIO 的 **2.3 倍**。这一性能优势源于 Rust 语言的零成本抽象和无 GC 暂停特性。

### 全面对比表

| 对比维度 | RustFS | 其他对象存储（MinIO 等） |
|----------|--------|--------------------------|
| 控制台体验 | 功能完善的管理界面，全面的可视化管理 | 基础/有限的控制台，功能简陋或缺失关键特性 |
| 语言与安全性 | 基于 Rust，内存安全由编译器保证 | 基于 Go 或 C，存在 GC 暂停或内存泄漏风险 |
| 数据主权 | 零遥测，完全合规 GDPR/CCPA/APPI | 存在遥测风险，可能的法律风险 |
| 许可证 | Apache 2.0，商业友好 | AGPL v3，商业使用受限 |
| 兼容性 | 100% S3 兼容，支持所有云厂商和客户端 | 兼容性参差不齐，可能缺乏部分 API 支持 |
| 边缘与 IoT | 轻量级，适合安全边缘设备 | 过于笨重，不适合边缘网关 |
| 企业风险 | 清晰的 IP 权利，安全的商业使用 | 知识产权模糊，使用限制 |

### 功能状态一览

| 功能 | 状态 | 功能 | 状态 |
|------|------|------|------|
| S3 核心功能 | 已上线 | Bitrot 保护 | 已上线 |
| 上传/下载 | 已上线 | 单节点模式 | 已上线 |
| 版本控制 | 已上线 | 桶复制 | 已上线 |
| 日志 | 已上线 | 生命周期管理 | 测试中 |
| 事件通知 | 已上线 | 分布式模式 | 测试中 |
| K8s Helm Chart | 已上线 | RustFS KMS | 测试中 |
| Keystone 认证 | 已上线 | 多租户 | 已上线 |
| Swift API | 已上线 | Swift 元数据操作 | 部分支持 |

### API 兼容性说明

RustFS 提供 100% S3 API 兼容性，这意味着：
- 所有使用 AWS SDK（Java/Python/Go/Node.js 等）的应用可直接切换到 RustFS
- 支持 S3 的标准操作：GET/PUT/DELETE/HEAD Object、List Objects、Multipart Upload 等
- 兼容 S3 客户端工具（aws-cli、s3cmd、rclone 等）
- 原生支持 OpenStack Swift API，可同时服务两套协议生态

## 6. 应用场景

- **AI/ML 数据湖**：为机器学习训练数据集提供高性能、低延迟的对象存储后端，适合大规模模型训练场景
- **MinIO 替代方案**：企业寻求商业友好许可证（Apache 2.0 vs AGPL v3）的对象存储替换方案，可从 MinIO 平滑迁移
- **边缘计算与 IoT**：Rust 的轻量级和低资源消耗特性使其非常适合边缘网关和 IoT 设备的本地存储
- **大数据分析平台**：作为 Spark、Presto、Hive 等大数据引擎的高吞吐存储后端
- **备份与归档**：利用版本控制和生命周期管理功能构建自动化的数据归档方案
- **合规敏感行业**：金融、医疗、政府等对数据主权有严格要求的机构，零遥测设计从架构层面保障数据不越境
- **OpenStack 环境**：原生 Swift API 支持使其可直接集成到现有 OpenStack 云平台
- **混合云/多云部署**：K8s Helm Chart 支持使跨云部署变得简单

## 7. Star 数据

- 总 Star 数：25,222
- Fork 数：1,072
- 今日增长：+182

## 8. 总结

RustFS 是对象存储领域一个强有力的挑战者，以 Rust 的原生性能优势为核心卖点，用 Apache 2.0 许可证解决了 MinIO AGPL 的商业限制问题。2.3 倍的性能提升和零遥测的数据主权设计，对追求性能和合规的企业极具吸引力。

项目提供了业界最丰富的部署方式选择（7 种安装方式），从一键脚本到 Kubernetes Helm Chart 覆盖了各种部署场景。功能矩阵显示核心存储功能已全部上线，分布式模式等高级功能正在测试中，适合在生产环境中逐步采用。

作为 ROSS Index 上最快增长的开源项目之一，RustFS 入选 Runa Capital 2025 Q4 榜单，并获 HelloGitHub 推荐，在云原生存储赛道上值得密切关注。项目活跃的社区贡献和持续的功能开发表明其正在快速成熟。
