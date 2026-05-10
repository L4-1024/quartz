---
title: 快速上手 21：怎样把网页稳定收进知识库？Web Clipper 最完整上手
aliases:
  - 快速上手 21：Web Clipper 完整指南
  - 快速上手 22：Web Clipper 完整指南
  - 快速上手 24：Web Clipper 完整指南
  - Obsidian Web Clipper 完整使用指南
tags:
  - Obsidian
  - 插件
  - 剪藏
  - 微信公众号专辑
  - 快速上手
created: 2026-04-12T00:00:00.000Z
author: leland17
series: Obsidian 快速上手
series_order: 21
status: 已整理
content_type: tutorial
difficulty: 进阶
target_platform:
  - Obsidian
  - 微信公众号
intended_audience: 需要把网页资料稳定导入知识库的读者
reading_gain: 完成 Web Clipper 安装、模板配置与剪藏流程设计
cover_image: assets/wechat-album/covers/web-clipper.png
source_type: 教程整理稿
---
# 快速上手 21：怎样把网页稳定收进知识库？Web Clipper 最完整上手

![[web-clipper.png|Web Clipper 完整指南封面]]

> 适读人群：需要把网页资料稳定导入知识库的读者
> 
> 阅读收获：完成 Web Clipper 安装、模板配置与剪藏流程设计

**Obsidian Web Clipper** 是 Obsidian 官方出品的浏览器插件，用于一键将网页内容保存到 Obsidian 笔记库中。

## 一、安装与基础配置

![[web-clipper-browser-flow.png|Web Clipper 浏览器工作流]]

### 1. 安装插件

访问官方地址：https://obsidian.md/zh/clipper

- Chrome / Edge：点击「Install for Chrome」从 Chrome Web Store 安装
- Firefox：点击「Install for Firefox」从 Firefox Add-ons 安装

安装完成后，浏览器右上角会出现 Obsidian 黑色图标。

### 2. 初始配置

点击浏览器右上角的 Obsidian 图标，点击齿轮设置图标，主要设置以下内容：

1. **Language**：改为 `中文`
2. **Vaults**：填入你的库名称
3. **Default open behavior**：默认打开方式，建议设置为 `Reader` 或 `Open in Reader mode`

### 3. 新建模板

进入模板页面，按照需求填写，例如：

- **笔记位置**：设置专门的文件夹，如 `clipps/{{date}}`
- **文件命名**：使用标题或自定义格式

## 二、网页剪藏

![[clipper-flow.png|网页剪藏到 Obsidian 的典型链路]]

### 基本使用

1. 打开需要剪藏的网页
2. 点击浏览器右上角的 Obsidian 图标
3. 选择剪藏模式：
   - **Article**：文章模式，自动提取正文
   - **Screenshot**：截图模式
   - **Selection**：选择模式，只保存选中内容
   - **Visible**：可见区域模式
   - **Entire page**：整页模式
4. 点击「Add to Obsidian」

### Reader 模式（推荐）

对于长文章、教程，强烈推荐使用 Reader 模式：

1. 点击 Obsidian 图标
2. 点击书本图标（Reader 模式）
3. 进入阅读视图，界面干净整洁
4. 可以高亮文本、添加笔记
5. 最终点击保存到 Obsidian

## 三、YouTube 视频智能阅读器

![[web-clipper-youtube-reader.png|Web Clipper 阅读模式示意]]

Web Clipper 1.4+ 版本新增了强大的 YouTube Reader 模式，可以将视频变成可搜索、可高亮的智能文档。

### 配置要求

- Web Clipper 版本 >= 1.4
- YouTube 视频需要带有字幕（自动字幕也可以）

### 使用步骤

1. 打开任意带字幕的 YouTube 视频
2. 点击浏览器右上角的 Obsidian 图标
3. 点击书本图标（Reader 模式）

### Reader 模式界面

- **左侧**：视频章节大纲（如果视频有章节自动显示）
- **中间**：干净的视频播放器
- **下方**：完整的带时间戳的字幕（transcript）

### 实用交互功能

- **点击字幕跳转**：点击任意一行字幕，视频立刻精准跳转到那个时间点
- **自动高亮**：视频播放时，当前正在说的那行字幕会自动高亮
- **自动滚动**：字幕会自动向下滚动，始终把当前行保持在屏幕中央
- **高亮保存**：选中字幕里的文字，可以直接高亮保存到 Obsidian（带视频链接和时间戳）

### 顶部开关建议

全部打开：
- ✅ **Pin player**：固定视频位置
- ✅ **Auto-scroll**：自动滚动
- ✅ **Highlight active line**：高亮当前行

## 四、图片本地化

### 问题

剪藏下来的文章，图片通常还是外链，时间久了原站图片可能会挂掉，而且 AI 无法读取挂掉的图片链接。

### 解决方案

1. **设置附件存储路径**
   - 打开 Obsidian 设置 → 「文件与链接」
   - 把附件存储路径设为当前文件夹下的 `attachments` 子文件夹

2. **绑定下载快捷键**
   - 打开 Obsidian 设置 → 「快捷键」
   - 搜索「下载」
   - 绑定 `Ctrl+Shift+D`（或其他你喜欢的组合）

3. **使用方法**
   - 剪藏完文章后按一下快捷键
   - 所有图片自动下载到本地

## 五、常见问题

### Q: 保存位置设置了日期，但实际保存时连时间也带上了？

A: 这是 Web Clipper 的默认行为。可以在模板设置中调整文件名格式，使用 `{{date:YYYY-MM-DD}}` 而不是 `{{date}}`。

### Q: Firefox 浏览器没有 Reader 模式？

A: Firefox 用户可能需要等 1-3 周才能更新到最新版，建议暂时使用 Chrome / Edge。

## 六、参考链接

- 官方帮助文档：https://obsidian.md/help/web-clipper/reader
- 插件下载：https://obsidian.md/zh/clipper

## 联系方式

如果希望进一步交流 Obsidian 使用、知识库整理、公众号专辑改写或相关工作流问题，可通过以下方式联系：

- 扫码或者加个人绿泡泡：`Jaguar017`

![[快速上手1-联系方式合集-公众号.png|公众号联系方式合集]]
