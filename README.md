# 屿上寻光·忆语 · GitHub Pages 部署包

这个目录是可直接发布的静态站点，不需要构建、不需要服务器。

- `index.html`：v16-mobile 完整游戏；已移除内嵌的 11.6 MB BGM，文件从 12.70 MB 降到约 1.11 MB，保留四岛、任务、传送、开始界面和手机触控。
- `.nojekyll`：告诉 GitHub Pages 不要用 Jekyll 处理，直接发布静态文件。
- 原文件 `world-tree-explorer-v16-mobile.html` 没有改动，BGM 仍保留在原文件里。

## 最快发布（GitHub 网页上传，无需命令行）

1. 登录 GitHub，点 **New repository**。
2. 仓库名建议 `yushang-xunguang`，选择 **Public**，不要勾选自动生成 README。
3. 进入空仓库，点 **Add file → Upload files**，把本目录的 `index.html` 和 `.nojekyll` 拖进去，提交到 `main`。
4. 打开 **Settings → Pages → Build and deployment**：
   - Source 选 **Deploy from a branch**
   - Branch 选 **main**
   - Folder 选 **/ (root)**
   - 点 **Save**
5. 等 1–3 分钟，访问：
   `https://<你的GitHub用户名>.github.io/yushang-xunguang/`
6. 用手机浏览器打开这个地址确认能玩，再把这个地址生成二维码放进 PPT。

## 命令行发布（可选）

在本目录执行：

```bash
git remote add origin https://github.com/<你的用户名>/yushang-xunguang.git
git push -u origin main
```

然后在 GitHub 仓库的 **Settings → Pages** 里选择 `main` + `/ (root)`。

## 手机操作

- 左下虚拟摇杆移动。
- 右下：互动、跳跃、按住奔跑。
- 右侧“岛屿”按钮打开传送菜单。
- 手机横屏体验更好；首次进入点“开始游戏”。

## 注意

- 这是无 BGM 版本，优先保证手机扫码能快速打开；如果之后要恢复音乐，建议把音频作为独立文件并在开始游戏后按需加载，不要再把 11.6 MB 的 base64 塞回 HTML。
- GitHub Pages 是公开静态站点，仓库必须是 Public（免费账号）。
