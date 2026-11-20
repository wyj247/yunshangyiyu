# 屿上寻光·忆语 · 手机网页版

扫码即玩：**https://wyj247.github.io/yunshangyiyu/**

## 仓库结构

| 文件 | 说明 |
| --- | --- |
| `index.html` | v16-mobile 完整游戏（约 **1.11 MB**），开始界面 / 四岛 / 任务 / 传送 / 触控全部保留 |
| `bgm.m4a` | 从原 HTML 第 910 行内嵌的 base64 中拆出的 BGM（约 **8.69 MB**） |
| `.nojekyll` | 关闭 Jekyll，让 Pages 直接发布静态文件 |

原文件 `world-tree-explorer-v16-mobile.html`（12.7 MB）未改动，BGM 仍完整内嵌其中。

## BGM 加载方式

```html
<audio id="bgm" loop preload="none" data-src="bgm.m4a"></audio>
```

没有内嵌 base64，也没有初始 `src`。玩家点「开始游戏」后，代码才把 `bgm.m4a` 挂到 audio 元素并调用 `play()`：

- 首屏只下载约 1.11 MB 的 HTML，不被 8.69 MB 音乐阻塞；
- BGM 在开始游戏后才请求；
- 音频加载失败或被自动播放策略拦截时，游戏继续运行。

## 发布方式

GitHub Pages，source = `main` 分支 `/`（root），由仓库推送自动重新构建。
