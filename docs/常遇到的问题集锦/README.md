
常遇到的问题集锦。

### 9.1. 安装相关
#### 9.1.1. JVM提示不能正常启动

安装jdk,配置环境变量后，发现双击spoon.bat无法打开可视化界面，多半是jdk版本的问题。
1. 检查一遍环境变量 `KETTLE_HOME`, `JAVA_HOME`配置是否有误
2. 检查安装的jdk版本，建议安装高版本的jdk。例如pdi1.7(Kettle版本)需要1.7及以上的jdk
3. 如果以上两点均没有问题，由于之前安装过低版本jdk,`java -version`发现jdk版本还是老版本，检查一下原版本的快捷方式`java.exe`是否还在，找到删除它。可能存在的地方有：
    - `C:\ProgramData\Java\javapath`
    - `C:\windows\System32 `
    - ......


### 9.2. 资源库相关
#### 9.2.1. 资源库的位置

新版本的资源库连接在右上角O(∩_∩)O哈！

#### 9.2.2. 新安装的KETTLE资源库点击 connect 后一片空白

看一下本地IE的版本，升级到9及9以上吧~

#### 9.2.3. 资源库迁移
资源库配置文件在`\data-integration\.kettle\repositories.xml`,在迁移时不要对该文件格式有变动。

### 9.3. 数据库相关
#### 9.3.1. 驱动找不到

1. 获取相关的驱动
2. 把驱动包放在`\data-integration\lib`目录下
3. 关闭spoon.bat重新打开
4. 如果还不行，请获取最新版本的驱动重复2和3

#### 9.3.2. ODBC不支持

如果使用的是jdk1.8及以上，ODBC方式就不支持了。

> The JDBC-ODBC Bridge should be considered a transitional solution; it will be removed in JDK 8. In addition, Oracle does not support the JDBC-ODBC Bridge. Oracle recommends that you use JDBC drivers provided by the vendor of your database instead of the JDBC-ODBC Bridge.

#### 9.3.3. Informix中文乱码

使用informix数据库，表输出抽取数据如果出现乱码，有两种情况：
1. 数据库连接带上编码，NEWCODESET根据数据库实际情况配置
   - 服务器名称如： `servername;;NEWCODESET=GBK,8859_1,819;`
   - jdbc字符串如： `jdbc:informix-sqli://ip:port/dbname:informixserver=servername;;NEWCODESET=GBK,8859_1,819;`
2. 如果已经完成1，还是乱码，可尝试在表输入时勾选“”

### 9.4. 跨平台相关
#### 9.4.1. 迁移到Linix日志乱码
确定非机器本身问题后，可修改spoon.sh如下片段，新增如 `-Dfile.encoding=UTF-8` 指定编码 ：
```shell
export LIBPATH

# ******************************************************************
# ** Set java runtime options                                     **
# ** Change 2048m to higher values in case you run out of memory  **
# ** or set the PENTAHO_DI_JAVA_OPTIONS environment variable      **
# ******************************************************************

if [ -z "$PENTAHO_DI_JAVA_OPTIONS" ]; then
    PENTAHO_DI_JAVA_OPTIONS="-Xms1024m -Xmx2048m -XX:MaxPermSize=256m -Dfile.encoding=UTF-8"
fi
```