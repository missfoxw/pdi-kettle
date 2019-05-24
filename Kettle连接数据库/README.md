- [2. Kettle连接数据库](#2-kettle%E8%BF%9E%E6%8E%A5%E6%95%B0%E6%8D%AE%E5%BA%93)
  - [2.1. ODBC方式](#21-odbc%E6%96%B9%E5%BC%8F)
    - [2.1.1. ODBC连Oracle](#211-odbc%E8%BF%9Eoracle)
    - [2.1.2. ODBC连Informix](#212-odbc%E8%BF%9Einformix)
  - [2.2. JDBC方式](#22-jdbc%E6%96%B9%E5%BC%8F)
    - [2.2.1. JDBC连Informix](#221-jdbc%E8%BF%9Einformix)
    - [2.2.2. JDBC连Oracle](#222-jdbc%E8%BF%9Eoracle)
    - [2.2.3. JDBC连Impala](#223-jdbc%E8%BF%9Eimpala)
  - [2.3. 通用数据库方式](#23-%E9%80%9A%E7%94%A8%E6%95%B0%E6%8D%AE%E5%BA%93%E6%96%B9%E5%BC%8F)
    - [2.3.1. hsqlDB](#231-hsqldb)
  - [2.4. JNDI方式](#24-jndi%E6%96%B9%E5%BC%8F)
    - [2.4.1. JNDI连Oracle](#241-jndi%E8%BF%9Eoracle)
    - [2.4.2. JNDI连h2](#242-jndi%E8%BF%9Eh2)
---
## 2. Kettle连接数据库

参见[PDI 学习3：数据库连接](https://www.cnblogs.com/missfox18/p/215340.html)。这里列出我用过的一些数据库供参考。
### 2.1. ODBC方式
**不推荐**，jdk8不再使用odbc桥。
> The JDBC-ODBC Bridge should be considered a transitional solution; it will be removed in JDK 8. In addition, Oracle does not support the JDBC-ODBC Bridge. Oracle recommends that you use JDBC drivers provided by the vendor of your database instead of the JDBC-ODBC Bridge.
#### 2.1.1. ODBC连Oracle
* Windows机器安装oracle客户端(也可在官网下载Oracle的Odbc包)，创建ODBC数据源，详见官网 [创建一般 ODBC 连接](https://docs.oracle.com/middleware/bidvhelp/desktop/zh_CN/BIDVD/GUID-13FE85B3-AEEC-4A2E-AD23-EDD4810EF4CE.htm#BIDVD-GUID-13FE85B3-AEEC-4A2E-AD23-EDD4810EF4CE)。
* 填写数据库信息，点击测试连接，输入账号密码测试通过
* 在Spoon界面新建连接，选择Oracle+ODBC方式连接,注意DSN和创建的数据源名称一致
#### 2.1.2. ODBC连Informix
* ODBC驱动：区别在于驱动，需要下载IBM Informix Client-SDK，根据系统版本下载安装后设置如图所示：

![odbc-informix1](imgs/odbc-informix1.png)

![odbc-informix2](imgs/odbc-informix2.png)

* 配置ODBC数据源，测试数据库连接

![odbc-informix3](imgs/odbc-informix3.png)

* 配置KETTLE数据源，选择Informix数据库类型，选择ODBC方式，记住使用DSN名称。

### 2.2. JDBC方式
**推荐**，常用的数据库连接方式。需要准备相关的驱动包，有时候如果数据库连接失败，需要注意是否驱动包版本太低。

基本的新建方式为：
获取jdbc驱动，放在`data-integration\lib` 目录下，然后再Spoon界面新建数据库连接。

#### 2.2.1. JDBC连Informix
* 需要准备驱动包如：`ifxjdbc.jar`
* 针对Informix中文乱码需要设置,对应服务器名称设置如：`$yourServerName$;;NEWCODESET=GBK,8859_1,819;`
* 表输出预览数据乱码：勾选 允许简易转换
  
#### 2.2.2. JDBC连Oracle
* 需要准备驱动包如：`ojdbc6.jar`

#### 2.2.3. JDBC连Impala
* 需要准备驱动包如：`ImpalaJDBC41-2.6.4.jar`

### 2.3. 通用数据库方式
本质上是jdbc方式
#### 2.3.1. hsqlDB
* 下载相应的JDBC驱动,比如`hsqldb-jar`，放在`..\data-integration\lib` 目录下
* 配置`Spoon`界面数据库连接
  - 连接方式选择`JDBC`
  - 连接类型选择通用数据库：`Generic database`
  - 连接名称如：`test_hsqlDB`
  - URL如：`jdbc:hsqldb:hsql://IP:PORT;`
  - 选择驱动名称：`org.hsqldb.jdbcDriver`( 刚刚的驱动包呐 )
  - 一般用户名 `sa` ,无密码；
### 2.4. JNDI方式
> JNDI是 Java 命名与目录接口（Java Naming and Directory Interface），在J2EE规范中是重要的规范之一。

* 官方给了一个H2的例子，详细见[2.4.2. JNDI连h2](#242-jndi%E8%BF%9Eh2)
* 配置文件：`..\data-integration\simple-jndi\jdbc.properties`
#### 2.4.1. JNDI连Oracle
[一个ORACLE 12c 的例子参考](https://www.cnblogs.com/wanggs/p/5055078.html)
#### 2.4.2. JNDI连h2
* 这是官方例子，配置文件内容如下：
```properties
SampleData/type=javax.sql.DataSource
SampleData/driver=org.h2.Driver
SampleData/url=jdbc:h2:file:samples/db/sampledb;IFEXISTS=TRUE
SampleData/user=PENTAHO_USER
SampleData/password=PASSWORD
```
* 页面配置如下：

![](imgs/JNDI-H2.png)