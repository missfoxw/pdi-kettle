
<!-- ## 4. JavaScript组件 -->
Kettle支持使用JS组件，下面列出一些JS组件在转换中较常见的用法。
### 4.1. 获取变量
命名参数和变量的在js里获取。
```js
//默认密码123456
var palin_code=getVariable("PLAIN_CODE","123456");
```

### 4.2. EncryptPassword
例如：Kettle数据库文件 .kjb 里 password 为加密结果。
```js
//对应的palin_code：********
//Encrypted 2be98af9f33edb182bc58fc2086886e3
var encrypted_password = "Encrypted " + Packages.org.pentaho.di.core.encryption.Encr.encryptPassword(palin_code);
```

### 4.3. 获取数据库信息
```js
var db = _step_.getTransMeta().findDatabase("dbKettleName");

//jdbc:informix-sqli://IP:Port/dbName:INFORMIXSERVER=serverName;;NEWCODESET=GBK,8859_1,819;;DELIMIDENT=Y
var url = db.getURL();
//IP
var hostname = db.getHostname();
```

### 4.4. JS循环处理判断
JS脚本会对每一个数据流操作，我们可以在某条数据处理完毕后停止。
> `SKIP_TRANSFORMATION`, `ERROR_TRANSFORMATION`, `CONTINUE_TRANSFORMATION` 是TRANSFORMATION已经预先定义好的静态常量,不可更改。作用是过滤记录行，控制转换流程

```js
trans_Status = CONTINUE_TRANSFORMATION;
//获取当前js处理第几条流数据
var processCount=getProcessCount("r");

if(getProcessCount("r")>5) { 
    //可以在第五条后停止循环处理
    trans_Status = SKIP_TRANSFORMATION;
}
```
### 4.5. 字段处理
可以对每一条数据的每一个字段进行处理，比如以下例子对所有字符类型字段的数据处理：把'E'替换成 'M'。

```js
//字段和字段类型的对象集合
var a = getInputRowMeta();
//第一个字段的类型
var field1_type = getInputRowMeta().getValueMeta(0).getTypeDesc();

for (var i=0;i<getInputRowMeta().size();i++) { //loop through the actual row

  // Grab the metadata for this value
  var valueMeta = getInputRowMeta().getValueMeta(i);

  //using the IDs instead of "String" would make it faster, see API for the IDs
  if (valueMeta.getTypeDesc().equals("String")) { //only for String types
    //所有字符类型字段数据里的 'E'替换成 'M'
    row[i]=replace(row[i],'E','M');
  }
}
```

### 4.6. 行数据新增/复制
该功能用来伪造数据（我确实干过）真的六到飞起。
* 处理前数据
  
|member|groupsField|
|-|-|
|Member 1|	Group1, Group2, Group3, Group4|
|Member 2|	Group1, Group2|

* 处理脚本

```js
if (groupsField!=null) 
{
  var groups = groupsField.split(",");
 
  for (i=0;i<groups.length;i++)
  {
    //拷贝新行数据
    newRow = createRowCopy(getOutputRowMeta().size());
    var rowIndex = getInputRowMeta().size();

    //新增两列数据
    newRow[rowIndex++] = trim( groups[i] );
    newRow[rowIndex++] = "N";
    //记录新增行
    putRow(newRow);
  }
}
//原始行数据新增列的赋值
var subgroup = "";
var ignore = "Y";
```

* 处理后数据
  
|member|groupsField|subgroup|ignore|
|-|-|-|-|
|Member 1|	Group1, Group2, Group3, Group4|	Group1|	N|
|Member 1|	Group1, Group2, Group3, Group4|	Group2|	N|
|Member 1|	Group1, Group2, Group3, Group4|	Group3|	N|
|Member 1|	Group1, Group2, Group3, Group4|	Group4|	N|
|Member 1|	Group1, Group2, Group3, Group4|	|	Y|
|Member 2|	Group1, Group2|		Group1|N|
|Member 2|	Group1, Group2|		Group2|N|
|Member 2|	Group1, Group2|		|Y|

### 4.7. 时间转换
一般周期运行的程序都会用到，支持js函数外，组件左侧列出了可用的已经定义的函数。
```js
// 2019/04/1 16:20:2295
var now=new java.util.Date();
// 昨天
var lastDay=new java.util.Date();
// 2019/04/16 16:20:2295
lastDay.setDate(lastDay.getDate()-1);
//2019-04-1 16:20:24
var nowStr=date2str(now,'yyyy-MM-dd HH:mm:ss');
// 20
var interval = dateDiff(lastDay,now,'HH');

// C:\temp\LIM_kettle\ST1PROTOKL.TENOPROD_2006_0_21_00_09
var dat = DIR.Clone().rightstr(16).str2dat("yyyy_MM_dd_HH_mm");
// 2006/0/21 00:09:00.000
```

### 4.8. bytes转换

