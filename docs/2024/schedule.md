---
sidebar_position: 0
---

# 嵌入式系統開發課程大綱

## 課程進度總覽

| 週次 | 日期 | 內容 |
|------|------|------|
| 第 1 週 | 11/18 - 11/22 | MOIL 系統介紹 <br /> Linux 基礎 |
| 第 2 週 | 11/25 - 11/29 | Yocto Project 開發實務 |
| 第 3 週 | 12/02 - 12/06 | GStreamer 多媒體框架 |
| 第 4 週 | 12/09 - 12/11 | Qt 圖形介面開發 <br /> 課程討論與總結 |

## 課程單元詳解

### 基礎環境建置篇

#### 開發環境導論

- MOIL 系統介紹
- 開發環境架構說明
- 課程學習路徑說明

#### Ubuntu 系統與 Linux 基礎

##### 基礎設定與操作

- Ubuntu Server 安裝與配置
- 基礎 Linux 指令操作
- 實作練習與問題排除

##### Ubuntu 相關資源

- [Ubuntu Server 安裝指南](https://ubuntu.com/tutorials/install-ubuntu-server#1-overview)
- [建立開機隨身碟教學](https://ubuntu.com/tutorials/install-ubuntu-desktop#3-create-a-bootable-usb-stick)
- [OpenSSH 伺服器設定](https://documentation.ubuntu.com/server/how-to/security/openssh-server/)
- [臺灣映像站設定](https://mirror.twds.com.tw/)

#### 容器化技術實務

##### Docker 基礎架構

- Docker 架構介紹
- Docker 安裝與配置
- Docker 容器管理
- 實作練習與問題排除

##### Docker 參考資源

- [Docker Engine 安裝指南](https://docs.docker.com/engine/install/ubuntu/)
- [Linux 環境 Docker 安裝後設定](https://docs.docker.com/engine/install/linux-postinstall/)
- [容器運行管理](https://docs.docker.com/engine/containers/run/)

#### WSL 開發環境配置

##### WSL 系統設定

- WSL 2 架構介紹
- WSL 安裝與配置
- WSL 實例管理
- 實作練習與問題排除

##### WSL 技術資源

- [WSL 安裝指南](https://learn.microsoft.com/en-us/windows/wsl/install)
- [WSL 進階設定配置](https://learn.microsoft.com/en-us/windows/wsl/wsl-config)
- [WSL 網路應用存取設定](https://learn.microsoft.com/en-us/windows/wsl/networking)
- [WSL 的 D3D12 GPU 視訊加速功能](https://devblogs.microsoft.com/commandline/d3d12-gpu-video-acceleration-in-the-windows-subsystem-for-linux-now-available/)

#### 開發工具整合環境

##### IDE 與版本控制設定

- VSCode 安裝與基礎配置
- VSCode 遠端開發環境設定
  - SSH 連線配置
  - WSL 開發環境整合
  - Docker 容器開發設定
- Git 版本控制與 GitHub 協作

##### 開發工具資源

- [Git 版本控制](https://git-scm.com/)
- [VSCode 環境設定指南](https://code.visualstudio.com/docs/setup/setup-overview)
- [VSCode 遠端開發](https://code.visualstudio.com/docs/remote/remote-overview)
- [VSCode Git 版本控制](https://code.visualstudio.com/docs/sourcecontrol/overview)

#### 技術文件管理系統

##### Docusaurus 文件平台

- Docusaurus 安裝與配置
- Markdown 文件撰寫
- 文件部署與版本管理
- 實作練習與問題排除

##### 文件系統資源

- [Node.js 安裝指南](https://nodejs.org/en/download/package-manager/)
- [Docusaurus 安裝教學](https://docusaurus.io/docs/installation)
- [Docusaurus 配置說明](https://docusaurus.io/docs/configuration)
- [Docusaurus 使用指南](https://docusaurus.io/docs/category/guides)
- [文件部署流程](https://docusaurus.io/docs/deployment)

### 嵌入式系統開發篇

#### Yocto Linux 系統建置

##### 開發環境準備步驟

- Yocto 開發環境建置
  - Docker 容器環境配置
  - 相關工具安裝與設定
- Yocto 系統客製化
  - 加入所需的 meta 層級
  - 配方檔案（recipe）修改
  - 系統組態檔案調整
- 系統建置與部署
  - BitBake 建置流程說明
  - 客製化 Linux 映像檔產生
  - SD 卡燒錄與系統啟動
  - 開發板功能驗證

##### Yocto 開發資源

- [Yocto Project 快速建置指南](https://docs.yoctoproject.org/brief-yoctoprojectqs/index.html)
- [RZ/G2L 開發套件說明](https://www.renesas.com/en/products/microcontrollers-microprocessors/rz-mpus/rzg2l-evkit-evaluation-board-kit-rzg2l-mpu)
- [RZ/G2L 評估板快速入門指南](https://www.renesas.com/en/document/qsg/rzg2l-evaluation-board-kit-quick-start-guide?r=1518686)
- [RZ/G Linux 驗證套件](https://www.renesas.com/en/products/microcontrollers-microprocessors/rz-mpus/rzg-linux-platform/rzg-marketplace/verified-linux-package/rzg-verified-linux-package)
- [Renesas 技術維基](https://jira-gasg.renesas.eu/confluence/display/REN/Renesas+Wiki)
- [balenaEtcher 燒錄工具](https://etcher.balena.io/)

#### GStreamer 應用實務

##### GStreamer 基礎概念

- 架構介紹
- 常用指令與工具操作
- Pipeline 設計原則

##### 跨平台開發與效能比較

- PC 端開發
  - GStreamer 開發套件安裝與設定
  - Pipeline 實作與測試

- RZ/G2L 開發板整合
  - Yocto 配方修改
  - 重新建置系統映像檔
  - SD 卡寫入與開發板啟動
  - Pipeline 實作與測試

- 效能分析與最佳化
  - 效能數據收集方法
  - PC 與 RZ/G2L 效能對比
  - 系統資源使用分析
  - 效能調校建議

##### GStreamer 技術資源

- [GStreamer 安裝指南](https://gstreamer.freedesktop.org/documentation/installing/index.html?gi-language=c)
- [基礎教學系列](https://gstreamer.freedesktop.org/documentation/tutorials/basic/index.html?gi-language=c)
- [插件開發文件](https://gstreamer.freedesktop.org/documentation/plugins_doc.html?gi-language=c)
- [Renesas GStreamer 技術文件](https://jira-gasg.renesas.eu/confluence/display/REN/GStreamer)

#### 圖形介面應用開發

##### Qt 框架整合

- Qt 開發環境建置
- Qt 應用程式開發
- RZ/G2L Qt 整合開發

##### Qt 開發資源

- [Renesas Qt 圖形技術文件](https://jira-gasg.renesas.eu/confluence/display/REN/Graphics)

#### 硬體介面控制開發

##### GPIO 系統程式設計

- 開發環境準備
- Qt GPIO 程式開發
- RZ/G2L GPIO 控制實作

##### GPIO 技術資源

- [Renesas 核心 GPIO 文件](https://jira-gasg.renesas.eu/confluence/display/REN/Kernel)

## 課程基礎要求

### 必要技能背景

- 程式語言基礎
  - C/C++ 程式設計基礎
  - Python 程式設計基礎
- Linux 系統操作經驗
  - 基本指令操作
  - 檔案系統管理
  - 權限設定概念

### 課程評量項目

#### 1. 環境建置專案

- 完整的開發環境配置
- 開發工具安裝與設定
- 基礎操作文件

#### 2. Linux 系統開發專案

- 客製化 Linux 系統
- 開發板啟動測試
- 建置過程文件

#### 3. 多媒體應用專案

- Pipeline 設計文件
- 功能測試報告
- 效能分析報告

#### 4. 使用者介面專案

- 使用者介面設計
- 功能實作程式碼
- 應用程式文件

#### 5. 硬體控制專案

- 硬體控制程式
- 測試驗證報告
- 技術文件

#### 6. 技術文件專案

- 開發環境建置指南
- 應用程式使用手冊
- 問題排除指南
