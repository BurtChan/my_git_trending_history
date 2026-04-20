# Xray-core 项目分析

## 项目名称

**Xray-core** — 高性能网络代理平台，支持 VLESS/XTLS/REALITY 等多种协议

- **GitHub**: [XTLS/Xray-core](https://github.com/XTLS/Xray-core)
- **许可证**: Mozilla Public License Version 2.0（MPL-2.0）

---

## 项目概述

Xray-core 是 Project X 的核心组件，源自 XTLS 协议，是一个功能强大的开源网络代理平台。它被广泛认为是最好的 v2ray-core 替代方案，支持多种代理协议和传输方式，包括独创的 VLESS、XTLS、REALITY 等协议。项目采用 Go 语言编写，拥有 1,800+ 次提交和活跃的开发者社区。

Xray-core 的核心优势在于其**协议创新**。项目原创了 VLESS 协议（极简轻量的代理协议）、XTLS（零开销的 TLS 代理技术）和 REALITY（无需域名和证书的 TLS 伪装技术），这些创新极大地降低了代理部署的门槛和成本。REALITY 协议无需购买域名和配置 TLS 证书，即可伪装成访问真实网站的 TLS 流量，是目前最前沿的代理技术之一。

Xray-core 还积极跟进最新的网络技术：最新版本已支持 TUN 入站（Windows & Linux，包括 Android）、Hysteria 2 出站和传输、WireGuard 协议等。项目提供跨平台支持，可通过 systemd、Homebrew 等方式安装，同时拥有丰富的 GUI 客户端生态。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **VLESS 协议** | 极简轻量代理协议，低开销高效率，支持 XTLS 直接转发 |
| **XTLS 技术** | 零开销 TLS 代理，无需额外加解密层，大幅提升传输性能 |
| **REALITY 协议** | 无需域名和 TLS 证书的 TLS 伪装技术，伪装成访问真实网站 |
| **多协议支持** | 支持 VMess、VLESS、Shadowsocks、Trojan、WireGuard、Hysteria 2 等 |
| **多种传输方式** | 支持 TCP、WebSocket、gRPC、HTTP/2、QUIC、XHTTP 等 |
| **TUN 入站** | 支持系统级透明代理（Windows/Linux/Android），无需手动配置代理 |
| **多路复用** | 支持连接多路复用（XUDP、PLUX），提升并发性能 |
| **可观测性** | 内置流量统计和日志系统，方便运维监控 |
| **跨平台** | 支持 Linux、Windows、macOS、Android、iOS（第三方客户端） |
| **Docker 支持** | 提供官方容器镜像，支持一键 Docker 部署 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Go |
| **协议** | VLESS、VMess、Shadowsocks、Trojan、WireGuard、Hysteria 2 |
| **传输层** | TCP、WebSocket、gRPC、HTTP/2、QUIC、XHTTP |
| **TLS 技术** | XTLS、REALITY、uTLS |
| **透明代理** | TUN 模式（Windows/Linux/Android） |
| **容器化** | Docker（官方镜像 xray-core） |
| **安装方式** | systemd、Homebrew、一键脚本 |
| **许可证** | Mozilla Public License 2.0 |

---

## 项目亮点

### 🚀 协议创新引领者
原创 VLESS、XTLS、REALITY 三大核心技术。其中 REALITY 协议无需购买域名和配置 TLS 证书，即可生成与真实网站完全一致的 TLS 指纹，是目前代理领域最前沿的技术突破。

### ⚡ 极致性能
XTLS 技术通过直接转发 TLS 内层流量，避免了传统代理中额外的加解密开销，实现了接近零性能损失的代理传输，在高带宽场景下优势尤为明显。

### 🔗 丰富的协议生态
不仅兼容 v2ray-core 的 VMess 协议，还持续集成最新的代理协议（Hysteria 2、WireGuard 等），并通过 XHTTP 等创新传输方式应对各种网络环境。

### 🌐 完善的客户端生态
拥有丰富的 GUI 客户端生态，覆盖 v2rayN（Windows）、v2rayNG（Android）、Nekoray/Nekobox（跨平台）、Streisand（iOS）等多平台客户端，普通用户也能轻松使用。

---

## 应用场景

### 🌍 网络自由访问
通过 REALITY 等协议伪装成正常 HTTPS 流量，在严格网络审查环境下安全可靠地访问全球互联网资源。

### 🏢 企业远程办公
为企业员工提供安全的远程访问通道，TUN 模式支持全局透明代理，无需逐应用配置，简化远程办公网络设置。

### 🔒 隐私保护
通过加密代理保护网络通信隐私，防止 ISP 和中间人对网络流量的监听和分析，保障个人通信安全。

### 🧪 网络研究与测试
作为网络协议研究的实验平台，Xray-core 的模块化架构支持自定义协议和传输方式开发，适合网络安全研究人员使用。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 35,600+ |
| **总 Forks** | 5,000+ |
| **今日新增 Stars** | ~52 |
| **许可证** | Mozilla Public License 2.0 |
| **主要语言** | Go |
| **总提交数** | 1,799+ |
| **发布版本** | 111+ |

---

## 总结

Xray-core 是**高性能网络代理平台的技术标杆**，35.6k+ Stars。它基于 Go 语言构建，原创了 VLESS、XTLS、REALITY 三大核心技术，其中 REALITY 协议无需域名和证书即可实现 TLS 伪装，是代理领域的重大创新。项目兼容 VMess 等传统协议，同时积极集成 Hysteria 2、WireGuard 等新技术，拥有 111+ 个发布版本和完善的跨平台客户端生态，是网络代理领域最具影响力的开源项目之一。

---

*数据来源：GitHub 仓库 (XTLS/Xray-core)、xtls.github.io 官方文档（2026 年 4 月访问）*
