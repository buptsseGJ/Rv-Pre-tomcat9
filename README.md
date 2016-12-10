# Rv-Predict测试Tomcat步骤
  > rv-predict下载链接https://runtimeverification.com/predict/
  
  > tomcat9下载链接http://tomcat.apache.org/download-90.cgi
  
## 1. jdk安装与配置
- jdk 1.8版本（因为rv-predict需要jdk 1.8）
- 设置相关的环境变量 

## 2. Ant安装与配置(windows系统)
- Ant 1.9.5及以上版本
- 设置ANT_HOME环境变量
`如 E:\tsmart\source of key\apache-ant-1.9.6`
*注意：请换成个人tomcat-lib所在的目录位置*
- 添加bin到path环境变量
` %ANT_HOME%\bin` 

## 3. Build Tomcat 8.0
- 下载地址 http://tomcat.apache.org/download-90.cgi
- 在tomcat根目录外新建文件夹
`如 tomcat-lib`
- tomcat根目录下新建文件 **build.properties**，添加如下内容到其中
```
base.path=E:/tomcat-rvpredict/tomcat-lib
```
*注意：请换成个人tomcat-lib所在的目录位置*
- 测试Tomcat的build是否成功，命令行进入根目录，输入**ant**, 若build successful即成功，否则failed是失败。

## 4. 集成Rv-predict命令
- 修改根目录下build.xml文件，大约1435行jvm部分附近增加如下内容：
` <jvmarg value="-javaagent:C:\RV-Predict\rv-predict.jar=--base-log-dir log"/>`
*注意：将C:\RV-Predict\rv-predict.jar换成个人的rv-predict安装目录*
- 运行rv-predict，命令**ant test**
