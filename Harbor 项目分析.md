# Harbor 项目分析

> **一句话总结** — Harbor 是由 CNCF 托管的 graduated 级别云原生制品仓库，提供容器镜像和 Helm Chart 的安全扫描、数字签名、访问控制和多 Registry 间策略复制，是企业构建可信容器供应链的核心基础设施。

- **GitHub**: [goharbor/harbor](https://github.com/goharbor/harbor)
- **语言**: Go
- **Stars**: 27,971 | **今日新增**: 23
- **Forks**: 5,165
- **许可证**: Apache 2.0
- **CNCF 状态**: Graduated（毕业项目）
- **最初作者**: VMware
- **安全审计**: Cure53（2019 年）

---

## 解决什么问题

在云原生时代，容器镜像是应用交付的基本单元。然而原生的 Docker Distribution（Registry）仅提供基础的存储和分发能力，缺少企业级场景所需的安全管控、身份认证、访问控制、漏洞扫描、镜像签名和跨数据中心同步等关键功能。

Harbor 的核心使命是成为 **Kubernetes 生态的可信云原生制品仓库**。它在 Docker Distribution 之上构建了一整套企业级能力，让组织能够：

- **统一管理**多种云原生制品（容器镜像、Helm Chart、CNAB、OPA 策略等）
- **保障安全合规**——通过漏洞扫描阻止有风险的镜像上线，通过内容签名确保镜像来源可信
- **跨环境协作**——通过策略驱动的复制实现混合云、多数据中心场景下的镜像同步
- **细粒度管控**——基于项目的 RBAC 权限体系，对接 LDAP/AD/OIDC 企业身份系统

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **云原生制品仓库** | 完全兼容 OCI 规范，支持容器镜像、OCI Image Index（多架构镜像）、Helm Chart、CNAB、OPA 策略等多种制品类型 |
| **基于角色的访问控制 (RBAC)** | 通过"项目"隔离资源，用户在不同项目中拥有不同权限，支持机器人账号 |
| **策略驱动的复制** | 支持 12+ 种 Registry 适配器（Docker Hub、AWS ECR、GCP GCR、Azure ACR、阿里云 ACR、华为 SWR、Quay、GitLab 等），可按仓库/标签/标签过滤规则自动同步，支持负载均衡和高可用部署 |
| **漏洞扫描** | 内置 Trivy（Aqua Security），同时支持 Anchore Engine、Clair（Red Hat）、DoSec 等多种扫描器，可配置策略阻止有漏洞的镜像被部署 |
| **内容信任与签名** | 通过 Notary 实现 Docker Content Trust，支持镜像签名验证，可设置策略阻止未签名镜像部署 |
| **LDAP/AD 集成** | 对接企业目录服务进行用户认证，支持导入 LDAP 组并授权到项目 |
| **OIDC/SSO 支持** | 通过 OpenID Connect 对接外部身份提供商，支持单点登录 |
| **镜像删除与垃圾回收** | 自动清理悬空 manifest 和未引用 blob，定期释放存储空间 |
| **配额管理** | 按项目设置存储配额，推送时自动校验 |
| **Tag 保留策略** | 可按规则自动清理历史标签，控制仓库膨胀 |
| **Webhook 通知** | 制品状态变更时通过 HTTP POST 或 Slack 通知外部系统 |
| **操作审计** | 所有仓库操作通过日志完整追踪 |
| **RESTful API** | 完整的管理 API，内嵌 Swagger UI 便于集成与调试 |
| **图形化管理门户** | 提供直观的 Web UI 浏览、搜索仓库和管理项目 |
| **Cosign 签名验证** | 从 v2.15.0 起，发布产物使用 Cosign 进行密码学签名，确保下载完整性 |

---

## 技术栈

| 层级 | 组件 | 说明 |
|------|------|------|
| **核心语言** | Go | 后端服务全部使用 Go 编写 |
| **前端** | Angular | Web 管理门户 |
| **反向代理** | Nginx | 统一入口，路由 API 和 Web 请求 |
| **制品存储** | Docker Distribution (OCI) | 底层 Registry，处理 push/pull 命令 |
| **Chart 仓库** | ChartMuseum | 第三方 Helm Chart 仓库服务器 |
| **内容信任** | Notary | 镜像签名与验证服务 |
| **数据库** | PostgreSQL | 存储项目、用户、角色、复制策略、扫描器等元数据 |
| **缓存/KV** | Redis | 数据缓存与 Job Service 临时任务元数据持久化 |
| **存储后端** | 文件系统 / S3 / OSS / GCS / Azure Blob 等 | 支持多种对象存储和本地文件系统 |
| **异步任务** | Job Service | 通用任务执行队列，处理复制、扫描、GC 等异步操作 |
| **容器编排** | Docker Compose / Kubernetes (Helm Chart) / Operator | 三种部署方式 |
| **CI/CD** | GitHub Actions | 持续集成与发布流水线 |
| **安全扫描** | Trivy / Clair / Anchore / DoSec | 可插拔的多扫描器架构 |

---

## 使用场景

| 场景 | 说明 |
|------|------|
| **企业私有 Registry** | 在防火墙内部署私有镜像仓库，满足数据主权和安全合规要求，避免依赖公有云 Registry |
| **混合云/多云镜像同步** | 通过策略复制在多个数据中心和云平台之间自动同步镜像，实现负载均衡和灾备 |
| **CI/CD 镜像供应链** | 集成到 Jenkins/GitLab CI/GitHub Actions 等流水线，推送镜像后自动触发漏洞扫描和签名 |
| **Kubernetes 集群镜像仓库** | 通过 Helm Chart 一键部署到 K8s 集群，作为集群内应用交付的镜像来源 |
| **安全合规审计** | 利用漏洞扫描策略阻止高危镜像上线，操作审计日志满足金融、医疗等行业的合规要求 |
| **多租户平台** | 通过项目和 RBAC 实现多团队/多业务线隔离，统一管理企业内所有容器制品 |
| **边缘计算场景** | 在边缘节点附近部署 Harbor 实例，加速镜像拉取，减少中心化依赖 |

---

## 知名用户与合作伙伴

- **用户**: CERN（欧洲核子研究中心）、中国移动、京东、网易、OVHcloud、Dynatrace、Trend Micro、荷兰铁路等
- **合作伙伴**: VMware、Rancher、Aqua Security、Anchore、Sysdig、灵雀云等

---

## 一句话总结

> Harbor 是 CNCF 毕业级的云原生制品仓库，为企业提供从安全扫描、内容签名到跨云复制的全链路镜像治理能力，是构建可信容器供应链的事实标准选择。
