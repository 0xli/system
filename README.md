# system
OS related
```
lsb_release and lshw
yum install -y redhat-lsb
yum install -y lshw
```
# yum repo
```
centos 6
curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-6.repo
curl -o /etc/yum.repos.d/CentOS-Base.repo https://www.xmpan.com/Centos-6-Vault-Aliyun.repo

yum makecache
yum update -y
if error 
yum -y remove qpid-cpp-client

https://www.cnblogs.com/echola/p/9970999.html
https://www.cnblogs.com/thatsit/p/5233349.html
```
#open port - firewall

firewall-cmd --zone=public --add-port=3000/tcp --permanent

firewall-cmd --reload

Use this command to find your active zone(s):

firewall-cmd --get-active-zones

It will say either public, dmz, or something else. You should only apply to the zones required.

In the case of public try:

firewall-cmd --zone=public --add-port=2888/tcp --permanent

Then remember to reload the firewall for changes to take effect.

firewall-cmd --reload

Otherwise, substitute public for your zone, for example, if your zone is dmz:

firewall-cmd --zone=dmz --add-port=2888/tcp --permanent

#IPTABLES
https://stackoverflow.com/questions/19034542/how-to-open-port-in-centos


First, you should disable selinux, edit file /etc/sysconfig/selinux so it looks like this:
```
SELINUX=disabled
SELINUXTYPE=targeted
```
Save file and restart system.

Then you can add the new rule to iptables:

iptables -A INPUT -m state --state NEW -p tcp --dport 8080 -j ACCEPT

and restart iptables with /etc/init.d/iptables restart

### sftp
```
sftp -oPort=2323 xxx@gxxxxx
rsync -avz -e 'ssh -p 2222' /data/filestore liwei@gfax.org:/home/liwei/data/GFAX/filestore 
```
### v2ray

https://github.com/v2fly/fhs-install-v2ray

// 安裝執行檔和 .dat 資料檔
# bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh)
