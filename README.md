# pdi-Kettle
整理使用Kettle过程中积累的知识点（更新中）
> 注：不讲安装，安装入门移步[KETTLE安装配置](https://www.cnblogs.com/missfox18/p/7215062.html)

## 写在前面的话
* [1. 写在前面的话](/ETL之Kettle使用手册2019（更新中）.md)

## Kettle连接数据库-2019年5月9日
* [2. Kettle连接数据库](Kettle连接数据库/README.md)
	* [2.1. ODBC方式](Kettle连接数据库/README.md#21-odbc方式)
		* [2.1.1. ODBC连Oracle](Kettle连接数据库/README.md#211-odbc连oracle)
		* [2.1.2. ODBC连Informix](Kettle连接数据库/README.md#212-odbc连informix)
	* [2.2. JDBC方式](Kettle连接数据库/README.md#22-JDBC方式)
		* [2.2.1. JDBC连Informix](Kettle连接数据库/README.md#221-jdbc连informix)
		* [2.2.2. JDBC连Oracle](Kettle连接数据库/README.md#222-jdbc连oracle)
		* [2.2.3. JDBC连Impala](Kettle连接数据库/README.md#223-jdbc连impala)
	* [2.3. 通用数据库方式](Kettle连接数据库/README.md#23-通用数据库方式)
		* [2.3.1. hsqlDB](Kettle连接数据库/README.md#231-hsqldb)
	* [2.4. JNDI方式](Kettle连接数据库/README.md)
		* [2.4.1. JNDI连Oracle](Kettle连接数据库/README.md#241-jndi连oracle)
		* [2.4.2. JNDI连h2](Kettle连接数据库/README.md#242-jndi连h2)

## Kettle脚本运行-2019年5月13日
- [3. Kettle脚本运行](Kettle脚本运行/README.md#3-kettle%E8%84%9A%E6%9C%AC%E8%BF%90%E8%A1%8C)
  - [3.1. 如何后台运行](Kettle脚本运行/README.md#31-%E5%A6%82%E4%BD%95%E5%90%8E%E5%8F%B0%E8%BF%90%E8%A1%8C)
    - [3.1.1. linux例子](Kettle脚本运行/README.md#311-linux%E4%BE%8B%E5%AD%90)
    - [3.1.2. windows例子](Kettle脚本运行/README.md#312-windows%E4%BE%8B%E5%AD%90)
  - [3.2. 例子说明](Kettle脚本运行/README.md#32-%E4%BE%8B%E5%AD%90%E8%AF%B4%E6%98%8E)
  - [3.3. 关于日志等级说明(/logfile)](Kettle脚本运行/README.md#33-%E5%85%B3%E4%BA%8E%E6%97%A5%E5%BF%97%E7%AD%89%E7%BA%A7%E8%AF%B4%E6%98%8Elogfile)
  - [3.4. 转换日志输出说明](Kettle脚本运行/README.md#34-%E8%BD%AC%E6%8D%A2%E6%97%A5%E5%BF%97%E8%BE%93%E5%87%BA%E8%AF%B4%E6%98%8E)

## JavaScript组件-2019年5月14日
* [4. JavaScript组件](JavaScript组件/README.md#4-javascript组件)
  * [4.1. 获取变量](JavaScript组件/README.md#41-获取变量)
  * [4.2. EncryptPassword](JavaScript组件/README.md#42-encryptpassword)
  * [4.3. 获取数据库信息](JavaScript组件/README.md#43-获取数据库信息)
  * [4.4. JS循环处理判断](JavaScript组件/README.md#44-js循环处理判断)
  * [4.5. 字段处理](JavaScript组件/README.md#45-字段处理)
  * [4.6. 行数据新增/复制](JavaScript组件/README.md#46-行数据新增复制)
  * [4.7. 时间转换](JavaScript组件/README.md#47-时间转换)
  * [4.8. bytes转换](JavaScript组件/README.md#48-bytes转换)
  * [4.9. JS弹出框输入](JavaScript组件/README.md#49-js弹出框输入)
  * [4.10. JS日志输出](JavaScript组件/README.md#410-js日志输出)
  * [4.11. 导出导入资源库](JavaScript组件/README.md#411-导出导入资源库)

## Java相关组件
* [5. Java相关组件](Java相关组件/README.md)

## 我的案例积累
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

## 常用调度方案
* [7. 常用调度方案](常用调度方案/README.md)
	* 7.1. 任务计划定时
	* 7.2. Crontab任务 
	* 7.3. Jenkins  
	* 7.4. 其他  

## 完整的开发实例-2019年5月24日
- [8. 完整的开发实例](完整的开发实例/README.md#8-%E5%AE%8C%E6%95%B4%E7%9A%84%E5%BC%80%E5%8F%91%E5%AE%9E%E4%BE%8B)
  - [8.1. 一次基于命名参数和任务计划定时的Windows开发案例](完整的开发实例/README.md#81-%E4%B8%80%E6%AC%A1%E5%9F%BA%E4%BA%8E%E5%91%BD%E5%90%8D%E5%8F%82%E6%95%B0%E5%92%8C%E4%BB%BB%E5%8A%A1%E8%AE%A1%E5%88%92%E5%AE%9A%E6%97%B6%E7%9A%84windows%E5%BC%80%E5%8F%91%E6%A1%88%E4%BE%8B)
    - [8.1.1. 前言](完整的开发实例/README.md#811-%E5%89%8D%E8%A8%80)
      - [8.1.1.1. 环境](完整的开发实例/README.md#8111-%E7%8E%AF%E5%A2%83)
      - [8.1.1.2. 业务说明](完整的开发实例/README.md#8112-%E4%B8%9A%E5%8A%A1%E8%AF%B4%E6%98%8E)
    - [8.1.2. 设计](完整的开发实例/README.md#812-%E8%AE%BE%E8%AE%A1)
      - [8.1.2.1. 流程组件设计](完整的开发实例/README.md#8121-%E6%B5%81%E7%A8%8B%E7%BB%84%E4%BB%B6%E8%AE%BE%E8%AE%A1)
      - [8.1.2.2. 关键点设计](完整的开发实例/README.md#8122-%E5%85%B3%E9%94%AE%E7%82%B9%E8%AE%BE%E8%AE%A1)
      - [8.1.2.3. 即将用到的组件](完整的开发实例/README.md#8123-%E5%8D%B3%E5%B0%86%E7%94%A8%E5%88%B0%E7%9A%84%E7%BB%84%E4%BB%B6)
    - [8.1.3. 开发](完整的开发实例/README.md#813-%E5%BC%80%E5%8F%91)
      - [8.1.3.1. 数据结构](完整的开发实例/README.md#8131-%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84)
      - [8.1.3.2. 定义文件](完整的开发实例/README.md#8132-%E5%AE%9A%E4%B9%89%E6%96%87%E4%BB%B6)
      - [8.1.3.3. 定义参数](完整的开发实例/README.md#8133-%E5%AE%9A%E4%B9%89%E5%8F%82%E6%95%B0)
      - [8.1.3.4. 作业流程](完整的开发实例/README.md#8134-%E4%BD%9C%E4%B8%9A%E6%B5%81%E7%A8%8B)
        - [8.1.3.4.1. 作业设置](完整的开发实例/README.md#81341-%E4%BD%9C%E4%B8%9A%E8%AE%BE%E7%BD%AE)
        - [8.1.3.4.2. START](完整的开发实例/README.md#81342-start)
        - [8.1.3.4.3. SFTP下载](完整的开发实例/README.md#81343-sftp%E4%B8%8B%E8%BD%BD)
        - [8.1.3.4.4. deleteBeforeInsert](完整的开发实例/README.md#81344-deletebeforeinsert)
        - [8.1.3.4.5. GetDataFromZipFile](完整的开发实例/README.md#81345-getdatafromzipfile)
      - [8.1.3.5. 子转换](完整的开发实例/README.md#8135-%E5%AD%90%E8%BD%AC%E6%8D%A2)
        - [8.1.3.5.1. 转换](完整的开发实例/README.md#81351-%E8%BD%AC%E6%8D%A2)
        - [8.1.3.5.2. zip文件输入](完整的开发实例/README.md#81352-zip%E6%96%87%E4%BB%B6%E8%BE%93%E5%85%A5)
        - [8.1.3.5.3. 数据处理](完整的开发实例/README.md#81353-%E6%95%B0%E6%8D%AE%E5%A4%84%E7%90%86)
        - [8.1.3.5.4. 表输出](完整的开发实例/README.md#81354-%E8%A1%A8%E8%BE%93%E5%87%BA)
    - [8.1.4. 调度运行](完整的开发实例/README.md#814-%E8%B0%83%E5%BA%A6%E8%BF%90%E8%A1%8C)
      - [8.1.4.1. 编写脚本](完整的开发实例/README.md#8141-%E7%BC%96%E5%86%99%E8%84%9A%E6%9C%AC)
      - [8.1.4.2. 任务计划](完整的开发实例/README.md#8142-%E4%BB%BB%E5%8A%A1%E8%AE%A1%E5%88%92)
  - [8.2. 一次基于资源库和jenkin调度的Linux开发案例](完整的开发实例/README.md#82-%E4%B8%80%E6%AC%A1%E5%9F%BA%E4%BA%8E%E8%B5%84%E6%BA%90%E5%BA%93%E5%92%8Cjenkin%E8%B0%83%E5%BA%A6%E7%9A%84linux%E5%BC%80%E5%8F%91%E6%A1%88%E4%BE%8B)
    - [8.2.1. 业务说明](完整的开发实例/README.md#821-%E4%B8%9A%E5%8A%A1%E8%AF%B4%E6%98%8E)
    - [8.2.2. 准备工作](完整的开发实例/README.md#822-%E5%87%86%E5%A4%87%E5%B7%A5%E4%BD%9C)
      - [8.2.2.1. 开发环境](完整的开发实例/README.md#8221-%E5%BC%80%E5%8F%91%E7%8E%AF%E5%A2%83)
      - [8.2.2.2. 生产环境Kettle](完整的开发实例/README.md#8222-%E7%94%9F%E4%BA%A7%E7%8E%AF%E5%A2%83kettle)
      - [8.2.2.3. 生产环境Jenkins](完整的开发实例/README.md#8223-%E7%94%9F%E4%BA%A7%E7%8E%AF%E5%A2%83jenkins)
    - [8.2.3. 作业流程](完整的开发实例/README.md#823-%E4%BD%9C%E4%B8%9A%E6%B5%81%E7%A8%8B)
      - [8.2.3.1. 涉及组件](完整的开发实例/README.md#8231-%E6%B6%89%E5%8F%8A%E7%BB%84%E4%BB%B6)
      - [8.2.3.2. 作业](完整的开发实例/README.md#8232-%E4%BD%9C%E4%B8%9A)
      - [8.2.3.3. 子转换](完整的开发实例/README.md#8233-%E5%AD%90%E8%BD%AC%E6%8D%A2)
        - [8.2.3.3.1. 获取判断条件](完整的开发实例/README.md#82331-%E8%8E%B7%E5%8F%96%E5%88%A4%E6%96%AD%E6%9D%A1%E4%BB%B6)
        - [8.2.3.3.2. 是否具备同步条件](完整的开发实例/README.md#82332-%E6%98%AF%E5%90%A6%E5%85%B7%E5%A4%87%E5%90%8C%E6%AD%A5%E6%9D%A1%E4%BB%B6)
        - [8.2.3.3.3. 同步Irms数据](完整的开发实例/README.md#82333-%E5%90%8C%E6%AD%A5irms%E6%95%B0%E6%8D%AE)
      - [8.2.3.4. 子子转换](完整的开发实例/README.md#8234-%E5%AD%90%E5%AD%90%E8%BD%AC%E6%8D%A2)
        - [8.2.3.4.1. targetTable](完整的开发实例/README.md#82341-targettable)
        - [8.2.3.4.2. sourceTable](完整的开发实例/README.md#82342-sourcetable)
        - [8.2.3.4.3. 调整IRMS数据的类型](完整的开发实例/README.md#82343-%E8%B0%83%E6%95%B4irms%E6%95%B0%E6%8D%AE%E7%9A%84%E7%B1%BB%E5%9E%8B)
        - [8.2.3.4.4. 根据关键字比较记录](完整的开发实例/README.md#82344-%E6%A0%B9%E6%8D%AE%E5%85%B3%E9%94%AE%E5%AD%97%E6%AF%94%E8%BE%83%E8%AE%B0%E5%BD%95)
        - [8.2.3.4.5. Switch/Case](完整的开发实例/README.md#82345-switchcase)
    - [8.2.4. 迁移至生产环境](完整的开发实例/README.md#824-%E8%BF%81%E7%A7%BB%E8%87%B3%E7%94%9F%E4%BA%A7%E7%8E%AF%E5%A2%83)
    - [8.2.5. 生产调度运行](完整的开发实例/README.md#825-%E7%94%9F%E4%BA%A7%E8%B0%83%E5%BA%A6%E8%BF%90%E8%A1%8C)

## 常遇到的问题集锦
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

