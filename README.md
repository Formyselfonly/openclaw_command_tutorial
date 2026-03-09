# OpenClaw CLI 完整命令行教学（Mac / Linux）

作者：Kerry Zheng 学习笔记

目标：从 **0 → 能正常运行 OpenClaw Gateway + 使用 Skills + 开发 Agent**

---

# 一、OpenClaw 是什么

OpenClaw 是一个 **AI Agent Runtime**。

核心作用：

LLM
↓
Agent
↓
Skills (Tools)
↓
Real World Actions

OpenClaw 提供：

- Gateway（Agent runtime）
- Skills（工具系统）
- MCP（模型工具协议）
- Dashboard UI
- CLI

默认 Gateway 端口：

[http://127.0.0.1:18789](http://127.0.0.1:18789/)

---

# 二、安装 OpenClaw

## 1 安装 CLI

Mac / Linux 推荐：

brew install openclaw

或者：

curl -fsSL [https://install.openclaw.ai](https://install.openclaw.ai/)
| bash

安装完成后测试：

openclaw --version

示例输出：

OpenClaw 2026.3.2

---

# 三、第一次初始化

初始化配置：

openclaw onboard

如果你想安装为系统后台服务：

openclaw onboard --install-daemon

但**学习阶段不推荐 daemon**。

---

# 四、OpenClaw 运行模式

OpenClaw 有两种运行模式：

### 1 前台模式（推荐学习）

openclaw gateway

或者：

openclaw gateway --port 18789

特点：

| 特点 | 说明 |
| --- | --- |
| 前台运行 | terminal关闭就停止 |
| 开发友好 | 能看到日志 |
| 推荐学习 | YES |

---

### 2 后台 daemon 模式

适合生产环境。

---

# 五、Daemon（后台服务）

## 1 安装 daemon

openclaw daemon install

macOS 本质是：

launchd service

---

## 2 启动 daemon

openclaw daemon start

---

## 3 停止 daemon

openclaw daemon stop

---

## 4 查看 daemon 状态

openclaw daemon status

---

## 5 重启 daemon

openclaw daemon restart

---

## 6 删除 daemon

openclaw daemon uninstall

---

# 六、Gateway 管理

Gateway 是 OpenClaw 的核心服务。

## 启动 Gateway

openclaw gateway

或者指定端口：

openclaw gateway --port 18789

---

## 安装 Gateway service

openclaw gateway install

---

## 停止 Gateway

openclaw gateway stop

---

# 七、查看 Gateway UI

启动后访问：

[http://127.0.0.1:18789](http://127.0.0.1:18789/)

你会看到：

OpenClaw Dashboard

可以：

- 查看 Agent
- 查看 Skills
- 查看 logs
- Debug

---

# 八、检查端口是否运行

Mac / Linux：

lsof -i :18789

如果看到：

LISTEN

说明 Gateway 正在运行。

---

# 九、杀死进程

如果端口被占用：

lsof -i :18789

得到 PID：

kill -9 PID

---

# 十、OpenClaw Skills

Skills 是 Agent 的工具。

结构：

skills/
├── web_search
├── file_reader
└── browser

---

## 查看 Skills

openclaw skills list

---

---

# 十二、Dashboard

OpenClaw Dashboard 是 UI 控制台。

打开：

openclaw dashboard

默认：

[http://127.0.0.1:18789](http://127.0.0.1:18789/)

---

# 十三、配置

配置文件：

~/.openclaw/config.yaml

修改配置：

openclaw configure

---

# 十四、日志

查看日志：

openclaw logs

实时日志：

openclaw logs -f

---

# 十五、Doctor（诊断）

诊断系统：

openclaw doctor

会检查：

- 配置
- skills
- gateway
- MCP

---

# 十六、常见问题

## 1 关闭 terminal 但服务还在

原因：

daemon mode

解决：

openclaw daemon stop

---

## 2 端口占用

检查：

lsof -i :18789

杀进程：

kill -9 PID

---

## 3 Gateway 启动失败

检查：

openclaw doctor

---

# 十七、OpenClaw 架构

User
↓
Gateway
↓
Agent
↓
MCP
↓
Skills
↓
Real Tools

---

# 十八、开发 AI Agent

典型流程：

1 安装 openclaw
2 启动 gateway
3 安装 skills
4 配置 LLM
5 创建 agent

---

# 十九、开发建议

学习顺序：

1 Gateway
2 Skills
3 MCP
4 Agent

不要一开始研究源码。

---

# 二十、学习路线（推荐）

Step 1
openclaw gateway

Step 2
openclaw dashboard

Step 3
openclaw skills list

Step 4
openclaw skills install browser

Step 5
测试 agent

---

# 二十一、推荐学习方式

不要只看文档。

建议：

terminal + dashboard + skills

边运行边看。

---

# 二十二、OpenClaw vs LangChain

| 系统 | 定位 |
| --- | --- |
| LangChain | Agent Framework |
| OpenClaw | Agent Runtime |

组合：

LangChain
↓
OpenClaw
↓
Skills

---

# 二十三、推荐开发方式

Vibe Coding：

LLM
↓
OpenClaw
↓
Skills
↓
Automation

---

# 二十四、总结

OpenClaw CLI 核心命令：

openclaw gateway
openclaw daemon start
openclaw daemon stop
openclaw skills list
openclaw skills install
openclaw dashboard
openclaw doctor

最常用：

openclaw gateway

---

# 二十五、给 Kerry 的建议

你现在做：

AI Agent
LangChain
DeepAgents
Automation

OpenClaw 非常适合：

AI Automation
Crypto Agent
Browser Agent
Web Scraping Agent

未来会成为：

AI Agent Infrastructure

非常值得深入学习。
