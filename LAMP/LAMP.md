# LAMP
### Giới thiệu về LAMP
LAMP là một bộ ứng dụng và hệ điều hành tạo môi trường webserver viết tắt của L - Linux, A - Apache, M - MySQL và P - PHP/Python/Perl

### Các thành phần của LAMP
- Linux: Là hệ điều hành làm cơ sở nền tảng cho các phần mềm khác chạy trên nó
- Apache: Là phần mềm web server
- MySQL: Là phần mềm cung cấp cơ sở dữ liệu giúp lưu trữ thông tin về website
- PHP/Python/Perl:
    - PHP: ngôn ngữ lập trình trang web
    - Python: là ngôn ngữ lập trình bậc cao, có cấu trúc rõ ràng, dễ tiếp cận

### Cài đặt các thành phần của LAMP
Cài đặt Apache, MySQL và PHP trên CentOS 7
##### Cài đặt Apache
Tham khảo tại tài liệu Webserver trên CentOS 7
```sh
https://github.com/quyen0508/thuctap-NhanHoa/blob/main/Webserver/Webserver%20tr%C3%AAn%20CentOS%207.md
```
Tạo một trang web VirtualHost có địa chỉ www.quyennx.com có đường dẫn chứa file index.html là /var/www/html/
##### Cài đặt MySQL
- Sử dụng MariaDB để thay thế của MySQL
- Sử dụng lệnh
```sh
yum install mariadb-server mariadb -y
```
để cài đặt MariaDB
- Khởi chạy dịch vụ cho ứng dụng
```sh
systemctl start mariadb
systemctl enable mariadb
```
- Bảo mật MariaDB bằng dòng lệnh
```sh
mysql_secure_installation
```
- Tiếp tục làm theo hướng dẫn để đặt mật khẩu bảo vệ, cân nhắc loại bỏ người dùng ẩn danh, không cho phép đăng nhập từ xa và bỏ cơ sở dữ liệu test

##### Cài đặt PHP
- Cài đặt epel-release bằng lệnh
```sh
yum -y install epel-release
```
- Thêm remi repo
```sh
rpm -Uvh http://rpms.remirepo.net/enterprise/remi-release-7.rpm
```
- Dùng lệnh ```yum update``` để lấy danh sách gói phần mềm
- Cài đặt PHP 7.3
```sh
yum-config-manager --enable remi-php73
yum install php php-common php-opcache php-mcrypt php-cli php-gd php-curl php-mysqlnd php-mysql php-xml php-soap php-xmlrpc php-mbstring php-json
```
- Tạo file info.php tại đường dẫn /var/www/html/ có nội dung
```<?php phpinfo(); ?>```
- Kết quả trang web truy cập tại máy ảo Windows 10 Pro bằng địa chỉ 192.168.14.128/info.php
![image](./image/LAMP%201.png)

### Cài đặt WordPress
##### Tạo cơ sở dữ liệu trong MySQL
- Đăng nhập vào mysql bằng lệnh
```sh
mysql -u root -p
```
- Tạo cơ sở dữ liệu wordpress
```sh
CREATE DATABASE wordpress;
```
- Tạo người dùng mới
```sh
CREATE USER quyennx@localhost IDENTIFIED BY '123456';
```
- Cấp quyền cơ sở dữ liệu cho người dùng vừa tạo
```sh
GRANT ALL PRIVILEGES ON wordpress.* TO quyennx@localhost IDENTIFIED BY '123456';
```
- Cập nhật lại quyền và thoát
```sh
FLUSH PRIVILEGES;
exit
```
- Cài đặt ```wget`` nếu chưa có
```sh
yum install wget
```
- Tải xuống file cài wordpress
```sh
wget http://wordpress.org/latest.tar.gz
```
- Giải nén file cài
```sh
tar -xzvf latest.tar.gz
```
- Copy file trong thư mục wordpress vào thư mục /etc/www/html
```sh
rsync -avP ~/wordpress/ /var/www/html/
```
- Cấp quyền apache cho thư mục wordpress
```sh
chown -R apache:apache /var/www/html/*
```
- Tạo một file cấu hình từ file cấu hình mẫu
```sh
cp wp-config-sample.php wp-config.php
```
- Chỉnh sửa file cấu hình
```sh
vi wp-config.php
```
Cấu hình tên cơ sở dữ liệu, tên người dùng và mật khẩu đã thiết lập trước đó
![image](./image/LAMP%202.png)
- Khởi động lại dịch vụ ```httpd```
```sh
systemctl reload httpd
```

##### Cấu hình WordPress bằng trình duyệt
- Sử dụng máy ảo Windows 10 Pro truy cập trang web http://www.quyennx.com/wp-admin/install.php
- Cài đặt ngôn ngữ
![image](./image/LAMP%203.png)
- Cài đặt các thông tin
![image](./image/LAMP%204.png)
- Đăng nhập vào trang quản lý
![image](./image/LAMP%205.png)
- Giao diện trang quản trị WordPress
![image](./image/LAMP%206.png)