---
title: TypeSet — Brand Typesetting
emoji: 🎨
colorFrom: blue
colorTo: gray
sdk: static
pinned: false
license: mit
short_description: Brand-exclusive WeChat typesetter — paste plain text, get styled typesetting instantly
---

# TypeSet / 品牌专属公众号排版器

> 品牌专属的公众号排版器 — 粘贴纯文字，自动排版，一键复制到公众号。
> Brand-exclusive WeChat official-account typesetter — paste plain text, get on-brand typesetting, copy to WeChat in one click.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Pure Frontend](https://img.shields.io/badge/stack-HTML%20%7C%20CSS%20%7C%20JS-blue.svg)](#技术栈)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-success.svg)](#快速开始)
[![No LLM](https://img.shields.io/badge/engine-rule--based%20(no%20LLM)-lightgrey.svg)](#设计原则)

---

[中文](#中文) | [English](#english)

---

## 中文

### 这是什么

**TypeSet** 是一款面向品牌方的公众号排版器。以 **Apple** 为示例品牌，把品牌固定的排版规范（配色、字号层级、字距、强调样式）**写死在代码里**——运营人员只需把写好的文字粘贴进来，工具自动识别文章结构、套用统一版式，再一键复制到公众号，从根上保证风格统一。

- ✅ 纯文字输入，零学习成本（无需 Markdown 等任何标记语法）
- ✅ 纯规则引擎，输出 100% 确定、可复现（不接大模型）
- ✅ 单文件离线运行，零依赖、无需联网、无需构建

### 核心功能

| 模块 | 说明 |
|:---:|------|
| 结构识别 | 纯规则启发式：第一行当标题、空行分段、长句按标点断句、列表符号识别、小节标题识别、引号关键词高亮 |
| 版式套用 | 把品牌视觉规范写成 CSS 设计 token（苹果蓝 #0071e3、近黑 #1d1d1f、浅灰底 #f5f5f7…） |
| 实时排版 | 左边输入，右边即时渲染，所见即所得，无需点击任何按钮 |
| 一键复制 | 把排版后的富文本复制进剪贴板，直接粘贴到公众号编辑器 |

### 启发式识别规则

- **大标题**：输入的第一行（或第一段概括出的主题句）识别为文章大标题
- **空行分段**：连续文字按空行分段；超长一行按句末标点（。！？；…）自动断句
- **列表**：以「·」「-」「•」「*」或数字序号（1. / 1、）开头的行识别为列表项
- **小节标题**：以「一、二、三…」开头、或独立成段的「结语 / 引言 / 前言」等词，自动加粗
- **行内强调**：「小标题：说明」结构自动加粗放大；引号（“ ” 「 」）内关键词自动加浅蓝高亮
- **容错兜底**：完全无分段、无标点也能按字数兜底拆分并自动提取标题

### 设计原则

- **品牌规范固化**：把「靠人记在脑子里」的排版规范，变成「靠工具写死在代码里」——风格由品牌方定死，一键套用，杜绝跑偏
- **纯规则、可复现**：同一篇文字任何时候贴进来，排版结果都一样。大模型无约束下容易「自由发挥」（幻觉），不适用于需要稳定一致的排版场景
- **AI 用在开发侧，不用在产品运行侧**：AI 用来写代码、定方案、调视觉；排版本身用确定性的规则引擎
- **设计规范可复用**：颜色、字号、圆角、阴影全部用 CSS 变量管理，换一个品牌只需改一组变量
- **零依赖、链路极短**：单文件 HTML，双击即用，连网络都不需要

### 项目结构

```
typeset/
├── index.html      # 核心原型：单文件（HTML + CSS + JS 全内联），双击即用
├── gen_doc.py      # 生成《项目说明》Word 文档的脚本（python-docx）
├── README.md
└── LICENSE
```

### 技术栈

| 层 | 技术 |
|------|------|
| 结构识别 | 纯规则启发式（无 LLM、无 API） |
| 界面 / 样式 | HTML + CSS（CSS 变量设计 token、scrollbar-gutter） |
| 交互 | 原生 JavaScript（实时排版、富文本复制） |
| 部署 | 零依赖，单文件静态页面 |

### 快速开始

```bash
# 1. 克隆仓库
git clone https://github.com/Rsaaaa9/typeset.git
cd typeset

# 2. 直接双击 index.html（或用浏览器打开）
# 无需安装、无需联网、无需构建
```

> 或在线预览：**https://rsaaaa9.github.io/typeset/**（GitHub Pages 部署，点开即用）

### 生成项目说明文档（可选）

```bash
pip install python-docx
python gen_doc.py   # 生成《秋芝2046线上笔试-公众号排版器-项目说明.docx》
```

### License

MIT — 自由使用、修改、分发。保留署名。

---

## English

### What is TypeSet?

**TypeSet** is a brand-exclusive typesetter for WeChat official accounts. Using **Apple** as the reference brand, it bakes the brand's fixed typesetting rules (colors, type hierarchy, letter-spacing, emphasis styles) **directly into code** — editors just paste their text, the tool recognizes the structure, applies the on-brand style, and copies the result to WeChat in one click.

- ✅ Plain-text input, zero learning curve (no Markdown or markup)
- ✅ Pure rule-based engine — 100% deterministic and reproducible (no LLM)
- ✅ Single-file, offline, zero dependencies, no build step

### Core Features

| Module | Description |
|:---:|------|
| Structure Recognition | Pure rule-based heuristics: first line as title, blank-line paragraphs, sentence-boundary splitting, list symbols, section titles, quoted keyword highlight |
| Style Application | Brand visual rules encoded as CSS design tokens (Apple blue #0071e3, near-black #1d1d1f, light-gray #f5f5f7…) |
| Real-time Typesetting | Type on the left, styled output on the right — WYSIWYG, no button needed |
| One-click Copy | Copies rich text to the clipboard, paste directly into the WeChat editor |

### Design Principles

- **Brand rules, codified**: Turn "rules kept in people's heads" into "rules written in code" — style is fixed by the brand, applied in one click
- **Deterministic and reproducible**: The same text always renders the same way. Unconstrained LLMs tend to "hallucinate" and are unfit for styling that must stay stable
- **AI for development, not runtime**: AI writes the code and tunes the visuals; typesetting itself uses a deterministic rule engine
- **Reusable design spec**: Colors, sizes, radii, and shadows live in CSS variables — switch brands by changing one set of variables
- **Zero-dependency, shortest path**: A single HTML file, double-click to run, no network needed

### Project Structure

```
typeset/
├── index.html      # Core prototype: single file (HTML + CSS + JS inlined), double-click to run
├── gen_doc.py      # Script that generates the project-description Word doc (python-docx)
├── README.md
└── LICENSE
```

### Tech Stack

| Layer | Tech |
|------|------|
| Structure Recognition | Pure rule-based heuristics (no LLM, no API) |
| UI / Styling | HTML + CSS (CSS variable design tokens, scrollbar-gutter) |
| Interaction | Vanilla JavaScript (real-time rendering, rich-text copy) |
| Deployment | Zero dependencies, single-file static page |

### Quick Start

```bash
# 1. Clone the repo
git clone https://github.com/Rsaaaa9/typeset.git
cd typeset

# 2. Double-click index.html (or open it in any browser)
# No install, no network, no build step
```

> Or try the live demo: **https://rsaaaa9.github.io/typeset/**

### License

MIT — free to use, modify, and distribute. Attribution appreciated.
