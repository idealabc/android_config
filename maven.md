# Mac OS 配置Maven



* Maven 地址http://maven.apache.org/

* 安装在本地目录 比如 ~/Library/apache-maven-3.3.9

* 环境变量

vi ~/.bash_profile  
```    
    export M2_HOME=~/Library/apache-maven-3.3.9
	export PATH=$PATH:$M2_HOME/bin
```

使配置生效
source ~/.bash_profile  

* 建立Maven目录 ~/.m2/repository

* 配置 ~/Library/apache-maven-3.3.9/setting.xml

```
Default: ${user.home}/.m2/repository

<server>
      <id>deploymentRepo</id>
      <username>repouser</username>
      <password>repopwd</password>
</server>

```

# 使用Nexus创建Maven私有仓库

* 下载地址: (http://www.sonatype.org/nexus/go)[http://www.sonatype.org/nexus/go]

* 下载war包，直接把war包放到tomcat的webapp下，启动tomcat

* http://localhost:8080/nexus/ 进入nexus

