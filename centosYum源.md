1.首先我们需要安装一个叫se”的软件包，这个软件包会自动配置yum的软件仓库。当然你也可以不安装这个包，自己配置软件仓库也是一样的。
#用于RHEL5系列
wget http://download.fedoraproject.org/pub/epel/5/i386/epel-release-5-4.noarch.rpm
rpm -ivh epel-release-5-4.noarch.rpm
#用于RHEL6系列
wget http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-5.noarch.rpm
rpm -ivh epel-release-6-5.noarch.rpm
2. 安装完成之后你就可以直接使用yum来安装额外的软件包了
yum clean all
yum install nginx pure-ftpd
还有一种更加便捷的方法就是直接自己手工添加软件仓库配置文件
vi /etc/yum.repos.d/epel.repo
[epel]
name=epel
mirrorlist=http://mirrors.fedoraproject.org/mirrorlist?repo=epel-$releasever&arch=$basearch
enabled=1
gpgcheck=0
添加完毕之后：
yum clean all && yum update”epel-release”的软件包，这个软件包会自动配置yum的软件仓库。当然你也可以不安装这个包，自己配置软件仓库也是一样的。
#用于RHEL5系列
wget http://download.fedoraproject.org/pub/epel/5/i386/epel-release-5-4.noarch.rpm
rpm -ivh epel-release-5-4.noarch.rpm
#用于RHEL6系列
wget http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-5.noarch.rpm
rpm -ivh epel-release-6-5.noarch.rpm
2. 安装完成之后你就可以直接使用yum来安装额外的软件包了
yum clean all
yum install nginx pure-ftpd
还有一种更加便捷的方法就是直接自己手工添加软件仓库配置文件
vi /etc/yum.repos.d/epel.repo
[epel]
name=epel
mirrorlist=http://mirrors.fedoraproject.org/mirrorlist?repo=epel-$releasever&arch=$basearch
enabled=1
gpgcheck=0
添加完毕之后：
yum clean all && yum update
