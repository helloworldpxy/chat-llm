# Chat-LLM v1.0

> **A tool that lets you input your API Key and chat with LLMs.**  
> 一个简洁高效的在线大模型对话工具，支持 DeepSeek 全系列模型，纯前端实现，无需后端部署。

[![GitHub stars](https://img.shields.io/github/stars/helloworldpxy/chat-llm?style=social)](https://github.com/helloworldpxy/chat-llm)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-v1.0-blue)](https://github.com/helloworldpxy/chat-llm)

---

## ✨ 特性

- 🤖 **支持 DeepSeek 全系列模型**  
  deepseek-v4-flash / deepseek-v4-pro / deepseek-chat / deepseek-reasoner，通过下拉菜单自由切换。

- 🧠 **思考模式 + 强度调节**  
  开启思考后可见模型的内部推理过程，支持 `high` / `max` 两种强度。

- 🌐 **联网搜索开关**  
  一键启用联网搜索，让模型获取实时信息。

- 📎 **多文件上传 + DOCX 解析**  
  支持上传 txt、md、pdf、docx、代码文件等多种格式，自动提取文本内容并加入对话。  
  DOCX 文件通过 Mammoth.js 在前端直接解析，无需服务器。

- 🎨 **科幻风 UI 设计**  
  玻璃拟态 + 霓虹渐变，支持夜间 / 白天 / 跟随系统三种主题模式。

- 🔒 **数据本地存储**  
  API Key、用户信息等所有设置保存在浏览器 localStorage 中，不会上传到任何服务器（除你指定的 API 端点外）。

- 🚀 **流式响应**  
  实时展示模型输出，支持随时中断生成。

- 📱 **响应式布局**  
  适配桌面和移动端浏览器。

---

## 🖼️ 界面预览


- ![Chat-LLM 界面截图1](<img width="2820" height="1408" alt="图片" src="https://github.com/user-attachments/assets/37a70333-2365-45e1-b1db-0da6bb97d198" />
)
- ![Chat-LLM 界面截图2](<img width="2820" height="1408" alt="图片" src="https://github.com/user-attachments/assets/7c737bc9-247f-48a4-b8ad-30868d490b89" />
)

---

## 🚀 快速开始

### 方式一：直接使用在线版（推荐）

1. 访问 GitHub Pages 或其他托管地址（如果已部署）  
   或者直接双击打开本地的 `Chat-LLM.html` 文件。
2. 点击左上角 **☰** 打开设置面板。
3. 填入你的 API Key（从 [DeepSeek 开放平台](https://platform.deepseek.com/api_keys) 获取）。
4. 可选：填写用户信息（作为 System Prompt 发送给模型）。
5. 保存设置，关闭面板，然后在底部输入框开始对话。

### 方式二：本地运行

```bash
# 克隆仓库
git clone https://github.com/helloworldpxy/chat-llm.git

# 进入目录
cd chat-llm

# 直接用浏览器打开 Chat-LLM.html
open Chat-LLM.html
```

> 注意：所有功能均基于浏览器 Web API，无需安装任何依赖或后端服务。

---

## 📖 使用说明

### 1. 获取 API Key

前往 [DeepSeek 开放平台](https://platform.deepseek.com/api_keys)，注册并创建 API Key。  
将 Key 填入设置面板的「API Key」输入框。

### 2. 配置 API Base URL

默认值为 `https://api.deepseek.com`，通常无需修改。  
如果你使用代理或自定义端点，可在此处更改。

### 3. 设定用户信息（可选）

在「用户信息」文本框中输入你想让模型了解的个人背景或偏好，例如：

```text
我是张三，一名 Python 开发者，喜好简洁代码风格。请用中文回答。
```

该内容将以 `system` 角色的形式拼接在对话历史之前。

### 4. 选择模型

通过顶部居中的下拉菜单选择当前使用的模型：

- **deepseek-v4-flash** – 速度最快，适合日常对话
- **deepseek-v4-pro** – 性能更强的旗舰版
- **deepseek-chat（兼容）** – 通用对话模型
- **deepseek-reasoner（思考）** – 专为复杂推理设计

### 5. 思考与搜索

- **思考模式**：开启后，每次回复会额外展示模型的内部推理过程（浅色框），有助于理解模型思路。  
  强度可选 `high` 或 `max`，`max` 会消耗更多 tokens 但推理更全面。
- **联网搜索**：开启后模型可进行联网检索，获取实时信息（需模型本身支持特性，目前 DeepSeek 部分模型已支持）。

### 6. 上传文件

点击输入框左侧的 **📎** 按钮，选择一个或多个文件。  
支持的文件类型：`pdf, doc, docx, xls, xlsx, ppt, pptx, txt, md, py, js, java, cpp, c, cs, rb, go, rs, ts, json, xml, yaml, yml, html, css`。

- **DOCX 文件**：使用 `mammoth.js` 在前端直接解析，无需上传服务器。
- **其他文本类文件**：通过浏览器 FileReader 读取为文本。
- 文件内容会自动拼接在用户消息的开头，发送后文件标签会被清除。

### 7. 快捷操作

| 操作 | 快捷键 / 方式 |
|------|--------------|
| 发送消息 | `Enter` |
| 换行输入 | `Shift` + `Enter` |
| 中断生成 | 点击右下角红色停止按钮 ⏹ |
| 打开设置 | 左上角 ☰ 或 `Ctrl` + `O` |
| 关闭面板 | 点击面板外部或按 `Esc` |
| 切换主题 | 右上角 🌓 按钮 |

---

## 🛠️ 技术架构

- **前端**：原生 HTML / CSS / JavaScript（零依赖，除 Mammoth.js 通过 CDN 引入）
- **Markdown 渲染**：自实现简易渲染（代码块、加粗、斜体等）
- **DOCX 解析**：[Mammoth.js](https://github.com/mwilliamson/mammoth.js) (CDN)
- **API 通信**：使用 `fetch` 流式读取 DeepSeek Chat Completions 端点
- **数据存储**：浏览器 `localStorage`

---

## 📁 项目结构

```
chat-llm/
├── Chat-LLM.html    # 主程序文件（包含全部前端代码）
├── README.md        # 本文件
```

---

## 🤝 贡献与开发

- **开发者**：HelloWorld05
- **GitHub**：[@helloworldpxy](https://github.com/helloworldpxy)
- **反馈与建议**：欢迎提交 Issue 或 Pull Request。

如果你有新功能想法（如支持其他 API 提供商、会话保存等），请开 Issue 讨论。

---

## 📄 开源协议

本项目基于 [MIT License](LICENSE) 开源。  
你可以自由使用、修改和分发，但需保留原始作者信息。

---

## 🌟 致谢

- [DeepSeek](https://deepseek.com) 提供强大的大模型 API
- [Mammoth.js](https://github.com/mwilliamson/mammoth.js) 让前端解析 DOCX 成为可能
- 所有贡献者和用户的支持

---

**Enjoy chatting with LLMs! 🚀**
