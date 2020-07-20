### 1. JAVA_HOME
1.1 作用
  - JAVA_HOME实际上是JDK的安装目录。例如，我把JDK安装在D:\Program Files\Java\jdk-11.0.7\这个目录下。设置JAVA_HOME可以方便在Path中使用、更新JDK目录。比如，jdk的安装路径是D:\Program Files\Java\jdk-11.0.7\，Path设置为D:\Program Files\Java\jdk-11.0.7\bin，而当我们把JAVA_HOME设为D:\Program Files\Java\jdk-11.0.7时，设置Path就可以写成%JAVA_HOME%\bin，以后当我们使用其他版本的JDK，就可以只修改JAVA_HOME的值，此外，当我们要使用Redis等组件时，也可以灵活使用JAVA_HOME做些改动。

1.2 配置
   - 请见 [Win10下 Java环境变量配置](https://www.cnblogs.com/cnwutianhao/p/5487758.html)
   - 在环境变量下的系统变量中，新建变量，变量名称设置为JAVA_HOME，值设置为JDK的安装目录。
### 2. path
2.1 作用
   - Windows在查找可执行文件是这样的：在终端输入某个命令，例如是java时，系统就会先在当前目录查找java程序，如果有就会执行java，否则就会在Path中指定的路径中找。因为我们在PATH配置了...\jdk\bin，系统会在这个路径下找到Java程序并执行。否则就提示找不到命令。Path的作用其实就是方便我们使用一些命令。
   
2.2 配置
   - 请见 [Win10下 Java环境变量配置](https://www.cnblogs.com/cnwutianhao/p/5487758.html)
   - 在环境变量下的系统变量中，找到Path这个变量，然后进行编辑，主要是添加两个内容：
     - %JAVA_HOME%\bin
     - %JAVA_HOME%\jre\bin
   - 在Win7系统下，这样添加：%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
### 3. CLASSPATH
3.1 作用
   - 编译、运行Java程序时，JRE会去该变量指定的路径中搜索所需的类（.class）文件。
   - 注意，JDK1.5版本后可以不用配置这个变量。但是为了保证兼容性，我们还是要配置这个变量。
 3.2 配置
   - 请见 [Win10下 Java环境变量配置](https://www.cnblogs.com/cnwutianhao/p/5487758.html)
   - 在环境变量下的系统变量中，新建变量，变量名称设置为CLASSPATH，值设置为：.;%JAVA_HOME%\bin;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar
   - 注意，这个值最前面的点（.），不要忘了。
### 4. 参考
1. [Java的JAVA_HOME、Path、CLASSPATH环境变量小结](https://blog.csdn.net/sinat_30973431/article/details/82556821)
2. [Win10下 Java环境变量配置](https://www.cnblogs.com/cnwutianhao/p/5487758.html)