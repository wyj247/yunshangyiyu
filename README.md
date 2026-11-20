# 屿上寻光·忆语 · GitHub Pages 部署包

这个目录是可直接发布的静态站点，不需要构建、不需要服务器。

## 文件

- `index.html`：v16-mobile 完整游戏，约 **1.11 MB**；开始界面、四岛、任务、传送和手机触控全部保留。
- `bgm.m4a`：从原 HTML 中拆出的 BGM，约 **8.69 MB**，作为独立音频文件。
- `.nojekyll`：告诉 GitHub Pages 不要用 Jekyll 处理，直接发布静态文件。
- 原文件 `world-tree-explorer-v16-mobile.html` 没有改动，BGM 仍完整保留在原文件里。

## BGM 加载方式

HTML 里只有：

```html
<audio id="bgm" loop preload="none" data-src="bgm.m4a"></audio>
```

没有内嵌 base64，也没有初始 `src`。玩家点“开始游戏”后，代码才把 `bgm.m4a` 挂到 audio 元素并调用 `play()`。所以：

- 首屏只需要下载约 1.11 MB 的 HTML，不会被 8.69 MB 音乐阻塞。
- BGM 在开始游戏后才请求和播放。
- 音频加载失败或被浏览器自动播放策略拦截时，游戏继续运行，不会报错退出。

## 最快发布（GitHub 网页上传，无需命令行）

1. 登录 GitHub，点 **New repository**。
2. 仓库名建议 `yushang-xunguang`，选择 **Public**，不要勾选自动生成 README。
3. 进入空仓库，点 **Add file → Upload files**，上传：
   - `index.html`
   - `bgm.m4a`
   - `.nojekyll`（隐藏文件；如果看不到，用 **Add file → Create new file** 新建空文件，文件名填 `.nojekyll`）
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

- GitHub Pages 免费账号需要 Public 仓库。
- 当前 `bgm.m4a` 保留原始音频，没有重新转码；如果之后想进一步缩小，可以把 BGM 转成 96–128 kbps 的 MP3/AAC，再替换 `bgm.m4a` 并保持文件名不变。
