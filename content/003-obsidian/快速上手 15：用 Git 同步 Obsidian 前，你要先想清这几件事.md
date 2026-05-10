---
title: 快速上手 15：用 Git 同步 Obsidian 前，你要先想清这几件事
aliases:
  - 快速上手 15：Obsidian Git 同步配置
tags:
  - Obsidian
  - 微信公众号专辑
  - 快速上手
created: 2026-04-12T00:00:00.000Z
author: leland17
series: Obsidian 快速上手
series_order: 15
status: 已整理
content_type: tutorial
difficulty: 进阶
target_platform:
  - Obsidian
  - 微信公众号
intended_audience: 希望用 Git 管理笔记历史和跨设备同步的读者
reading_gain: 完成 Obsidian Git 基础配置并理解认证方式与同步节奏
cover_image: assets/wechat-album/covers/obsidian-git.png
source_type: 教程整理稿
---
# 快速上手 15：用 Git 同步 Obsidian 前，你要先想清这几件事

![[obsidian-git.png|Obsidian Git 同步配置封面]]

> 适读人群：希望用 Git 管理笔记历史和跨设备同步的读者
> 
> 阅读收获：完成 Obsidian Git 基础配置并理解认证方式与同步节奏

## 概述

![[git-sync.png|Git 同步流程示意]]

通过 Git 实现 Vault 版本管理与多端同步，确保笔记安全并可在多设备间同步。

---

## 安装 Obsidian Git 插件

### 方式一：插件市场安装

1. `设置 → 第三方插件 → 安全模式` → 关闭
2. 搜索 "Obsidian Git"
3. 安装并启用

### 方式二：手动安装

1. 下载 Release 文件（`main.js`、`manifest.json`）
2. 创建 `.obsidian/plugins/obsidian-git/`
3. 复制文件，重启 Obsidian

---

## 基础配置

![[git-sync-auth-choice.png|Git 同步认证方式选择图]]

### 设置仓库信息

```
设置 → Obsidian Git → Git 设置
```

| 配置项 | 建议值 | 说明 |
|--------|--------|------|
| 仓库路径 | 空（使用 Vault 根目录） | 或指定子文件夹 |
| 自动提交间隔 | 30 分钟 | 自动保存更改 |
| 自动推送间隔 | 60 分钟 | 推送到远程仓库 |
| 自动拉取间隔 | 30 分钟 | 从远程拉取更新 |

### 认证方式

#### 方式一：SSH Key（推荐）

1. 生成 SSH Key：
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```

2. 将公钥添加到 GitHub/GitCode：
   - GitHub：`Settings → SSH and GPG keys → New SSH key`
   - GitCode：个人设置 → SSH 公钥

3. 测试连接：
   ```bash
   ssh -T git@github.com
   ```

#### 方式二：Token

1. GitHub：Settings → Developer settings → Personal access tokens → Generate new token
2. 设置仓库读写权限
3. 使用 URL 方式配置远程：
   ```
   https://ghp_TOKEN@github.com/username/repo.git
   ```

---

## 使用命令

### 命令面板操作

1. `Ctrl/Cmd + P` 打开命令面板
2. 输入 "Obsidian Git" 查看可用命令：

| 命令 | 说明 |
|------|------|
| Open Git panel | 打开 Git 面板 |
| Commit | 手动提交 |
| Push | 推送到远程 |
| Pull | 从远程拉取 |
| Commit and push | 提交并推送 |

### 快捷键配置

```
设置 → Obsidian Git → 快捷键
```

| 命令 | 建议快捷键 |
|------|------------|
| Commit | `Ctrl + Shift + G` |
| Push | `Ctrl + Shift + P` (Push) |
| Pull | `Ctrl + Shift + U` (Pull) |

---

## Git 面板功能

安装插件后，侧边栏会显示 Git 面板：

- **Changes**：显示已修改但未提交的文件
- **Staged Changes**：已暂存的文件
- **Commit**：提交按钮
- **Push/Pull**：推送/拉取按钮

---

## 最佳实践

### 1. 定期提交

- 设置较短的自动提交间隔（如 15-30 分钟）
- 重要更改后手动提交

### 2. 提交信息规范

```bash
# 格式
[类型] 简短描述

# 示例
[feat] 添加项目笔记
[fix] 修复模板变量问题
[docs] 更新配置文档
```

### 3. 分支策略

- `main`：稳定版本
- `draft`：草稿笔记
- 按需求创建功能分支

### 4. 忽略敏感文件

创建 `.gitignore` 文件：

```gitignore
# Obsidian 配置（按需忽略）
# .obsidian/workspace

# 临时文件
*.tmp
*.bak

# 系统文件
.DS_Store
Thumbs.db
```

---

## 多端同步工作流

```
桌面端（写笔记）
    ↓ 自动 commit
GitHub / GitCode
    ↓ 自动 pull
移动端（查看/编辑）
    ↓ 自动 commit
GitHub / GitCode
    ↓ 自动 pull
桌面端（同步）
```

---

## 常见问题

**Q：推送失败？**

A：检查 SSH Key 配置或 Token 是否有效。

**Q：冲突如何处理？**

A：Obsidian Git 不会自动合并冲突，需要手动处理或使用外部 Git 工具。

**Q：能否同步 .obsidian 配置？**

A：可以，但不建议同步插件列表（不同设备可能需要不同插件）。

---

## 联系方式

如果希望进一步交流 Obsidian 使用、知识库整理、公众号专辑改写或相关工作流问题，可通过以下方式联系：

- 扫码或者加个人绿泡泡：`Jaguar017`

![[快速上手1-联系方式合集-公众号.png|公众号联系方式合集]]
