# opengauss使用指南

# 一、商品链接

[opengauss数据库]()

# 二、商品说明

**opengauss** 是一款开源的关系型数据库管理系统，它具有多核高性能、全链路安全性、智能运维等企业级特性。

# 三、商品购买示例

您可以在云商店搜索 **opengauss数据库*。

其中，地域、规格、推荐配置使用默认，购买方式根据您的需求选择按需/按月/按年，短期使用推荐按需，长期使用推荐按月/按年，确认配置后点击“立即购买”。

## 3.1、ECS控制台自定义购买示例

### 准备工作

在使用ECS控制台配置前，需要您提前配置好 **安全组规则**。

> **安全组规则的配置如下：**
* 入方向规则放通端口:15432，源地址内必须包含您的客户端ip，提供远程访问
* 入方向规则放通 CloudShell 连接实例使用的端口 `22`，以便在控制台登录调试
* 出方向规则一键放通

### 创建ECS

以购买“spark分布式计算引擎”做为示例，描述ECS控制台购买镜像商品全流程

前提工作准备好后，选择 ECS 控制台配置跳转到[购买ECS](https://support.huaweicloud.com/qs-ecs/ecs_01_0103.html) 页面，ECS 资源的配置如下图所示：

#### 选择CPU架构和规格

1.根据镜像所适配的架构选择对应的架构

2.选择的规格要大于或等于说明文档中提供的最小规格

![image](images/img_2.png)

#### 选择镜像

1.点击市场镜像，进入市场进行列表

2.选择需要购买的商品的规格镜像

![img.png](images/img.png)

#### 其他参数配置

1.其他参数根据实际情况进行填写

2.安全组选择提前配置好的安全组

3.配置完成之后点击立即购买即可

![image](images/img_1.png)

**值得注意的是：**

* VPC 您可以自行创建
* 安全组选择 [**准备工作**](#准备工作)中配置的安全组；
* 弹性公网IP选择现在购买，推荐选择“按流量计费”，带宽大小可设置为5Mbit/s；
* 高级配置需要在高级选项支持注入自定义数据，所以登录凭证不能选择“密码”，选择创建后设置；
* 其余默认或按规则填写即可。


# 四、商品使用

## 4.1 操作数据库

进入容器内部
```bash
docker exec -it opengauss bash
```

基础功能验证
```bash
# 切换用户
su - omm
# gsql连接数据库
gsql -d postgres -U gaussdb -W QwErTy@123!

# 创建测试数据库
CREATE DATABASE testdb;

# 切换数据库
\c testdb;
# 密码：QwErTy@123!

# 建表并插入数据
CREATE TABLE test_table (id INT, name VARCHAR(20));
INSERT INTO test_table VALUES (1, 'opengauss');

# 查询验证
SELECT * FROM test_table;
```
![img.png](images/img_3.png)
![img_1.png](images/img_4.png)


# 参考文档
[opengauss官网](https://opengauss.org/zh/)
