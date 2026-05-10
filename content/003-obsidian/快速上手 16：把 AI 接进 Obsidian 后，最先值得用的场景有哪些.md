---
title: 快速上手 16：把 AI 接进 Obsidian 后，最先值得用的场景有哪些
aliases:
  - 快速上手 16：Claudian AI 助手配置
tags:
  - Obsidian
  - 微信公众号专辑
  - 快速上手
created: 2026-04-12T00:00:00.000Z
author: leland17
series: Obsidian 快速上手
series_order: 16
status: 已整理
content_type: tutorial
difficulty: 专题
target_platform:
  - Obsidian
  - 微信公众号
intended_audience: 希望在 Obsidian 中引入 AI 辅助整理与写作的读者
reading_gain: 完成 Claudian 安装与基础配置，并了解适用场景
cover_image: assets/wechat-album/covers/claudian.png
source_type: 教程整理稿
---
# 快速上手 16：把 AI 接进 Obsidian 后，最先值得用的场景有哪些

![[claudian.png|Claudian AI 助手配置封面]]

> 适读人群：希望在 Obsidian 中引入 AI 辅助整理与写作的读者
> 
> 阅读收获：完成 Claudian 安装与基础配置，并了解适用场景

## 概述

![[ai-assistant.png|AI 助手协作流程示意]]

Claudian 插件将 Claude Code 嵌入 Obsidian，获得 AI 协作能力，支持 Inline Edit、Slash Commands、@mention 引用文件、Plan Mode、MCP Server 等功能。

---

## 安装方式

### 方式一：手动安装（推荐国内用户）

