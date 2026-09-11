---
AIGC:
    Label: "1"
    ContentProducer: 001191440300708461136T1XGW3
    ProduceID: 3ba162c2950f5dc2f1e88d93afbda41d_a106d116adf811f18874525400287e28
    ReservedCode1: 5oOZpuineE/XzZIqpHbJuep9lv1NSvjgdaioh6aDhkEESc2+3wdCVnhOtePQzyppNBdRargmVQmIBkC9nV9uAjOHUgWwBi8KYRlz1q1bb04xbouu+vDYh2KcWrP0djkPw3en2L6dtbZ8LMVSL5TSGPnnRwQFptfzUwGeO8Wu3A5dD/h8qW2Yyl0kpXs=
    ContentPropagator: 001191440300708461136T1XGW3
    PropagateID: 3ba162c2950f5dc2f1e88d93afbda41d_a106d116adf811f18874525400287e28
    ReservedCode2: 5oOZpuineE/XzZIqpHbJuep9lv1NSvjgdaioh6aDhkEESc2+3wdCVnhOtePQzyppNBdRargmVQmIBkC9nV9uAjOHUgWwBi8KYRlz1q1bb04xbouu+vDYh2KcWrP0djkPw3en2L6dtbZ8LMVSL5TSGPnnRwQFptfzUwGeO8Wu3A5dD/h8qW2Yyl0kpXs=
---

# Marvis Arcade · 轻量级静态游戏合集

纯 **HTML / CSS / JavaScript** 实现的静态游戏站点，**零后端、零构建、零编译**，可直接拖到任意静态托管平台上线。

## 项目结构

```
games/
├── index.html        # 合集门户（游戏列表 + 规划路线图）
├── snake.html        # 贪吃蛇   · 休闲      · ≈4.5KB
├── tetris.html       # 俄罗斯方块 · 益智     · ≈6.9KB
├── breakout.html     # 打砖块   · 休闲动作   · ≈5.8KB
├── 2048.html         # 2048     · 益智      · ≈6.2KB
└── README.md         # 本文件
```

每款游戏均为**单文件自包含**（内联 CSS/JS，无外部请求），除字体外不加载任何 CDN 依赖。

## 1. 本地运行（任选其一）

```bash
# Python（无需安装任何东西）
python -m http.server 8000

# Node（需先安装 serve）
npx serve -l 8000 .
```

浏览器打开 `http://localhost:8000` 即可。建议用本地 HTTP 服务而非直接双击打开文件——部分浏览器对 `file://` 协议下的模块/存储行为有差异。

## 2. 部署到静态托管平台

| 平台 | 方式 | 说明 |
|------|------|------|
| GitHub Pages | 推送到仓库 → Settings → Pages → 选分支根目录 | 免费、自动 HTTPS |
| Cloudflare Pages | 连接 Git 仓库，构建命令留空 | 全球 CDN，免费 |
| Netlify / Vercel | 拖拽 `games/` 目录或连 Git | 无需配置构建 |
| itch.io | 见下方第 3 节 | 面向玩家分发的首选 |

无需构建步骤：把 `games/` 目录整体上传即可，`index.html` 为入口。

## 3. itch.io 分发（HTML5 上传）

1. 在 itch.io 新建项目，勾选 **HTML** 类型；
2. 将 `games/` 目录压成 zip（入口文件需命名为 `index.html`）；
3. 命令行方式上传（butler）：

```bash
# 安装 butler（一次性）
# Windows:  scoop install butler ，或从 https://itch.io/docs/butler/ 下载

# 上传（ITCh_API_KEY 从 itch.io → Settings → API Keys 生成）
set ITCH_API_KEY=<你的 API Key>       # 仅作环境变量，勿写入仓库/明文文件
butler push .\games.zip <user>/<game>:html5
```

> 安全提示：API Key 仅通过环境变量注入，**不要**把密钥写进任何配置文件或提交到 Git。

## 4. 扩展与后续路线

规划路线图中的玩法均为纯 JS 可实现，推荐引擎/库：

- **引擎**：Phaser 3（2D 通用）/ Kaboom.js（极简友好）/ PixiJS（重渲染性能）/ p5.js（创意快速原型）
- **音频**：Howler.js（WebAudio 封装，节奏游戏必需精确节拍）
- **存储**：原生 `localStorage` 存档即可，无需后端

新游戏按现有模式放入单文件 `.html`，在 `index.html` 的门户网格中登记一行卡片即完成接入。

## 5. 性能基线

| 指标 | 数值 |
|------|------|
| 单文件平均体积 | ≈5.8KB |
| 外部请求 | 0（离线亦可用） |
| 首个可玩 | <1s（无网络依赖） |
| 支持输入 | 键盘 / 触屏（均已适配） |
*（内容由AI生成，仅供参考）*
