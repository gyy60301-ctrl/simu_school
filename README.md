# simu_school

一个用于课堂展示、语音识别、知识整理和互动问答的本地项目。仓库里同时包含前端页面、Node.js 后端，以及若干 Python 工具脚本。

## 项目说明

### 主要文件

- `index.html`、`script.js`、`style.css`：前端页面和交互逻辑
- `server.js`：本地 Node.js 服务，负责接口转发和数据保存
- `语音转换识别.py`、`语音转换识别多语种版.py`、`指标获取.py`、`语音启动程序.py`：Python 工具脚本
- `kb_reference.json`：项目知识库或参考数据
- `images/`、`notes/`、`assets/`：项目素材

### GitHub 上传约定

- 不提交真实 API Key
- 使用 `.env` 保存本地环境变量
- `node_modules/`、`__pycache__/`、虚拟环境目录和常见本地缓存已在 `.gitignore` 中忽略

## 环境依赖安装

下面按顺序执行。建议不要跳步。

### 1. 安装 Node.js

先确认 Node.js 已安装：

```bash
node -v
npm -v
```

如果这两条命令都能正常输出版本号，就继续下一步。

### 2. 安装 Node.js 依赖

在项目根目录执行：

```bash
npm install
```

这个项目的 Node 依赖主要是：

- `express`
- `cors`
- `node-fetch`

### 3. 配置本地环境变量

把 `.env.example` 复制为 `.env`，然后填写本地密钥：

- `BIGMODEL_API_KEY`
- `ZHIPUAI_API_KEY`

如果你暂时不使用这些接口，也可以先留空，但相关 Python 脚本在启动时会检查环境变量。

### 4. 创建 Python 虚拟环境

建议单独给这个项目建一个虚拟环境。下面给出常用做法：

```bash
python -m venv .venv
```

激活方式：

```bash
.venv\Scripts\activate
```

如果你用的是 Conda，也可以改成你自己的环境创建方式，原则是先进入独立环境，再安装依赖。

### 5. 安装 Python 依赖

激活虚拟环境后执行：

```bash
pip install -r requirements.txt
```

其中核心依赖包括：

- `numpy`
- `sounddevice`
- `funasr`
- `openai`
- `requests`
- `PyMuPDF`
- `python-pptx`
- `python-docx`
- `pynput`
- `scipy`
- `matplotlib`
- `pandas`
- `tkinterdnd2`

可选依赖：

- `faster-whisper`，仅 `语音转换识别多语种版.py` 会用到，没装也能运行其他脚本

## 启动顺序

建议按这个顺序启动：

### 1. 启动 Node.js 后端

```bash
node server.js
```

默认监听：

```text
http://localhost:3000
```

### 2. 打开前端页面

直接打开 `index.html`，或者用 VS Code 的 Live Server。

### 3. 运行 Python 工具

按需运行对应脚本，例如：

```bash
python 语音转换识别.py
```

```bash
python 语音转换识别多语种版.py
```

```bash
python 指标获取.py
```

```bash
python 语音启动程序.py
```

## 常见注意事项

- `语音转换识别.py`、`指标获取.py` 和 `语音转换识别多语种版.py` 都会读取 `BIGMODEL_API_KEY` 或 `ZHIPUAI_API_KEY`
- 如果缺少音频、文档或 GUI 相关依赖，通常会先在 `pip install -r requirements.txt` 这一步报出来
- 如果你只想先看网页效果，可以先只装 Node 依赖，不跑 Python 脚本

## 建议的提交内容

上传 GitHub 前，建议确认以下内容已经准备好：

- `.env.example` 保留，`.env` 不提交
- `requirements.txt` 已包含 Python 依赖
- `.gitignore` 已忽略依赖、缓存和本地环境目录

