# 何军伟 · 个人网站

一个使用原生 HTML / CSS / JavaScript 构建的多页个人网站：首页、作品、关于、联系。没有框架、没有构建步骤、没有外部 CDN，解压后双击 `index.html` 就能打开。

- 在线访问：<http://8.137.104.233>
- 仓库：<https://github.com/wdsj-hsdj/personal-site>
- GitHub：<https://github.com/wdsj-hsdj>
- 作者：何军伟 · 四川传媒学院 计算机科学与技术 2026 级

## 技术栈

- HTML5 / CSS3 / 原生 JavaScript
- Git / GitHub
- Linux（Ubuntu 22.04）/ Nginx
- 阿里云 ECS（2 核 2GiB，成都）

## 页面

| 页面 | 文件 | 内容 |
|---|---|---|
| 首页 | `index.html` | 首屏、精选作品、关于摘要、现在、联系 |
| 作品 | `works.html` | 个人网站案例、AI 陪伴应用（开发中）、制作过程 |
| 关于 | `about.html` | 自我介绍、技能、经历、接下来 |
| 联系 | `contact.html` | 邮箱、GitHub、位置、状态 |

## 目录结构

```text
personal-site/
├── index.html
├── works.html
├── about.html
├── contact.html
├── assets/
│   ├── css/style.css
│   ├── js/main.js
│   └── img/
│       ├── avatar.svg
│       └── favicon.svg
├── README.md
└── .gitignore
```

## 本地预览

方式一：直接双击 `index.html`。

方式二：在项目目录启动一个本地 HTTP 服务：

```bash
python -m http.server 8000
```

然后打开 <http://localhost:8000>。

> 页面按 `file://` 场景做了兼容：不使用 ES modules、`fetch()` 或外部字体；复制邮箱带有 `execCommand` 兜底。

## 部署

服务器：阿里云 ECS，Ubuntu 22.04，Nginx。

站点根目录：

```text
/var/www/hejunwei
```

Nginx 站点配置：

```nginx
server {
    listen 80 default_server;
    listen [::]:80 default_server;
    server_name _;

    root /var/www/hejunwei;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

当前更新方式（scp）：

```powershell
scp -i "<你的密钥路径>" index.html root@8.137.104.233:/var/www/hejunwei/
```

静态文件更新后不需要重启 Nginx，刷新浏览器即可。

> 代码已托管在 GitHub；如果以后在服务器上用 `git clone` 部署，也可以改成 `git pull` 更新。

## 设计说明

- 配色：纸白 `#F7F5EF`、墨黑 `#111315`、电光蓝 `#1F4FFF`、暖橙 `#C96F4A`。
- 字体：系统字体栈 + 等宽标签，不加载网络字体。
- 多页共享一套 CSS/JS；所有路径为相对路径。
- 响应式断点：1024 / 860 / 640。
- 可访问性：skip link、键盘焦点、图片 alt、`prefers-reduced-motion`。

## 说明

- 本站为静态展示站，没有后端、数据库或在线 AI 服务。
- AI 陪伴应用仍在开发中，作品页只放目标、关注点和界面示意，不冒充已完成产品。
- 不收集访客数据，不使用第三方统计或广告。

## 相关项目

- **佳代子 AI 伴侣**：Electron + Python + DeepSeek + GPT-SoVITS 的桌面 AI 伴侣，支持 Spine 立绘、语音回复、长期记忆和断线重连，目前本地运行。

## 作者

- 何军伟
- 四川传媒学院 · 智慧广电学院（人工智能与互动媒体学院）
- 计算机科学与技术 · 2026 级
- 邮箱：hejunwei@example.com
- GitHub：<https://github.com/wdsj-hsdj>
