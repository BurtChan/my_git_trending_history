# 项目名称

**Keycloak** — 开源身份与访问管理平台

GitHub 地址：[https://github.com/keycloak/keycloak](https://github.com/keycloak/keycloak)

---

# 项目概述

Keycloak 是由 Red Hat（现为 IBM 子公司）主导开发的开源身份与访问管理（IAM）解决方案，专为现代应用和服务设计。该项目于 2013 年 7 月创建，最初作为 JBoss 社区项目孵化，如今已成为全球最受欢迎的开源 IAM 平台之一。2023 年 4 月，Keycloak 正式加入 CNCF（云原生计算基金会）成为孵化项目，标志着其在云原生生态中的战略地位得到行业认可。

Keycloak 提供了一套完整的、开箱即用的 IAM 服务，以单一轻量级容器镜像交付，极大地简化了部署和扩展流程。其核心理念是让开发者能够以最小的工作量为应用程序添加身份认证功能，同时为企业提供强大的用户管理、细粒度授权和安全合规能力。

项目采用 Apache-2.0 许可证，完全免费且开放，这意味着企业可以零成本获得与 Auth0、Okta 等商业 IAM 产品功能对等的解决方案，并享有完全的自主可控权。截至最新数据，Keycloak 已累计获得超过 35,100 个 GitHub Star，8,500+ Fork，31,428 次提交，108 个正式版本发布（最新版本 26.6.3），展现了极其活跃的开发节奏和强大的社区生命力。

---

# 核心功能

## 1. 单点登录（SSO）与身份联邦

Keycloak 支持基于 **OpenID Connect（OIDC）** 和 **SAML 2.0** 协议的单点登录，用户只需一次登录即可访问多个应用。其身份联邦功能允许将 Keycloak 与外部身份提供者（如 Google、GitHub、Facebook、LinkedIn、Azure AD 等）集成，实现社交登录和企业身份打通。最新版本还支持身份代理（Identity Brokering）API，可在认证过程中存储和管理外部身份提供者颁发的令牌和响应。

## 2. 用户管理与用户联邦

Keycloak 提供全面的用户管理功能，包括用户创建、角色分配、分组管理、属性管理等。其独特的**用户联邦（User Federation）**机制支持与 LDAP、Active Directory、Kerberos 等传统企业目录服务无缝集成，使企业无需迁移现有用户数据即可享受现代化的身份管理体验。同时支持 SCIM 2.0 协议（实验性），实现跨组织的用户自动同步。

## 3. 强身份认证（MFA & Passkeys）

Keycloak 支持多种多因素认证（MFA）方式，包括：
- **OTP（一次性密码）**：基于 TOTP/HOTP 标准
- **WebAuthn/Passkeys**：基于生物识别和硬件安全密钥的无密码认证（已正式支持）
- **条件认证（Conditional Authentication）**：根据用户上下文动态调整认证策略
- **X509 证书认证**：适用于高安全要求的场景
- **FAPI 2 Final 与 DPoP**：提供金融级安全保障

## 4. 细粒度授权

Keycloak 提供基于策略的授权服务，支持 UMA 2.0（用户管理的访问控制），允许资源所有者精细化控制谁可以访问其资源。通过策略执行器（Policy Enforcer），开发人员可以在应用层面实现声明式和编程式的访问控制，支持 JavaScript、Node.js 等多种语言的策略执行。

## 5. 工作流引擎

最新版本正式支持 **Workflows（工作流）** 功能，管理员可以自定义用户注册、邮箱更新等业务流程的审批和执行逻辑，极大地提升了在复杂企业场景中的适配能力。

## 6. 联合客户端认证

Keycloak 26.6.0 引入了**联合客户端认证（Federated Client Authentication）**，消除了在 Keycloak 中为每个客户端管理独立密钥的繁琐工作。支持外部 OpenID Connect 身份提供者颁发的客户端断言以及 Kubernetes Service Account 认证。

## 7. 持久化用户会话

从版本 26 开始，**持久化用户会话（Persistent User Session）** 默认启用，会话数据自动保存到数据库中，在分布式部署场景下提供更可靠的用户会话体验，节点间同步更加高效。

---

# 技术栈

## 编程语言构成

| 语言 | 占比 | 用途 |
|------|------|------|
| **Java** | 91.8% | 核心服务引擎、认证授权逻辑、管理控制台后端 |
| **TypeScript** | 7.2% | 管理控制台前端（基于 React），REST API 客户端 |
| **FreeMarker** | 0.6% | 邮件模板、主题页面渲染 |
| **其他** | 0.4% | 配置文件、脚本等 |

## 核心框架与架构

- **Quarkus 框架**：Keycloak 从 WildFly 迁移到 Quarkus 框架是近年最重要的架构变革。Quarkus 提供了更快的启动速度、更低的内存占用以及与 Kubernetes 的深度集成能力，使 Keycloak 在云原生环境中的表现显著提升。
- **Jakarta EE**：基于 Jakarta EE 标准构建，确保与企业级 Java 生态的兼容性。
- **Infinispan**：内置分布式缓存支持，为集群部署提供高性能的会话和缓存管理。
- **Hibernate ORM**：支持 PostgreSQL、MySQL、MariaDB、Oracle、Microsoft SQL Server 等多种数据库。

## 关键目录结构

| 目录 | 说明 |
|------|------|
| `core/` | 核心引擎代码，包含认证、授权、用户管理等核心模块 |
| `quarkus/` | Quarkus 框架集成层，包含容器化部署配置 |
| `operator/` | Kubernetes Operator，实现 Keycloak 在 K8s 环境中的自动化运维 |
| `adapters/` | 各语言/框架的适配器（Spring Boot、Node.js、JavaScript 等） |
| `saml-core/` | SAML 2.0 协议核心实现 |
| `authz/` | 授权服务模块，实现基于策略的细粒度访问控制 |
| `crypto/` | 加密模块，处理令牌签名、密钥管理等 |
| `rest/` | RESTful API 接口层 |
| `scim/` | SCIM 2.0 用户管理协议支持 |

## 部署方式

```bash
# 本地开发启动
bin/kc.sh start-dev

# Docker 容器启动
docker run quay.io/keycloak/keycloak start-dev

# Kubernetes 部署（通过 Operator）
kubectl apply -f keycloak-operator.yaml
```

---

# 项目亮点

## 1. CNCF 孵化项目，云原生身份管理标杆

Keycloak 于 2023 年加入 CNCF 成为孵化项目，与 Argo、Envoy、Jaeger、Kubernetes 等云原生核心项目形成深度集成生态。CNCF 的背书为其在企业级市场的采用提供了强有力的信任基础，也意味着 Keycloak 正在从传统的 Java EE 应用向真正的云原生身份基础设施演进。

## 2. 开源免费，Auth0/Okta 的强力替代方案

在 IAM 市场被 Auth0（被 Okta 收购）和 Okta 等商业产品主导的格局下，Keycloak 以完全开源免费的方式提供了功能对等的解决方案。据 Phase Two 等专业服务商的评价，Keycloak "在所有主要功能上与商业 IAM 系统完全对等"。对于注重数据主权、合规性和成本控制的企业（尤其是欧洲和亚太市场），Keycloak 是极具吸引力的选择。

## 3. Quarkus 架构迁移，性能飞跃

从 WildFly 迁移到 Quarkus 是 Keycloak 历史上最重要的架构升级。Quarkus 的原生编译（GraalVM）支持、快速启动（毫秒级）和低内存占用使 Keycloak 能够更好地适应 Serverless、Kubernetes 等云原生部署模式。这一迁移也体现了项目团队对技术趋势的前瞻性判断。

## 4. 无密码认证（Passkeys）的先行者

Keycloak 是首批正式支持 Passkeys/WebAuthn 认证的主流开源 IAM 平台之一，这与 2026 年 IAM 行业趋势——无密码认证成为企业基准线——高度契合。Gartner 的 2026 年战略技术趋势报告强调，身份优先的安全基础架构是应对日益复杂的数字生态系统风险的关键。

## 5. 企业级运维能力完善

Red Hat 提供商业支持的 **Red Hat build of Keycloak**，从版本 26.x 起提供至少 2 年的完整支持周期（27.x 起为 3 年），为企业客户提供了长期稳定的升级路径。同时，Keycloak 26.1 引入了基于 Prometheus 的服务等级指标（SLI）监控，包括可用性、延迟和错误率追踪。

## 6. 极为活跃的开发节奏

31,428 次提交、108 个版本发布，平均每年发布约 9-10 个版本。这种高频迭代确保了安全漏洞的快速修复和新特性的持续交付，也反映了背后庞大的开发者社区和 Red Hat 专业团队的投入。

---

# 应用场景

## 1. 企业单点登录（SSO）门户

Keycloak 最常见的应用场景是作为企业内部的统一身份认证门户，将 OA、CRM、ERP、DevOps 平台等多个系统的认证统一到 Keycloak，实现一次登录、全网通行。通过 LDAP/AD 联邦，可以直接复用企业现有的用户目录。

## 2. 零信任架构的身份基础

在零信任安全模型中，"永不信任，始终验证"是核心理念。Keycloak 作为零信任架构的身份层基础设施，为每个请求提供实时、基于上下文的身份验证和授权决策。CNCF 官方博客专门撰文介绍了如何利用 Keycloak 26.2 构建应用层的零信任架构。

## 3. B2B/B2C 多租户 SaaS 平台

Keycloak 的 Realm 机制天然支持多租户架构。每个租户（Realm）拥有独立的用户、角色、策略和配置，但共享同一个 Keycloak 实例。这种架构非常适合 SaaS 平台的场景，配合 SAML adapter 的多租户支持，可以实现更灵活的租户定制。

## 4. 微服务 API 安全网关

在微服务架构中，Keycloak 充当集中式的令牌发放和验证中心，通过 OIDC 令牌为服务间通信提供身份保障。配合 Envoy 等 Service Mesh 技术，可以在不修改应用代码的情况下实现 API 级别的认证和授权。

## 5. Kubernetes 集群身份管理

Keycloak 提供了官方的 Kubernetes Operator，支持在 K8s 环境中的一键部署和自动化运维。通过联合客户端认证功能，可以直接使用 Kubernetes Service Account 进行身份验证，实现容器化环境中的身份管理与集群身份的深度融合。

## 6. 政务与医疗行业统一身份平台

Keycloak 已被多个大型政务和医疗项目采用。例如，巴西政府的 Gov.br 平台通过 IFTM 集成 Keycloak 实现面向数百万公民的 SSO 服务；日本已有超过 20 万医疗用户通过 Azure 上的 Keycloak 实现统一身份管理。

---

# Star 数据

| 指标 | 数据 |
|------|------|
| **总 Star 数** | 35,122 |
| **总 Fork 数** | 8,548 |
| **今日新增 Star** | 11 |
| **主要语言** | Java（91.8%） |
| **开源协议** | Apache-2.0 |
| **创建时间** | 2013 年 7 月 2 日 |
| **总提交数** | 31,428 |
| **总版本数** | 108（最新 26.6.3） |
| **CNCF 状态** | 孵化项目（Incubating） |
| **Fork/Star 比率** | 约 24.3%（表明较高的社区参与深度） |
| **日均 Star 增长** | 约 8-12（持续稳定增长，非爆发式） |

Keycloak 的 Star 增长曲线呈现稳定上升态势，而非爆发式增长。这种模式反映了 IAM 领域的特性——企业客户的技术选型周期较长，但一旦选定便具有极高的粘性。当前 35,000+ 的 Star 数在 Java 生态中位居前列，在安全/IAM 细分领域仅次于 HashiCorp Vault 等少数项目。

---

# 总结

Keycloak 是当今开源 IAM 领域最具影响力和成熟度的项目，也是企业数字化身份基础设施的关键选择。从 2013 年诞生至今，它经历了从 JBoss 社区项目到 CNCF 孵化项目的蜕变，完成了从 WildFly 到 Quarkus 的架构飞跃，始终走在身份安全领域的技术前沿。

## 核心竞争力总结

1. **标准先行**：深度支持 OIDC、SAML 2.0、OAuth 2.0、SCIM 2.0、FAPI 2、UMA 2.0 等主流身份安全标准，确保与生态系统的广泛兼容。
2. **架构现代**：基于 Quarkus 的云原生架构，加上 Kubernetes Operator、分布式部署、持久化会话等能力，使其在容器化和微服务场景中表现卓越。
3. **安全前沿**：Passkeys/WebAuthn 无密码认证、DPoP 令牌绑定、FAPI 2 金融级安全等特性，使其始终走在安全趋势前列。
4. **企业就绪**：Red Hat 商业支持、完善的文档、活跃的社区、CNCF 治理框架，为企业级采用提供了全方位保障。
5. **成本优势**：零许可证费用、自主可控的数据主权、灵活的部署方式（公有云/私有云/混合云/本地），在与 Auth0、Okta 的竞争中具备独特的价值主张。

## 行业背景与趋势

全球 IAM 市场规模预计将从 2025 年的 218.1 亿美元增长至 2026 年的 252.3 亿美元（CAGR 15.7%）。随着零信任架构的普及、无密码认证成为企业基准、AI 驱动的安全威胁日益严峻，以及非人类身份（机器身份、AI Agent 身份）管理的需求爆发，身份安全正从"IT 运维工具"升级为"企业安全核心基础设施"。Keycloak 凭借其开源、标准、可扩展的特性，正处于这一历史性趋势的有利位置。

对于关注云原生安全、零信任架构和身份治理的开发者和企业来说，Keycloak 是一个值得深入研究和投入的战略级开源项目。其 35,000+ Star 的社区规模和持续的高频迭代，预示着这个项目将在未来相当长的时间内持续引领开源 IAM 领域的发展方向。
