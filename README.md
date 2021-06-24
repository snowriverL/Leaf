## 基于版本：jenv 0.5.2
### jenv 安装下载
复制代码
 1 brew install jenv
 2 
 3 # 环境变量
 4 # Shell: bash
 5 echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.bash_profile
 6 echo 'eval "$(jenv init -)"' >> ~/.bash_profile
 7 
 8 # Shell: zsh
 9 echo 'export PATH="$HOME/.jenv/bin:$PATH"' >> ~/.zshrc
10 echo 'eval "$(jenv init -)"' >> ~/.zshrc
复制代码
 

jenv 检查
1 yfc@yfcMacBook:~/.jenv$  jenv doctor
2 [OK]    No JAVA_HOME set
3 [OK]    Java binaries in path are jenv shims
4 [OK]    Jenv is correctly loaded
 

jenv 管理java版本
 

1、官网下载java安装包


 

 

 

2、安装后默认的包路径
1 /Library/Java/JavaVirtualMachines/jdk1.8.0_201.jdk/Contents/Home
 

 3、将不同版本的jdk ，添加到jenv管理
1 jenv add /Library/Java/JavaVirtualMachines/jdk1.8.0_201.jdk/Contents/Home
2 
3 jenv add /Library/Java/JavaVirtualMachines/jdk-11.0.11.jdk/Contents/Home
 

4、查看全部版本信息
复制代码
 1 yfc@yfcMacBook:~/.jenv$  jenv versions
 2   system
 3   1.8
 4   1.8.0.201
 5   11
 6   11.0
 7   11.0.11
 8 * 8 (set by /Users/yanfuchang/.jenv/.java-version)
 9   oracle64-1.8.0.201
10   oracle64-11.0.11
复制代码
 

5、设置全局的jdk版本
1 jenv global  1.8
全局默认jdk版本，默认会写入：$HOME/.jenv/version  文件中

 

6、设置当前要使用的jdk版本，切换版本
1 jenv  local  1.8
当前使用的jdk版本，默认会写入：$HOME/.jenv/.java-version 文件中，当把.java-version 文件删除后，全局设置生效

 

没错，我们现在有了Java的多个版本，并且可以在它们之间轻松切换。更多的使用方法可以在jEnv官网(https://www.jenv.be/)的官网查询到。

 
启用和停用插件
有很多构建工具运行时是需要JDK的, 但是很多这种工具会在安装时指定固定的JDK, 而这就会导致jenv配置的JDK对于这些构建工具失效了. 要解决这种问题就需要启动对应的插件.注意这是一个全局配置.

 

1、查看jenv支持的插件列表

复制代码
 1 $> jenv plugins
 2 ant
 3 export
 4 golo
 5 gradle
 6 grails
 7 groovy
 8 lein
 9 maven
10 sbt
11 scala
12 springboot
13 vlt
复制代码
 

2、启动插件

1 $> jenv enable-plugin maven
2 maven plugin activated
 

3、停用插件

1 $> jenv disable-plugin maven
2 maven disabled
