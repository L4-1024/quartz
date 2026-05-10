---
title: 快速上手 23：从 Obsidian 到公众号发布，完整流程到底怎么搭
aliases:
  - 快速上手 23：公众号发布工作流速览
  - 快速上手 23：公众号发布工作流
  - 快速上手 24：公众号发布工作流
  - 快速上手 26：公众号发布工作流完整指南
  - 公众号发布工作流完整指南
tags:
  - Obsidian
  - 公众号
  - 工作流
  - 图床
  - 微信公众号专辑
  - 快速上手
created: 2026-04-12T00:00:00.000Z
author: leland17
series: Obsidian 快速上手
series_order: 23
status: 已整理
content_type: tutorial
difficulty: 进阶
target_platform:
  - Obsidian
  - 微信公众号
intended_audience: 需要把 Obsidian 文章稳定发布到微信公众号的读者
reading_gain: 搭建从本地写作到公众号排版发布的完整链路
cover_image: assets/wechat-album/covers/wechat-publish-full.png
source_type: 教程整理稿
---
# 快速上手 23：从 Obsidian 到公众号发布，完整流程到底怎么搭

![[wechat-publish-full.png|公众号发布工作流封面]]

> 适读人群：需要把 Obsidian 文章稳定发布到微信公众号的读者
> 
> 阅读收获：搭建从本地写作到公众号排版发布的完整链路

本文给出一套适合 Obsidian 到微信公众号的完整发布链路，包括图床配置、图片替换、排版工具和发布步骤。本文整合了流程速览与完整配置内容，适合作为公众号发布主题的统一入口。

## 一、核心方案

![[wechat-publish-pipeline.png|公众号发布流程管线图]]

三个关键环节：

1. **对象存储图床**：负责托管文章图片
2. **Obsidian 图片上传插件**：负责替换本地图片链接
3. **公众号 Markdown 排版工具**：负责把 Markdown 转成适合后台粘贴的样式

这样可以减少手动上传图片和手工重排版带来的重复工作。

## 二、准备工作

![[wechat-oss.png|图床、图片替换与发布步骤关系图]]

### 1. 配置对象存储图床

以阿里云 OSS 为例，常见准备项如下：

1. 注册账号并开通 OSS
2. 创建 Bucket
3. 记录 AccessKey ID、AccessKey Secret、Bucket 名称和地域
4. 把读取权限设置为适合文章访问的公开模式

**配置提示**：

- Bucket 地域参数需与实际地域一致
- 发布完成后可按需清理临时图片
- 建议把公众号图片单独放到固定前缀目录中，便于统一管理

### 2. 配置 Obsidian 图片上传插件

常用插件为 `obsidian-image-upload-toolkit`。

需要重点确认的配置项：

| 配置项 | 作用 |
|------|------|
| AccessKey ID / Secret | 用于连接对象存储 |
| Bucket 名称 | 指定图片上传目标 |
| Bucket 地域 | 决定上传接口和访问地址 |
| 存储路径 | 统一图片目录结构 |

建议将公众号发布相关图片统一保存到类似 `wechat/YYYY-MM/` 的路径中，便于后续清理和追踪。

### 3. 选择公众号 Markdown 排版工具

常用工具为 `doocs/md` 提供的 WeChat Markdown Editor。

常见使用方式：

- 在线使用：<https://doocs-md.pages.dev>
- 自行部署：Fork 项目后启用 GitHub Pages

自建的优势在于样式和版本可控，适合长期维护固定品牌风格。

## 三、完整发布流程

### 第 1 步：在 Obsidian 中完成写作

- 正文使用标准 Markdown
- 图片先保留本地引用
- 尽量提前统一标题层级、引用样式和代码块语言标记

### 第 2 步：上传并替换图片

在命令面板中执行图片上传插件的发布命令，插件通常会完成以下工作：

1. 找到当前文章中的本地图片
2. 上传到对象存储
3. 把 Markdown 中的本地图片路径替换为公网路径
4. 生成可继续排版的正文内容

示例：

```markdown
![本地图片](logo.jpg)
```

替换后会变成：

```markdown
![云端图片](https://example-oss.com/wechat/logo.jpg)
```

### 第 3 步：执行排版

将处理后的 Markdown 内容粘贴到排版工具中，重点检查：

- 标题字号是否统一
- 引用块和代码块样式是否清晰
- 分隔线、图片间距、列表缩进是否稳定
- 移动端阅读时是否过密或过松

### 第 4 步：在公众号后台发布

完成排版后，复制到公众号后台并检查：

1. 图片是否正常加载
2. 封面、摘要和标题是否匹配
3. 段落间距是否适合手机阅读
4. 外链、代码块和表格是否需要额外调整

## 四、配置建议

![[wechat-publish-checklist.png|公众号发布检查清单]]

| 项目 | 建议 |
|------|------|
| 图片路径 | 使用固定前缀目录，按年月分类 |
| 清理策略 | 发布后按需清理临时图片 |
| 排版样式 | 固定一套公众号模板，减少每次重复调整 |
| 安全性 | AccessKey 仅用于图床配置，不写入公开文章 |

## 五、适合继续扩展的方向

### 自建排版模板

- 统一封面、引用、强调色和分隔线风格
- 保持不同文章之间的品牌一致性

### 多平台分发

- 在公众号之外同步到知乎、掘金、博客等平台
- 将图片托管与 Markdown 模板设计成通用流程

### 发布前检查清单

- 图片全部可访问
- 标题层级不超过三级
- 引用、列表和表格在手机端可读
- 文末保留相关阅读与行动提示

## 六、相关资源

- `obsidian-image-upload-toolkit`：<https://github.com/addozhang/obsidian-image-upload-toolkit>
- `doocs/md`：<https://github.com/doocs/md>
- 在线编辑器：<https://doocs-md.pages.dev>

## 联系方式

如果希望进一步交流 Obsidian 使用、知识库整理、公众号专辑改写或相关工作流问题，可通过以下方式联系：

- 扫码或者加个人绿泡泡：`Jaguar017`

![[快速上手1-联系方式合集-公众号.png|公众号联系方式合集]]
