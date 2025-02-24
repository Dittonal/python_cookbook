# 使用pem解决权限不安全的问题
- ![](./禁用继承.png)
- ![](./删除其他只剩用户名的用户具有权限.png)
# 在Linux上部署各类软件


```{warning}
出自黑马课程笔记
```

## MySQL数据库管理系统安装部署

### MySQL5.7版本在CentOS系统安装

> 注意：安装操作需要root权限



MySQL的安装我们可以通过前面学习的yum命令进行。



#### 安装

1. 配置yum仓库

   ```shell
   # 更新密钥
   rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
   
   # 安装Mysql yum库
   rpm -Uvh http://repo.mysql.com//mysql57-community-release-el7-7.noarch.rpm
   ```

   ![image-20221012182514865](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/12/20221012182514.png)

   > 由于MySQL并不在CentOS的官方仓库中，所以我们通过上述rpm命令：
   >
   > - 导入MySQL仓库的密钥
   > - 配置MySQLQ的yum仓库

2. 使用yum安装MySQL

   ```shell
   # yum安装Mysql
   yum -y install mysql-community-server
   ```

   ![image-20221012182555420](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/12/20221012182556.png)

3. 安装完成后，启动MySQL并配置开机自启动

   ```shell
   systemctl start mysqld		# 启动
   systemctl enable mysqld		# 开机自启
   ```

   > MySQL安装完成后，会自动配置为名称叫做：`mysqld`的服务，可以被systemctl所管理

4. 检查MySQL的运行状态

   ```shell
   systemctl status mysqld
   ```

   ![image-20221012182716598](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/12/20221012182716.png)



#### 配置

主要配置管理员用户root的密码以及配置允许远程登录的权限。



1. 获取MySQL的初始密码

   ```shell
   # 通过grep命令，在/var/log/mysqld.log文件中，过滤temporary password关键字，得到初始密码
   grep 'temporary password' /var/log/mysqld.log
   ```

   ![image-20221012182744115](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/12/20221012182744.png)

2. 登陆MySQL数据库系统

   ```shell
   # 执行
   mysql -uroot -p
   # 解释
   # -u，登陆的用户，MySQL数据库的管理员用户同Linux一样，是root
   # -p，表示使用密码登陆
   
   # 执行完毕后输入刚刚得到的初始密码，即可进入MySQL数据库
   ```

   ![image-20221012182805966](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/12/20221012182806.png)

3. 修改root用户密码

   ```sql
   # 在MySQL控制台内执行
   ALTER USER 'root'@'localhost' IDENTIFIED BY '密码';	-- 密码需要符合：大于8位，有大写字母，有特殊符号，不能是连续的简单语句如123，abc
   ```

4. [扩展]，配置root的简单密码

   > 我们可以给root设置简单密码，如123456.
   >
   > 请注意，此配置仅仅是用于测试环境或学习环境的MySQL，如果是正式使用，请勿设置简单密码

   ```sql
   # 如果你想设置简单密码，需要降低Mysql的密码安全级别
   set global validate_password_policy=LOW; # 密码安全级别低
   set global validate_password_length=4;	 # 密码长度最低4位即可
   
   # 然后就可以用简单密码了（课程中使用简单密码，为了方便，生产中不要这样）
   ALTER USER 'root'@'localhost' IDENTIFIED BY '简单密码';
   ```

5. [扩展]，配置root运行远程登录

   > 默认情况下，root用户是不运行远程登录的，只允许在MySQL所在的Linux服务器登陆MySQL系统
   >
   > 请注意，允许root远程登录会带来安全风险

   ```sql
   # 授权root远程登录
   grant all privileges on *.* to root@"IP地址" identified by '密码' with grant option;  
   # IP地址即允许登陆的IP地址，也可以填写%，表示允许任何地址
   # 密码表示给远程登录独立设置密码，和本地登陆的密码可以不同
   
   # 刷新权限，生效
   flush privileges;
   ```

6. 退出MySQL控制台页面

   ```sql
   # 退出命令
   exit
   
   # 或者通过快捷键退出：ctrl + d
   ```

