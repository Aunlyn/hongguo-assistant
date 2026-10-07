<p align="center">
    <img width="96" height="96" alt="红果短剧助手图标" src="https://github.com/Aunlyn/hongguo-assistant/blob/main/image/appicon.png?raw=true" />
</p>
<h1 align="center">红果短剧助手</h1>
<p align="center">Rust 驱动的跨平台红果短剧助手，覆盖榜单发现、本地推荐、分类筛选到在线播放与离线下载的一站式体验。</p>
<p align="center">
    <img src="https://img.shields.io/badge/react-19-61DAFB.svg?style=flat-square" alt="React 19">
    <img src="https://img.shields.io/badge/tauri-v2-lightgrey.svg?style=flat-square" alt="Tauri v2">
    <img src="https://img.shields.io/badge/rust-orange.svg?style=flat-square" alt="Rust">
    <img src="https://img.shields.io/badge/typescript-5.9-3178C6.svg?style=flat-square" alt="TypeScript 5.9">
    <img src="https://img.shields.io/badge/vite-7-646CFF.svg?style=flat-square" alt="Vite 7">
    <img src="https://img.shields.io/badge/tailwind-v4-06B6D4.svg?style=flat-square" alt="Tailwind CSS v4">
</p>

---

> 红果短剧助手是一款面向红果短剧的桌面端第三方助手，将榜单、推荐、分类、搜索、收藏、历史、下载与播放整合进统一界面。

## 技术特性

1. 基于 Tauri v2 构建的桌面客户端，业务后端全部由 Rust 实现，Windows 优先
2. 现代化 Web 前端，基于 React 19 + TypeScript + Vite + Tailwind CSS v4，配 Radix UI Themes、Phosphor 图标与 TanStack React Query
3. 官方榜单聚合：热播榜（红果全部、漫剧、AI 剧、真人剧四个官网榜单）、漫剧新剧榜与最新上架，停留时每 5 分钟自动刷新
4. 本地智能推荐：在本地按观看进度、观看时长、近期行为与收藏生成加权标签画像，排序推荐并保留少量探索内容，观看记录与推断偏好不上传上游
5. 分类与筛选：漫剧、AI 剧、真人剧，动态读取主题、设定、背景、排序、受众、状态、上架时间等可用筛选维度
6. 无转码播放：Range 下载 + 样本级 AES-CTR 解密 + MP4 封装还原，视频由系统解码、零转码，优先选择可用 H.264
7. 离线下载与续播：播放与导出共享内核，进度随历史保存在本地，从榜单、分类、收藏或历史重新打开自动续播
8. 独立播放窗口：上一集/下一集、自动连播、倍速、音量、侧栏折叠、全屏；小窗移出自动暂停隐藏，移回续播
9. 个性化主题：珊瑚、鸢尾、樱粉、晴空预设与自定义配色，深浅色主题随页面切换，标题栏高斯模糊
10. 系统托盘与关闭偏好：关闭主窗口可选隐藏到托盘或退出，支持「不再提示」记忆，重复启动激活已有窗口

## 项目架构

仓库采用「Rust 核心 + Web 前端」的 Tauri 分层结构，业务经 Tauri IPC 通信，媒体二进制由受鉴权的本机随机端口直接传给 WebView，避免大块视频经 JSON 复制：


## 实机效果

<p align="center">
    <a href="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Ranking.png">
        <img width="31%" src="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Ranking.png" alt="榜单">
    </a>
    <a href="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Recommend.png">
        <img width="31%" src="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Recommend.png" alt="推荐">
    </a>
    <a href="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Classification.png">
        <img width="31%" src="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Classification.png" alt="分类">
    </a>
</p>
<p align="center">
    <a href="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Collection.png">
        <img width="31%" src="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Collection.png" alt="收藏">
    </a>
    <a href="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Dark.png">
        <img width="31%" src="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Dark.png" alt="收藏（深色主题）">
    </a>
    <a href="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/History.png">
        <img width="31%" src="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/History.png" alt="历史">
    </a>
</p>
<p align="center">
    <a href="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Settings.png">
        <img width="31%" src="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/Settings.png" alt="设置">
    </a>
    <a href="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/player.png">
        <img width="31%" src="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/player.png" alt="播放器">
    </a>
    <a href="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/SmallWindow.png">
        <img width="31%" src="https://raw.githubusercontent.com/Aunlyn/hongguo-assistant/refs/heads/main/image/%E2%85%A0/SmallWindow.png" alt="小窗">
    </a>
</p>

## 下载

<p align="center">
    <a href="https://github.com/Aunlyn/hongguo-assistant/releases">
        <img
            height="54"
            alt="从 GitHub 下载"
            src="https://img.shields.io/badge/Windows-GitHub%20Releases-24292f?style=for-the-badge&logo=github&logoColor=white"
        >
    </a>
</p>

## 使用
双击下载的安装包即可安装，软件体积仅6MB
