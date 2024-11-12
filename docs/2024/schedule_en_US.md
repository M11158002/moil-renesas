---
sidebar_position: 1
---

# Embedded Systems Development Course Outline

## Course Progress Overview

| Week | Date | Content |
|------|------|------|
| Week 1 | 11/18 - 11/22 | MOIL System Introduction <br /> Linux Basics |
| Week 2 | 11/25 - 11/29 | Yocto Project Development Practice |
| Week 3 | 12/02 - 12/06 | GStreamer Multimedia Framework |
| Week 4 | 12/09 - 12/11 | Qt Graphical Interface Development <br /> Course Discussion and Summary |

## Detailed explanation of course units

### Basic environment construction

#### Introduction to Development Environment

- MOIL system introduction
- Development environment architecture description
- Course learning path description

#### Ubuntu system and Linux basics

##### Basic settings and operations

- Ubuntu Server installation and configuration
- Basic Linux command operations
- Practical exercises and problem solving

##### Ubuntu related resources

- [Ubuntu Server Installation Guide](https://ubuntu.com/tutorials/install-ubuntu-server#1-overview)
- [Create a bootable USB stick tutorial](https://ubuntu.com/tutorials/install-ubuntu-desktop#3-create-a-bootable-usb-stick)
- [OpenSSH Server Settings](https://documentation.ubuntu.com/server/how-to/security/openssh-server/)
- [Taiwan Mirror Station Settings](https://mirror.twds.com.tw/)

#### Containerization technology practice

##### Docker Infrastructure

- Introduction to Docker architecture
- Docker installation and configuration
- Docker container management
- Practical exercises and problem solving

##### Docker reference resources

- [Docker Engine Installation Guide](https://docs.docker.com/engine/install/ubuntu/)
- [Linux environment Docker post-installation settings](https://docs.docker.com/engine/install/linux-postinstall/)
- [Container Run Management](https://docs.docker.com/engine/containers/run/)

#### WSL development environment configuration

##### WSL system settings

- Introduction to WSL 2 architecture
- WSL installation and configuration
- WSL instance management
- Practical exercises and problem solving

##### WSL Technical Resources

- [WSL Installation Guide](https://learn.microsoft.com/en-us/windows/wsl/install)
- [WSL Advanced Settings Configuration](https://learn.microsoft.com/en-us/windows/wsl/wsl-config)
- [WSL Web Application Access Settings](https://learn.microsoft.com/en-us/windows/wsl/networking)
- [WSL's D3D12 GPU video acceleration function](https://devblogs.microsoft.com/commandline/d3d12-gpu-video-acceleration-in-the-windows-subsystem-for-linux-now-available/)

#### Development tool integration environment

##### IDE and version control settings

- VSCode installation and basic configuration
- VSCode remote development environment settings
- SSH connection configuration
- WSL development environment integration
- Docker container development settings
- Git version control and GitHub collaboration

##### Development tool resources

- [Git version control](https://git-scm.com/)
- [VSCode Environment Setup Guide](https://code.visualstudio.com/docs/setup/setup-overview)
- [VSCode remote development](https://code.visualstudio.com/docs/remote/remote-overview)
- [VSCode Git version control](https://code.visualstudio.com/docs/sourcecontrol/overview)

#### Technical Document Management System

##### Docusaurus Document Platform

- Docusaurus installation and configuration
- Markdown file writing
- File deployment and version management
- Practical exercises and problem solving

##### File system resources

- [Node.js Installation Guide](https://nodejs.org/en/download/package-manager/)
- [Docusaurus installation tutorial](https://docusaurus.io/docs/installation)
- [Docusaurus Configuration Instructions](https://docusaurus.io/docs/configuration)
- [Docusaurus User Guide](https://docusaurus.io/docs/category/guides)
- [Document deployment process](https://docusaurus.io/docs/deployment)

### Embedded system development

#### Yocto Linux system setup

##### Development environment preparation steps

- Yocto development environment setup
- Docker container environment configuration
- Installation and settings of related tools
- Yocto system customization
- Add the required meta levels
-Recipe file modification
- System configuration file adjustment
- System construction and deployment
- BitBake build process instructions
- Customized Linux image file generation
- SD card burning and system startup
- Development board function verification

##### Yocto Development Resources

- [Yocto Project Quick Setup Guide](https://docs.yoctoproject.org/brief-yoctoprojectqs/index.html)
- [RZ/G2L Development Kit Description](https://www.renesas.com/en/products/microcontrollers-microprocessors/rz-mpus/rzg2l-evkit-evaluation-board-kit-rzg2l-mpu)
- [RZ/G2L Evaluation Board Quick Start Guide](https://www.renesas.com/en/document/qsg/rzg2l-evaluation-board-kit-quick-start-guide?r=1518686)
- [RZ/G Linux Verification Kit](https://www.renesas.com/en/products/microcontrollers-microprocessors/rz-mpus/rzg-linux-platform/rzg-marketplace/verified-linux-package/rzg- verified-linux-package)
- [Renesas Technology Wiki](https://jira-gasg.renesas.eu/confluence/display/REN/Renesas+Wiki)
- [balenaEtcher burning tool](https://etcher.balena.io/)

#### GStreamer application practice

##### GStreamer basic concepts

- Architecture introduction
- Commonly used commands and tool operations
- Pipeline design principles

##### Cross-platform development and performance comparison

- PC development
- GStreamer Development Kit Installation and Settings
- Pipeline implementation and testing

- RZ/G2L development board integration
- Yocto recipe modification
- Rebuild system image file
- SD card writing and development board startup
- Pipeline implementation and testing

- Performance analysis and optimization
- Performance data collection methods
- Performance comparison between PC and RZ/G2L
- System resource usage analysis
- Performance tuning suggestions

##### GStreamer technical resources

- [GStreamer Installation Guide](https://gstreamer.freedesktop.org/documentation/installing/index.html?gi-language=c)
- [Basic Teaching Series](https://gstreamer.freedesktop.org/documentation/tutorials/basic/index.html?gi-language=c)
- [Plug-in development documents](https://gstreamer.freedesktop.org/documentation/plugins_doc.html?gi-language=c)
- [Renesas GStreamer technical documentation](https://jira-gasg.renesas.eu/confluence/display/REN/GStreamer)

#### Graphical interface application development

##### Qt framework integration

- Qt development environment setup
- Qt application development
- RZ/G2L Qt integrated development

##### Qt development resources

- [Renesas Qt Graphics Technical Documents](https://jira-gasg.renesas.eu/confluence/display/REN/Graphics)

#### Hardware interface control development

##### GPIO system programming

- Development environment preparation
- Qt GPIO program development
- RZ/G2L GPIO control implementation

##### GPIO Technical Resources

- [Renesas Core GPIO File](https://jira-gasg.renesas.eu/confluence/display/REN/Kernel)

## Basic course requirements

### Necessary skills background

- Basics of programming languages
- C/C++ programming basics
- Python programming basics
- Linux system operating experience
- Basic command operations
- File system management
- Permission setting concept

### Course Evaluation Items

#### 1. Environmental construction project

- Complete development environment configuration
- Development tool installation and settings
- Basic operation files

#### 2. Linux system development project

- Customized Linux system
- Development board startup test
- Build process documentation

#### 3. Multimedia application project

- Pipeline design files
- Functional test report
- Performance analysis report

#### 4. User interface project

- User interface design
- Function implementation code
- Application documents

#### 5. Hardware control project

- Hardware control program
- Test verification report
- technical documents

#### 6. Technical Documentation Project

- Development environment setup guide
- Application manual
- Troubleshooting guide
