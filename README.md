# pdi-Kettle
## [整理使用Kettle过程中积累的知识点（更新中）](/ETL之Kettle使用手册2019（更新中）.md)
> 注：不讲安装，安装入门移步[KETTLE安装配置](https://www.cnblogs.com/missfox18/p/7215062.html)

* [1. 写在前面的话](/ETL之Kettle使用手册2019（更新中）.md)
---
* [2. Kettle连接数据库-2019年5月9日](Kettle连接数据库/README.md)
	* [2.1. ODBC方式](Kettle连接数据库/README.md)
		* 2.1.1. ODBC连Oracle
		* 2.1.2. ODBC连Informix
	* [2.2. JDBC方式](Kettle连接数据库/README.md)
		* 2.2.1. JDBC连Informix
		* 2.2.2. JDBC连Oracle
		* 2.2.3. JDBC连Impala
	* [2.3. 通用数据库方式](Kettle连接数据库/README.md)
		* 2.3.1. hsqlDB
	* [2.4. JNDI方式](Kettle连接数据库/README.md)
		* 2.4.1. JNDI连Oracle
		* 2.4.2. JNDI连h2
---
* [3. Kettle脚本运行-2019年5月13日](Kettle脚本运行/README.md)
	* [3.1. 如何后台运行](Kettle脚本运行/README.md)
		* 3.1.1. linux例子
		* 3.1.2. windows例子
	* [3.2. 例子说明](Kettle脚本运行/README.md)
	* [3.3. 关于日志等级说明(/logfile)](Kettle脚本运行/README.md)
	* [3.4. 转换日志输出说明](Kettle脚本运行/README.md)
---
* [4. JavaScript组件-2019年5月14日](JavaScript组件/README.md)
	* [4.1. 获取变量](JavaScript组件/README.md)
	* [4.2. EncryptPassword](JavaScript组件/README.md)
	* [4.3. 获取数据库信息](JavaScript组件/README.md)
	* [4.4. JS循环处理判断](JavaScript组件/README.md)
	* [4.5. 字段处理](JavaScript组件/README.md)
	* [4.6. 行数据新增/复制](JavaScript组件/README.md)
	* [4.7. 时间转换](JavaScript组件/README.md)
	* [4.8. bytes转换](JavaScript组件/README.md)
	* [4.9. JS弹出框输入](JavaScript组件/README.md)
	* [4.10. JS日志输出](JavaScript组件/README.md)
	* [4.11. 导出导入资源库](JavaScript组件/README.md)
---
* [5. Java相关组件](Java相关组件/README.md)
---
* [6. 我的案例积累](我的案例积累/README.md)
	* 6.1. 数据库迁移  
	* 6.2. 调用webService接口处理数据入库
	* 6.3. 增量同步 
	* 6.4. 读取数据库数据生成xml文件  
	* 6.5. 读取xml文件 
	* 6.6. 生成指定分隔符文件上传FTP服务器  
	* 6.7. 采集文件解析入库  
		* 6.7.1. CRT采集  
		* 6.7.2. FTP/SFTP 
		* 6.7.3. 文本文件 
		* 6.7.4. ZIP/gz
		* 6.7.5. JSON文件 
	* 6.8. 生成报表 
	* 6.9. 统计数据 
		* 6.9.1. 行列转换 
		* 6.9.2. 分组聚合 
		* 6.9.3. 过滤去重 
---
* [7. 常用调度方案](常用调度方案/README.md)
	* 7.1. 任务计划定时
	* 7.2. Crontab任务 
	* 7.3. Jenkins  
	* 7.4. 其他  
---
* [8. 完整的开发实例-2019年5月24日](完整的开发实例/README.md)
	* [8.1. 一次基于命名参数和任务计划定时的Windows开发案例](完整的开发实例/README.md)
	* [8.2. 一次基于资源库和jenkin调度的Linux开发案例](完整的开发实例/README.md)
---
* [9. 常遇到的问题集锦](常遇到的问题集锦/README.md)  
	* 9.1. 安装相关 
		* 9.1.1. JVM提示不能正常启动  
	* 9.2. 资源库相关  
		* 9.2.1. 资源库的位置
		* 9.2.2. 新安装的KETTLE资源库点击 connect 后一片空白  
	* 9.3. 数据库相关  
		* 9.3.1. 驱动找不到  
		* 9.3.2. ODBC不支持  
		* 9.3.3. Informix中文乱码  
	* 9.4. 跨平台相关  
		* 9.4.1. 迁移到Linix日志乱码  
---