7. 检查端口

   MySQL默认绑定了3306端口，可以通过端口占用检查MySQL的网络状态

   ```shell
   netstat -anp | grep 3306
   ```

   ![image-20221012183746802](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/12/20221012183746.png)



至此，MySQL就安装完成并可用了，请妥善保存好MySQL的root密码。





### MySQL8.0版本在CentOS系统安装

> 注意：安装操作需要root权限



#### 安装

1. 配置yum仓库

   ```shell
   # 更新密钥
   rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
   
   # 安装Mysql8.x版本 yum库
   rpm -Uvh https://dev.mysql.com/get/mysql80-community-release-el7-2.noarch.rpm
   ```

2. 使用yum安装MySQL

   ```shell
   # yum安装Mysql
   yum -y install mysql-community-server
   ```

3. 安装完成后，启动MySQL并配置开机自启动

   ```shell
   systemctl start mysqld		# 启动
   systemctl enable mysqld		# 开机自启
   ```

   > MySQL安装完成后，会自动配置为名称叫做：`mysqld`的服务，可以被systemctl所管理

4. 检查MySQL的运行状态

   ```shell
   systemctl status mysqld
   ```



#### 配置

主要修改root密码和允许root远程登录



1. 获取MySQL的初始密码

   ```shell
   # 通过grep命令，在/var/log/mysqld.log文件中，过滤temporary password关键字，得到初始密码
   grep 'temporary password' /var/log/mysqld.log
   ```

2. 登录MySQL数据库系统

   ```shell
   # 执行
   mysql -uroot -p
   # 解释
   # -u，登陆的用户，MySQL数据库的管理员用户同Linux一样，是root
   # -p，表示使用密码登陆
   
   # 执行完毕后输入刚刚得到的初始密码，即可进入MySQL数据库
   ```

3. 修改root密码

   ```sql
   ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '密码';	-- 密码需要符合：大于8位，有大写字母，有特殊符号，不能是连续的简单语句如123，abc
   ```

4. [扩展]，配置root的简单密码

   > 我们可以给root设置简单密码，如123456.
   >
   > 请注意，此配置仅仅是用于测试环境或学习环境的MySQL，如果是正式使用，请勿设置简单密码

   ```sql
   set global validate_password.policy=0;		# 密码安全级别低
   set global validate_password.length=4;		# 密码长度最低4位即可
   ```

   

5. 允许root远程登录，并设置远程登录密码

   > 默认情况下，root用户是不运行远程登录的，只允许在MySQL所在的Linux服务器登陆MySQL系统
   >
   > 请注意，允许root远程登录会带来安全风险

   ```sql
   # 第一次设置root远程登录，并配置远程密码使用如下SQL命令
   create user 'root'@'%' IDENTIFIED WITH mysql_native_password BY '密码!';	-- 密码需要符合：大于8位，有大写字母，有特殊符号，不能是连续的简单语句如123，abc
   
   # 后续修改密码使用如下SQL命令
   ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY '密码';
   ```

6. 退出MySQL控制台页面

   ```sql
   # 退出命令
   exit
   
   # 或者通过快捷键退出：ctrl + d
   ```

7. 检查端口

   MySQL默认绑定了3306端口，可以通过端口占用检查MySQL的网络状态

   ```shell
   netstat -anp | grep 3306
   ```

   ![image-20221012192303607](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/12/20221012192303.png)

8. 重启linux出现错误
- RROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
- 重启服务，sudo /etc/init.d/mysql restart
- 



至此，MySQL就安装完成并可用了，请妥善保存好MySQL的root密码。



## Tomcat安装部署

### 安装

Tomcat的安装非常简单，主要分为2部分：

1. 安装JDK环境
2. 解压并安装Tomcat



> 本次安装使用Tomcat版本是：9.0.76版本，需要Java（JDK）版本最低为JDK8或更高版本
>
> 课程中使用的JDK版本是：JDK8u351版本



#### 安装JDK环境

