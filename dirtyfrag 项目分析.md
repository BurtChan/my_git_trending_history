# dirtyfrag 项目分析

## 项目名称

**Dirty Frag** — Linux 内核本地提权漏洞链及概念验证代码

- **GitHub**: [V4bel/dirtyfrag](https://github.com/V4bel/dirtyfrag)
- **许可证**: Unknown

---

## 项目概述

Dirty Frag 是由安全研究员 Hyunwoo Kim（@v4bel）发现并披露的一个新型 Linux 内核本地提权漏洞链，涉及两个 CVE 编号：CVE-2026-43284（xfrm-ESP Page-Cache Write）和 CVE-2026-43500（RxRPC Page-Cache Write）。该漏洞链允许已获得本地访问权限的攻击者提升至 root 权限，影响范围极广。

Dirty Frag 是 Dirty Pipe 和 Copy Fail 漏洞类别的扩展。漏洞名称来源于其攻击原理——通过"污染"`struct sk_buff` 结构体的 `frag` 成员来实现任意页面缓存写入。xfrm-ESP Page-Cache Write 提供了一个强大的任意 4 字节 STORE 原语（类似 Copy Fail），且存在于大多数 Linux 发行版中（需 namespace 创建权限）；RxRPC Page-Cache Write 则不需要 namespace 创建权限，但 `rxrpc.ko` 模块不在大多数发行版中默认加载。

该项目在 2026 年 5 月 7 日发布概念验证代码后，迅速在安全社区引发广泛关注。ReversingLabs 截至同年 5 月 8 日已记录了 163 个与该漏洞相关的恶意样本。Wiz、Automox 等安全公司相继发布分析报告和缓解方案。受影响的代码路径可追溯至约 2017 年（ESP 子系统）和 2023 年（RxRPC 子系统），意味着大量内核版本受到影响。

---

## 核心功能

1. **xfrm-ESP 漏洞利用**：利用 Linux 内核 xfrm-ESP（IPsec）子系统的页面缓存写入漏洞（CVE-2026-43284），获取任意 4 字节的内存写入原语，实现权限提升。

2. **RxRPC 漏洞利用**：利用 Linux 内核 RxRPC 子系统的页面缓存写入漏洞（CVE-2026-43500），提供无需 namespace 权限的替代攻击路径。

3. **漏洞链组合**：展示如何将两个漏洞串联组合，构建完整的从普通用户到 root 的提权攻击链。

4. **缓解措施指南**：提供详细的安全缓解方案，包括禁用受影响的内核模块（esp4 和 rxrpc）的具体命令和操作步骤。

---

## 技术栈

| 技术 | 说明 |
|------|------|
| **C** | 漏洞利用代码实现语言 |
| **Linux Kernel** | 目标系统（xfrm-ESP 和 RxRPC 子系统） |
| **CVE-2026-43284** | xfrm-ESP Page-Cache Write 漏洞编号 |
| **CVE-2026-43500** | RxRPC Page-Cache Write 漏洞编号 |
| **Shell** | 缓解措施脚本 |

---

## 项目亮点

1. **新型漏洞类别**：Dirty Frag 扩展了 Dirty Pipe 和 Copy Fail 的漏洞类别，发现了一种全新的内核页面缓存写入攻击面，对安全研究具有重要价值。

2. **影响范围极广**：xfrm-ESP 子系统的漏洞代码可追溯至 2017 年，意味着过去近 10 年的大多数 Linux 内核版本都可能受到影响。

3. **完整的概念验证**：提供了从漏洞分析到利用实现的完整 PoC 代码，安全团队可据此快速评估自身系统风险并部署防御措施。

4. **即时缓解方案**：附带简单的模块禁用缓解命令，管理员可在官方补丁发布前快速降低风险（`sh -c "printf 'install esp4 /bin/true\ninstall rxrpc /bin/true\n' > /etc/modprobe.d/disable-dirtyfrag.conf"`）。

---

## 应用场景

1. **安全漏洞评估**：安全团队利用 Dirty Frag 的 PoC 代码评估自身 Linux 系统的漏洞暴露情况，验证现有安全防护是否有效。

2. **渗透测试**：渗透测试人员在获得授权的情况下，使用 Dirty Frag 验证 Linux 系统的本地提权防护措施。

3. **安全研究与教学**：安全研究人员和高校通过分析 Dirty Frag 的漏洞原理和利用技术，深入理解 Linux 内核安全机制。

4. **应急响应**：在漏洞公开后，运维和安全团队根据项目提供的缓解措施快速加固系统，等待官方补丁发布。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| **总 Stars** | 4,791 |
| **总 Forks** | 771 |
| **今日新增 Stars** | ~60 |
| **许可证** | Unknown |
| **主要语言** | C |

---

## 总结

Dirty Frag 是 2026 年最重要的 Linux 内核安全漏洞之一，由安全研究员 V4bel 发现并公开披露。该漏洞链组合了 xfrm-ESP 和 RxRPC 两个子系统缺陷，可实现从普通用户到 root 的完整提权。项目提供了完整的 PoC 代码和缓解方案，对全球 Linux 系统管理员和安全团队来说是一个必须关注的安全事件。

---

*数据来源：GitHub 仓库 (V4bel/dirtyfrag)，分析日期 2026年6月1日*
