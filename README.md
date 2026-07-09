# 写作输入法 · macOS 版 — 官网

介绍 macOS 版功能并提供安装包下载的静态站点，可直接部署到 GitHub Pages。

## 目录结构

```
writingime-mac-site/
├── index.html          # 官网首页（唯一页面，内联样式，无外部依赖）
├── assets/
│   ├── icon.png        # 应用图标（logo / favicon）
│   └── shot-01..06.png # 6 张 macOS App Store 截图
└── download/
    └── icon.png        # ★ 下载占位文件（当前“下载 App”下载到本地即为 icon.png）
```

## ★ 替换为真正的安装包

当前「下载 App」按钮是**占位**，指向 `download/icon.png`，仅用于验证下载功能。
拿到真正的安装包（如 `WritingIME.dmg`）后：

1. 把安装包放进 `download/`，例如 `download/WritingIME.dmg`。
2. 在 `index.html` 中把所有 `href="download/icon.png"` 改为 `href="download/WritingIME.dmg"`
   （共 3 处：导航栏、Hero、底部下载区各按钮；`grep -n 'download/icon.png' index.html` 可定位）。
3. 可选：删掉 `download/icon.png` 占位文件。

## 部署到 GitHub Pages

与技术支持站同样的流程（新建或复用一个仓库 → 开启 Pages → 推送）：

```bash
cd writingime-mac-site
git init
git add -A && git commit -m "写作输入法 macOS 官网"
git branch -M main
git remote add origin <你的仓库地址>
git push -u origin main
```

在仓库 Settings → Pages 里把 Source 设为 `main` 分支根目录，几十秒后即可访问。
`index.html` 会被 Pages 优先作为首页。

## 本地预览

直接双击 `index.html` 用浏览器打开即可（无需服务器）。
