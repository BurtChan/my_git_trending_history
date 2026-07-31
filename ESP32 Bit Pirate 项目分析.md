# ESP32 Bit Pirate 项目分析

## 项目名称
**ESP32 Bit Pirate** — 基于 ESP32 的多协议硬件黑客工具，Bus Pirate 的现代继承者
- **GitHub**: [geo-tp/ESP32-Bit-Pirate](https://github.com/geo-tp/ESP32-Bit-Pirate)
- **许可证**: MIT
- **官网**: [geo-tp.github.io/ESP32-Bit-Pirate](https://geo-tp.github.io/ESP32-Bit-Pirate/)

---

## 项目概述
ESP32 Bit Pirate 是一个开源固件，将 ESP32 微控制器变身为多协议开发和分析工具，灵感源自经典的 Bus Pirate 硬件黑客工具。它支持通过 USB 串口或 WiFi Web 界面进行交互，能够嗅探、发送、录制和分析包括 I2C、UART、SPI、1-Wire、CAN、蓝牙、Wi-Fi、Sub-GHz、RFID、JTAG 等 20 余种数字和无线协议。

该项目以极低的硬件成本（一块 ESP32-S3 开发板即可）提供了专业级协议分析能力，大幅降低了硬件黑客和安全研究的入门门槛。Web 界面支持从任何设备的浏览器直接操作，无需安装串口终端软件。

---

## 核心功能

| 协议模式 | 功能描述 |
|----------|----------|
| **I2C** | 扫描、毛刺注入、从机模式、EEPROM 读写 |
| **SPI** | EEPROM、Flash、SD 卡读写，从机模式 |
| **UART** | 桥接、读写、自动波特率检测、AT 命令 |
| **1-Wire** | iButton、EEPROM |
| **2/3-Wire** | 嗅探、智能卡、EEPROM |
| **CAN** | 嗅探、发送和接收帧 |
| **JTAG** | 扫描、SWD、OpenOCD 集成 |
| **蓝牙** | BLE HID、扫描、欺骗、嗅探 |
| **Wi-Fi** | 嗅探、去认证、nmap、netcat |
| **Sub-GHz** | 分析、录制、重放 |
| **RFID** | 读取、写入、克隆 |
| **红外** | 发送、录制、通用遥控（80+ 协议） |
| **USB** | HID、flashrom、存储、USB-UART |
| **FM** | 分析、广播 |
| **SIM/Cell** | SIM 卡信息读取、短信、通话 |

---

## 技术栈

| 组件 | 技术 |
|------|------|
| 主控芯片 | ESP32-S3（8MB Flash 最低要求） |
| 固件框架 | ESP-IDF |
| 用户界面 | Web CLI（WiFi）+ Serial CLI（USB）+ Standalone（M5 Cardputer） |
| 脚本支持 | Bus Pirate 风格字节码指令 + Python 自动化 |
| 数据存储 | LittleFS（HTTP 导入/导出） |
| 支持硬件 | ESP32-S3 DevKit、LILYGO T-Display/Embed、M5 Cardputer/Stick S3 等 |

---

## 项目亮点

### 20+ 协议的全面支持
从基本的数字总线（I2C、SPI、UART）到无线协议（蓝牙、Wi-Fi、Sub-GHz、RFID），再到高级调试接口（JTAG/SWD），ESP32 Bit Pirate 覆盖了硬件黑客日常工作中几乎所有的协议分析需求。一块几十元的开发板就能替代数千元的专业协议分析仪。

### 三种交互模式
USB 串口（快速响应、适合高频交互）、WiFi Web 界面（无需串口线、支持手机/平板远程操作）、Standalone 模式（M5 Cardputer 独立运行，完全脱离电脑）。三种模式共享相同的命令结构，可随时切换。

### 丰富的硬件生态支持
支持 10+ 种主流 ESP32-S3 开发板（包括 LILYGO T-Embed CC1101 带射频模块版本、M5 Cardputer 带键盘版本），每种开发板的引脚映射都经过优化配置。还提供 Bus Expander 扩展板增加 5GHz WiFi 等高级功能。

### Python 自动化与 Web 工具
内置 Python Lab 支持在浏览器中编写和测试自动化脚本，Serial Tools 提供基于 Web Serial API 的串口终端，无需安装 PuTTY 或 minicom 等传统工具。

---

## 应用场景

### 硬件安全研究
安全研究员可用于 IoT 设备协议分析、固件提取、侧信道攻击研究等场景。

### IoT 设备调试与开发
嵌入式开发者使用 I2C/SPI/UART 模式调试传感器、EEPROM、Flash 等外设，比传统逻辑分析仪更灵活。

### 智能家居协议分析
通过 Sub-GHz 和 RFID 模式分析智能家居设备的无线通信协议，适用于安全审计和兼容性研究。

### 硬件教学与实验
低成本、高覆盖面的特点使其成为电子工程和安全课程的理想教学工具。

---

## Star 数据

| 指标 | 数值 |
|------|------|
| ⭐ Stars | 4,712 |
| 🍴 Forks | 384 |
| 📝 语言 | C/C++（ESP-IDF） |
| 📅 创建时间 | 2025 年 |

---

## 总结
ESP32 Bit Pirate 以 ESP32 微控制器为基础，成功复刻并超越了经典 Bus Pirate 的功能，将专业级多协议分析能力带到了几十元的硬件平台上。20+ 协议支持、三种交互模式、10+ 开发板兼容性使其成为硬件黑客和安全研究领域的瑞士军刀，是「用最少的硬件做最多的事」这一理念的绝佳实践。

---

*数据来源：GitHub 仓库 (geo-tp/ESP32-Bit-Pirate)，2026 年 7 月访问*
