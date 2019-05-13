- [3. Kettle脚本运行](#3-kettle%E8%84%9A%E6%9C%AC%E8%BF%90%E8%A1%8C)
  - [3.1. 如何后台运行](#31-%E5%A6%82%E4%BD%95%E5%90%8E%E5%8F%B0%E8%BF%90%E8%A1%8C)
    - [3.1.1. linux例子](#311-linux%E4%BE%8B%E5%AD%90)
    - [3.1.2. windows例子](#312-windows%E4%BE%8B%E5%AD%90)
  - [3.2. 例子说明](#32-%E4%BE%8B%E5%AD%90%E8%AF%B4%E6%98%8E)
  - [3.3. 关于日志等级说明(/logfile)](#33-%E5%85%B3%E4%BA%8E%E6%97%A5%E5%BF%97%E7%AD%89%E7%BA%A7%E8%AF%B4%E6%98%8Elogfile)
  - [3.4. 转换日志输出说明](#34-%E8%BD%AC%E6%8D%A2%E6%97%A5%E5%BF%97%E8%BE%93%E5%87%BA%E8%AF%B4%E6%98%8E)

## 3. Kettle脚本运行
Kettle开发的脚本分为转换(trans)如：`test.ktr` 和作业(job)如：`test.kjb` 。在Spoon可视化界面可运行调试转换和作业，Kettle提供Pan和Kitchen后台分别执行它们。
### 3.1. 如何后台运行
#### 3.1.1. linux例子
使用资源库`myRepo`，作业的相对路径为`dataSync/finally-Sync-testTable`，我们可以新建脚本`Run.sh`，脚本内容如下：
```shell
#!/bin/sh -l
#======================SetVar====================================
# 执行日期
yyyyMMdd=`date +%Y%m%d`
# 资源库名称
KettleBase=myRepo
# 定义日志文件
LogFile=/opt/pdi/log/dataSync/"$yyyyMMdd".log
# 执行的脚本
JobFile=dataSync/finally-Sync-testTable
#======================RunJob====================================
# job
sh $KETTLE_HOME/kitchen.sh -rep=$KettleBase -user=admin -pass=admin -job=$JobFile -level=basic>>$LogFile
#======================RunTrans==================================
# trans
# sh $KETTLE_HOME/pan.sh -rep=$KettleBase -user=admin -pass=admin -trans=$TransFile -level=basic>>$LogFile
```
#### 3.1.2. windows例子
使用资源库`myRepo`，作业的相对路径为`dataSync/finally-Sync-testTable`，假如我们使用了一个命名参数`DT`，需要传入当前日期，我们可以新建脚本`Run.bat`，脚本内容如下：
```bat
@echo off
setlocal enabledelayedexpansion 
for /f "tokens=2 delims==" %%a in ('wmic path win32_operatingsystem get LocalDateTime /value') do (
  set t=%%a
)
rem ======================SetVAR====================================
rem 执行日期
set yyyyMMdd=%t:~0,4%%t:~4,2%-%t:~6,2%%t:~8,2%
rem 资源库名称
set KettleBase=myRepo
rem 定义日志文件
set LogFile=E:\PDI\Logs\dataSync\%yyyyMMdd%.log
rem 执行的脚本
set JobFile=dataSync//finally-Sync-testTable
rem ======================RunJob===================================
rem job DT是命名参数
%KETTLE_HOME%\Kitchen.bat -rep %KettleBase% -user admin -pass admin -job %JobFile% -param:"DT=%yyyyMMdd%"  -level=basic>> %LogFile%
rem ======================RunTrans==================================
rem trans
rem %KETTLE_HOME%\pan.bat -rep=%KettleBase% -user=admin -pass=admin -trans=%TransFile% -level=basic>> %LogFile%
```
### 3.2. 例子说明
* 作业和转换
    - job由kitchen脚本执行
    - trans由pan脚本执行
* 跨平台
    - linux系统对应的是`kitchen.sh`和`pan.sh`
    - windows系统对应的是`kitchen.bat`和`pan.bat`
* 使用资源库
    - 不使用资源库需要使用作业和转换的绝对路径以及后缀
    - 使用资源库可以更好的管理数据链接，作业和转换；推荐使用资源库。
* 以下是一个不使用资源库在linux上执行作业的例子
```sh
$KETTLE_HOME/kitchen.sh -file /opt/pdi/dataSync/finaly-test.kjb -level Basic -logfile /opt/pdi/log/dataSync/2019041_test.log
```
* 关于执行参数说明(pan和Kitchen相似，以下是Kitchen执行参数)
  - /rep        : repository name
  - /user       : repository username
  - /pass       : repository password
  - /job        : the name of the job to launch
  - /dir        : the directory (dont forget the leading /)
  - /file       : the filename (job xml) to launch
  - /level      : the logging level (basic, detailed, debug, rowlevel, error, nothing)
  - /logfile    : the logging file to write to
  - /listdir    : list the directories in the repository
  - /listjobs   : list the jobs in the specified directory
  - /listrep    : list the available repositories
  - /norep      : do not log into the repository
  - /version    : show the version, revision and build date
  - /param      : set a named parameter <name>=<value>. for example -param:foo=bar
  - /listparam  : list information concerning the defined parameters in the specified job.
  - /export     : exports all linked resources of the specified job. the argument is the name of a zip file.

### 3.3. 关于日志等级说明(/logfile)

日志输出共分七个等级：没有日志`Nothing`、错误日志`Error`、最小日志`Minimal`、基本日志`Basic`、详细日志`Detailed`、调试日志`Debug`、行级日志`Rowlevel`。默认为基本日志。

如例子中的`-level Basic`可缺省，表示基本日志。

* Nothing: 不显示任何输出
* Error: 仅仅显示错误信息
* Minimal: 使用最小的日志
* Basic: 缺省的日志级别
* Detailed: 给出日志输出的细节
* Debug: 调试目的，调试输出
* Rowlevel: 打印出每一行记录的信息

### 3.4. 转换日志输出说明
下面是一个基本日志输出的例子：
* I: 当前步骤生成的记录数（从表输入、文件读入）
* O: 当前步骤输出的记录数（输出到文件、表）
* R: 当前步骤从前一步聚读取的记录数
* W: 当前步骤向后面步骤抛出的记录数
* U: 当前步骤更新过的记录数
* E: 当前步骤处理出错的记录数
