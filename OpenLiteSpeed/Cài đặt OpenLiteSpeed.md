# Cài đặt OpenLiteSpeed
- Cập nhật các gói phần mềm lên phiên bản mới nhất bằng lệnh

```sh
yum install epel-release -y
yum update -y
```

- Cài đặt mã nguồn OpenLiteSpeed

```sh
rpm -ivh http://rpms.litespeedtech.com/centos/litespeed-repo-1.1-1.el7.noarch.rpm
yum install openlitespeed -y
```

- Cài đặt PHP 7.4

```sh
yum install lsphp74 lsphp74-gd lsphp74-json lsphp74-common lsphp74-process lsphp74-mbstring lsphp74-mysqlnd lsphp74-xml lsphp74-opcache lsphp74-mcrypt lsphp74-pdo lsphp74-imap lsphp74-bcmath lsphp74-pecl-memcache lsphp74-pecl-memcached lsphp74-pecl-redis lsphp74-pgsql lsphp74-zip -y
```

- Thiết lập tài khoản Admin cho OpenLiteSpeed WebAdmin GUI: Nhập thông tin đăng ký tài khoản

```sh
/usr/local/lsws/admin/misc/admpass.sh
```

![image](./image/OLS%201.png)

- Mở port cho OpenLiteSpeed: OpenLiteSpeed hoạt động trên cổng 7080

```sh
firewall-cmd --zone=public --add-port=7080/tcp --permanent
firewall-cmd --reload
```

- Truy cập trang web và đăng nhập

![image](./image/OLS%202.png)

- Giao diện chính

![image](./image/OLS%203.png)