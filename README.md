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


一、用 GitHub Pages 发布
1. 创建一个 GitHub 仓库
在电脑浏览器打开 GitHub 并登录，然后：
1. 点击右上角 + → New repository。
2. 仓库名称填写 myschedule-app。
3. 选择 Public。GitHub Free 的 Pages 支持公开仓库；发布后，网站本身也能被任何人访问。不要把私人信息放进仓库。 GitHub Pages 官方说明
4. 不用勾选添加 README、License 等初始化选项，然后点击 Create repository。
2. 上传课表文件
在新仓库页面点击 Add file → Upload files，把 D:\MyProject\Myschedule 目录中的这些文件上传到仓库根目录：
- index.html
- manifest.webmanifest
- service-worker.js
- icon.png
- icon.svg
- README.md
上传后点击页面下方的 Commit changes 保存。注意是上传这几个文件本身，别把它们再放进仓库里的子文件夹；index.html 需要位于根目录。
3. 开启 GitHub Pages
在仓库里打开：
1. Settings → 左侧 Pages。
2. 在 Build and deployment 下，把 Source 设为 Deploy from a branch。
3. Branch 选 main，目录选 /(root)，点击 Save。
GitHub 会自动发布这个目录。发布完成后，Pages 设置页会显示网站地址，格式通常是：
https://你的GitHub用户名.github.io/myschedule-app/
第一次发布可能需要等几分钟。之后更新仓库文件，网站也会随之重新发布。 GitHub Pages 发布配置说明
二、在 iPhone 上添加到主屏幕
1. 把上面显示的网址发到 iPhone，或直接在 iPhone 上打开。
2. 用 Safari 打开网址，确认页面正常显示。
3. 点 Safari 的分享按钮。
4. 向下滚动，点 添加到主屏幕。如果没看到，可在分享菜单底部的 编辑操作 中添加此选项。
5. 可以开启 作为网页 App 打开，再点 添加。主屏幕上就会出现课表图标。 Apple 官方操作说明
三、确认离线能打开
第一次请在有网络时用 Safari 打开课表，等页面加载完成，让浏览器缓存页面文件。之后可以先关闭网络，再从主屏幕图标打开，确认课表仍能显示。
离线功能需要 Service Worker；它要求网站通过 HTTPS 提供，localhost 是本地开发时的例外。GitHub Pages 提供的地址是 HTTPS，所以适合这个用途。 Service Worker 安全环境说明
课表本身不依赖在线数据，离线时仍可查看和切换周次；在线字体可能退回系统字体显示。
