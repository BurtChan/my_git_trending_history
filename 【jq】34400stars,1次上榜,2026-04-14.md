# jq 项目分析

## 项目名称与地址

**jq - Command-line JSON Processor**

项目地址：https://github.com/jqlang/jq

官网文档：https://jqlang.org

在线试用：https://play.jqlang.org

## 项目概述

jq 是一个轻量级、灵活的命令行 JSON 处理器，定位为 JSON 数据领域的 sed、awk 和 grep。项目由 Stephen Dolan 于 2012 年创建，最初托管在 stedolan/jq 下，后来迁移到 jqlang 组织进行社区维护。jq 用可移植的 C 语言编写，零运行时依赖，可轻松对结构化数据进行切片、过滤、映射和转换。

jq 不仅仅是一个简单的 JSON 解析器，它拥有自己专属的领域特定语言（DSL），支持变量、函数定义、条件语句、循环结构和模块导入，足以胜任复杂的数据处理任务。作为 JSON 处理领域的事实标准，jq 已被广泛集成到各类开发工作流中，几乎所有主流编程语言都有对应的 jq 绑定库。

项目当前版本为 1.8.1（2025 年 7 月发布），已有 1,903 次提交，保持持续维护更新。

## 核心功能

### JSON 过滤与查询

使用简洁的点号语法和管道操作符提取 JSON 数据中的任意字段：

```bash
# 提取单个字段
echo '{"name":"Alice","age":30}' | jq '.name'
# 输出: "Alice"

# 提取嵌套字段
echo '{"user":{"address":{"city":"Beijing"}}}' | jq '.user.address.city'
# 输出: "Beijing"

# 从数组中提取所有元素
echo '[1,2,3,4,5]' | jq '.[]'
```

### 数据转换

支持丰富的数据转换操作，包括映射、过滤、排序和分组：

```bash
# 过滤数组元素
echo '[1,2,3,4,5]' | jq 'map(select(. > 3))'
# 输出: [4,5]

# 对对象数组进行排序和分组
echo '[{"name":"B","age":20},{"name":"A","age":30}]' | jq 'sort_by(.age)'

# 使用 reduce 进行聚合计算
echo '[1,2,3,4,5]' | jq 'reduce .[] as $x (0; . + $x)'
# 输出: 15
```

### 流式管道处理

支持 Unix 管道操作，可与其他命令行工具无缝配合：

```bash
# 从 API 响应中提取数据
curl -s 'https://api.github.com/repos/jqlang/jq' | jq '.stargazers_count'

# 处理日志文件
cat app.log.json | jq 'select(.level == "error") | .message'

# 链式管道处理
cat data.json | jq '.items | map(.price) | add'
```

### 条件与控制结构

支持 if-then-else、try-catch、reduce、foreach、label-break 等控制结构：

```bash
# 条件判断
echo '15' | jq 'if . > 10 then "big" else "small" end'

# 异常处理
echo '{"a":"not a number"}' | jq 'try (.a | tonumber) catch "invalid"'

# foreach 迭代
echo '[1,2,3,4,5]' | jq '[foreach .[] as $x (0; . + $x)]'
```

### 内置函数库

提供大量内置函数处理各类数据类型：

- **字符串处理**：`length`、`split`、`join`、`ascii_downcase`、`ascii_upcase`、`gsub`、`sub`、`test`、`capture`、`scan`、`ltrimstr`、`rtrimstr`、`tostring`、`tonumber`
- **数组操作**：`map`、`select`、`sort`、`sort_by`、`group_by`、`unique`、`flatten`、`reverse`、`min`、`max`、`min_by`、`max_by`、`any`、`all`
- **对象操作**：`keys`、`values`、`has`、`del`、`to_entries`、`from_entries`、`with_entries`
- **数学运算**：`+`、`-`、`*`、`/`、`%`、`floor`、`ceil`、`round`、`sqrt`、`pow`、`abs`、`nan`、`infinite`
- **路径操作**：`path`、`getpath`、`setpath`、`delpaths`、`leaf_paths`
- **类型检测**：`type`、`null`、`boolean`、`number`、`string`、`array`、`object`、`iterable`
- **输入输出**：`input`、`inputs`、`env`、`debug`、`halt`、`halt_error`

### 格式化输出

支持多种输出格式以满足不同需求：

```bash
# 美化输出（默认）
echo '{"a":1,"b":2}' | jq '.'
# {
#   "a": 1,
#   "b": 2
# }

# 紧凑输出
echo '{"a":1,"b":2}' | jq -c '.'

# 原始字符串输出（去掉引号）
echo '{"name":"Alice"}' | jq -r '.name'
# 输出: Alice（无引号）

# 排序键名输出
echo '{"b":2,"a":1}' | jq -S '.'
# {
#   "a": 1,
#   "b": 2
# }
```

### 模块系统

支持自定义函数和模块导入，可复用复杂逻辑：

```bash
# 导入模块
jq 'include "my_module"; my_function'

# 定义和导入自定义函数
# 文件 ~/.jq/mylib.jq:
# def greet: "Hello, " + . + "!";
echo '"World"' | jq 'include "mylib"; greet'
```

## 技术栈