1. 下载JDK软件

   https://www.oracle.com/java/technologies/downloads

   在页面下方找到：

   <img src="https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/17/20221017163411.png" alt="image-20221017163411651" style="zoom: 67%;" />

   下载`jdk-8u351-linux-x64.tar.gz`

   ![image-20221017163440491](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/17/20221017163440.png)

   ==在弹出的页面中输入Oracle的账户密码即可下载（如无账户，请自行注册，注册是免费的）==

2. 登陆Linux系统，切换到root用户

   ![](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/17/20221017163607.png)

3. 通过FinalShell，上传下载好的JDK安装包

   ![image-20221017163706026](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/17/20221017163706.png)

4. 创建文件夹，用来部署JDK，将JDK和Tomcat都安装部署到：/export/server 内

   ```shell
   mkdir -p /export/server
   ```

5. 解压缩JDK安装文件

   ```shell
   tar -zxvf jdk-8u351-linux-x64.tar.gz -C /export/server
   ```

6. 配置JDK的软链接

   ```shell
   ln -s /export/server/jdk1.8.0_351 /export/server/jdk
   ```

7. 配置JAVA_HOME环境变量，以及将$JAVA_HOME/bin文件夹加入PATH环境变量中

   ```shell
   # 编辑/etc/profile文件
   export JAVA_HOME=/export/server/jdk
   export PATH=$PATH:$JAVA_HOME/bin
   ```

8. 生效环境变量

   ```shell
   source /etc/profile
   ```

9. 配置java执行程序的软链接

   ```shell
   # 删除系统自带的java程序
   rm -f /usr/bin/java
   # 软链接我们自己安装的java程序
   ln -s /export/server/jdk/bin/java /usr/bin/java
   ```

10. 执行验证：

    ```shell
    java -version
    javac -version
    ```



#### 解压并部署Tomcat

> Tomcat建议使用非Root用户安装并启动
>
> 可以创建一个用户：tomcat用以部署



1. 首先，放行tomcat需要使用的8080端口的外部访问权限

   > CentOS系统默认开启了防火墙，阻止外部网络流量访问系统内部
   >
   > 所以，如果想要Tomcat可以正常使用，需要对Tomcat默认使用的8080端口进行放行
   >
   > 放行有2种操作方式：
   >
   > 1. 关闭防火墙
   > 2. 配置防火墙规则，放行端口

   ```shell
   # 以下操作2选一即可
   # 方式1：关闭防火墙
   systemctl stop firewalld		# 关闭防火墙
   systemctl disable firewalld		# 停止防火墙开机自启
   
   # 方式2：放行8080端口的外部访问
   firewall-cmd --add-port=8080/tcp --permanent		# --add-port=8080/tcp表示放行8080端口的tcp访问，--permanent表示永久生效
   firewall-cmd --reload								# 重新载入防火墙规则使其生效
   ```

   > 方便起见，建议同学们选择方式1，直接关闭防火墙一劳永逸
   >
   > 防火墙的配置非常复杂，后面会视情况独立出一集防火墙配置规则的章节。

2. 以root用户操作，创建tomcat用户

   ```shell
   # 使用root用户操作
   useradd tomcat
   # 可选，为tomcat用户配置密码
   passwd tomcat
   ```

3. 下载Tomcat安装包

   ```shell
   # 使用root用户操作
   wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.76/bin/apache-tomcat-9.0.76.tar.gz
   # 如果出现https相关错误，可以使用--no-check-certificate选项
   wget --no-check-certificate https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.76/bin/apache-tomcat-9.0.76.tar.gz
   ```

   > 如果Linux内下载过慢，可以复制下载链接在Windows系统中使用迅雷等软件加速下载然后上传到Linux内即可
   >
   > 或者使用课程资料中提供的安装包

4. 解压Tomcat安装包

   ```shell
   # 使用root用户操作，否则无权限解压到/export/server内，除非修改此文件夹权限
   tar -zxvf apache-tomcat-9.0.76.tar.gz -C /export/server
   ```

5. 创建Tomcat软链接

   ```shell
   # 使用root用户操作
   ln -s /export/server/apache-tomcat-9.0.76/export/server/tomcat
   ```