```js
var F1 = 'VGV4dCBmaWxlIGlucHV0';
// binary:
var bytes = Packages.org.apache.commons.codec.binary.Base6decodeBase64( FgetString().getBytes() );
// 
var decString = new Packages.java.lang.String( bytes );
// VGV4dCBmaWxlIGlucHV0
var encString = new Packages.java.lang.String( Packages.org.apache.commons.codec.binary.Base6encodeBase64( decString.getBytes() ) );
```	
### 4.9. JS弹出框输入
sample里给的一个例子，弹出框输入开始日期和结束日期：
```js
// This JavaScript asks for a start and ending date with text dialog boxes.
// It is  a proof of concept if dialogs could be used out of JavaScript within transformations.
// This could be a base for discussion if a general input step dialog should be created.
// It runs within Spoon, Pan and launched by the "Test script" button within the JavaScript editor.
// @author Jens Bleuel
// @since 2006-0-11

// to get the "Test script" button at the editor working correctly we need the existing Display / Shell
var display;
var displayHasToBeDisposed=false;
var shell=null;

try {
    display=Packages.org.eclipse.swt.widgets.Display.getCurrent();
    shell=display.getActiveShell();
} catch(e) {
    // if it runs in batch mode (Pan or preview mode) no Display is available, so we have to create one
    display=new Packages.org.eclipse.swt.widgets.Display();
    displayHasToBeDisposed=true;
    shell=new Packages.org.eclipse.swt.widgets.Shell(display);
}

// if we run in Pan we need to load the properties:
if(!Packages.org.pentaho.di.ui.core.PropsUI.isInitialized()) {
    Packages.org.pentaho.di.ui.core.PropsUI.init(display,2); //2=TYPE_PROPERTIES_PAN
}

var dateDefaultFrom=DateFromProposal.getString().substr(0,10); //only the date and not the time
var dialogDateFrom=new Packages.org.pentaho.di.ui.core.dialog.EnterTextDialog(shell, "Date from", "Please enter the beginning date", dateDefaultFrom);
var dateFromAsString=dialogDateFrom.open();

if(dateFromAsString!=null && dateFromAsString.length()>0) {
    var dateDefaultTo=DateToProposal.getString().substr(0,10); //only the date and not the time;
    var dialogDateTo=new Packages.org.pentaho.di.ui.core.dialog.EnterTextDialog(shell, "Date to", "Please enter the ending date", dateDefaultTo);
    var dateToAsString=dialogDateTo.open();
    if(dateToAsString!=null && dateToAsString.length()>0) {
        // here you could check or change formats a.s.o
    } else {
        // stop transformation when user cancels
        throw new Packages.java.lang.RuntimeException("Input canceled by the user.");
    }
} else {
    // stop transformation when user cancels
    throw new Packages.java.lang.RuntimeException("Input canceled by the user.");
}

if(displayHasToBeDisposed) {
  display.dispose();
}
```
### 4.10. JS日志输出
例如在第五行输出字符串：
```js
if(getProcessCount("r") == 5) { 
  writeToLog('m',str);
}
```
### 4.11. 导出导入资源库
```js
/*
 * 导出
 */
// Get the repository we're connected to
var rep = _step_.getTrans().getRepository();
// Ask the repository for its exporter
var exporter = rep.getExporter();
// Find the directory to export in the repository
var repdir = rep.loadRepositoryDirectoryTree().findDirectory(directory);
// Export all the objects from the directory into the filename we specified
exporter.exportAllObjects(null, filename, repdir, "all");

/*
 * 导入
 */
// Get the repository we're connected to
var rep = _step_.getTrans().getRepository();
// Load the repository directory structure
var root = rep.loadRepositoryDirectoryTree();

// Find the directory we want to import into in the repository and create it if it doesn't exist.
//
var repdir = root.findDirectory(directory);
if (repdir==null) {
 repdir = rep.createRepositoryDirectory(root, directory);
}
// Ask the repository for its importer
var importer = rep.getImporter();

// Set the directory overrides if they're being used
if (transDirOverride != null && !"".equals(transDirOverride)) {
  importer.setTransDirOverride(transDirOverride);
}
if (jobDirOverride != null && !"".equals(jobDirOverride)) {
  importer.setJobDirOverride(jobDirOverride);
}

// Get the file that was specified as FILENAME
var file = new Packages.java.io.File(filename);

// Must pass file names to import as an array
var filenames = null;
// Check if the filename is a directory
if (file.isDirectory()) {
  // If the file is a directory find all the files inside of it
  // and use those for the import
  var files = file.listFiles();
  filenames = java.lang.reflect.Array.newInstance(
    java.lang.String, // Element type, do not change
    files.length  // Number of file names to pass in
  );
  for (i=0;i<files.length;i++) {
    filenames[i] = files[i].getAbsolutePath();
  }
} else {
  // If the file is not a directory it is the only file to be used
  // for importing
  filenames = java.lang.reflect.Array.newInstance(
    java.lang.String, // Element type, do not change
    1  // Number of file names to pass in
  );
  filenames[0] = filename;
}

// Set the overwrite flag
var overwrite = Packages.java.lang.Boolean.parseBoolean(overwrite);

// Perform the import
//
importer.importAll(
   importer,        // The feedback object
   null,            // Relative file directory of filenames (next parameter)
   filenames,       // The export files to import
   repdir,          // The directory to import into
   overwrite,            // Overwrite existing objects
   true,            // Continue on error
   "Batch import"); // Version comment
```
