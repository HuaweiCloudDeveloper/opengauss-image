<p align="center">
  <h1 align="center">opengauss数据库</h1>
  <p align="center">
    <a href="README.md"><strong>English</strong></a> | <strong>简体中文</strong>
  </p>

## 目录

- [仓库简介](#项目介绍)
- [前置条件](#前置条件)
- [镜像说明](#镜像说明)
- [获取帮助](#获取帮助)
- [如何贡献](#如何贡献)

## 项目介绍
[opengauss](https://gitcode.com/opengauss/openGauss-server) 是一款开源的关系型数据库管理系统，它具有多核高性能、全链路安全性、智能运维等企业级特性。‌

### **核心功能：**

**高性能**

openGauss突破了多核CPU的瓶颈，实现两路鲲鹏128核150万tpmC，内存优化表（MOT）引擎达350万tpmC。

**数据分区**

内部线程共享的关键数据结构进行数据分区，减少加锁访问冲突。比如CLOG就采用分区优化，解决ClogControlLock锁瓶颈。

**NUMA化内核数据结构**

关键数据结构NUMA化分配，减少跨CPU访问。比如全局PGPROC数组按照NUMA Node的数目分为多份，分别在对应NUMA Node上申请内存。解决ProcArrayLock锁瓶颈。

**绑核优化**

把网络中断绑核和后台业务线程绑核区分开，避免运行线程在核间迁移造成的性能不稳定。

**ARM指令优化**

结合ARM平台的原子操作lse进行优化，实现关键互斥变量原子高效操作。

**SQL BY PASS**

通过SQL BY PASS优化SQL执行流程，简化CPU执行开销。

**高可靠**

正常业务负载情况下，RTO小于10秒，降低节点故障导致的业务不可用时间。

**并行恢复**

主机日志传输到备机时，备机日志落盘的同时，发送给重做恢复分发线程，分发线程根据日志类型和日志操作的数据页发给多个并行恢复线程进行日志重做，保证备机的重做速度跟上主机日志的产生速度。这样备机实时处于ready状态，从而实现瞬间故障切换。


**MOT引擎（Beta发布）**

内存优化表（MOT）存储引擎是一个专为多核大内存优化的存储引擎，具有极高的联机事务处理（OLTP）性能和资源利用率。MOT的数据和索引完全存储在内存中，通过NUMA感知执行，算法消除闩锁争用以及查询JIT本地编译，提供低时延数据访问及高效事务执行。更多请参考[MOT引擎文档](https://opengauss.org/zh/docs/2.0.0/docs/Developerguide/%E5%86%85%E5%AD%98%E8%A1%A8%E7%89%B9%E6%80%A7.html) 。

**安全**

openGauss支持账号管理，账号认证，口令复杂度检查，账号锁定，权限管理和校验，传输加密，操作
审计等全方位的数据库安全能力，保护业务满足安全要求。

**易运维**

openGauss将AI算法集成到数据库中，减少数据库维护的负担。

- **SQL预测**

openGauss根据收集的历史性能数据进行编码和基于深度学习的训练及预测，支持SQL执行时间预测。

- **SQL诊断器**

openGauss支持SQL执行语句的诊断器，提前发现慢查询。

- **参数自动调整**

openGauss通过机器学习方法自动调整数据库参数，提高调参效率，降低正确调参成本。


本项目提供的开源镜像商品 [**opengauss数据库**](https://marketplace.huaweicloud.com/contents/9237bc7f-d361-4953-835d-0ecb9dfd7da6#productid=OFFI1161477894538182656) ，已预先安装openGauss及其相关运行环境，并提供部署模板。快来参照使用指南，轻松开启“开箱即用”的高效体验吧。

> **系统要求如下：**
> - CPU: 2GHz 或更高
> - RAM: 4GB 或更大
> - Disk: 至少 40GB

## 前置条件
[注册华为账号并开通华为云](https://support.huaweicloud.com/usermanual-account/account_id_001.html)

## 镜像说明

| 镜像规格                                                                                                        | 特性说明                                           | 备注 |
|-------------------------------------------------------------------------------------------------------------|------------------------------------------------| --- |
| [opengauss-7.0.0-RC1-kunpeng](https://github.com/HuaweiCloudDeveloper/opengauss-image/tree/opengauss-7.0.0-RC1-kunpeng) | 基于 鲲鹏服务器 + Huawei Cloud EulerOS 2.0 64bit 安装部署 |  |

## 获取帮助
- 更多问题可通过 [issue](https://github.com/HuaweiCloudDeveloper/opengauss-image/issues) 或 华为云云商店指定商品的服务支持 与我们取得联系
- 其他开源镜像可看 [open-source-image-repos](https://github.com/HuaweiCloudDeveloper/open-source-image-repos)

## 如何贡献
- Fork 此存储库并提交合并请求
- 基于您的开源镜像信息同步更新 README.md