6. 修改tomcat安装目录权限

   ```shell
   # 使用root用户操作，同时对软链接和tomcat安装文件夹进行修改，使用通配符*进行匹配
   chown -R tomcat:tomcat /export/server/*tomcat*
   ```

7. 切换到tomcat用户

   ```shell
   su - tomcat
   ```

8. 启动tomcat

   ```shell
   /export/server/tomcat/bin/startup.sh
   ```

9. tomcat启动在8080端口，可以检查是否正常启动成功

   ```shell
   netstat -anp | grep 8080
   ```

   ![image-20221017223814737](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/17/20221017223814.png)

10. 打开浏览器，输入：

    http://centos:8080或http://192.168.88.130:8080

    使用主机名（需配置好本地的主机名映射）或IP地址访问Tomcat的WEB页面

    ![image-20221017223915498](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/17/20221017223915.png)



至此，Tomcat安装配置完成。





## Nginx安装部署

### 简介

*Nginx* (engine x) 是一个高性能的HTTP和反向代理web服务器，同时也提供了IMAP/POP3/SMTP服务。

同Tomcat一样，Nginx可以托管用户编写的WEB应用程序成为可访问的网页服务，同时也可以作为流量代理服务器，控制流量的中转。



Nginx在WEB开发领域，基本上也是必备组件之一了。



### 安装

Nginx同样需要配置额外的yum仓库，才可以使用yum安装

> 安装Nginx的操作需要root身份



1. 安装yum依赖程序

   ```shell
   # root执行
   yum install -y yum-utils
   ```

2. 手动添加，nginx的yum仓库

   yum程序使用的仓库配置文件，存放在：`/etc/yum.repo.d`内。

   ```shell
   # root执行
   # 创建文件使用vim编辑
   vim /etc/yum.repos.d/nginx.repo
   # 填入如下内容并保存退出
   [nginx-stable]
   name=nginx stable repo
   baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
   gpgcheck=1
   enabled=1
   gpgkey=https://nginx.org/keys/nginx_signing.key
   module_hotfixes=true
   
   [nginx-mainline]
   name=nginx mainline repo
   baseurl=http://nginx.org/packages/mainline/centos/$releasever/$basearch/
   gpgcheck=1
   enabled=0
   gpgkey=https://nginx.org/keys/nginx_signing.key
   module_hotfixes=true
   ```

   > 通过如上操作，我们手动添加了nginx的yum仓库

3. 通过yum安装最新稳定版的nginx

   ```shell
   # root执行
   yum install -y nginx
   ```

4. 启动

   ```shell
   # nginx自动注册了systemctl系统服务
   systemctl start nginx		# 启动
   systemctl stop nginx		# 停止
   systemctl status nginx		# 运行状态
   systemctl enable nginx		# 开机自启
   systemctl disable nginx		# 关闭开机自启
   ```

5. 配置防火墙放行

   nginx默认绑定80端口，需要关闭防火墙或放行80端口

   ```shell
   # 方式1（推荐），关闭防火墙
   systemctl stop firewalld		# 关闭
   systemctl disable firewalld		# 关闭开机自启
   
   # 方式2，放行80端口
   firewall-cmd --add-port=80/tcp --permanent		# 放行tcp规则下的80端口，永久生效
   firewall-cmd --reload							# 重新加载防火墙规则
   ```

6. 启动后浏览器输入Linux服务器的IP地址或主机名即可访问

   http://192.168.88.130 或 http://centos

   > ps：80端口是访问网站的默认端口，所以后面无需跟随端口号
   >
   > 显示的指定端口也是可以的比如：
   >
   > - http://192.168.88.130:80
   > - http://centos:80



至此，Nginx安装配置完成。

![image-20221018143113053](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/18/20221018143113.png)







## RabbitMQ安装部署

### 简介

RabbitMQ一款知名的开源消息队列系统，为企业提供消息的发布、订阅、点对点传输等消息服务。

RabbitMQ在企业开发中十分常见，课程为大家演示快速搭建RabbitMQ环境。



### 安装

> rabbitmq在yum仓库中的版本比较老，所以我们需要手动构建yum仓库



