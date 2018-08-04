java调用wsdl接口

前提：① 已经提供了一个wsdl接口② 该接口能正常调用
总体分为两种方式：
1.使用cxf的wsdl2java工具生成本地类（使用方式就是本地类的使用）。 
2.调用远程的web service方法：创建client来远程调用接口。
因为第二种方式，需要熟悉wsdl，没深入了解不太好操作，主要说下第一种方式。

使用cxf的wsdl2java工具生成本地类主要步骤如下：
1、安装JDK环境（jdk版本是1.6的话，后续会报错jdk6最高只支持ws2.1规范版本）
2、下载apache-cxf发布包，下载CXF：http://cxf.apache.org/download.html 目前最新版本为3.1.7，解压发布包，设置CXF_HOME，并添加%CXF_HOME %/bin到path环境变量。
3、CMD命令行输入wsdl2java -help，有正常提示说明环境已经正确配置。 
4、CMD运行命令 ： wsdl2java -encoding utf-8 -d D:\javalib\web http://m.zsjsjy.com/services/resource?wsdl 
（wsdl 的路径）
-encoding表示生成的Java文件编码格式为utf8，-d表示代码生成路径为D:\javalib\we。运行后会在运行命令的当前路径生成以供使用的类 
5、把生成的类导入项目。一般服务都叫XXXService，这是我们最为关心的接口文件

 
上述过程中的遇到的问题：
1、
因为jdk是1.6版本的，导致下载的apache-cxf发布包解压后使用报错，这是cxf和jdk的jar包有冲突引起的！
就下载了老版本的apache-cxf-2.6.12.zip ，查了一些资料，保险起见接着把jdk换成了1.7，
如果还报错 就在jdk1.7文件夹下的jre下的lib文件下创建一个endorsed文件夹（D:\java\jdk1.7.0_16\jre\lib\endorsed），
把apache-cxf中jaxb对应的三个2.2jar包复制到endorsed中，最后成功生产本地java类。
2、
成功生成java文件导入项目后，调整完java中报错的包文件，结果serviece类中还是有构造函数报错，注释说需要jaxws2.2来重新生成才可。
查了下资料说其不能正常编译通过是由于jax-ws2.2规约与java6冲突。 但程序又不能仅以java5来编译，故需要降低jax-ws规约版本。
解决办法：执行命令： wsdl2java -frontend jaxws21 -d D:\javalib\cn http://m.zsjsjy.com/services/resource?wsdl 
重新生成来解决。
3、
接口调用测试时报错，Exception in thread "main" org.apache.cxf.service.factory.ServiceConstructionException
原因是生成接口java类，namespace路径是它原来默认的，而我放进项目时类的路径已经是现在的了。解决办法：
需要 自定义-p路径 重新生成：
 wsdl2java -frontend jaxws21 -encoding utf-8 -p cn.teacheredu.app.projectconfigcenter.proj.module.screen.tlogin.zswebservice -d D:\javalib\cn http://m.zsjsjy.com/services/resource?wsdl  
 