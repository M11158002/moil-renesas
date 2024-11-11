---
sidebar_position: 1
---

# 嵌入式系統開發課程大綱

| Week#       | Content     |
| ----------- | ----------- |
| #1 ( 11/18 - 11/22 ) | MOIL Introduction |
|  | Linux basics |
| #2 ( 11/25 - 11/29 ) | 1. Yocto Project |
| #3 ( 12/02 - 12/06 ) | 2. GStreamer |
| #4 ( 12/09 - 12/11 ) | 3. Qt |
|  | 4. Discussion |

## 第一部分：基礎環境建置

### 1. 課程簡介與開發環境概述

- MOIL Introduction
- 開發環境架構說明
- 課程學習路徑說明

### 2. Linux 基礎與 Ubuntu

- Ubuntu 安裝與配置
- 基礎 Linux 指令
- 實作練習

[Install Ubuntu Server](https://ubuntu.com/tutorials/install-ubuntu-server#1-overview)  
[Create a Bootable USB stick](https://ubuntu.com/tutorials/install-ubuntu-desktop#3-create-a-bootable-usb-stick)
[OpenSSH Server](https://documentation.ubuntu.com/server/how-to/security/openssh-server/)
[Taiwan Mirror](https://mirror.twds.com.tw/)

### 3. 容器技術基礎 - Docker

- Docker 架構介紹
- Docker 安裝與配置
- Docker 容器管理
- 實作練習

[Install Docker Engine](https://docs.docker.com/engine/install/ubuntu/)  
[Linux post-installation steps for Docker Engine](https://docs.docker.com/engine/install/linux-postinstall/)  
[Running containers](https://docs.docker.com/engine/containers/run/)

### 4. Windows Subsystem for Linux

- WSL 2 架構介紹
- WSL 安裝與配置
- WSL 實例管理
- 實作練習

[How to install Linux on Windows with WSL](https://learn.microsoft.com/en-us/windows/wsl/install)  
[Advanced settings configuration in WSL](https://learn.microsoft.com/en-us/windows/wsl/wsl-config)  
[Accessing network applications with WSL](https://learn.microsoft.com/en-us/windows/wsl/networking)  
[D3D12 GPU Video acceleration in the Windows Subsystem for Linux now available!](https://devblogs.microsoft.com/commandline/d3d12-gpu-video-acceleration-in-the-windows-subsystem-for-linux-now-available/)

### 5. 開發工具配置

- VSCode 安裝與配置
- VSCode 遠端開發配置
  - SSH 連接配置
  - WSL 開發環境
  - Docker 容器開發
- Git 與 GitHub 基礎操作

[Git](https://git-scm.com/)
[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)  
[VS Code Remote Development](https://code.visualstudio.com/docs/remote/remote-overview)  
[Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)

### 6. 技術文件開發與管理

- Docusaurus 安裝與配置
- Markdown 語法基礎
- 文件部署與維護
- 實作練習與故障排除

[Node.js Install](https://nodejs.org/en/download/package-manager/)  
[Installation](https://docusaurus.io/docs/installation)  
[Configuration](https://docusaurus.io/docs/configuration)  
[Docusaurus Guides](https://docusaurus.io/docs/category/guides)  
[Deployment](https://docusaurus.io/docs/deployment)

## 第二部分：嵌入式系統開發

### 7. Yocto 客製化 Linux 系統

- Yocto 開發環境建置
  - 容器環境配置
  - 必要工具安裝
- Yocto 配置與客製化
  - 初始化
  - 配置設定檔
- 系統建置與部署
  - 建置 自訂 Linux 映像
  - 燒錄 SD 卡
  - 啟動與測試

[Yocto Project Quick Build](https://docs.yoctoproject.org/brief-yoctoprojectqs/index.html)  
[RZ/G2L-EVKIT](https://www.renesas.com/en/products/microcontrollers-microprocessors/rz-mpus/rzg2l-evkit-evaluation-board-kit-rzg2l-mpu)  
[RZ/G2L Evaluation Board Kit Quick Start Guide](https://www.renesas.com/en/document/qsg/rzg2l-evaluation-board-kit-quick-start-guide?r=1518686)  
[RZ/G Verified Linux Package](https://www.renesas.com/en/products/microcontrollers-microprocessors/rz-mpus/rzg-linux-platform/rzg-marketplace/verified-linux-package/rzg-verified-linux-package)  
[Renesas Wiki](https://jira-gasg.renesas.eu/confluence/display/REN/Renesas+Wiki)  
[balenaEtcher](https://etcher.balena.io/)

### 8. 多媒體應用開發 - GStreamer

- 開發環境建置
- GStreamer 插件開發
- RZ/G2L 開發板配置
  - Yocto 配方修改
- 應用開發與除錯
  - Pipeline 設計與實作
  - 效能優化
  - 故障排除

[Installing GStreamer](https://gstreamer.freedesktop.org/documentation/installing/index.html?gi-language=c)  
[Basic tutorials](https://gstreamer.freedesktop.org/documentation/tutorials/basic/index.html?gi-language=c)  
[Plugins](https://gstreamer.freedesktop.org/documentation/plugins_doc.html?gi-language=c)  
[Renesas Wiki GStreamer](https://jira-gasg.renesas.eu/confluence/display/REN/GStreamer)

### 9. 使用者介面開發 - Qt

- Qt 開發環境建置
- Qt 程式開發
- RZ/G2L Qt 程式開發

[Renesas Wiki Qt](https://jira-gasg.renesas.eu/confluence/display/REN/Graphics)

### 10. 硬體控制開發 - GPIO

- 開發環境準備
- Qt GPIO 程式開發
- RZ/G2L GPIO 程式開發

[Renesas Wiki Kernel GPIO](https://jira-gasg.renesas.eu/confluence/display/REN/Kernel)

## 建議的先修知識

- 基礎程式語言知識
- 基礎 Linux 操作經驗

## 課程產出

1. 個人開發環境建置
2. Yocto 客製化映像檔
3. GStreamer Pipeline
4. Qt GUI Application
5. GPIO Control Application
6. Written Documentation
