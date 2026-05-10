# Obsidian 快速上手配置管理指南

本目录旨在帮助用户快速配置和管理 Obsidian，打造**采集 → 整理 → 同步 → 发布**全链路打通的知识工作站。

---
## TODO
1. 快速找到没有被使用的附件/图片内容并且清理
2. 规划如何快速开PC迁移保持Obsidian的用户使用不变，装了一大堆的插件不需要重复的搞


## 整体架构

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                              Obsidian 知识工作站                                  │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                 │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    │
│  │   采集层    │───▶│   整理层    │───▶│   AI 层     │───▶│   同步层    │    │
│  └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘    │
│         │                 │                 │                 │                 │
│         ▼                 ▼                 ▼                 ▼                 │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    │
│  │ Web Clipper │    │  模板系统   │    │ Claudian   │    │   Git       │    │
│  │ 易记App    │    │  标签系统   │    │ LLM Wiki   │    │ Remotely    │    │
│  │ 微信/Flomo │    │  双链笔记   │    │ CC-Switch  │    │   Save      │    │
│  └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘    │
│                                                                                 │
└─────────────────────────────────────────────────────────────────────────────────┘

信息流：采集 ──→ 整理 ──→ AI加工 ──→ 同步备份 ──→ 输出发布
```

### 采集层

| 来源 | 工具 | 说明 |
|------|------|------|
| 网页 | Obsidian Web Clipper | 浏览器扩展一键剪藏 |
| YouTube | Web Clipper Reader 模式 | 视频转智能字幕阅读器 |
| 手机灵感 | 易记 App + 微信语音 | 语音快速捕捉 |
| 微信文章 | 微信读书 → Readwise | 文章同步 |
| X (Twitter) | Readwise | 高亮导入 |

### 整理层

| 工具 | 功能 |
|------|------|
| 模板系统 | 标准化笔记结构 |
| 标签系统 | 多维度分类 |
| 双链笔记 | 知识网络构建 |
| 数据库插件 | 可视化看板管理 |

### AI 层

| 工具 | 功能 |
|------|------|
| Claudian | Inline Edit、总结、翻译 |
| LLM Wiki | AI 自动编译整理知识 |
| CC-Switch | 多 AI 供应商切换 |

### AI 知识工程

深入理解 AI 工程化方法论与前沿实践：

| 主题 | 说明 |
|------|------|
| Harness Engineering | AI Agent 的工程化驾驭体系（R.E.S.T 模型、六大设计原则） |
| LLM Wiki | Karpathy 提出的 AI 驱动知识管理方法论 |

详见：[01-tech/ai-knowledge/README.md](../../ai-knowledge/README.md)

### 同步层

| 工具 | 场景 |
|------|------|
| Obsidian Git | 桌面端 → GitHub |
| Remotely Save | 移动端同步（S3/WebDAV） |
| 坚果云 | 易记 App → Vault |

### 输出层

| 方式 | 说明 |
|------|------|
| GitHub / GitCode | 笔记版本管理 |
| 公众号 / 博客 | 内容发布 |

---

## ✅ 已完成

### 1. Git 自动同步

Vault 通过 Git 推送至 GitHub / GitCode，实现版本管理与多端同步。

详见：[details/入门19-Obsidian-Git同步配置.md](details/入门19-Obsidian-Git同步配置.md)

### 2. Claudian AI 助手接入

通过 **Claudian 插件** 将 Claude Code 嵌入 Obsidian，获得 AI 协作能力。

| 项目 | 说明 |
|------|------|
| 插件 | [YishenTu/claudian](https://github.com/YishenTu/claudian) — MIT 协议 |
| 核心能力 | Inline Edit、Slash Commands、@mention 引用文件、Plan Mode、MCP Server |
| 中继管理 | 推荐 **CC-Switch**（[GitHub](https://github.com/farion1231/cc-switch)） |
| 成本策略 | 月包为主 + 按量备用 + CC-Switch 热切换 |

详见：[details/入门20-Claudian-AI助手配置.md](details/入门20-Claudian-AI助手配置.md)

---

## 🔲 待建设

### 3. 图片自动管理

**目标**：统一图片存储路径，粘贴/剪藏时自动归档。

**推荐方案**：
- Obsidian 设置 → 文件与链接 → 附件默认路径 → 设为 `attachments/` 或 `assets/`
- 插件 **Custom Attachment Location**：按 `assets/${filename}/` 规则自动归档
- 插件 **Local Images Plus**：自动将远程图片下载到本地

详见：[details/入门8-附件与图片管理.md](details/入门8-附件与图片管理.md)

### 4. 打通 X 平台信息检索

**目标**：将 X（Twitter）上的收藏导入 Obsidian。

**推荐方案**：
- **Obsidian Web Clipper**：浏览器扩展，一键剪藏
- **Readwise** → Obsidian：支持 X 高亮导入
- **IFTTT / n8n**：X 收藏 → Webhook → Vault

### 5. Lint 语法检查

**目标**：保证 Markdown 格式一致性。

**推荐方案**：
- 插件 **Obsidian Linter**：保存时自动修正格式
- 配合 Git pre-commit hook：提交前自动 lint

详见：[details/入门21-Obsidian-Linter配置.md](details/入门21-Obsidian-Linter配置.md)

### 6. 每日总结与事项规划

**目标**：自动化日记模板 + AI 生成每日回顾。

**推荐方案**：
- 插件 **Templater**：每日笔记模板自动填充
- 插件 **Tasks** / **Dataview**：汇总全库待办
- Claudian 场景：`/summarize-day` 和 `/plan-day`

详见：[details/入门16-日周复盘系统.md](details/入门16-日周复盘系统.md)

### 7. 微信打通能力

**目标**：微信好内容一键保存到 Vault。

**推荐方案**：
- **微信读书 → Readwise → Obsidian**
- **Flomo → Obsidian**
- **简悦 SimpRead**：支持微信文章剪藏

### 8. 手机端数据互联

**目标**：手机与桌面端同步。

详见：[details/入门22-手机端同步方案.md](details/入门22-手机端同步方案.md)

---

## 工具速查表

| 工具 / 插件 | 用途 | 状态 |
|-------------|------|------|
| Obsidian Git | Git 自动同步 | ✅ 已配置 |
| Claudian | AI 助手（Claude Code 嵌入） | ✅ 已接入 |
| CC-Switch | 多 AI 供应商切换 | ✅ 已推荐 |
| Obsidian Web Clipper | 浏览器一键剪藏 | ✅ 已安装 |
| Custom Attachment Location | 图片自动归档 | 📋 待安装 |
| Obsidian Linter | Markdown 格式检查 | 📋 待安装 |
| Templater | 日记/模板自动化 | 📋 待安装 |
| Tasks | 待办事项管理 | ✅ 已在用 |
| Remotely Save / Syncthing | 手机同步 | 📋 待选型 |

---

## 核心配置要点

### 1. 插件汉化配置（I18N 插件）

对于中文用户，插件界面的中文翻译是首要任务。

**安装步骤：**
1. 设置 → 第三方插件 → 禁用安全模式
2. 搜索 "obsidian-i18n" 并安装
3. 重启 Obsidian

**基础配置：**
- 目标语言：`zh-cn`
- 启用"本地文件模式"
- 启用"智能更新"

详见：[details/入门17-插件配置中文指南.md](details/入门17-插件配置中文指南.md)

### 2. Git 同步

详见：[details/入门19-Obsidian-Git同步配置.md](details/入门19-Obsidian-Git同步配置.md)

### 3. AI 助手

详见：[details/入门20-Claudian-AI助手配置.md](details/入门20-Claudian-AI助手配置.md)

### 4. 格式检查

详见：[details/入门21-Obsidian-Linter配置.md](details/入门21-Obsidian-Linter配置.md)

### 5. 手机端同步

详见：[details/入门22-手机端同步方案.md](details/入门22-手机端同步方案.md)

---

## 快速上手教程（details/）

共 28 篇教程，覆盖从核心概念到高级配置的完整学习路径。

### 第一阶段：核心入门

| 序号 | 标题 | 文件 |
|------|------|------|
| 1 | Obsidian 核心概念 | [快速上手1-Obsidian核心概念.md](details/快速上手1-Obsidian核心概念.md) |
| 2 | 编辑器基础 | [快速上手2-编辑器基础.md](details/快速上手2-编辑器基础.md) |
| 3 | 链接与搜索 | [快速上手3-链接与搜索.md](details/快速上手3-链接与搜索.md) |
| 4 | 标签系统 | [快速上手4-标签系统.md](details/快速上手4-标签系统.md) |
| 5 | 附件与图片管理 | [快速上手5-附件与图片管理.md](details/快速上手5-附件与图片管理.md) |
| 6 | 核心插件-模板 | [快速上手6-核心插件-模板.md](details/快速上手6-核心插件-模板.md) |

### 第二阶段：进阶功能

| 序号 | 标题 | 文件 |
|------|------|------|
| 7 | 模板系统进阶 | [快速上手7-模板系统进阶.md](details/快速上手7-模板系统进阶.md) |
| 8 | Calendar 日历 | [快速上手8-Calendar日历.md](details/快速上手8-Calendar日历.md) |
| 9 | 第三方插件安装 | [快速上手9-第三方插件安装.md](details/快速上手9-第三方插件安装.md) |
| 10 | Canvas 白板与 Excalidraw | [快速上手10-Canvas白板与Excalidraw.md](details/快速上手10-Canvas白板与Excalidraw.md) |
| 11 | 任务管理(TODO) | [快速上手11-任务管理.md](details/快速上手11-任务管理.md) |
| 12 | 搜索完全指南 | [快速上手12-搜索完全指南.md](details/快速上手12-搜索完全指南.md) |

### 第三阶段：精通技巧

| 序号 | 标题 | 文件 |
|------|------|------|
| 13 | 日周复盘系统 | [快速上手 13：记录很多却没沉淀？试试这套日周复盘系统.md](details/快速上手 13：记录很多却没沉淀？试试这套日周复盘系统.md) |
| 14 | 插件配置中文指南 | [快速上手 14：插件设置页看不懂？这套中文化方案更省心.md](details/快速上手 14：插件设置页看不懂？这套中文化方案更省心.md) |
| 15 | Obsidian-Git同步配置 | [快速上手 15：用 Git 同步 Obsidian 前，你要先想清这几件事.md](details/快速上手 15：用 Git 同步 Obsidian 前，你要先想清这几件事.md) |
| 16 | Claudian-AI助手配置 | [快速上手 16：把 AI 接进 Obsidian 后，最先值得用的场景有哪些.md](details/快速上手 16：把 AI 接进 Obsidian 后，最先值得用的场景有哪些.md) |
| 17 | Obsidian-Linter配置 | [快速上手 17：Obsidian 越用越乱前，先把 Linter 规范起来.md](details/快速上手 17：Obsidian 越用越乱前，先把 Linter 规范起来.md) |
| 18 | 手机端同步方案 | [快速上手 18：手机和电脑怎么同步最省心？常见方案一次对比.md](details/快速上手 18：手机和电脑怎么同步最省心？常见方案一次对比.md) |

### 第四阶段：高级配置

| 序号 | 标题 | 文件 |
|------|------|------|
| 19 | 完整工作流总览 | [快速上手 19：从采集到发布，怎样把 Obsidian 串成完整工作流.md](details/快速上手 19：从采集到发布，怎样把 Obsidian 串成完整工作流.md) |
| 20 | 数据库插件 | [快速上手 20：什么时候该上数据库视图？别一开始就用复杂了.md](details/快速上手 20：什么时候该上数据库视图？别一开始就用复杂了.md) |
| 21 | Web Clipper 完整指南 | [快速上手 21：怎样把网页稳定收进知识库？Web Clipper 最完整上手.md](details/快速上手 21：怎样把网页稳定收进知识库？Web Clipper 最完整上手.md) |
| 22 | LLM Wiki 知识管理与搭建 | [快速上手 22：想把 Obsidian 升级成 AI 知识库？从这套 LLM Wiki 开始.md](details/快速上手 22：想把 Obsidian 升级成 AI 知识库？从这套 LLM Wiki 开始.md) |
| 23 | 公众号发布工作流 | [快速上手 23：从 Obsidian 到公众号发布，完整流程到底怎么搭.md](details/快速上手 23：从 Obsidian 到公众号发布，完整流程到底怎么搭.md) |

### 第五阶段：实战补充

| 序号 | 标题 | 文件 |
|------|------|------|
| 24 | 手机端笔记同步助手配置 | [快速上手24-手机端笔记同步助手配置.md](details/快速上手24-手机端笔记同步助手配置.md) |
| 25 | Marp Slides 幻灯片制作 | [快速上手25-Marp-Slides幻灯片制作.md](details/快速上手25-Marp-Slides幻灯片制作.md) |

---

## 关键资源

- I18N 插件下载：[GitHub - eondrcode/obsidian-i18n](https://github.com/eondrcode/obsidian-i18n)
- Claudian 插件：[YishenTu/claudian](https://github.com/YishenTu/claudian)
- CC-Switch：[farion1231/cc-switch](https://github.com/farion1231/cc-switch)
- 官方文档：[Obsidian 中文帮助](https://publish.obsidian.md/help-zh/)
- 社区论坛：[Obsidian 中文论坛](https://forum-zh.obsidian.md/)

---

## 下一步

1. [快速上手 1：Obsidian 不只是笔记软件，先搞懂它的核心思路.md](快速上手 1：Obsidian 不只是笔记软件，先搞懂它的核心思路.md) - 了解核心概念
2. [快速上手 3：第一次打开 Obsidian，先学会这几个高频操作.md](快速上手 3：第一次打开 Obsidian，先学会这几个高频操作.md) - 创建第一篇笔记
3. [快速上手 19：从采集到发布，怎样把 Obsidian 串成完整工作流.md](快速上手 19：从采集到发布，怎样把 Obsidian 串成完整工作流.md) - 了解整体架构
