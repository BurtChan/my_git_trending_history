# System Prompts Leaks 项目分析

## 项目名称
**System Prompts Leaks** — 主流AI产品系统提示词提取与公开仓库
- **GitHub**: [asgeirtj/system_prompts_leaks](https://github.com/asgeirtj/system_prompts_leaks)
- **许可证**: CC0-1.0（公共领域许可）
- **项目主页**: https://asgeirtj.github.io/system_prompts_leaks/

---

## 项目概述

System Prompts Leaks 是一个开源的 GitHub 仓库，致力于收集并公开各大 AI 公司在其聊天机器人产品中使用的系统提示词（System Prompts）。系统提示词是 AI 产品在用户对话前发送给大语言模型的一段隐藏指令，用于定义助手的身份、行为边界、拒绝规则、人格特征以及工具调用方式。这个仓库通过逆向工程技术从 Anthropic Claude、OpenAI ChatGPT、Google Gemini、xAI Grok、Microsoft Copilot 等主流 AI 产品中提取这些"隐藏的配置文件"，并以 Markdown 格式公开发布。

该项目自创建以来持续高频更新，截至 2026 年 6 月已累计超过 583 次 commits，覆盖了几乎所有主流 AI 厂商的产品。仓库采用 CC0-1.0 公共领域许可证，意味着任何人都可以自由使用、复制、修改和分发其中的内容，无需署名且无任何版权限制。这一许可选择与项目的教育初衷高度一致——让 AI 系统提示词成为公共知识，供开发者和研究者学习参考。

该项目在 AI 社区产生了广泛影响，《华盛顿邮报》等主流媒体曾对其进行报道，Hackernoon 等技术媒体也发表了基于该仓库数据的深度分析文章。多位独立研究者利用该仓库的提示词数据进行了跨版本对比分析，例如 David Breunig 通过对比 Claude 3.7 与 Claude 4 的系统提示词变化，揭示了 Anthropic 在产品策略上的优先级演变。项目已获得超过 44,000 个 Star，成为 GitHub 上最受欢迎的 AI 提示词资源之一。

---

## 核心功能

### 多厂商系统提示词提取
仓库覆盖了当前 AI 行业几乎全部主流厂商的产品线。**Anthropic** 方面收录了 Claude Fable 5、Opus 4.8/4.7/4.6、Sonnet 4.6、Claude Code、Claude Design 以及 Claude.ai 的提醒（Reminders）机制。**OpenAI** 方面包含 ChatGPT 5.5 Thinking/Instant、Codex、o3、GPT-4.5 等模型的系统提示词。**Google** 方面涵盖 Gemini 3.5 Flash、3.1 Pro、Antigravity 等产品。**xAI** 则收录了 Grok 4.2、Grok 3 及 Grok Account 的提示词。

### 工具级提示词归档
除了基础聊天模型的系统提示词外，仓库还收录了大量 AI 工具和增强功能的提示词，包括 Web Search（网页搜索）、Deep Research（深度研究）、Python 代码执行、Canvas 协作画布等功能模块的专用提示词。这些工具级提示词揭示了 AI 厂商如何通过自然语言指令来定义模型在不同工具场景下的行为规范和能力边界。

### 跨版本历史追踪
仓库设有 `old/` 子目录，保留了历史版本模型的系统提示词，如 Claude Opus 4.5、Sonnet 4.5、Sonnet 4、Claude 3.7 Sonnet 等。这种版本归档机制使研究者能够追踪同一产品线在不同迭代中的提示词演变，洞察厂商在安全策略、功能设计和用户体验方面的迭代思路。

### 第三方与新兴产品覆盖
除头部厂商外，仓库还收录了 **Cursor**（AI 编程编辑器）、**Meta AI**、**Perplexity**（AI 搜索引擎）、**Mistral**、**Notion AI**（智能笔记）、**Zed AI**（编程助手）、**Confer**、**Hermes**、**t3.chat**、**t3 Code** 等新兴 AI 产品和工具的提示词，形成了对整个 AI 生态系统的全面覆盖。

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 主要语言 | JavaScript（仓库标记语言） |
| 内容格式 | Markdown (.md) / 纯文本 (.txt) / XML |
| 托管平台 | GitHub |
| 许可证 | CC0-1.0（公共领域） |
| 项目主页 | GitHub Pages (asgeirtj.github.io) |
| 版本控制 | Git（583+ commits） |
| 社区监控 | 537 Watchers、7,318 Forks |
| 内容组织 | 按公司分目录（Anthropic/、OpenAI/、Google/、xAI/ 等） |

---

## 项目亮点

### 公共领域许可的知识共享精神
项目采用 CC0-1.0 许可证，将所有收集的系统提示词完全贡献至公共领域。这一选择超越了典型的开源许可（如 MIT、Apache），意味着任何人无需署名、无版权顾虑地自由使用全部内容。在 AI 行业普遍将系统提示词视为商业机密的背景下，这种彻底开放的做法体现了"知识应当自由流动"的理念，也最大程度降低了研究者使用数据的法律门槛。

### 媒体认可与学术影响力
该项目不仅受到开发者社区的追捧，还获得了《华盛顿邮报》等权威媒体的报道。Hackernoon 发表的深度分析文章《The 'Moat' is a Config File》基于该仓库数据，论证了 AI 厂商所谓的"竞争护城河"本质上只是一份配置文件。独立研究者 David Breunig 通过对比不同版本 Claude 的系统提示词（均来自该仓库），揭示了 Anthropic 在搜索功能、Artifacts 使用和上下文管理方面的策略演变。这种跨领域的影响力证明了该项目在 AI 透明度研究中的独特价值。

### 高频更新与全面覆盖
截至 2026 年 6 月，仓库仍在持续更新（最近更新于 6 月 18 日），583 次 commits 体现了维护者的持续投入。仓库覆盖了从 Anthropic、OpenAI、Google、xAI 四大巨头到 Cursor、Perplexity、Notion AI、Zed AI 等新兴工具的完整生态系统。每当厂商发布新模型或更新产品，仓库通常会在短时间内同步收录最新的系统提示词，确保数据的时效性。

### 教育价值与安全研究的双重意义
该项目为 AI 安全研究提供了宝贵的数据集。安全研究者可以通过分析系统提示词中的拒绝规则、人格设定和行为约束，评估各厂商的安全防护策略，并发现潜在的安全漏洞。同时，对于 Prompt Engineering 从业者而言，这些真实生产环境的系统提示词是最好的学习素材——它们展示了顶级 AI 公司如何通过精心设计的自然语言指令来塑造模型行为，远比教科书上的示例更具参考价值。

---

## 应用场景

### Prompt Engineering 学习与参考
对于提示词工程师而言，该仓库是学习行业最佳实践的宝库。通过研究 OpenAI 如何构建 ChatGPT 的拒绝机制、Anthropic 如何定义 Claude 的搜索行为、Google 如何配置 Gemini 的工具调用规则，工程师可以学习到如何编写更精确、更有效的系统提示词。Claude 4 的系统提示词约 23,000 tokens，占据了上下文窗口的 11% 以上，展示了复杂提示词工程的实际规模。

### AI 产品安全审计与对比分析
安全研究团队可以利用该仓库对不同 AI 产品的系统提示词进行横向对比，分析各厂商在内容安全、拒绝策略、隐私保护等方面的差异和共同点。例如，通过对比 ChatGPT 和 Claude 对敏感话题的处理方式，可以发现不同厂商在安全边界设定上的理念差异。这种对比分析有助于推动整个行业安全标准的提升。

### AI 产品设计与策略研究
产品经理和 AI 产品设计师可以通过研究系统提示词来理解竞争对手的产品策略。例如，Claude 从 3.7 到 4.0 的系统提示词变化，揭示了 Anthropic 从"被动搜索"到"主动搜索"的策略转变；Claude Code 的提示词展示了 Anthropic 如何为编程助手定制专用行为规范。这些洞察对于 AI 产品开发具有重要的参考价值。

### AI 教育与学术研究
在高校和研究机构中，该仓库可作为 AI 伦理、AI 安全和自然语言处理课程的补充教材。学生可以通过真实案例了解 AI 系统的"隐藏指令层"，理解模型行为并非仅由训练数据决定，系统提示词同样发挥着关键作用。该仓库已被多篇技术博客和分析文章引用，成为 AI 透明度研究领域的重要数据来源。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| 总 Star | 44,250 |
| 今日新增 | 366 |
| Fork | 7,318 |
| Watchers | 537 |
| 总 Commits | 583+ |
| 创建时间 | 2025-05-03 |
| 主要语言 | JavaScript |
| 许可证 | CC0-1.0 |
| 标签 | ai, ai-agents, anthropic, chatbot, chatgpt, claude, claude-code, codex, deep-learning, education, gemini, generative-ai, google, llm, machine-learning, nlp, open-source, openai, prompt-engineering |

---

## 总结

System Prompts Leaks 是 2025-2026 年 AI 开源社区中最具影响力的透明度项目之一。它以 CC0-1.0 公共领域许可的方式，系统性提取并公开了 Anthropic、OpenAI、Google、xAI 等几乎所有主流 AI 厂商产品的系统提示词，为 Prompt Engineering、AI 安全研究、产品策略分析提供了独一无二的数据资源。该项目获得《华盛顿邮报》等权威媒体的关注，44,000+ 的 Star 数量证明了社区对其价值的广泛认可。随着 AI 行业的快速发展，这个仓库已成为理解"AI 产品如何通过自然语言指令塑造模型行为"的关键窗口，是每一位 AI 从业者都值得收藏的参考资源。

---

*数据来源：GitHub 仓库 (asgeirtj/system_prompts_leaks)，2026 年 6 月访问*
