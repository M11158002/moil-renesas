# 嵌入式系統開發課程大綱

## 第一部分：基礎環境建置 (4小時)

### 1. 課程簡介與開發環境概述 (30分鐘)

- Moil 專案介紹
- 開發環境架構說明
- 課程學習路徑說明

### 2. Linux 基礎與 Ubuntu Server (1小時)

ubuntu

- Ubuntu 22.04 Server 安裝與配置
- 基礎 Linux 指令操作
- 實作練習與故障排除

[Install Ubuntu Server](https://ubuntu.com/tutorials/install-ubuntu-server#1-overview)  
[OpenSSH Server](https://documentation.ubuntu.com/server/how-to/security/openssh-server/)

### 3. 容器技術基礎 - Docker (1小時)

docker

- Docker 架構介紹
- Docker 安裝與配置
- Docker 容器管理
- 實作練習與故障排除

[Install Docker Engine](https://docs.docker.com/engine/install/ubuntu/)  
[Linux post-installation steps for Docker Engine](https://docs.docker.com/engine/install/linux-postinstall/)

### 4. Windows Subsystem for Linux (1小時)

wsl

- WSL 2 架構介紹
- WSL 安裝與配置
- WSL 實例管理
- 實作練習與故障排除

[How to install Linux on Windows with WSL](https://learn.microsoft.com/en-us/windows/wsl/install)  
[Advanced settings configuration in WSL](https://learn.microsoft.com/en-us/windows/wsl/wsl-config)  
[Accessing network applications with WSL](https://learn.microsoft.com/en-us/windows/wsl/networking)

### 5. 開發工具配置 (30分鐘)

git
vscode

- VSCode 安裝與配置
- VSCode 遠端開發配置
  - SSH 連接配置
  - WSL 開發環境
  - Docker 容器開發
- Git 與 GitHub 基礎操作

[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)  
[VS Code Remote Development](https://code.visualstudio.com/docs/remote/remote-overview)  
[Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)

## 第二部分：專案文件與版本控制 (1小時)

### 6. 技術文件開發與管理

fnm
nodejs npm
github actions ci/cd

- Docusaurus 安裝與配置
- Markdown 語法基礎
- 文件部署與維護
- 實作練習與故障排除

## 第三部分：嵌入式系統開發 (10小時)

### 7. Yocto 客製化 Linux 系統 (7.5小時)

linux command
docker

vscode
balenaEtcher

- Yocto 開發環境建置 (45分鐘)
  - 容器環境配置
  - 必要工具安裝
- Yocto 配置與客製化 (1小時)
  - Recipe 修改
  - Image 配置
- 系統建置與部署 (5.5小時)
  - Image 建置
  - SD 卡燒錄
  - 系統啟動與測試

### 8. 多媒體應用開發 - GStreamer (4小時)

yocto

- 開發環境建置 (1小時)
- GStreamer 插件開發 (30分鐘)
- RZ/G2L 開發板配置 (30分鐘)
- 應用開發與除錯 (2小時)
  - Pipeline 設計與實作
  - 效能優化
  - 故障排除

### 9. 使用者介面開發 - Qt (3小時)

yocto

- Qt 開發環境建置 (1小時)
- Qt 程式開發 (1小時)
- RZ/G2L Qt 程式開發 (1小時)

### 10. 硬體控制開發 - GPIO (3小時)

qt
yocto

- 開發環境準備 (1小時)
- Qt GPIO 程式開發 (1小時)
- RZ/G2L GPIO 程式開發 (1小時)

## 建議的先修知識

- 基礎 Linux 操作經驗
- 基礎程式開發能力

## 課程產出

1. 個人開發環境建置
2. Yocto 客製化映像檔
3. GStreamer 多媒體應用
4. Qt GUI 應用程式
5. GPIO 控制應用
6. 完整專案文件

## GStreamer Performance Comparison

rzg2l yocto
rzv2h yocto
imx8m plus yocto
jetson tx2 ubnutu image
rockchip rk3588 ubuntu image
