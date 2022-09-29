# Cài đặt Zabbix
### Cài đặt Zabbix Server trên CentOS 7
- Vô hiệu hoá SELinux nếu đang bật bằng cách sửa file có đường dẫn /etc/sysconfig/selinux với thuộc tính SELINUX = disabled

- Cài đặt Apache webserver
```sh
yum -y install  httpd
```

- Khởi động dịch vụ và cho phép khởi chạy cùng hệ thống
```sh
systemctl start httpd
systemctl enable httpd
```

- Cài đặt epel và remi repo
```sh
yum -y install epel-release
yum -y install http://rpms.remirepo.net/enterprise/remi-release-7.rpm
```

- Vô hiệu hoá PHP 5 repo và hiệu lực hoá PHP 7.2 repo
```sh
yum-config-manager --disable remi-php54
yum-config-manager --enable remi-php72
```

- Cài đặt PHP
```sh
yum -y install php php-pear php-cgi php-common php-mbstring php-snmp php-gd php-pecl-mysql php-xml php-mysql php-gettext php-bcmath
```

- Chỉnh sửa timezone của PHP tại file cài đặt của PHP có đường dẫn /etc/php.ini
```sh
date.timezone = Asia/Ho_Chi_Minh
```

- Cài đặt MariaDB
```sh
yum --enablerepo=remi install mariadb-server
```

- Khởi động và khởi chạy cùng hệ thống
```sh
systemctl start mariadb
systemctl enable mariadb
```

- Cấu hình bảo mật ban đầu cho MariaDB
```sh
mysql_secure_installation
```

- Đăng nhập vào MariaDB
```sh
mysql -u root -p
```

- Tạo database cho Zabbix
```sh
create database forzabbix CHARACTER SET UTF8 COLLATE UTF8_BIN;
```

- Tạo user cho database
```sh
create user 'zabbixuser'@'localhost' identified BY '123456a@';
```

- Gán quyền DB cho user và cập nhật lại quyền DB
```sh
grant all privileges on forzabbix.* to zabbixuser@localhost;
flush privileges;
quit;
```

- Cài đặt Zabbix
```sh
rpm -ivh https://repo.zabbix.com/zabbix/4.0/rhel/7/x86_64/zabbix-release-4.0-1.el7.noarch.rpm
yum -y install zabbix-server-mysql zabbix-web-mysql zabbix-agent zabbix-get
```

- Cấu hình timezone cho Zabbix httpd tại file có đường dẫn ```/etc/httpd/conf.d/zabbix.conf```
```sh
php_value date.timezone Asia/Ho_Chi_Minh (dòng 20)
```

- Khởi động lại httpd để áp dụng cấu hình
```sh
systemctl restart httpd
```

- Import MySQL tại thư mục có đường dẫn /usr/share/doc/zabbix-server-mysql-4.0.44/
```sh
cd /usr/share/doc/zabbix-server-mysql-4.0.44/
zcat create.sql.gz | mysql -u zabbixuser -p forzabbix
```

- Cấu hình cho Zabbix server tại file có đường dẫn /etc/zabbix/zabbix_server.conf
```sh
DBHost=localhost (dòng 91)
DBName=forzabbix (dòng 100)
DBUser=zabbixuser (dòng 116)
DBPassword=123456a@ (dòng 124)
```

- Khởi động lại dịch vụ Zabbix Server
```sh
systemctl restart zabbix-server
systemctl enable zabbix-server
```

- Truy cập trang web có đường dẫn ```http://<ip_address>/zabbix``` để tiếp tục thiết lập Zabbix

![image](./image/Zabbix%201.png)

- Kiểm tra các điều kiện tiên quyết liên quan tới thiết lập cấu hình PHP, nếu mọi thứ đã OK, chuyển sang bước tiếp theo, nếu không, sửa file ```/etc/php.ini``` với những giá trị yêu cầu của Zabbix, sau đó khởi động lại ```zabbix-server``` và ```httpd```

![image](./image/Zabbix%202.png)

- Cấu hình kết nối DB

![image](./image/Zabbix%203.png)

- Cấu hình tên host và port

![image](./image/Zabbix%204.png)

- Kiểm tra lại các thông số thiết lập

![image](./image/Zabbix%205.png)

- Cấu hình thành công

![image](./image/Zabbix%206.png)

### Cài đặt Zabbix Agent để quản lý máy host
- Tải về Zabbix Agent
```sh
rpm -Uvh https://repo.zabbix.com/zabbix/4.4/rhel/7/x86_64/zabbix-agent-4.4.0-1.el7.x86_64.rpm
```

- Cài đặt Zabbix Agent
```sh
yum -y install zabbix-agent
```

- Cấu hình Zabbix Agent tại file có đường dẫn ```/etc/zabbix/zabbix_agentd.conf```
```sh
Server=<địa-chỉ-ip-của-zabbix-server> (dòng 98)
ServerActive=<địa-chỉ-ip-của-zabbix-server> (dòng 139)
Hostname=<tên-server> (dòng 150)
```

- Mở port 10050 nếu đang sử dụng firewall

- Khởi động lại ```zabbix-agent```
```sh
systemctl restart zabbix-agent
systemctl enable zabbix-agent
```

- Truy cập Zabbix Server để kiểm tra hoạt động của Zabbix Agent
```sh
zabbix_get -s <địa-chỉ-ip-của-zabbix-agent> -k agent.version
```

- Truy cập vào trang quản lý Zabbix Server để tiến hành thêm host, chọn **Configuration** -> **Hosts**

![image](./image/Zabbix%207.png)

- Chọn **Create host**

![image](./image/Zabbix%208.png)

- Tại tab **Host**, nhập các thông tin như **Hostname**, **Groups**, **Agent interfaces**

![image](./image/Zabbix%209.png)

- Tại tab **Templates**, tại **Link new templates**, nhập **Template App Zabbix Agent**, sau đó chọn **Add** và chọn **Add** dưới cùng để thêm host

![image](./image/Zabbix%2010.png)

- Host được thêm thành công

![image](./image/Zabbix%2011.png)