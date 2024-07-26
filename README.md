# zerotier_planet

### 介绍
全自动安装 zerotier 搭建自建 planet 脚本

### 详细安装
centos 执行脚本：**zertotier_planet_forSelf.sh** 【zertotier_planet.sh为原脚本】
ubuntu、debain 执行脚本：zertotier_planet_debain.sh

1. 打开 http://云服务器ip或者域名:3443 用户名 admin 密码默认 password，更改密码
2. Add network 栏创建网络，点击创建的网络进去，Easy setup 栏配置地址池【可点击 Generate network address自动生成配置】
3. 客户端安装 ZeroTier 程序，运行 ZeroTier，如果之前已加入网络，disconnect 并且 forget
4. 找到脚本同目录下的 **planet** 文件，替换客户端的 planet，windows系统是 **C:\ProgramData\ZeroTier\One**
5. 重启客户端的 Zertotier 服务【windows系统】或者重启机器
6. windows 系统进入到 **C:\Program Files (x86)\ZeroTier\One**， **管理员命令行**方式执行：zerotier-cli.bat join <网络ID>
7. 回到 ztncui 页面，勾选上对应客户端的 **Authorized** 选项，再点击该栏的 IP assignment 进去查看分配的 ip地址
8. 客户端执行命令 Zerotier-cli.bat listpeers 查看具体网络下的信息，只有一个 Planet 说明正常（中间必须显示为地址，不能是-1，-1说明没有连接上）

  
### 一键安装 
`wget https://github.com/c2-don/zerotier_planet/blob/master/zertotier_planet_forSelf.sh && chmod +x zerotierplanet.sh && ./zerotierplanet.sh`  
**配置文件**  
Linux配置文件 /var/lib/zerotier-one/  
Windows 下缺省在 `C:\ProgramData\ZeroTier\One\`  

### 卸载
删除 ztncui  
rpm -e ztncui-0.8.7-1.x86_64  

删除zerotier-one服务  
sudo rpm -e zerotier-one  

删除zerotier-one文件夹，该文件夹存储了address地址，删除后再次安装会获得新的address地址  
sudo rm -rf /var/lib/zerotier-one/
