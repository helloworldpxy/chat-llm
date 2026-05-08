# Chat-LLM

> **A powerful browser‑based chat client for multiple LLMs. Input your API keys and start chatting.**  
> 一个支持多厂商、多模型的前端对话工具，可自由切换 DeepSeek、OpenAI、Claude 等，无需后端部署。

[![GitHub stars](https://img.shields.io/github/stars/helloworldpxy/chat-llm?style=social)](https://github.com/helloworldpxy/chat-llm)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Version](https://img.shields.io/badge/version-v1.1-blue)](https://github.com/helloworldpxy/chat-llm)

---

## ✨ 特性

- 🌐 **多厂商 & 多模型**  
  内置 DeepSeek、OpenAI、Moonshot、Anthropic、Groq、Together 等厂商预设，支持自定义 Base URL。随时添加、切换不同 API 配置。

- 🔐 **灵活 API 密钥管理**  
  可同时保存多组 API Key，一键激活当前使用的配置，密钥均存储在浏览器本地。

- 🤖 **动态模型列表**  
  自动从厂商 `/models` 接口拉取可用模型，也可手动切换（支持下拉选择）。不局限于 DeepSeek，任何兼容 OpenAI API 格式的服务均可接入。

- 🧠 **思考模式（DeepSeek 优化）**  
  当使用 DeepSeek 模型时，开启思考后可展示内部推理过程，支持 `high` / `max` 两种强度。

- 🌐 **联网搜索开关**  
  一键启用联网搜索，获得实时信息（需模型本身支持）。

- 📎 **多文件上传 + DOCX 解析**  
  支持 txt、md、pdf、docx、代码文件等多种格式，DOCX 由 Mammoth.js 在前端解析，无需服务器。

- 🎨 **科幻风 UI 设计**  
  玻璃拟态 + 霓虹渐变，支持夜间 / 白天 / 跟随系统三种主题模式。

- 🔒 **数据本地存储**  
  所有配置（API Key、用户信息、设置）保存在浏览器 `localStorage` 中，不会上传到任何第三方服务器。

- 🚀 **流式响应**  
  实时展示模型输出，支持随时中断生成。

- 📱 **响应式布局**  
  适配桌面和移动端浏览器。

---

## 🖼️ 界面预览

![Chat-LLM 界面截图1](<img width="2526" height="1186" alt="图片" src="https://github.com/user-attachments/assets/e5d70c9a-6569-4578-ab84-f7eeef272290" />
)
![Chat-LLM 界面截图2](<img width="2526" height="1186" alt="图片" src="https://github.com/user-attachments/assets/912f179c-57c7-498b-ae8b-65486f499041" />
)
![Chat-LLM 界面截图3](<img width="2526" height="1186" alt="图片" src="https://github.com/user-attachments/assets/49a1ddd6-93a9-4ef5-912b-f8ee66853456" />
)

---

## 🚀 快速开始

### 方式一：直接使用在线版（推荐）

1. 访问 GitHub Pages 地址（如果已部署），或直接双击打开 `Chat-LLM.html`。
2. 点击左上角 **☰** 打开设置面板。
3. 在「API 配置管理」中 **添加或激活** 一组 API 配置：
   - 填写名称（如 DeepSeek、OpenAI）
   - 输入 API Key（从对应平台获取）
   - 设置 Base URL（可使用预设值，或自定义）
4. 可选：填写「系统消息」（将作为 system prompt 发送）。
5. 点击 **保存并应用**，关闭面板后，顶部下拉菜单会自动加载可用模型，选择即可开始对话。

### 方式二：本地运行

```bash
git clone https://github.com/helloworldpxy/chat-llm.git
cd chat-llm
# 直接用浏览器打开 Chat-LLM.html（即 v1.1 版本文件）
open Chat-LLM.html
```

> 所有功能完全基于浏览器 Web API，零依赖（除 Mammoth.js 通过 CDN 引入），无需安装 Node.js 或后端服务。

---

## 📖 使用说明

### 1. 配置 API 密钥

打开设置面板（☰），在 **🔐 API 配置管理** 区域可以：

- **添加配置**：点击“➕ 添加API配置”，填写名称、API Key 和 Base URL。
- **激活配置**：通过单选框选择当前要使用的 API，顶部模型列表将自动刷新。
- **查看/隐藏密钥**：点击 👁️ 按钮切换密钥显示。
- **删除配置**：点击 🗑️（至少保留一组）。

> 支持的预设厂商（可在页面底部看到）：
> - OpenAI: `https://api.openai.com/v1`
> - DeepSeek: `https://api.deepseek.com`
> - Moonshot: `https://api.moonshot.cn/v1`
> - Anthropic: `https://api.anthropic.com`
> - Groq: `https://api.groq.com/openai/v1`
> - Together: `https://api.together.xyz/v1`
> - Custom: 可自行填入任意兼容端点

如需添加/修改厂商默认 Base URL，可在 **⚙️ 高级设置 · 厂商 API Base** 中编辑。

### 2. 设定系统消息（可选）

在「用户信息」文本框中输入你想让模型了解的个人背景或偏好，例如：

```text
我是张三，一名 Python 开发者，喜好简洁代码风格。请用中文回答。
```

该内容将以 `system` 角色拼接在对话历史之前。

### 3. 选择模型

顶部下拉菜单会自动获取当前激活配置下的可用模型。  
若获取失败，会根据配置名称加载预设模型（如 DeepSeek → `deepseek-chat`, `deepseek-reasoner`；OpenAI → `gpt-4o`, `gpt-3.5-turbo` 等）。

### 4. 思考与搜索

- **思考模式**：仅对 DeepSeek 模型生效（其他模型会自动忽略相关参数）。开启后，每次回复会展示模型的推理过程。  
  强度可选 `high` 或 `max`。
- **联网搜索**：开启后模型可进行联网检索（需模型本身支持，目前 DeepSeek 部分模型已支持）。

### 5. 上传文件

点击输入框左侧的 **📎** 按钮，选择一个或多个文件。  
支持的文件类型：`pdf, doc, docx, xls, xlsx, ppt, pptx, txt, md, py, js, java, cpp, c, cs, rb, go, rs, ts, json, xml, yaml, yml, html, css`。

- **DOCX 文件**：使用 `mammoth.js` 在前端直接解析。
- **其他文本类文件**：通过 FileReader 读取为文本。
- 文件内容会自动拼接在用户消息的开头，发送后文件标签会被清除。

### 6. 快捷操作

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

- **前端**：原生 HTML / CSS / JavaScript，除 Mammoth.js 通过 CDN 引入外零依赖
- **Markdown 渲染**：自实现简易渲染（代码块、加粗、斜体等）
- **DOCX 解析**：[Mammoth.js](https://github.com/mwilliamson/mammoth.js) (CDN)
- **API 通信**：使用 `fetch` 流式读取 OpenAI 兼容的 Chat Completions 端点
- **模型获取**：调用 `/models` 或 `/v1/models` 接口获取模型列表
- **数据存储**：浏览器 `localStorage`

---

## 📁 项目结构

```
chat-llm/
├── Chat-LLM.html    # 主程序文件（v1.1，包含全部前端代码）
├── README.md        # 本文件
```

---

## 🤝 贡献与开发

- **开发者**：HelloWorld05
- **GitHub**：[@helloworldpxy](https://github.com/helloworldpxy)
- **反馈与建议**：欢迎提交 Issue 或 Pull Request。

如果你有新功能想法（如会话保存、Markdown 导出、多会话管理、更多厂商适配等），请开 Issue 讨论。

---

## 📄 开源协议

本项目基于 [MIT License](LICENSE) 开源。  
你可以自由使用、修改和分发，但需保留原始作者信息。

---

## 🌟 致谢

- [DeepSeek](https://deepseek.com)、[OpenAI](https://openai.com)、[Mammoth.js](https://github.com/mwilliamson/mammoth.js) 以及所有提供开放 API 的厂商
- 所有贡献者和用户的支持

---

**Enjoy chatting with any LLM! 🚀**