1. 访问 [Claudian GitHub](https://github.com/YishenTu/claudian)
2. 下载 Release 文件：
   - `main.js`
   - `manifest.json`
   - `styles.css`（如有）

3. 创建插件目录：
   ```
   <vault>/.obsidian/plugins/claudian/
   ```

4. 复制文件到该目录
5. 重启 Obsidian
6. 在插件列表中启用

### 方式二：使用 Skill 一键安装

```bash
# 使用 skills 安装
git clone https://github.com/chujianyun/skills
# 参考 Claudian 一键安装 Skill
```

---

## 基础配置

### 设置 API

1. `设置 → Claudian`
2. 配置 Claude API：
   - API Key：输入 Claude API Key
   - 或使用反代地址

### 推荐配置

| 配置项 | 建议值 |
|--------|--------|
| 模型 | Claude 3.5 Sonnet |
| Temperature | 0.7 |
| 最大 Token | 4096 |
| 启用 Inline Edit | ✅ |
| 启用 Slash Commands | ✅ |

---

## 核心功能

![[claudian-capability-map.png|Claudian 能力地图]]

### 1. Inline Edit（逐词 Diff）

在编辑模式下，选中文字后使用 Claudian 进行改写：

1. 选中需要修改的文本
2. 输入 `/edit` 或右键选择 Claudian Edit
3. AI 逐词对比，Accept/Reject 每个修改

### 2. Slash Commands

在笔记中输入 `/` 触发命令：

| 命令 | 功能 |
|------|------|
| `/edit` | 编辑选中内容 |
| `/summarize` | 总结内容 |
| `/translate` | 翻译内容 |
| `/explain` | 解释概念 |
| `/plan` | 制定计划 |

### 3. @mention 引用文件

使用 `@` 引用 Vault 中的文件：

```
`@[[笔记名称]]` - 引用整篇笔记
`@[[笔记名称#段落]]` - 引用特定段落
```

### 4. Plan Mode

规划模式，用于长文档写作：

1. 输入 `/plan` 启动
2. AI 分析当前内容
3. 生成大纲建议
4. 按计划逐步生成内容

### 5. MCP Server

支持 Model Context Protocol，可连接外部工具：

- Web Search
- File System
- Custom Tools

## 从聊天助手到知识库维护者

Claudian 真正有价值的地方，不只是“帮你改一段话”，而是把 AI 从临时聊天窗口，变成 Obsidian 里的长期维护者。

Karpathy 在 LLM Wiki 的思路里强调了一点：AI 不该只负责回答问题，还应该负责维护知识页之间的关系。这对 Claudian 特别适用。

### 更值得优先使用的三个场景

1. **入库整理**：读一篇新资料，生成摘要，补充已有主题页
2. **横向对比**：把多篇笔记整理成对比表、结论页、专题页
3. **例行体检**：扫描孤立页面、重复结论、过期说法、缺失概念

### 使用原则

- 不要只让它“回答”，要让它“回写结构化结果”
- 不要一次扔太多杂乱材料，优先一篇一篇处理
- 不要让重要结论只留在对话里，要沉淀回笔记
- 不要把 raw 素材和整理后的结论混在同一个层级

一句话说，Claudian 最强的不是替你写一句话，而是替你长期做那些人类懒得反复做的整理、补链和维护工作。

---

## 配合 CC-Switch 使用

CC-Switch 是多 AI 供应商切换工具，支持 Claude Code / Codex / Gemini 等 50+ 供应商。

### 安装 CC-Switch

1. 访问 [CC-Switch GitHub](https://github.com/farion1231/cc-switch)
2. 下载并安装

### 配置

1. 启动 CC-Switch
2. 添加 API Key（多个供应商）
3. 设置默认供应商
4. 设置快捷键切换

### 使用方式

```
Claudian → CC-Switch → 自动路由到可用 AI
```

### 成本策略

| 策略 | 方案 | 适用场景 |
|------|------|----------|
| 月包 | CodeSome 289元/月（900美元额度） | 日常高频使用 |
| 按量 | AigoCode / PackyAPI | 低频/备用 |
| 热切换 | CC-Switch | 避免单点故障 |

#### 成本优化三层方案

1. **月包打底**：CodeSome 月包 289 元/月，每天 30 美金额度，一个月 900 美金
2. **按量补充**：额度用完或不稳定时，切换到按量付费中转站
3. **工具切换**：通过 CC-Switch 在多家中转站间无感切换

**优势**：
- 单点故障风险低：同时不稳定的概率很低
- 固定成本可控：月包是固定成本，按量只是备份
- 全程无广告：推荐的中转站都是作者亲身使用过的

---

## 使用场景

### 场景一：每日结束总结

```
1. 打开当日日记
2. 输入 /summarize-day
3. AI 汇总今日完成项
4. 自动写入日记
```

### 场景二：每日开始规划

```
1. 打开当日日记
2. 输入 /plan-day
3. AI 根据未完成 Tasks 生成计划
4. 确认后写入待办
```

### 场景三：笔记优化

```
1. 选中需要优化的笔记内容
2. 输入 /edit
3. AI 提供优化建议
4. Accept/Reject 修改
```

---

## 常见问题

**Q：API 调用失败？**

A：检查 API Key 是否正确，网络是否可达。

**Q：如何切换 AI 供应商？**

A：通过 CC-Switch 一键切换。

**Q：是否支持本地模型？**

A：支持配置本地模型地址（如 Claude Local）。

---

## 进阶理念：Karpathy 的 LLM Wiki 工作流

AI 大神 Karpathy 分享了一种全新的 Obsidian 使用方式：**让 LLM 当你的知识库管理员**。

### 核心理念：知识「编译器」

传统的 RAG 检索像图书馆员——你问一个问题，它跑去书架上翻几本最相关的段落。

LLM Wiki 更像全职助手——它把所有材料都读完了，自己维护一份持续更新的笔记本。

| 对比   | RAG 检索   | LLM Wiki     |
| ---- | -------- | ------------ |
| 工作方式 | 每次现找相关段落 | 提前消化，持续更新知识  |
| 组织方式 | 原始材料不变   | AI 主动整理、建立关联 |
| 效果   | 越用越聪明？❌  | 越用越聪明 ✅      |

### Obsidian 作为「IDE 前端」

Karpathy 把 Obsidian 当作这个系统的 IDE 前端，同时看三层东西：

- **原始资料**：`raw/` 目录存放文章、论文、图片等
- **LLM 编译的 wiki**：`wiki/` 目录存放 AI 生成的结构化知识
- **可视化结果**：基于资料继续生成的内容

### LLM Wiki 的价值

在知识库达到一定规模后（100篇文章、40 万词），你可以直接对着整个 wiki 问复杂问题。

关键判断：**在中小规模阶段，未必需要很重的 RAG**。

LLM 自己维护索引文件、摘要文件、概览文件，已经能把很多问题处理得很好：

- 临时去翻仓库 vs 在自己整理过的书房里找东西
- 效率和感觉完全不是一回事

### 知识回流

最值钱的输出不是终端里那一坨字，而是能继续回流进知识库的东西：

- Markdown 文件
- Marp 格式的 slides
- matplotlib 图片

**每问一次，知识库不是被消耗一次，反而会变厚一点。**

---

## 相关资源

- Claudian：[YishenTu/claudian](https://github.com/YishenTu/claudian)
- CC-Switch：[farion1231/cc-switch](https://github.com/farion1231/cc-switch)
- 参考资料：《让 Claude 成为你的 Obsidian 助手》

---

## 联系方式

如果希望进一步交流 Obsidian 使用、知识库整理、公众号专辑改写或相关工作流问题，可通过以下方式联系：

- 扫码或者加个人绿泡泡：`Jaguar017`

![[快速上手1-联系方式合集-公众号.png|公众号联系方式合集]]
