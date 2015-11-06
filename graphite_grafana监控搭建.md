#Centos下安装graphite + grafana监控系统

##前言
安装graphite依赖版本问题，官网文档不明确，特此记录。  
共享给那些搭建监控软件还在纠结中的朋友
cairo 收集  
graphite 展示  
grafana 好用及漂亮的图形展示工具(可以添加多种数据源包括:graphite)  
软件安装位置为 /opt  

##安装需要软件包
软件包下载地址：http://yunpan.cn/cLKiyBKLIkt8P （提取码：457c）

```Bash
sudo yum install cairo-devel
sudo pip install graphite-project-ceres-dba08b0.tar.gz
sudo pip install Twisted-11.1.0.tar.bz2
sudo pip install txAMQP-0.6.2.tar.gz
sudo pip install whisper-0.9.13.tar.gz
sudo pip install Django-1.4.8.tar.gz
sudo pip install django-tagging-0.3.3.tar.gz
sudo pip install carbon-0.9.13.tar.gz
sudo pip install graphite-web-0.9.13.tar.gz
sudo rpm -ivh grafana-2.5.0-1.x86_64.rpm
sudo /sbin/chkconfig --add grafana-server
```

##配置
```Bash
cd /opt/graphite/conf
sudo mv aggregation-rules.conf.example aggregation-rules.conf
sudo mv blacklist.conf.example blacklist.conf
sudo mv carbon.amqp.conf.example carbon.amqp.conf
sudo mv carbon.conf.example carbon.conf
sudo mv dashboard.conf.example dashboard.conf
sudo mv graphTemplates.conf.example graphTemplates.conf
sudo mv graphite.wsgi.example graphite.wsgi
sudo mv relay-rules.conf.example relay-rules.conf
sudo mv rewrite-rules.conf.example rewrite-rules.conf
sudo mv storage-aggregation.conf.example storage-aggregation.conf
sudo mv storage-schemas.conf.example storage-schemas.conf
sudo mv whitelist.conf.example whitelist.conf
```
###添加数据库支持
将graphite.db拷贝到/opt/graphite/storage 目录中

###修支持UDP模式
修改UDP模式，通信不需要握手非阻塞。即使监控系统挂掉了也不会影响业务系统的正常运行
```Bash
sudo vim /opt/graphite/conf/carbon.conf
ENABLE_UDP_LISTENER = True
```
#启动所需要的服务
```Bash
sudo python /opt/graphite/bin/carbon-cache.py start
sudo python /opt/graphite/webapp/graphite/manage.py runserver 0.0.0.0:8020  >/dev/null 2>&1 &
sudo service grafana-server start
```
grafana  登录名：admin 密码：admin  
graphite 登录名：zgnlihui 密码：zgnlihui
