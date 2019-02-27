# 利用旧的x200笔记本搭建 nextcloud 私有云盘

## 模拟测试

### 硬件准备及测试

1. 购买测试磁盘框
        
        https://item.jd.com/40614743817.htm
        
        https://item.jd.com/4934568.html

    > 根据预算及功能，使用 ubuntu server 软 raid 做基础平台，购5盘位无阵列磁盘框，及2T紫盘5块，到货后，连接安装及连接到 x200 + ubuntu18 desktop 查看，发现5个 /dev/sdb ... /dev/sdf 共5个盘磁盘，符合需求。 

1. 测试 ubuntu server 基础环境

    > 通过虚拟机安装 ubuntu server，连接多块虚拟磁盘，搭建 raid，及 nextcloud 平台，并进行坏盘故障模拟和系统损坏重装系统重建环境模拟。

    1. 安装 ubuntu server

        1. 新建虚拟机。

        1. 安装过程中配置 raid5

            > 本地20G磁盘 + lvm

            > raid5 10G*3 + lvm 模式 mount /var/lib/ 用于存储 docker 数据巻及镜像 
        
        2. 系统安装完成后，配置 nat + host-only 网络
            > 参见： https://www.hi-linux.com/posts/49513.html

        3. 连接 ssh 更新 docker
            > 参见： https://docs.docker.com/install/linux/docker-ce/ubuntu/

        4. 备份


## 前期测试
1. docker 拉取 nextcloud 的官方镜像

        docker pull nextcloud:latest

        docker pull nextcloud:fpm

    其中 nextcloud:latest 为集成了 apache 的官方应用，nextcloud:fpm 为基于 php:fpm 并集成了相应扩展的 php 镜像，后续因需要部署 https 所以先试验 nextcloud:latest 后使用 nextcloud:fpm 实际部署,同时配置 nginx 以实现远程下载 （aria2c -D)

