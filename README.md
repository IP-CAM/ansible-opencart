# OpenCart Automation Installation and Deployment

This project is an [OpenCart] (https://www.opencart.com/) automation installer developed by [https://www.Websoft9.com). The development language is ansible. With this item, you only need to run a command on Linux, you can automate the installation of OpenCart, so that the original complex installation process has no technical threshold.

This project is an open source project with LGPL3.0 open source protocol.

## Configuration requirements

Install this project to ensure that conditions are met:

| Conditions | Details | Remarks |
| ------------------------------- |
| Operating System | Centos7.x |
| AWS, AZURE, Ali Cloud, Huawei Yun, Tencent Cloud | Optional |
| Private Cloud | KVM, VMware, VirtualBox, OpenStack | Optional |
| Server configuration | Minimum 1 core 1G, the bandwidth required for installation is not less than 10m | It is recommended to use 100M bandwidth |

##

The core components included are: OpenCart official original or opencart Chinese version + Apache / Nginx + MySQL + PHP

See you more, see: [Parameter Table] (/ DOCS / ZH / STACK-COMPONENTS.MD)

## Do you install the latest version of OpenCart?

This project is installed by downloading [OpenCart source] (https://github.com/opencart/opencart), where the version number is stored in: [main.yml] (/ Roles / OpenCart / defaults / main.yml)

`` `
# Two release of metadata. The project on OpenCart Github has 180,000 files, not using gitclone
OpenCART_DISTRIBUTION_META:

  ORIGINAL:
    Download_URL: "https://github.com/opencart/opencart/releases/download/3.0.3.2/opencart-3.0.3.2.zip"
    DocumentRoot: "Upload"
  
  CHINESE:
    Download_URL: "https://libs.websoft9.com/apps/opencart/opencart-v36-free-20190715.zip"
    DocumentRoot: "Upload"
`` `
If you want to modify the version number:

- Original: Please check the OpenCart warehouse [RELESES] page, get the download link of OpenCart specified version, then modify [Role / OpenCart / Default / Main .yml] (/ Roles / OpenCart / defaults / main.yml) file in the `Download_URL` variable.
- Chinese: Please go to the official [Download Center] (https://www.opencart.cn/download # anc "Download, upload it to the role / opencart / files directory of this project, then modify [Main.yml] (/ Roles / OpenCart / Defaults / Main.yml) file in the `Download_url` Volume.

We will check the version regularly and test the availability of official version to ensure that users can install the latest version smoothly.

## Installation Guide

Log in to Linux with root users, run the following ** One-button Automation Installation Command ** can start automation deployment. If there is no root user, run the `sudo su -` command after logging in to Linux with other users, then runs the following script.

`` `
Wget -n https://Raw.githubuserContent.com/websoft9/ansible-linux/main/scripts/install.sh; bash install.sh -r opencart
`` `

After the script starts, start the automation installation, if necessary, the user needs to make interactive selection, then patiently wait until the installation is successful.

** Precautions in installation: **

1. Inadvertent operation or changes in the network may cause the SSH connection to be interrupted, the installation will fail, please reinstall
2. Slow installation, stagnation or no reason, mainly the download problem caused by the network is not (or the speed of the network), please reinstall

For a variety of reasons, it cannot be installed smoothly.

## license

[LGPL-3.0] (/ license.md), Additional Terms: It is not allowed to public on this repository in any Cloud Platform's Marketplace.
Copyright (c) 2016-present, WebSoft9

## Document

Document link: https://support.Websoft9.com/docs/opencart/en

## faq

- What is the difference between command script deployment and mirror deployment? Please refer to: [Mirror Deployment-VS-Script Deployment] (https://support.websoft9.com/docs/faq/en/bz-product.html# Mirror Deployment - VS - Script Deployment)
- Does this project support run on ANSIBLE TOWER? stand by

## To do

* Add NGINX Support
* Add ubuntu18.04, Amazon Linux2 support

---------

# OpenCart 自动化安装与部署

本项目是由 [Websoft9](https://www.websoft9.com) 研发的 [OpenCart](https://www.opencart.com/) 自动化安装程序，开发语言是 Ansible。使用本项目，只需要用户在 Linux 上运行一条命令，即可自动化安装 OpenCart，让原本复杂的安装过程变得没有任何技术门槛。  

本项目是开源项目，采用 LGPL3.0 开源协议。

## 配置要求

安装本项目，确保符合如下的条件：

| 条件       | 详情       | 备注  |
| ------------ | ------------ | ----- |
| 操作系统       | CentOS7.x       |   |
| 公有云| AWS, Azure, 阿里云, 华为云, 腾讯云 | 可选 |
| 私有云|  KVM, VMware, VirtualBox, OpenStack | 可选 |
| 服务器配置 | 最低1核1G，安装时所需的带宽不低于10M |  建议采用按量100M带宽 |

## 组件

包含的核心组件为：opencart官方原版 或 Opencart中文版 + Apache/Nginx + MySQL + PHP

更多请见：[参数表](/docs/zh/stack-components.md)

## 本项目安装的是 opencart 最新版吗？

本项目通过下载[opencart源码](https://github.com/opencart/opencart)进行安装，其中版本号存储在：[main.yml](/roles/opencart/defaults/main.yml)

```
#两个发行版的元数据。Opencart Github上的项目有18万个文件，不使用Git clone
opencart_distribution_meta:

  original:
    download_url: "https://github.com/opencart/opencart/releases/download/3.0.3.2/opencart-3.0.3.2.zip"
    documentroot: "upload"
  
  chinese:
    download_url: "https://libs.websoft9.com/apps/opencart/opencart-v36-free-20190715.zip"
    documentroot: "upload"
```
如果你想修改版本号：

- 官方原版（original）：请先查看 opencart 仓库 [releases](https://github.com/opencart/opencart/releases) 页面，获取 opencart 指定版本的下载链接，再修改 [role/opencart/default/main.yml](/roles/opencart/defaults/main.yml) 文件中的 `download_url` 变量值。
- 中文版（chinese）：请先到官方[下载中心](https://www.opencart.cn/download#anchor-download)，下载后上传到本项目的 role/opencart/files 目录下，然后修改 [main.yml](/roles/opencart/defaults/main.yml) 文件中的 `download_url` 变量值。

我们会定期检查版本，并测试官方版本的可用性，以保证用户可以顺利安装最新版。

## 安装指南

以 root 用户登录 Linux，运行下面的**一键自动化安装命令**即可启动自动化部署。若没有 root 用户，请以其他用户登录 Linux 后运行 `sudo su -` 命令提升为 root 权限，然后再运行下面的脚本。

```
wget -N https://raw.githubusercontent.com/Websoft9/ansible-linux/main/scripts/install.sh; bash install.sh -r opencart
```

脚本后启动，就开始了自动化安装，必要时需要用户做出交互式选择，然后耐心等待直至安装成功。

**安装中的注意事项：**  

1. 操作不慎或网络发生变化，可能会导致SSH连接被中断，安装就会失败，此时请重新安装
2. 安装缓慢、停滞不前或无故中断，主要是网络不通（或网速太慢）导致的下载问题，此时请重新安装

多种原因导致无法顺利安装，请使用我们在公有云上发布的 [opencart镜像](https://apps.websoft9.com/opencart) 的部署方式

## License

[LGPL-3.0](/License.md), Additional Terms: It is not allowed to publish free or paid image based on this repository in any Cloud platform's Marketplace.
Copyright (c) 2016-present, Websoft9

## 文档

文档链接：https://support.websoft9.com/docs/opencart/zh

## FAQ

- 命令脚本部署与镜像部署有什么区别？请参考：[镜像部署-vs-脚本部署](https://support.websoft9.com/docs/faq/zh/bz-product.html#镜像部署-vs-脚本部署)
- 本项目支持在 Ansible Tower 上运行吗？支持

## To do

* 添加 Nginx 支持
* 添加 Ubuntu18.04, Amazon Linux2 支持