- **核心语言**：C（79.1%）
- **辅助语言**：M4（6.7%）、Shell（5.3%）、Yacc（3.4%）、jq（1.6%）、C++（1.5%）
- **正则引擎**：内置 Oniguruma 正则表达式库（作为 git submodule）
- **构建系统**：Autotools（autoconf/automake/libtool）
- **解析器生成**：Flex（词法分析）+ Bison/Yacc（语法分析）
- **数值库**：decNumber（高精度十进制运算）
- **Docker 镜像**：ghcr.io/jqlang/jq
- **平台支持**：Linux、macOS、Windows、FreeBSD 等，支持交叉编译
- **分发方式**：预编译二进制、Docker 镜像、系统包管理器（apt/brew/yum 等）
- **许可证**：MIT License（代码）、CC BY 3.0（文档）、ICU License（decNumber）

## 项目亮点

- **经典 Unix 工具地位**：JSON 处理领域的事实标准，已有十余年生产环境验证，被 Stack Overflow 上数万问答引用
- **极致性能**：纯 C 语言原生实现，处理 GB 级 JSON 文件速度远超 Node.js/Python 实现的同类工具。对比测试中，jq 处理 100MB JSON 文件的速度约为 jsonpp 的 5 倍、python -m json.tool 的 20 倍
- **零依赖部署**：编译后为单一静态二进制文件，无运行时依赖，适合容器和嵌入式环境
- **强大 DSL**：专用的 jq 语言比通用语言中的 JSON 库更简洁，复杂查询一行即可完成
- **丰富的生态绑定**：Python（pyjq）、Ruby（ruby-jq）、Go（go-jq）、Rust（jaq）、Node.js（node-jq）等几乎所有语言都有绑定
- **持续演进**：2025 年发布 1.8.1 版本，1,903 次提交，活跃的社区和 358 个开放 Issue

### 与其他 JSON 处理工具对比

| 特性 | jq | jsonpp | python -m json.tool | dasel | jc |
|------|------|--------|---------------------|-------|----|
| 实现语言 | C | C++ | Python | Go | Python |
| 单二进制 | 是 | 是 | 否（需 Python） | 是 | 否（需 Python） |
| DSL 表达力 | 极强 | 无（仅格式化） | 无（仅格式化） | 中等 | 弱 |
| 流式处理 | 支持 | 支持 | 不支持 | 支持 | 不支持 |
| 性能 | 极高 | 高 | 低 | 高 | 低 |

## 应用场景

- **API 响应处理**：从 curl 返回的 JSON 数据中提取特定字段，如 `curl -s api.example.com | jq '.data[].name'`
- **日志分析**：处理 JSON 格式的应用日志（如 Docker 日志、CloudTrail 日志），快速筛选和统计
- **CI/CD 流水线**：在 GitHub Actions/GitLab CI 中解析 JSON 配置、提取版本号、读取构建元数据
- **Kubernetes 管理**：处理 kubectl 返回的 JSON 状态信息，如 `kubectl get pods -o json | jq '.items[] | select(.status.phase=="Running")'`
- **数据清洗**：批量处理 JSON 数据集，进行格式转换、字段筛选、数据重命名
- **配置文件处理**：解析和修改 JSON 格式的配置文件（package.json、tsconfig.json 等）
- **Shell 脚本集成**：在 Bash/Zsh 脚本中作为 JSON 数据处理的标准组件

## 安装方法

### macOS

```bash
brew install jq
# 或使用 port
port install jq
```

### Linux

```bash
# Debian/Ubuntu
sudo apt-get install jq

# Fedora
sudo dnf install jq

# Arch
sudo pacman -S jq

# Alpine
apk add jq
```

### Windows

```bash
# 使用 winget
winget install jqlang.jq

# 使用 Chocolatey
choco install jq

# 使用 Scoop
scoop install jq

# 或从 GitHub Releases 下载 exe 文件
```

### Docker

```bash
# 直接运行
docker run --rm -i ghcr.io/jqlang/jq:latest < package.json '.version'

# 挂载目录运行
docker run --rm -i -v "$PWD:$PWD" -w "$PWD" ghcr.io/jqlang/jq:latest '.version' package.json
```

### 从源码编译

```bash
git clone https://github.com/jqlang/jq.git
cd jq
git submodule update --init
autoreconf -i
./configure --with-oniguruma=builtin
make -j8
make check
sudo make install
```

## Star 数据

- 总 Star 数：34,400
- Fork 数：1,800
- Watch 数：345
- 今日增长：+48
- 累计 Releases：15 个（最新：jq 1.8.1，2025 年 7 月发布）
- 开源许可：MIT License

## 总结

jq 是 JSON 处理领域不可替代的经典基础设施工具。虽然它不是新项目，但作为 JSON 数据处理的标准工具，几乎每个开发者在职业生涯中都会用到。C 语言实现保证了极致性能，零依赖保证了部署便利，而专用的 DSL 语言则在简洁性和表达能力之间取得了完美平衡。

对于需要在命令行或脚本中处理 JSON 数据的开发者，jq 提供了无可替代的价值。无论你是后端开发者处理 API 响应、运维工程师分析日志、数据工程师清洗数据，还是前端开发者查看 JSON 配置，jq 都是工具箱中必备的瑞士军刀。其 34K+ 的 Star 数和活跃的社区维护证明了它在开发工具链中的核心地位。
