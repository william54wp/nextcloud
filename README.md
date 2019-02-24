# 利用旧的x200笔记本搭建 nextcloud 私有云盘
## 环境测试
1. 搭建 ubuntu server 基础环境
1. 测试磁盘框

    /dev/sdb ... /dev/sdf 共5个盘

> 通过 ubuntu server，连接磁盘框，搭建raid，本地搭建 nextcloud 环境，

## 前期测试
1. docker 拉取 nextcloud 的官方镜像

        docker pull nextcloud:latest

        docker pull nextcloud:fpm

    其中 nextcloud:latest 为集成了 apache 的官方应用，nextcloud:fpm 为基于 php:fpm 并集成了相应扩展的 php 镜像，后续因需要部署 https 所以先试验 nextcloud:latest 后使用 nextcloud:fpm 实际部署
