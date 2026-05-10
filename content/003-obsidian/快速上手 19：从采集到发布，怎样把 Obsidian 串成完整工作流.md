---
title: 快速上手 19：从采集到发布，怎样把 Obsidian 串成完整工作流
aliases:
  - 快速上手 19：完整工作流总览
tags:
  - Obsidian
  - 微信公众号专辑
  - 快速上手
created: 2026-04-12T00:00:00.000Z
author: leland17
series: Obsidian 快速上手
series_order: 19
status: 已整理
content_type: tutorial
difficulty: 进阶
target_platform:
  - Obsidian
  - 微信公众号
intended_audience: 希望从单点技巧过渡到完整工作流设计的读者
reading_gain: 理解整套知识管理流程的关键环节与工具分工
cover_image: assets/wechat-album/covers/workflow.png
source_type: 教程整理稿
---
# 快速上手 19：从采集到发布，怎样把 Obsidian 串成完整工作流

![[workflow.png|完整工作流总览封面]]

> 适读人群：希望从单点技巧过渡到完整工作流设计的读者
> 
> 阅读收获：理解整套知识管理流程的关键环节与工具分工

## 整体架构

![[workflow-map.png|完整工作流结构图]]

```
信息源                    中转处理                 存储 & 同步              输出
───────────────────────────────────────────────────────────────────────────
浏览器 / 微信 / X ──→  Web Clipper / 微信转发  ──→  Obsidian Vault  ──→  GitHub / GitCode
手机端 ──────────────→  易记 App (语音捕捉)      ──→       ↑↓             ──→  公众号 / 博客
                        Claudian AI 助手        ──→  Lint & 图片管理
                        CC-Switch 中继管理              每日总结
```

### 采集层的重要性

采集层是整个体系的入口，也是最容易被忽视的瓶颈所在。

碎片化灵感捕捉的最佳组合：**易记 App + 微信语音输入法 + 坚果云**

```
灵感 → 易记 App（语音输入）→ 坚果云 WebDAV → inspiration 文件夹
```

---

## 采集 → 整理 → 同步 → 发布

### 1. 信息采集

| 来源 | 工具 | 说明 |
|------|------|------|
| 网页 | Obsidian Web Clipper | 浏览器扩展，一键剪藏 |
| 微信 | 微信读书 → Readwise | 文章同步 |
| X (Twitter) | Readwise | X 高亮导入 |
| 微博 | 简悦 SimpRead | 稍后读 |
| 本地文件 | 拖拽/粘贴 | 自动归档到 attachments |

### 2. 整理

| 工具 | 功能 |
|------|------|
| I18N 插件 | 插件界面中文化 |
| 模板系统 | 标准化笔记结构 |
| 标签系统 | 多维度分类 |
| Claudian AI | 内容优化、总结、翻译 |
| Obsidian Linter | 格式自动检查 |

### 2.5 知识编译层

如果你已经开始积累大量文章、纪要、剪藏和研究材料，建议在“整理”阶段和“同步”阶段之间，再加一层：**知识编译层**。

它的核心思路来自 Karpathy 的 LLM Wiki：

- raw 层保存原始资料，只读不回写
- wiki 层保存 AI 整理后的知识页面
- schema 层用 `CLAUDE.md` 或 `AGENTS.md` 约束写法与流程

这样做之后，Obsidian 不只是“存笔记”，而是在持续生成一个可查询、可扩展、可体检的知识中间层。

### 3. 同步

![[sync-options.png|常见同步方案对比图]]

| 方案 | 适用场景 |
|------|----------|
| Obsidian Git | 桌面端自动同步到 GitHub/GitCode |
| Remotely Save | 移动端同步（支持 S3/WebDAV/OneDrive） |
| Syncthing | P2P 同步，不依赖云服务 |

### 4. 发布

| 方式 | 工具 |
|------|------|
| 博客 | Obsidian 导出 + Hexo/Hugo |
| 公众号 | AI 辅助排版 |
| GitHub Pages | 直接部署 |
| 静态站点 | Quartz / Hugo |

## 编译式知识工作流

很多人把 AI 当成一次性问答工具，但更稳的方式是把它纳入长期工作流。

### 三个关键动作

1. **Ingest**：新资料进入 raw，AI 负责生成摘要、更新话题页、补实体页、记录日志
2. **Query**：提问时优先读取 wiki，而不是每次重新翻 raw
3. **Lint**：周期性检查矛盾、过期结论、孤岛页面和缺失概念

### 为什么这层很值钱

- 同一份资料不会被你反复从零理解
- 查询结果更稳定，因为很多概念已经整理过
- 问答本身也能继续回流，变成新页面、新对比、新结论

对个人知识管理来说，这一层相当于把“记笔记”升级成“维护一个持续生长的知识系统”。

---

## 工具速查表

### 已配置 ✅

| 工具/插件 | 用途 | 文档 |
|-----------|------|------|
| Obsidian Git | Git 自动同步 | 对应“快速上手 15：Obsidian Git 同步配置” |
| Claudian | AI 助手 | 对应“快速上手 16：Claudian AI 助手配置” |
| CC-Switch | 多 AI 切换 | 同上 |
| Tasks | 待办管理 | 对应“快速上手 12：任务管理” |

### 待安装 📋

| 工具/插件 | 用途 | 文档 |
|-----------|------|------|
| Obsidian Web Clipper | 浏览器剪藏 | 对应“快速上手 21：Web Clipper 完整指南” |
| Custom Attachment Location | 图片自动归档 | 对应“快速上手 6：附件与图片管理” |
| Obsidian Linter | Markdown 检查 | 对应“快速上手 17：Obsidian Linter 配置” |
| Templater | 日记/模板自动化 | 对应“快速上手 8：模板系统进阶” |
| Remotely Save | 手机同步 | 对应“快速上手 18：手机端同步方案” |

---

## 每日工作流

![[workflow-daily-loop.png|每日工作流循环图]]

### 晨间（5 分钟）

1. 打开 Obsidian
2. Calendar 查看今日日记
3. `/plan-day` - AI 生成今日计划
4. 确认并填入 Tasks

### 日间（随时）

1. 看到好内容 → Web Clipper 剪藏
2. 随手记 → 快速添加标签
3. 任务完成 → 勾选 TODO

### 晚间（10 分钟）

1. 打开今日日记
2. 填充复盘内容
3. `/summarize-day` - AI 生成总结
4. 检查同步状态

---

## 配置清单

### 第一阶段：核心配置

- [x] 安装 I18N 插件（中文界面）
- [x] 配置 Git 自动同步
- [x] 配置 Calendar + 模板
- [x] 配置 Tasks 插件

### 第二阶段：AI 增强

- [x] 安装 Claudian 插件
- [x] 配置 CC-Switch 多供应商
- [ ] 配置 AI 辅助写作流程

### 第三阶段：移动端

- [ ] 安装 Remotely Save
- [ ] 配置 S3 存储
- [ ] 测试移动端同步

### 第四阶段：质量保证

- [x] 安装 Obsidian Linter ✅ 2026-04-12
- [ ] 配置格式规则
- [x] 配置 Git pre-commit hook ✅ 2026-04-28

---

## 联系方式

如果希望进一步交流 Obsidian 使用、知识库整理、公众号专辑改写或相关工作流问题，可通过以下方式联系：

- 扫码或者加个人绿泡泡：`Jaguar017`

![[快速上手1-联系方式合集-公众号.png|公众号联系方式合集]]
