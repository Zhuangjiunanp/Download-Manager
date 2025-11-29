# Advanced Download Manager 🚀

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
![JDK](https://img.shields.io/badge/JDK-17-orange)
[![Android](https://img.shields.io/badge/Android-8.0%2B-green.svg)](https://android.com)
[![AI-Beta](https://img.shields.io/badge/AI--Beta-Available-orange.svg)](https://github.com/your-username/your-repo/releases/tag/ai-beta)

一个功能强大、高度可扩展的 Android 下载管理器，集成了智能优化与多协议支持，旨在提供终极下载体验。

## ✨ 核心特性

### 🚀 下载引擎
- **多协议支持**: 全面支持 HTTP/HTTPS、FTP、SFTP、WebDAV
- **智能断点续传**: 网络异常自动恢复，支持大规模文件下载
- **多线程加速**: 动态线程调配，最大化下载速度
- **流量控制**: 可配置速度限制，避免影响其他网络活动

### 🧠 智能功能
- **AI-Beta 模式**: 集成机器学习算法，智能预测最佳下载时段和策略
- **资源嗅探**: 内置浏览器引擎，自动检测网页中的可下载资源
- **类型预判**: 自动识别文件类型并分类存储
- **智能去重**: 防止重复下载，节省流量与存储空间

### 🌐 网络与集成
- **云存储支持**: 无缝对接 WebDAV、SFTP 等云存储服务
- **浏览器集成**: 基于 GeckoView 的高性能浏览器组件
- **深度链接**: 全面支持 `intent://` 和 `http://` 链接调用
- **后台服务**: 独立的下载服务，应用关闭后仍持续下载

### 🎨 用户体验
- **Material You**: 支持 Android 12+ 的动态主题取色
- **实时监控**: 详细的速度曲线、进度统计和剩余时间预估
- **通知管理**: 丰富的下载状态通知与快捷操作
- **手势操作**: 滑动快捷操作，批量任务管理

## 📸 界面预览

| 主下载界面 | 任务详情 | 浏览器集成 |
|-----------|----------|------------|
| ![主界面](https://via.placeholder.com/300x600?text=主界面) | ![详情页](https://via.placeholder.com/300x600?text=任务详情) | ![浏览器](https://via.placeholder.com/300x600?text=浏览器) |


## 🛠 技术架构

### 核心框架
- **Kotlin**: 主要开发语言，协程支持异步任务
- **AndroidX**: 现代化 Android 组件库
- **Material Design 3**: 最新的材料设计规范

### 网络协议栈
- **OkHttp**: 高性能 HTTP 客户端
- **JSch**: 完整的 SFTP/SSH 实现
- **Sardine-Android**: WebDAV 协议客户端
- **JSoup**: HTML 解析与数据提取

### 媒体处理
- **ExoPlayer + Media3**: 专业级媒体播放与流媒体支持
- **DASH/HLS/SmoothStreaming**: 自适应流媒体协议

### 浏览器引擎
- **GeckoView**: Mozilla Firefox 渲染引擎
- **AgentWeb**: 轻量级网页容器与下载拦截
- **WebView/Windows WebView**: 让你随时随地轻松的下载文件和浏览

### 架构模式
- **MVVM**: 清晰的架构分层
- **Repository**: 统一的数据源管理
- **Navigation**: 单 Activity 多 Fragment 导航

## 📦 安装指南

### 系统要求
- **Android 8.0.0 (Oreo)** (API level 26+)
- **最小内存**: 2GB RAM (推荐 4GB+)
- **存储空间**: 500MB 可用空间

### 下载方式

#### 正式稳定版
从 [GitHub Releases](https://github.com/your-username/your-repo/releases/latest) 下载最新稳定版 APK。

#### AI-Beta 测试版
体验最新 AI 功能：[AI-Beta 版本](https://github.com/your-username/your-repo/releases/tag/ai-beta)

#### 源码编译
```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
./gradlew assembleRelease
```

# 🚀 快速开始

## 基础下载

1. 直接下载: 在主界面输入下载链接  
2. 浏览器下载: 使用内置浏览器访问网页，点击下载链接  
3. 批量操作: 长按任务进行多选，批量管理  

### 高级用法

#### 代码集成示例

```kotlin
// 创建下载任务
val task = DownloadTask.Builder()
    .url("https://example.com/large-file.zip")
    .title("大型资源文件")
    .destination(Environment.DIRECTORY_DOWNLOADS)
    .threadCount(8)
    .enableResume(true)
    .notificationVisibility(NotificationVisibility.VISIBLE)
    .addHeader("User-Agent", "Advanced-Download-Manager/1.0")
    .build()

val taskId = downloadManager.enqueue(task)

downloadManager.getProgress(taskId).collect { progress ->
    println("进度: ${progress.percent}%")
    println("速度: ${progress.speedBps} B/s")
    println("剩余: ${progress.remainingTime}")
}
```

#### SFTP 下载配置

```kotlin
val sftpConfig = SftpConfig.Builder()
    .host("sftp.example.com")
    .port(22)
    .username("your-username")
    .privateKey(privateKey)
    .remotePath("/files/large-backup.tar.gz")
    .localPath("/sdcard/Backups/")
    .build()

sftpDownloader.download(sftpConfig)
```

### ⚙️ 配置说明

#### 网络设置

```yaml
下载设置:
  同时任务数: 1-5个可调
  单任务线程数: 1-16线程
  速度限制: 无限制/自定义KBps
  仅WiFi下载: 是/否
  自动重试: 3次(可配置)
```

## 存储管理

- **默认路径:** /sdcard/Download/  
- **分类存储:** 自动按类型分类到子文件夹  
- **历史记录:** 下载历史保存与清理策略  
- **缓存管理:** 自动清理临时文件  

## 通知定制

- **进度通知:** 显示实时下载进度  
- **完成通知:** 下载完成提醒与打开选项  
- **错误通知:** 失败原因分析与重试建议  

# 🔄 更新日志

## 版本 6.5.5 (当前)

- ✅ 基础多协议下载引擎  
- ✅ 智能断点续传  
- ✅ 多线程加速  
- ✅ Material Design 3 界面  
- ✅ 基础通知系统  

## AI-Beta 版本特性

- 🧠 智能下载调度  
- 🔮 网络状态预测  
- 📊 下载模式自学习  
- ⚡ 动态参数优化  

## 开发路线图

- 🔄 v1.1.0: 插件系统架构  
- 🔄 v1.2.0: 云存储同步  
- 🔄 v1.3.0  
- 🔄 v2.0.0: 桌面版与多平台支持  
- [未] 跨设备任务同步  

## 🤝 参与贡献

我们热烈欢迎社区贡献！请阅读我们的贡献指南。

# 开发环境搭建

1. 安装 Android Studio Arctic Fox+  
2. 克隆仓库并导入项目  
3. 配置 Kotlin 1.8.22 SDK  
4. 同步 Gradle 依赖  

# 贡献方式

## 代码贡献

- 修复 Bug、实现新功能  
- 文档改进: 完善文档、翻译本地化  
- 测试反馈: 测试各版本并提供反馈  
- 功能建议: 在 Issues 提出宝贵建议  

# 提交规范

```bash
git commit -m "feat: 添加SFTP下载支持"
git commit -m "fix: 修复断点续传内存泄漏"
git commit -m "docs: 更新安装指南"
```

# 📄 许可证

Licensed under the Apache License, Version 2.0.  
详见 LICENSE 文件。

# 🏆 致谢

特别感谢以下开源项目：

- AndroidX  
- Kotlin  
- ExoPlayer  
- GeckoView  
- OkHttp  
- 以及所有项目依赖的开源库作者  

# 📞 支持与反馈

- 问题报告: GitHub Issues  
- 功能讨论: Discussions  
- 邮箱联系: zhuangjiunang@gmail.com  
- 文档网站: GitHub Wiki  
- 官方网站: https://zhuangjiunanp.github.io 

[![License](https://zhuangjiunanp.github.io/Webdevelopmentresources/ic_launcher.png)](https://zhuangjiunanp.github.io)
---

如果这个项目对您有帮助，请给我们一颗 ⭐ 以示支持！

让下载变得更智能、更高效！
