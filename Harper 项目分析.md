# Harper 项目分析

## 项目名称

**Harper** — 离线优先的隐私保护英语语法检查器

- **GitHub**: [Automattic/harper](https://github.com/Automattic/harper)
- **许可证**: Apache-2.0

---

## 项目概述

Harper 是由 Automattic（WordPress 母公司）开发的开源英语语法检查器，核心目标是做到「刚刚好」——比 Grammarly 更尊重隐私、比 LanguageTool 更轻量高效。其完全离线运行的设计确保用户的所有文本数据都不会被发送到任何服务器，这对处理敏感内容的律师、记者和企业用户尤为重要。

在性能方面，Harper 的表现极其出色：文档检查在毫秒级完成，内存占用不到 LanguageTool 的五十分之一。Grammarly 需要网络往返才能返回建议，LanguageTool 需要下载约 16GB 的 n-gram 数据集且检查中等长度文档需要数秒，而 Harper 在完全离线的情况下实现了亚秒级检查。项目使用 Rust 编写核心引擎，并通过 WebAssembly 编译使得浏览器端也能获得原生级别的性能。

Harper 的编辑器生态覆盖广泛——支持 VS Code、Neovim、Helix、Emacs、Zed、Obsidian 等主流编辑器，并通过 Language Server Protocol（harper-ls）实现统一的集成接口。此外还提供 CLI 工具（harper-cli）、JavaScript 绑定（harper.js）和格式特定的解析器（支持 AsciiDoc、HTML、TeX、Typst、Git 提交信息等），形成了完整的语法检查工具链。

---

## 核心功能

1. **毫秒级语法检查**：利用 Rust 的高性能特性，文档检查在毫秒级完成，团队将较长的检查时间视为 Bug 而非性能限制。

2. **完全离线运行**：所有语法检查在本地完成，不向任何服务器发送数据。用户文本的隐私得到完全保障，适合处理法律文件、商业机密等敏感内容。

3. **极低内存占用**：内存占用不到 LanguageTool 的 1/50，无需下载 GB 级别的数据集，即装即用。

4. **广泛的编辑器集成**：通过 harper-ls（Language Server）支持 VS Code、Neovim、Helix、Emacs、Zed、Obsidian 等主流编辑器，以及 harper.js（JavaScript 绑定）支持 Web 端集成。

5. **多格式解析支持**：内置针对 AsciiDoc、HTML、TeX、Typst、Git 提交信息、Literate Haskell、JJ 描述等格式的专用解析器，确保在专业写作场景中的语法检查准确度。

6. **同义词词库**：内置 harper-thesaurus 模块，不仅检查语法错误，还能提供同义词建议，辅助用户优化表达。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 核心引擎 | Rust（78%） |
| Language Server | Rust（harper-ls，LSP 实现） |
| Web 端 | WebAssembly（harper-wasm） |
| JS 绑定 | TypeScript/JavaScript（harper.js） |
| 桌面应用 | Svelte + TypeScript |
| CLI 工具 | Rust（harper-cli） |
| Tree-sitter | Rust 集成（harper-tree-sitter） |

---

## 项目亮点

### 对 Grammarly 和 LanguageTool 的精准差异化

Harper 并非简单地做一个开源版 Grammarly，而是针对现有方案的痛点进行了精准设计：Grammarly 过于昂贵且需要网络传输所有文本（隐私风险），LanguageTool 需要 16GB 数据集和数秒处理时间。Harper 用 Rust 实现了毫秒级检查和极低内存占用，同时完全离线运行。这种「比商业产品更快、比开源竞品更轻」的定位，在开发者和技术写作社区中引发了强烈共鸣。

### Automattic 的工程实力背书

作为 WordPress 母公司的开源项目，Harper 体现了 Automattic 在文本处理领域的深厚积累。项目已发布 110 个版本、4,400+ 次提交，开发节奏稳定且活跃。Apache-2.0 许可证确保了企业级用户的采用无障碍，而 Automattic 的品牌背书也降低了用户对项目可持续性的顾虑。

### WebAssembly 实现真正的跨平台

Harper 的核心引擎通过 WebAssembly 编译，可以在浏览器中直接运行（writewithharper.com）。这意味着用户无需安装任何软件，打开网页即可获得与本地应用同等的语法检查性能。对于需要在不同设备间切换写作的用户，这种零安装的体验极具吸引力。

---

## 应用场景

### 开发者日常写作

开发者编写 Git 提交信息、代码注释、技术文档和 Markdown 笔记时，Harper 可以直接在 VS Code、Neovim 等编辑器中实时检查语法错误。其 Git 提交信息专用解析器（harper-git-commit）确保提交信息的规范性，而 TeX 和 Typst 解析器则服务于学术论文写作场景。

### 隐私敏感领域的文本编辑

律师、记者、医疗工作者和企业管理者在处理敏感文档时，不能使用 Grammarly 等需要上传文本的云服务。Harper 的完全离线运行确保所有文本数据留在用户设备上，是这些场景下的理想选择。

### 技术文档和学术写作

Harper 的多格式解析器（AsciiDoc、TeX、Typst 等）使其成为技术文档和学术论文写作的得力助手。配合 Obsidian 集成和同义词词库功能，研究者和工程师可以在保持隐私的同时获得高质量的写作辅助。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Stars | 12,106 |
| 总 Forks | 448 |
| 主要语言 | Rust |
| 创建时间 | 2023-10-22 |
| 今日新增 Stars | 590 |

---

## 总结

Harper 是 Automattic 推出的高性能离线英语语法检查器，用 Rust 实现了毫秒级检查和极低内存占用，在隐私保护、性能表现和编辑器生态覆盖三个维度上全面超越了 Grammarly 和 LanguageTool。对于重视隐私的开发者和专业写作者而言，Harper 是目前最优秀的开源语法检查方案。

---

*数据来源：GitHub 仓库 (Automattic/harper)，2026 年 7 月访问*