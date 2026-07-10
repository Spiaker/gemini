# 演示：https://spiaker.github.io

## Gemini 2.0 代理

使用 Deno 免费代理 Google Gemini，国内直连，不限地区/网络环境，打开即用。

免费使用 Gemini 地表最强大的 100万 Token 上下文模型。

兼容的 OpenAI 格式，可对接 AI 编程，接入ChatBox、Cherry Studio、Cursor、Cline 等 AI 客户端。

## 分享

- [Midjourney API](https://github.com/trueai-org/midjourney-proxy)：市面上最强大，完全免费开源的免费绘图平台。
- [MDrive](https://github.com/trueai-org/mdrive)：阿里云盘官方 API 授权的自动同步和备份工具，支持挂载到本地磁盘。
- [Grok](https://github.com/trueai-org/grok)：使用 Deno 免费代理马斯克 Grok3，免登录，国内直连，不限地区/不限网络/不限设备，打开即用。

## 本地部署（推荐）

> 由于 Deno 封锁问题，推荐使用本地部署到国外的服务器（例如：新加坡）

```bash
# 1. 克隆项目（如果还没有）
git clone https://github.com/trueai-org/gemini.git
cd gemini

# 2. 给部署脚本执行权限
chmod +x deploy.sh

# 3. 运行部署
./deploy.sh
```

## Deno 部署

> Bilibili 视频教程：<https://www.bilibili.com/video/BV1DDA3eEEYn/>

1. 免费创建一个 Gemini API Key [https://aistudio.google.com](https://aistudio.google.com/app/apikey)
1. 点击 [Fork](https://github.com/trueai-org/gemini/fork) 本项目（万分感谢帮助点个 `Star`）
2. 登录/注册 Deno https://dash.deno.com/
3. 点击创建项目 https://dash.deno.com/new_project
4. 选择此项目，填写项目名字（分配域名）
5. 部署 Entrypoint 填写 `src/deno_index.ts` 其他字段留空 
6. 点击 **Deploy Project**
7. 部署成功后获得域名，可以作为Chat API的代理使用。
8. 下载安装 **[Cherry Studio](https://cherry-ai.com/)** -> 设置 -> 添加模型服务 -> 输入域名和 Token -> 添加模型 -> 开启 AI 会话。

## Deno 调试

Windows 安装 Deno:
> irm https://deno.land/install.ps1 | iex

Mac/Linux 安装 Deno:
> curl -fsSL https://deno.land/install.sh | sh

启动项目：

> cd gemini

> deno run --allow-net --allow-read src/deno_index.ts

## 鸣谢

- https://github.com/tech-shrimp/gemini-playground
- https://github.com/PublicAffairs/openai-gemini

## 项目总结
这是一个 Gemini 2.0 代理项目，用于在国内环境下代理 Google Gemini API，实现免费使用 Google Gemini 的强大 AI 模型。

## 项目概述
名称: gemini
类型: API 代理服务
目标: 允许国内用户通过代理访问 Google Gemini API，绕过地区限制
兼容性: 兼容 OpenAI 格式，可对接多种 AI 客户端
主要功能
API 代理: 代理 Google Gemini 的 chat/completions, embeddings, models 等接口
WebSocket 支持: 处理实时流式响应
格式转换: 将 Gemini 响应转换为 OpenAI 兼容格式
多模型支持: 支持 Gemini 1.5 Pro 等多个模型
## 技术架构
主入口: src/index.js - Cloudflare Workers 入口文件，处理 WebSocket 和 API 请求
API 代理: src/api_proxy/worker.mjs - 核心代理逻辑，处理 Gemini API 请求和响应转换
Deno 支持: src/deno_index.ts - 支持 Deno 部署
部署方式: 支持本地部署和 Deno 部署
## 关键特性
免费使用: 利用 Deno 免费额度提供免费服务
国内直连: 解决 Google Gemini 在国内的访问限制
兼容性: 支持 ChatBox、Cherry Studio、Cursor、Cline 等客户端
流式处理: 支持 SSE (Server-Sent Events) 流式响应
安全性: 包含安全设置和内容过滤
## 部署方式
本地部署: 推荐部署到国外服务器（如新加坡）
Deno 部署: 通过 Deno Deploy 提供云端服务
## 项目结构

gemini/
├── deno.json
├── deploy.sh
├── docker-compose.yml
├── Dockerfile
├── LICENSE
├── package.json
├── README.md
└── src/
    ├── api_proxy/
    │   └── worker.mjs          # API 代理核心逻辑
    ├── deno_index.ts          # Deno 入口文件
    └── index.js              # Cloudflare Workers 入口
这个项目是一个开源的 Gemini API 代理解决方案，旨在让国内用户能够方便地使用 Google 的强大 AI 模型。
