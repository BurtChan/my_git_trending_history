# Vaultwarden 项目分析

## 项目名称

**Vaultwarden** — 轻量级自托管 Bitwarden 服务器替代实现，用 Rust 编写

- **GitHub**: [dani-garcia/vaultwarden](https://github.com/dani-garcia/vaultwarden)
- **许可证**: AGPL-3.0

---

## 项目概述

Vaultwarden 是一个**非官方的 Bitwarden 客户端 API 服务器实现**，使用 Rust 语言编写。它完全兼容所有官方 Bitwarden 客户端（桌面端、移动端、浏览器扩展、CLI 和 Web Vault），允许个人、家庭和组织运行自己的私有密码管理服务器，无需依赖 Bitwarden 的云基础设施。

Vaultwarden 的核心价值在于**极致轻量**。官方 Bitwarden 服务器需要约 2 GB 内存和多个 Docker 容器，而 Vaultwarden 仅需约 50 MB 内存即可运行在单个二进制文件中。这使得它非常适合部署在树莓派、VPS、NAS 甚至旧笔记本电脑上，5 分钟内即可通过 Docker 完成部署。

项目原名 bitwarden_rs，后更名为 Vaultwarden 以避免与官方 Bitwarden 混淆。尽管是非官方实现，Vaultwarden 已获得 47k+ Stars，是 GitHub 上最受欢迎的自托管密码管理解决方案之一。它免费解锁了官方 Bitwarden 付费版才有的功能（如 TOTP 验证器存储、紧急访问等），近期还新增了 OpenID Connect SSO 支持，使其在企业级部署中更具吸引力。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **端到端加密** | 采用与 Bitwarden 相同的加密模型，确保只有用户可以访问自己的保险库数据 |
| **跨平台同步** | 无缝同步至所有平台——桌面（Windows/macOS/Linux）、移动（iOS/Android）、浏览器扩展和 Web Vault |
| **多因素认证（MFA）** | 支持 TOTP、YubiKey/WebAuthn、Duo 和邮件 2FA |
| **组织支持** | 团队/家庭的共享集合，支持细粒度访问控制 |
| **管理面板** | 内置 Web 管理面板，用于服务器管理、用户管理和诊断 |
| **OpenID Connect SSO** | 支持 OIDC 集中认证，兼容 Authentik、Keycloak、Google 等 IdP |
| **Bitwarden Send** | 支持临时加密分享文本和文件，可配置过期时间 |
| **紧急访问** | 指定受信任的人在紧急情况下请求访问你的保险库 |
| **TOTP 验证器存储** | 在保险库中存储 TOTP 密钥，替代独立验证器 App（官方免费版需付费） |
| **多数据库后端** | 支持 SQLite（默认）、MySQL/MariaDB 和 PostgreSQL |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Rust（83%+ 代码） |
| **Web 框架** | Rocket（异步 Rust Web 框架） |
| **ORM** | Diesel（支持 SQLite、MySQL、PostgreSQL） |
| **数据库** | SQLite（默认）、MySQL/MariaDB、PostgreSQL |
| **前端** | 修改版 Bitwarden Web Vault（容器中打包） |
| **认证** | JWT、argon2（密码哈希）、WebAuthn |
| **加密** | AES-256-CBC、RSA-2048+（ring、openssl） |
| **容器化** | Docker、Podman |
| **镜像仓库** | Docker Hub、GHCR、Quay.io |
| **安全** | Rust lint 禁止 unsafe_code |

---

## 项目亮点

### 超轻量单二进制部署
编译为单个 Rust 二进制文件，内存占用仅约 50 MB，对比官方 Bitwarden 服务器的 2+ GB 内存需求。可在树莓派、5 美元 VPS 或旧笔记本上流畅运行。

### 100% Bitwarden 客户端兼容
完全兼容所有官方 Bitwarden 应用（桌面、移动、浏览器扩展、CLI），用户无需任何修改即可使用，服务端对客户端完全透明。

### 免费解锁付费功能
免费提供官方 Bitwarden 付费版才有的功能，包括 TOTP 验证器存储、紧急访问和组织功能。

### OpenID Connect SSO 支持
近期新增的 OIDC SSO 支持（2025 年）是自托管环境的重大突破，可与 Authentik、Keycloak、Dex 等 IdP 集成，实现统一身份管理。

---

## 应用场景

### 个人/家庭自托管密码管理
注重隐私的用户在家庭服务器、树莓派或 NAS 上部署，通过反向代理（Nginx/Caddy）+ TLS 提供服务，享受 Bitwarden 客户端的完整体验同时保持数据完全自主。

### 小团队/组织共享密码库
小团队和组织使用 Vaultwarden 的组织功能进行共享密码管理，无需按用户付费的 Bitwarden 订阅费。支持基于角色的访问控制。

### 家庭密码共享
家庭成员通过共享集合共享 WiFi 密码、流媒体账号、保险信息等敏感凭据，每个成员拥有独立的主密码和 2FA。

### Homelab/SSO 集成身份中心
自托管爱好者将 Vaultwarden 与 OIDC 提供商（Authentik、Keycloak）集成，作为统一认证生态的一部分，一次登录即可访问所有自托管服务。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 66,071 |
| **总 Forks** | 3,124 |
| **今日新增 Stars** | 195 |
| **许可证** | AGPL-3.0 |
| **最新版本** | v1.35.2 |
| **主要语言** | Rust |

---

## 📋 更新记录

### 更新 1 — 2026 年 8 月 23 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单，今日新增 +68 Stars

**最新动态**：
- 距 4 月 24 日首次分析约四个月，Star 从约 47,000 增长至 65,876（+18,876），Fork 约 2,700 → 3,124，作为自托管 Bitwarden 兼容服务器的事实标准保持稳定增长
- Rust 轻量实现（单一二进制、SQLite/MySQL/PostgreSQL 后端可选、极低内存占用）对 homelab 与私有部署用户依然不可替代
- 随着密码安全与数据自托管意识的提升，配合 Vaultwarden 与官方客户端（桌面/移动/浏览器扩展）全兼容的特性，社区活跃度长期维持在高位

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 47,000 | 65,876 | +18,876 |
| 总 Forks | 2,700 | 3,124 | +424 |

**核心变化概要**：
- 四个月 Star 增长近 1.9 万，自托管密码管理刚需稳定
- Rust 单二进制轻量部署优势保持
- 与 Bitwarden 官方客户端全兼容的生态位无人替代

---

### 更新 2 — 2026 年 8 月 25 日（再次登上 Trending）
**更新原因**：项目再次登上 GitHub Trending 榜单

**最新动态**：Vaultwarden 连续三日在榜（8 月 23-25 日），Star 数从 65,876 增至 66,071，正式突破 6.6 万。自托管密码管理刚需持续释放，Rust 单二进制 + 极致轻量的部署优势与 Bitwarden 官方客户端全兼容的生态位依然无人替代。

**最新 Star 数据**：

| 指标 | 上次记录 | 最新数据 | 变化 |
|------|----------|----------|------|
| 总 Stars | 65,876 | 66,071 | +195 |
| 总 Forks | 3,134 | 3,135 | +1 |

**核心变化概要**：
- Star 数 65,876 → 66,071（+195），连续三天登上 Trending
- 自托管密码管理赛道需求稳定增长
- Rust 轻量实现 + Bitwarden 全兼容生态位保持独特优势

---

## 总结

Vaultwarden 是 GitHub 上最受欢迎的**自托管密码管理服务器**，47k+ Stars。它用 Rust 编写，以约 50 MB 内存的极致轻量实现了与官方 Bitwarden 完全兼容的 API，免费解锁付费功能（TOTP 存储、紧急访问、组织支持），近期新增 OIDC SSO 支持。是隐私敏感用户和自托管社区的首选密码管理方案。

---

*数据来源：GitHub 仓库 (dani-garcia/vaultwarden)（2026 年 4 月访问）*

*首次分析：见文件头部 | 最近更新：2026 年 8 月 25 日*
