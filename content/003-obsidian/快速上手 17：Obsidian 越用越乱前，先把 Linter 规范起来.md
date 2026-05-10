---
title: 快速上手 17：Obsidian 越用越乱前，先把 Linter 规范起来
aliases:
  - 快速上手 17：Obsidian Linter 配置
tags:
  - Obsidian
  - 微信公众号专辑
  - 快速上手
created: 2026-04-12T00:00:00.000Z
author: leland17
series: Obsidian 快速上手
series_order: 17
status: 已整理
content_type: tutorial
difficulty: 进阶
target_platform:
  - Obsidian
  - 微信公众号
intended_audience: 希望统一笔记格式、减少排版杂乱的读者
reading_gain: 建立适合长期维护的 Markdown 规范化配置
cover_image: assets/wechat-album/covers/linter.png
source_type: 教程整理稿
---
# 快速上手 17：Obsidian 越用越乱前，先把 Linter 规范起来

![[linter.png|Obsidian Linter 配置封面]]

> 适读人群：希望统一笔记格式、减少排版杂乱的读者
> 
> 阅读收获：建立适合长期维护的 Markdown 规范化配置

## 概述

![[linter-rules.png|Linter 规则清单示意]]

Obsidian Linter 插件用于自动检查和修正 Markdown 格式，保证笔记格式一致性，减少 Frontmatter 缺失、链接失效等问题。

---

## 安装

### 插件市场安装

1. `设置 → 第三方插件 → 安全模式` → 关闭
2. 搜索 "Obsidian Linter"
3. 安装并启用

### 手动安装

1. 下载 Release 文件
2. 创建 `.obsidian/plugins/obsidian-linter/`
3. 复制文件，重启 Obsidian

---

## 基础配置

![[linter-rule-stack.png|Linter 规则层级图]]

### 设置路径

`设置 → Linter`

### 核心配置项

| 配置项 | 建议值 | 说明 |
|--------|--------|------|
| 自动格式化 | 启用 | 保存时自动格式化 |
| 格式化间隔 | 实时 | 实时检查格式 |
| 缩进类型 | Spaces | 使用空格缩进 |
| 缩进大小 | 2 | 缩进 2 个空格 |

---

## 常用规则

### 1. YAML Frontmatter 规则

```yaml
# 强制要求 Frontmatter
require-yaml: true

# 强制字段
required-fields:
  - created
  - tags

# 自动添加 created 字段
auto-add-created: true

# 自动更新 modified 字段
auto-add-modified: true
```

### 2. 标题层级规则

```yaml
# 标题层级检查
heading-levels:
  start: 1
  end: 6

# 禁止跳过标题级别（如 H1 后直接 H3）
prevent-lowercase-headers: true
```

### 3. 空行规则

```yaml
# 段落之间必须有空行
paragraph-blank-line: true

# 列表项之间有空行
list-item-blank-line: true
```

### 4. 链接规则

```yaml
# 移除空链接
remove-empty-links: true

# 规范化内部链接
normalize-links: true
```

### 5. 标签规则

```yaml
# 标签小写
tags-lowercase: true

# 标签不允许空格
tags-no-spaces: true

# 自动整理标签排序
tags-sort: true
```

---

## 自定义规则示例

### 完整配置示例

```yaml
# .obsidian/linter.yaml
ruleGroups:
  - name: "Frontmatter"
    enabled: true
    rules:
      - require-yaml
      - required-fields:
          - created
          - tags

  - name: "Formatting"
    enabled: true
    rules:
      - heading-levels
      - paragraph-blank-line
      - list-item-blank-line

  - name: "Tags & Links"
    enabled: true
    rules:
      - tags-lowercase
      - remove-empty-links
```

---

## 使用方式

### 手动格式化

1. `Ctrl/Cmd + P` 打开命令面板
2. 输入 "Linter"
3. 选择格式化命令

### 保存时自动格式化

```
设置 → Linter → 启用 "Format on Save"
```

### 快捷键

| 命令 | 快捷键 |
|------|--------|
| 格式化整个文件 | `Ctrl + Shift + L` |
| 格式化选中文本 | `Ctrl + Shift + ;` |

---

## 配合 Git Hook 使用

### pre-commit hook 配置

1. 在 Vault 根目录创建 `.git/hooks/pre-commit`（Windows 用 `.git/hooks/pre-commit.bat`）：

```bash
#!/bin/bash
# 格式化 Markdown 文件
for file in $(git diff --cached --name-only --diff-filter=ACM | grep '\.md$'); do
  obsidian-linter --file "$file"
  git add "$file"
done
```

2. 添加执行权限：
   ```bash
   chmod +x .git/hooks/pre-commit
   ```

---

## 配合 Claudian 使用

Claudian 可用于语义层面的质量检查：

```markdown
# 使用 Claudian 检查
/semantic-check

# AI 检查内容：
# - 重复内容
# - 断链问题
# - 内容连贯性
# - 语义错误
```

---

## 常见问题

**Q：格式化和原有内容冲突？**

A：先在备份上测试，确认无误后再应用。

**Q：能否只检查不修改？**

A：使用 "Lint" 命令仅检查，不自动修改。

**Q：自定义规则不生效？**

A：检查 YAML 语法，确保配置文件格式正确。

---

## 相关资源

- Obsidian Linter：[GitHub](https://github.com/platers/obsidian-linter)
- 规则配置文档：[官方文档](https://platers.github.io/obsidian-linter/)

---

## 联系方式

如果希望进一步交流 Obsidian 使用、知识库整理、公众号专辑改写或相关工作流问题，可通过以下方式联系：

- 扫码或者加个人绿泡泡：`Jaguar017`

![[快速上手1-联系方式合集-公众号.png|公众号联系方式合集]]
