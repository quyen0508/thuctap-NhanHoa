# LEMP
### Giới thiệu về LEMP
LEMP là một bộ ứng dụng và hệ điều hành bao gồm L- Linux, E - Nginx, M - MySQL và P - PHP/Perl/Python

### Các thành phần của LEMP
- Linux: Là hệ điều hành làm cơ sở nền tảng cho các phần mềm khác chạy trên nó
- Nginx: Là phần mềm web server
- MySQL: Là hệ quản trị cơ sở dữ liệu giúp lưu trữ thông tin về website
- PHP/Python/Perl:
    - PHP: ngôn ngữ lập trình trang web
    - Python: là ngôn ngữ lập trình bậc cao, có cấu trúc rõ ràng, dễ tiếp cận

### Cài đặt các thành phần của LEMP
##### Cài đặt Nginx
- Cài đặt EPEL repo trước để cài đặt nginx
```sh
yum install epel-release -y
```
- Cài đặt gói phần mềm nginx
```sh
yum install nginx -y
```
- Khởi động dịch vụ nginx và cài đặt tự động chạy khi khởi động hệ điều hành
```sh
systemctl start nginx
systemctl enable nginx
```
- Mở cổng 80 trên CentOS
    - Để mở cổng, sử dụng lệnh
```sh
firewall-cmd --zone=public --add-port=80/tcp --permanent
```
    - Để khởi động lại firewall giúp thay đổi phía trên có hiệu lực, sư dụng lệnh
```sh
firewall-cmd --reload
```

- Kết quả khi truy cập trang web trên trình duyệt
![image](./image/LEMP%201.png)

###### Sử dụng VirtualHost để tạo nhiều website
- Tạo các thư mục sites-available và sites-enabled tại /etc/nginx/ để quản lý các virtualhost thuận tiện
```sh
mkdir sites-available
mkdir sites-enabled
```
- Cấu hình file nginx.conf để nhận cấu hình của các trang trong sites-enabled bằng cách thêm ```include /etc/nginx/sites-enabled/*.conf;``` vào cuối file
![image](./image/LEMP%202.png)

- Tạo file cấu hình cho virtualhost tại thư mục sites-available có nội dung
```sh
server {
      listen 80;
      server_name quyenweb1.xyz www.quyenweb1.xyz;
      location / {
            root /var/www/web1;
            index index.html;
            try_files $uri $uri/ =404;
      }
}
```
![image](./image/LEMP%203.png)
```sh
server {
      listen 80;
      server_name quyenweb2.xyz www.quyenweb2.xyz;
      location / {
            root /var/www/web2;
            index index.html;
            try_files $uri $uri/ =404;
      }
}
```
![image](./image/LEMP%204.png)

- Tạo các file html trong thư mục mỗi trang web tại thư mục /var/www/
![image](./image/LEMP%205.png)
![image](./image/LEMP%206.png)

- Tạo soft link cấu hình các trang web từ thư mục sites-available sang sites-enabled để kích hoạt các trang web
```sh
ln -s /etc/nginx/sites-available/web1.conf /etc/nginx/sites-enabled/web1.conf
ln -s /etc/nginx/sites-available/web2.conf /etc/nginx/sites-enabled/web2.conf
```

- Khởi động lại dịch vụ nginx để cập nhật cấu hình
```sh
systemctl restart nginx
```

- Kết quả truy cập bằng trình duyệt trên máy ảo Windows 10 Pro đã thêm địa chỉ trong file hosts
![image](./image/LEMP%207.png)
![image](./image/LEMP%208.png)

##### Cài đặt MySQL
Tham khảo tại [LAMP - Cài đặt MySQL](https://github.com/quyen0508/thuctap-NhanHoa/blob/main/LAMP/LAMP.md#c%C3%A0i-%C4%91%E1%BA%B7t-mysql)

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
yum install php php-common php-opcache php-mcrypt php-cli php-gd php-curl php-mysqlnd php-mysql php-xml php-soap php-xmlrpc php-mbstring php-json php-fpm
```
- Tạo file index.php tại đường dẫn /var/www/html/ có nội dung
```<?php phpinfo(); ?>```

- Tạo file cấu hình VirtualHost cho PHP là phpweb.conf tại đường dẫn có nội dung
```sh
server {
        listen   80;

        root /var/www/html;
        index index.php index.html index.htm;
        server_name  xqn.com www.xqn.com;

        location / {
                try_files $uri $uri/ /index.html;
        }

	error_page 404 /404.html;
        error_page 500 502 503 504 /50x.html;
        location = /50x.html {
              root /usr/share/nginx/www;
        }

	location ~ .php$ {
                try_files $uri =404;
                fastcgi_pass 127.0.0.1:9000;
                fastcgi_index index.php;
                fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
                include fastcgi_params;
        }
}
```

- Tạo đường dẫn file sang thư mục sites-enabled để kích hoạt trang web
```sh
ln -s /etc/nginx/sites-available/phpweb.conf /etc/nginx/sites-enabled/phpweb.conf
```

- Khởi động lại các dịch vụ
```sh
systemctl restart nginx
systemctl restart php-fpm
```

- Kiểm tra kết quả bằng cách truy cập vào trang web www.xqn.com
![image](./image/LEMP%209.png)

### Cài đặt WordPress
Tham khảo tại [LAMP - Cài đặt WordPress](https://github.com/quyen0508/thuctap-NhanHoa/blob/main/LAMP/LAMP.md#c%C3%A0i-%C4%91%E1%BA%B7t-wordpress)