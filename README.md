# 研究生课表 iPhone App

这是一个可安装到 iPhone 主屏幕的 PWA，不需要 App Store 或额外构建步骤。课表按日期自动计算教学周：以 2026 年 8 月 31 日为第 1 周周一（根据 2026 年 10 月 12 日处于第 7 周推算）。

## 本地预览

在项目目录启动任意静态 HTTP 服务，例如：

```powershell
python -m http.server 8000
```

然后用浏览器打开 `http://localhost:8000`。Service Worker 需要 HTTP(S) 环境；直接双击 `index.html` 时离线缓存不会启用。

## 安装到 iPhone

将整个目录部署到 HTTPS 静态站点，然后在 iPhone Safari 打开站点，点“分享”→“添加到主屏幕”。首次联网打开后，页面资源会缓存，可离线查看。

## 文件

- `index.html`：课表界面与交互
- `manifest.webmanifest`：主屏幕应用配置
- `service-worker.js`：离线缓存
- `icon.png` / `icon.svg`：应用图标
