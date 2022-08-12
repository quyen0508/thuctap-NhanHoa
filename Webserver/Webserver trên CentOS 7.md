# Webserver trên CentOS 7
Sử dụng tài khoản root để thực hiện các lệnh
### Cập nhật CentOS
Sử dụng lệnh
```sh
yum update
```
để lấy danh sách các gói phần mềm cũng như thông báo các bản cập nhật của các gói phần mềm

### Cài đặt ```httpd```
Sử dụng lệnh
```sh
yum -y install httpd
```
để cài đặt httpd và các gói cần thiết

### Cấu hình file /etc/httpd/conf/httpd.conf
Đặt tên trang web tại dòng 95

![image](./image/CentOS%201.png)

### Tạo file index.html trong thư mục /var/www/html
Nội dung trang web:

![image](./image/CentOS%202.png)

### Khởi động lại Apache:
Sử dụng lệnh
```sh
systemctl restart httpd
```
Ngoài ra còn một vài lệnh khác liên quan tới ```systemctl``` để quản lý Apache Service:
- ```systemctl start httpd``` dùng để khởi động Apache
- ```systemctl stop httpd``` dùng để dừng Apache
- ```systemctl reload httpd``` đùng để chạy lại Apache khi thay đổi cấu hình
- ```systemctl enable httpd``` dùng để tự động chạy dịch vụ Apache khi khởi động hệ điều hành
- ```systemctl disable httpd``` dùng để ngưng tự động khởi chạy dịch vụ Apache khi khởi động hệ điều hành

### Mở cổng 80 trên CentOS
Sử dụng lệnh
```sh
firewall-cmd --zone=public --add-port=80/tcp --permanent
```
để mở cổng
Sư dụng lệnh
```sh
firewall-cmd --reload
```
để khởi động lại firewall giúp thay đổi phía trên có hiệu lực

### Cấu hình các VirtualHost
Tạo các file index.html với mỗi trang web nằm trong các thư mục tương ứng VirtualHost tại /var/www/
- Nội dung trang www.quyennxweb1.com:

![image](./image/CentOS%205.png)
- Nội dung trang www.quyennxweb2.com:

![image](./image/CentOS%206.png)
Thêm dòng
```sh
IncludeOptional sites-enabled/*.conf
```
vào cuối file /etc/httpd/conf/httpd.conf để thêm cấu hình VirtualHost vào file cấu hình chính của httpd
Tạo các file cấu hình của các VirtualHost trong thư mục /etc/httpd/sites-available:
- Cấu hình trang web www.quyennxweb1.com

![image](./image/CentOS%203.png)
- Cấu hình trang web www.quyennxweb2.com

![image](./image/CentOS%204.png)
Để kích hoạt các VirtualHost, tạo lối tắt các file cấu hình VirtualHost từ thư mục /etc/httpd/sites-available sang /etc/httpd/sites-enabled bằng lệnh:
```sh
ln -s /etc/httpd/sites-available/web1.conf /etc/httpd/sites-enabled/web1.conf
ln -s /etc/httpd/sites-available/web2.conf /etc/httpd/sites-enabled/web2.conf
```
Khởi động lại dịch vụ httpd để cập nhật cấu hình bằng lệnh
```sh
systemctl restart httpd
```

### Kết quả thực hiện
- Dùng máy ảo chạy Windows 10 Pro để truy cập các trang web trên
- Trước tiên phải sửa file host trỏ các trang web trên vào địa chỉ của máy ảo chạy CentOS 7:

![image](./image/CentOS%2010.png)
- Trang web chính:

![image](./image/CentOS%207.png)
- Trang web VirtualHost 1:

![image](./image/CentOS%208.png)
- Trang web VirtualHost 2:

![image](./image/CentOS%209.png)