1. 准备yum仓库

   ```shell
   # root执行
   # 1. 准备gpgkey密钥
   rpm --import https://github.com/rabbitmq/signing-keys/releases/download/2.0/rabbitmq-release-signing-key.asc
   rpm --import https://packagecloud.io/rabbitmq/erlang/gpgkey
   rpm --import https://packagecloud.io/rabbitmq/rabbitmq-server/gpgkey
   
   # 2. 准备仓库文件
   vim /etc/yum.repos.d/rabbitmq.repo
   # 填入如下内容
   ##
   ## Zero dependency Erlang
   ##
   
   [rabbitmq_erlang]
   name=rabbitmq_erlang
   baseurl=https://packagecloud.io/rabbitmq/erlang/el/7/$basearch
   repo_gpgcheck=1
   gpgcheck=1
   enabled=1
   # PackageCloud's repository key and RabbitMQ package signing key
   gpgkey=https://packagecloud.io/rabbitmq/erlang/gpgkey
          https://github.com/rabbitmq/signing-keys/releases/download/2.0/rabbitmq-release-signing-key.asc
   sslverify=1
   sslcacert=/etc/pki/tls/certs/ca-bundle.crt
   metadata_expire=300
   
   [rabbitmq_erlang-source]
   name=rabbitmq_erlang-source
   baseurl=https://packagecloud.io/rabbitmq/erlang/el/7/SRPMS
   repo_gpgcheck=1
   gpgcheck=0
   enabled=1
   # PackageCloud's repository key and RabbitMQ package signing key
   gpgkey=https://packagecloud.io/rabbitmq/erlang/gpgkey
          https://github.com/rabbitmq/signing-keys/releases/download/2.0/rabbitmq-release-signing-key.asc
   sslverify=1
   sslcacert=/etc/pki/tls/certs/ca-bundle.crt
   metadata_expire=300
   
   ##
   ## RabbitMQ server
   ##
   
   [rabbitmq_server]
   name=rabbitmq_server
   baseurl=https://packagecloud.io/rabbitmq/rabbitmq-server/el/7/$basearch
   repo_gpgcheck=1
   gpgcheck=0
   enabled=1
   # PackageCloud's repository key and RabbitMQ package signing key
   gpgkey=https://packagecloud.io/rabbitmq/rabbitmq-server/gpgkey
          https://github.com/rabbitmq/signing-keys/releases/download/2.0/rabbitmq-release-signing-key.asc
   sslverify=1
   sslcacert=/etc/pki/tls/certs/ca-bundle.crt
   metadata_expire=300
   
   [rabbitmq_server-source]
   name=rabbitmq_server-source
   baseurl=https://packagecloud.io/rabbitmq/rabbitmq-server/el/7/SRPMS
   repo_gpgcheck=1
   gpgcheck=0
   enabled=1
   gpgkey=https://packagecloud.io/rabbitmq/rabbitmq-server/gpgkey
   sslverify=1
   sslcacert=/etc/pki/tls/certs/ca-bundle.crt
   metadata_expire=300
   ```

2. 安装RabbitMQ

   ```shell
   # root执行
   yum install erlang rabbitmq-server -y
   ```

   ```shell
   Installed:
     erlang.x86_64 0:23.3.4.11-1.el7           rabbitmq-server.noarch 0:3.10.0-1.el7
   ```

3. 启动

   ```shell
   # root执行
   # 使用systemctl管控，服务名：rabbitmq-server
   systemctl enable rabbitmq-server		# 开机自启
   systemctl disable rabbitmq-server		# 关闭开机自启
   systemctl start rabbitmq-server			# 启动
   systemctl stop rabbitmq-server			# 关闭
   systemctl status rabbitmq-server		# 查看状态
   ```

4. 放行防火墙，RabbitMQ使用5672、15672、25672 3个端口

   ```shell
   # 方式1（推荐），关闭防火墙
   systemctl stop firewalld		# 关闭
   systemctl disable firewalld		# 关闭开机自启
   
   # 方式2，放行5672 25672端口
   firewall-cmd --add-port=5672/tcp --permanent		# 放行tcp规则下的5672端口，永久生效
   firewall-cmd --add-port=15672/tcp --permanent		# 放行tcp规则下的15672端口，永久生效
   firewall-cmd --add-port=25672/tcp --permanent		# 放行tcp规则下的25672端口，永久生效
   firewall-cmd --reload								# 重新加载防火墙规则
   ```

