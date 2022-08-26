# Các thao tác với OpenLiteSpeed
### Thêm website trong Webserver OpenLiteSpeed
- Truy cập **Virtual Hosts**, tại mục **Virtual Host List** chọn **Add**

![image](./image/OLS%2014.png)

- Điền các thông tin của Virtual Host

![image](./image/OLS%2015.png)

- Khi nhấn **Save** sẽ báo lỗi tại **Config File**, chọn **CLICK TO CREATE** để tạo file cấu hình và chọn lại **Save** để lưu cấu hình Virtual Host

![image](./image/OLS%2016.png)

- Chuyển sang tab **General**, chỉnh sửa mục **General**

![image](./image/OLS%2017.png)

- Chỉnh sửa mục **Index Files**

![image](./image/OLS%2018.png)

- Chuyển sang tab **Log**, chỉnh sửa mục **Virtual Host Log**

![image](./image/OLS%2019.png)

- Chỉnh sửa mục **Access Log**

![image](./image/OLS%2020.png)

- Chuyển sang tab **Security**, chỉnh sửa mục **Access Control**

![image](./image/OLS%2021.png)

- Truy cập **Listeners**, chọn **View** tại mục **Default** và chỉnh sửa **Virtual Host Mappings**

![image](./image/OLS%2022.png)

- Truy cập bằng Terminal vào server, tạo các thư mục bằng lệnh
```sh
mkdir /usr/local/lsws/web1.quyennx.xyz
mkdir /usr/local/lsws/web1.quyennx.xyz/{html,logs}
```

- Tạo và thêm nội dung cho file index.html tại đường dẫn /usr/local/lsws/web1.quyennx.xyz/html/
```sh
nano /usr/local/lsws/web1.quyennx.xyz/html/index.html
```

- Khởi động lại OpenLiteSpeed để áp dụng cấu hình

![image](./image/OLS%2023.png)

- Kết quả truy cập website trên trình duyệt

![image](./image/OLS%2024.png)

### Cài đặt WordPress trong Webserver OpenLiteSpeed
##### Cấu hình CSDL
- Truy cập MariaDB với user root
```sh
mysql -u root -p
```

- Tạo một cơ sở dữ liệu WordPress
```sh
CREATE DATABASE wp1;
```

- Tạo một user mới
```sh
CREATE USER 'wpuser1'@'localhost' IDENTIFIED BY '123456a@';
```

- Cấp quyền truy cập CSDL WordPress cho user vừa mới tạo
```sh
GRANT ALL PRIVILEGES ON wp1.* TO 'wpuser1'@'localhost' IDENTIFIED BY '123456a@';
```

- Cập nhật lại thông tin về quyền CSDL và thoát
```sh
FLUSH PRIVILEGES;
exit;
```

##### Cài đặt WordPress
- Chuyển thư mục làm việc về /usr/local/lsws/web1.quyennx.xyz/html/
``sh
cd /usr/local/lsws/web1.quyennx.xyz/html
```

- Tải phiên bản WordPress mới nhất
```sh
wget http://wordpress.org/latest.tar.gz
```

- Giải nén file vừa tải về
```sh
tar -zxvf latest.tar.gz
```

- Di chuyển nội dung trong thư mục vừa giải nén ra thư mục gốc html và xóa thư mục wordpress rỗng
```sh
mv wordpress/* /usr/local/lsws/web1.quyennx.xyz/html && rm -rf wordpress
```

- Cấp quyền cho thư mục
```sh
chown -R nobody:nobody /usr/local/lsws/web1.quyennx.xyz/html
```

##### Cấu hình WordPress hoạt động với OpenLiteSpeed
- Cấu hình ban đầu cho WordPress

![image](./image/OLS%2025.png

![image](./image/OLS%2026.png

![image](./image/OLS%2027.png

![image](./image/OLS%2028.png

![image](./image/OLS%2029.png

![image](./image/OLS%2030.png

- Đăng nhập vào WordPress, chọn **Plugins** -> **Add New**

![image](./image/OLS%2031.png)

- Tìm **LiteSpeed Cache** và tiến hành cài đặt bằng cách chọn **Install**, sau khi cài đặt xong, chọn **Active** để kích hoạt plugin

![image](./image/OLS%2032.png)

- Khởi động lại OpenLiteSpeed bằng cách chọn **Grateful Restart**

- LiteSpeed Cache Dashboard trên WordPress

![image](./image/OLS%2033.png)

### Cài đặt SSL Let's Encrypt
##### Cài đặt Certbot
- Cài EPEL Repository
```sh
rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```

- Cài đặt Certbot
```sh
yum install certbot -y
```

##### Tạo chứng chỉ Let's Encrypt bằng Certbot
```sh
certbot certonly --webroot -w /usr/local/lsws/web1.quyennx.xyz/html/ -d web1.quyennx.xyz
```

![image](./image/OLS%2034.png)

- Các file chứng chỉ được lưu tại /etc/letsencrypt/live/tên-miền

![image](./image/OLS%2035.png)

##### Cấu hình SSL trên OpenLiteSpeed
- Tại trang quản lý của OpenLiteSpeed, chọn **Listeners**, sau đó chọn **Add** để mở thêm cổng

![image](./image/OLS%2036.png)

- Truy cập vào Listener vừa tạo, tại tab **General**, sửa mục **Virtual Host Mappings**

![image](./image/OLS%2037.png)

- Chuyển sang tab **SSL**, sửa mục **SSL Private Key & Cerificate**

![image](./image/OLS%2038.png)

- Sửa mục **SSL Protocol**

![image](./image/OLS%2039.png)

- Kết quả khi truy cập trang web

![image](./image/OLS%2040.png)

##### Thao tác gia hạn chứng chỉ Let's Encrypt
```sh
crontab -e
```

- Thêm vào cuối file với nội dung
```sh
30 4 * * * /usr/bin/certbot renew --quiet
```
Lệnh gia hạn sẽ được chạy vào lúc 4h30 mỗi ngày

##### Cấu hình SSL bằng WordPress
- Ngoài cách sử dụng dòng lệnh, trên WordPress có sẵn một plugin tên là ```Really Simple SSL```
- Để sử dụng cần tìm kiếm tại kho Plugin và tiến hành cài đặt -> kích hoạt plugin

![image](./image/OLS%2041.png)