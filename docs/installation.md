# opengauss部署指南

## ‌一、环境准备

### 一、更新系统

```bash
yum -y update  
yum -y upgrade
```

## ‌二、安装docker

参考：[安装Docker](https://support.huaweicloud.com/bestpractice-hce/hce_bp_0002.html)

## ‌二、安装opengauss

```bash
cd /opt
# 下载
wget https://download-opengauss.osinfra.cn/archive_test/7.0.0-RC1/openGauss7.0.0-RC1.B023/openEuler20.03/arm/openGauss-Docker-7.0.0-RC1-aarch64.tar

# 加载
docker load -i openGauss-Docker-7.0.0-RC1-aarch64.tar

# 运行
docker run -d --name opengauss   --privileged=true   -p 15432:5432   -e GS_PASSWORD="QwErTy@123!"   -v /data/opengauss:/var/lib/opengauss   --shm-size=1g   --memory=4g   opengauss:7.0.0-rc1

# 检查容器状态
docker ps -a | grep opengauss
```
