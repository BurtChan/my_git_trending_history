# Sherlock 项目分析

> **通过一个用户名，在 400+ 社交网络中猎取目标账号** — 最流行的开源用户名侦察（Username OSINT）工具，一条命令即可扫描全网社交平台。

- **GitHub**: [sherlock-project/sherlock](https://github.com/sherlock-project/sherlock)
- **官网**: [sherlockproject.xyz](https://sherlockproject.xyz/)
- **语言**: Python
- **Stars**: 67,101 | **Forks**: 7,707
- **许可证**: MIT License
- **版本**: 0.16.0
- **创建时间**: 2018-12-24
- **原作者**: Siddharth Dushantha
- **维护者**: Paul Pfeister, Matheus Felipe, Sondre Karlsen Dyrnes

---

## 项目定位

Sherlock 是目前**最流行的开源用户名侦察工具**，67k+ Stars。它以 Python 编写，只需输入一个用户名，即可在 400+ 社交网络和网站上自动检测该用户名是否已被注册，帮助安全研究人员、渗透测试工程师和 OSINT 调查人员快速定位目标在网络上的数字足迹。项目名字来源于著名侦探"夏洛克-福尔摩斯"（Sherlock Holmes），寓意其强大的信息追踪能力。

---

## 解决什么问题

在网络安全侦察和开源情报（OSINT）调查中，确定目标人物在互联网上的活动范围是一项基础但极为耗时的任务：

- **手动逐一排查**：调查人员需要逐个访问数百个社交网站，手动输入用户名进行搜索，效率极低
- **信息碎片化**：目标可能使用同一用户名注册了大量平台，人工方式难以做到全面覆盖
- **数字足迹追踪困难**：社工调查、红队渗透中，需要快速绘制目标的全网画像
- **品牌保护成本高**：企业监控自有品牌在各大平台是否被冒用，需要逐一查询

Sherlock 将这一切简化为一条命令：

```bash
sherlock username
```

即可在数分钟内完成对 400+ 平台的自动化扫描，并输出所有匹配结果。

---

## 核心功能

| 功能 | 说明 |
|------|------|
| **全网用户名扫描** | 一条命令同时检测 400+ 社交网络和网站上的用户名注册情况 |
| **批量查询** | 支持同时查询多个用户名（`sherlock user1 user2 user3`） |
| **模糊匹配** | 支持 `{?}` 通配符，自动替换为 `_`、`-`、`.` 来检测相似用户名 |
| **多格式输出** | 支持文本文件、CSV、Excel（xlsx）多种输出格式 |
| **Tor 匿名扫描** | 支持 `--tor` 和 `--unique-tor` 参数，通过 Tor 网络发送请求以保护隐私 |
| **代理支持** | 支持 SOCKS5/HTTP 代理（`--proxy socks5://127.0.0.1:1080`） |
| **指定站点扫描** | 可通过 `--site` 参数限定扫描特定网站，提升效率 |
| **超时控制** | 可设置请求超时时间（默认 60 秒） |
| **浏览器打开** | `--browse` 参数可直接在浏览器中打开所有找到的结果 |
| **NSFW 站点** | `--nsfw` 参数可包含成人内容网站的扫描 |
| **自定义数据源** | 支持通过 `--json` 加载自定义的 JSON 数据文件，扩展扫描范围 |
| **云端运行** | 提供 Apify Actor，无需安装即可在云端运行 |
| **详细调试** | `--verbose` 模式输出调试信息和性能指标 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| **核心语言** | Python（兼容 3.9 ~ 3.13） |
| **HTTP 请求** | requests + requests-futures（异步并发请求） |
| **数据处理** | pandas（结果分析与表格输出） |
| **Excel 导出** | openpyxl（生成 .xlsx 文件） |
| **Tor 集成** | stem（Python Tor 控制器库） |
| **网络代理** | PySocks（SOCKS 代理支持） |
| **SSL 证书** | certifi（Mozilla CA 证书包） |
| **终端美化** | colorama（跨平台彩色终端输出） |
| **配置解析** | tomli（TOML 文件解析） |
| **构建管理** | Poetry（依赖管理与打包） |
| **测试框架** | pytest + pytest-xdist（并行测试） |
| **容器化** | Docker（官方 Docker 镜像） |
| **数据定义** | JSON（站点列表与检测规则） |

---

## 安装与使用

### 安装方式

```bash
# 方式一：pipx 安装（推荐）
pipx install sherlock-project

# 方式二：pip 安装
pip install sherlock-project

# 方式三：Docker 运行
docker run -it --rm sherlock/sherlock

# 方式四：Fedora dnf 安装
dnf install sherlock-project
```

社区维护的包还支持 Debian (>= 13)、Ubuntu (>= 22.10)、Homebrew、Kali Linux 和 BlackArch。

### 基本用法

```bash
# 搜索单个用户名
sherlock user123

# 搜索多个用户名
sherlock user1 user2 user3

# 只搜索指定网站
sherlock user123 --site GitHub --site Twitter

# 通过 Tor 匿名扫描
sherlock user123 --tor

# 输出为 CSV 格式
sherlock user123 --csv

# 输出为 Excel 格式
sherlock user123 --xlsx

# 使用代理
sherlock user123 --proxy socks5://127.0.0.1:1080

# 只输出找到的结果
sherlock user123 --print-found
```

### 云端运行（Apify）

```bash
echo '{"usernames":["user123"]}' | apify call -so netmilk/sherlock
```

无需本地安装，直接在云端执行扫描。

---

## 使用场景

| 场景 | 说明 |
|------|------|
| **OSINT 调查** | 开源情报分析师快速定位目标人物在互联网上的所有社交账号 |
| **渗透测试 / 红队** | 在授权的安全评估中，收集目标用户的数字足迹，扩大攻击面分析 |
| **网络威胁情报（CTI）** | 追踪威胁行为者的账号活动，关联分析其在不同平台的行为模式 |
| **数字取证** | 执法和取证人员追踪嫌疑人或失踪人员的网络活动痕迹 |
| **品牌保护** | 企业监控自有品牌名称在各大社交平台是否被冒用或抢注 |
| **用户名可用性检查** | 个人用户检查自己喜欢的用户名在哪些平台上还可注册 |
| **社工防范意识** | 安全团队演示一个用户名能暴露多少个人信息，提高员工安全意识 |
| **学术研究** | 研究人员在网络科学、社交网络分析等领域收集数据 |
| **招聘背景调查** | HR 和猎头了解候选人的公开网络活动和社交形象 |

---

## 工作原理

Sherlock 的核心机制基于**站点数据文件**（data.json），其中为每个目标网站定义了检测规则：

1. **URL 模板**：将用户名插入到目标网站的用户主页 URL 中
2. **检测逻辑**：通过 HTTP 请求访问构造的 URL，根据响应状态码、页面内容中的特定字符串（错误提示文本）来判断用户名是否存在
3. **并发请求**：使用 requests-futures 实现异步并发，同时对数百个站点发起请求
4. **结果汇总**：将所有匹配结果汇总输出到终端和文件

这种模式使得新增站点支持非常简单 -- 只需在 JSON 数据文件中添加一条配置记录，无需修改任何代码。

---

## 项目亮点

- **67k+ Stars**，GitHub 上最热门的 OSINT 工具之一，社区高度活跃
- **覆盖 400+ 社交网络**，检测范围极为广泛
- **极简使用**：一条命令 + 一个用户名即可开始扫描，零学习曲线
- **Python 纯编写**，跨平台运行，支持 Windows / macOS / Linux
- **多种安装方式**：pip、Docker、系统包管理器、云端 Apify Actor
- **隐私保护**：原生支持 Tor 和代理，保护调查者身份
- **灵活输出**：文本、CSV、Excel 多格式导出，方便后续分析
- **高度可扩展**：JSON 数据文件驱动的站点配置，社区持续贡献新站点
- **MIT 开源许可证**，商用友好，可自由集成到安全工具链中
- **持续维护**：项目自 2018 年创建至今，仍在活跃开发中，由 sherlock-project 组织维护

---

## 一句话总结

> Sherlock 是**最流行的开源用户名侦察工具**，67k+ Stars，用 Python 编写，一条命令即可在 400+ 社交网络中检测目标用户名的注册情况，支持 Tor 匿名、代理、多格式输出，是 OSINT 调查、渗透测试和数字取证领域的事实标准工具。
