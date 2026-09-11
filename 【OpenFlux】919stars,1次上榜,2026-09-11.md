# OpenFlux 项目分析

## 项目名称

**OpenFlux** — 网络栈研究工具：把 TCP 流量封装进 Yandex Docs 光标消息的可插拔传输隧道

- **GitHub**: [p1neappleXpress/OpenFlux](https://github.com/p1neappleXpress/OpenFlux)
- **许可证**: GPL-3.0

---

## 项目概述

OpenFlux 自称「Network stack research tool. TCP tunnel with pluggable transports」，架构是 `Client (SOCKS5) → Transport → Exit Node → Internet`：客户端在本地跑一个 SOCKS5 代理，把 TCP 流量封装成所选传输通道的消息流，出口节点解封装后转发到真实互联网。它的噱头在于传输后端的选材——**Yandex Docs 在线文档的光标消息**（协作编辑时不断广播的光标位置更新）被用作数据载体，另一个可选后端是 MAX Messenger 的 WebRTC datachannel。

换句话说，防火墙看到的只是「有人在协作编辑文档」，而实际承载的是任意 TCP 流量。这是 domain-fronting / 协作平台隧道（类似把流量藏进 Telegram/Google Docs 的思路）的最新变体。项目仅 16 次提交、Go 语言实现，结构清晰：transport 接口层（可插拔新增后端）、tunnel 核心（虚拟网卡端点、raw socket）、SOCKS5 服务、网络校验与解析。README 注明「Educational use only. Test on your own machines and networks」，且当前要求使用 Yandex Docs 旧版编辑器。

今日 +201 Star、总 919 Star，传播显然由「用文档光标传流量」的话题性驱动。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| SOCKS5 客户端 | 本地 :1080 代理，浏览器/应用即插即用 |
| 可插拔传输 | Transport 接口抽象，当前实现 Yandex Docs 与 MAX (WebRTC) 两个后端 |
| 出口节点 | 解封装并 raw socket 转发至真实目标（需 root） |
| 移动端构建 | build_android.sh / build_ios.sh 脚本，可编译到手机 |
| 传输扩展 | 实现接口 + main.go 注册即可新增任意消息平台后端 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 语言 | Go |
| 核心 | 自研 tunnel/transport/socks5 模块 |
| 数据载体 | Yandex Docs 光标消息、WebRTC datachannel |

---

## 项目亮点

### 脑洞大开的传输信道选择
「协作文档的光标消息」作为隐蔽信道，把流量伪装成正常协作行为，是流量伪装研究里少见的新载体。

### 干净的可插拔架构
Transport 接口 + 注册 switch 的设计，让接入新平台（任意 IM/协作文档）只需实现一个包。

### 极小代码基
16 commits 就完成端到端 SOCKS5 隧道，Go 网络编程教学价值高。

---

## 应用场景

### 网络审查研究
学习/研究应用层隐蔽信道与流量伪装（域前置、collab 平台隧道）的对抗原理。

### Go 网络编程学习
SOCKS5 实现、raw socket、校验和与包解析的完整可读样本。

### 网络栈可插拔设计参考
传输抽象层的接口设计可移植到合法的隧道/代理项目中。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 919 |
| 总 Forks | 78 |
| 今日新增 | +201 |

---

## 总结

OpenFlux 用 16 个 commit 证明了「任何有持续消息广播的平台都能变成隧道」，是应用层隐蔽信道路线最简洁的开源演示之一（仅供教育用途）。

---

*数据来源：GitHub 仓库 (p1neappleXpress/OpenFlux)，2026 年 9 月访问*