5. 启动RabbitMQ的WEB管理控制台

   ```shell
   rabbitmq-plugins enable rabbitmq_management
   ```

6. 添加admin用户，并赋予权限

   ```shell
   rabbitmqctl add_user admin 'Itheima66^'
   rabbitmqctl set_permissions -p "/" "admin" ".*" ".*" ".*"
   rabbitmqctl set_user_tags admin administrator
   ```

   

7. 浏览器打开管理控制台

   http://192.168.88.130:15672

   ![image-20221018154823983](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/18/20221018154824.png)



至此，RabbitMQ已经安装完成了。



## Redis安装部署

### 安装

1. 配置`EPEL`仓库

   > EPEL 的全称叫 Extra Packages for Enterprise Linux 。EPEL是由 Fedora 社区打造，为 RHEL 及衍生发行版如 CentOS、Scientific Linux 等提供高质量软件包的项目。装上了 EPEL之后，就相当于添加了一个第三方源。EPEL则为服务器版本提供大量的rpm包(yum程序所使用的程序安装包，类似Windows的exe)，而且大多数rpm包在官方 repository 中是找不到的。

   ```shell
   # root执行
   yum install -y epel-release
   ```

2. 安装redis

   ```shell
   # root执行
   yum install -y redis
   ```

3. 启动redis

   ```shell
   # root执行
   # 使用systemctl管控，服务名：redis
   systemctl enable redis		# 开机自启
   systemctl disable redis		# 关闭开机自启
   systemctl start redis		# 启动
   systemctl stop redis		# 关闭
   systemctl status redis		# 查看状态
   ```

4. 放行防火墙，redis使用端口6379

   ```shell
   # 方式1（推荐），关闭防火墙
   systemctl stop firewalld		# 关闭
   systemctl disable firewalld		# 关闭开机自启
   
   # 方式2，放行6379端口
   firewall-cmd --add-port=6379/tcp --permanent		# 放行tcp规则下的6379端口，永久生效
   firewall-cmd --reload	
   ```

5. 进入redis服务

   ```shell
   # 执行redis-cli
   [root@centos ~]# redis-cli
   127.0.0.1:6379> set mykey hello
   OK
   127.0.0.1:6379> get mykey
   "hello"
   127.0.0.1:6379> 
   ```



至此，redis安装完成。



## ElasticSearch安装部署

### 安装

1. 添加yum仓库

   ```shell
   # root执行
   # 导入仓库密钥
   rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch
   
   # 添加yum源
   # 编辑文件 
   vim /etc/yum.repos.d/elasticsearch.repo
   
   [elasticsearch-7.x]
   name=Elasticsearch repository for 7.x packages
   baseurl=https://artifacts.elastic.co/packages/7.x/yum
   gpgcheck=1
   gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
   enabled=1
   autorefresh=1
   type=rpm-md
   
   
   # 更新yum缓存
   yum makecache
   ```

2. 安装es

   ```shell
   yum install -y elasticsearch
   ```

3. 配置es

   ```shell
   vim /etc/elasticsearch/elasticsearch.yml
   
   # 17行，设置集群名称
   cluster.name: my-cluster
   
   # 23行，设置节点名称
   node.name: node-1
   
   # 56行，允许外网访问
   network.host: 0.0.0.0
   
   # 74行，配置集群master节点
   cluster.initial_master_nodes: ["node-1"]
   ```

4. 启动es

   ```shell
   systemctl start | stop | status | enable | disable elasticsearch
   ```

5. 关闭防火墙

   ```shell
   systemctl stop firewalld
   systemctl disable firewalld
   ```

6. 测试

   浏览器打开：http://ip:9200/?pretty

   ![image-20221025085432335](https://image-set.oss-cn-zhangjiakou.aliyuncs.com/img-out/2022/10/25/20221025085432.png)