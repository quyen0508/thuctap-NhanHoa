# Cài đặt chứng chỉ SSL có trả phí
### Đăng ký chứng chỉ SSL trên ssls.com
- Đăng ký thông tin theo chỉ dẫn của website
- Ở bước xác thực SSL, chọn xác thực bằng phương thức File-based
- Sao chép file có tên ```6F302D7C394DF1870408DD08C9D15B16.txt``` vào đường dẫn /var/www/quyennx/.well-known/pki-validation bằng lệnh để xác nhận mình là chủ sở hữu của tên miền

![image](./image/SSLs%202.png)
```sh
scp C:\Users\thuctap\Downloads\6F302D7C394DF1870408DD08C9D15B16.txt root@quyennx.xyz:/var/www/quyennx.xyz/.well-known/pki-validation
```

- Chọn ```Confirm file upload``` để SSLs xác minh file

![image](./image/SSLs%201.png)
- Chờ thời gian xác thực lần cuối trước khi được cấp chứng chỉ SSL

![image](./image/SSLs%203.png)
- Sau khi được xác thực thành công, tải file SSL về và tiến hành cài đặt

![image](./image/SSLs%204.png)

- Copy tất cả các file nhận được từ website SSLs vào cùng thư mục đặt tên là ```ssl``` và copy thư mục này vào đường dẫn /etc/
```sh
scp -r C:\Users\thuctap\Downloads\ssl root@quyennx.xyz:/etc/
```

![image](./image/SSLs%205.png)

- Kết hợp các file chứng chỉ thành 1, sử dụng lệnh
```sh
cat quyennx.xyz.crt quyennx.xyz.ca-bundle >> ssl_bundle.crt
```

##### Cài đặt trên NGINX server
- Mở file cấu hình website tại đường dẫn /etc/nginx/sites-available và thay đổi nội dung thành

![image](./image/SSLs%206.png)
```sh
server {
listen 443;
ssl on;
ssl_certificate /etc/ssl/ssl_bundle.crt;
ssl_certificate_key /etc/ssl/quyennx.xyz.key;

server_name quyennx.xyz www.quyennx.xyz;
location / {
            root /var/www/quyennx.xyz;
            index index.html;
            try_files $uri $uri/ =404;
      }
}
```
Trong đó:
- ```listen 443;```: trang web lắng nghe trên cổng 443 (https)
- ```ssl on;```: bật ssl
- ```ssl_certificate /etc/ssl/ssl_bundle.crt;```: xác định đường dẫn của chứng chỉ SSL
- ```ssl_certificate_key /etc/ssl/quyennx.xyz.key;```: xác định đường dẫn khóa (key) của chứng chỉ SSL

- Khởi động lại nginx bằng lệnh
```sh
systemctl restart nginx
```
- Kết quả:
![image](./image/SSLs%207.png)

##### Cài đặt trên Apache server
- Mở file cấu hình website tại đường dẫn /etc/httpd/sites-available và thay đổi nội dung thành

![image](./image/SSLs%208.png)
```sh
<VirtualHost *:443>
     ServerName www.quyennx.xyz
     ServerAlias quyennx.xyz
     DocumentRoot /var/www/quyennx.xyz
     DirectoryIndex index.html

     SSLEngine on
     SSLCertificateFile /etc/ssl/ssl_bundle.crt
     SSLCertificateKeyFile /etc/ssl/quyennx.xyz.key
     SSLCertificateChainFile /etc/ssl/quyennx.xyz.ca-bundle
</VirtualHost>
```
Trong đó:
- ```SSLCertificateFile /etc/ssl/ssl_bundle.crt```: xác định đường dẫn của chứng chỉ SSL
- ```SSLCertificateKeyFile /etc/ssl/quyennx.xyz.key```: xác định đường dẫn khóa (key) của chứng chỉ SSL
- ```SSLCertificateChainFile /etc/ssl/quyennx.xyz.ca-bundle```: đường dẫn tới file CA-Bundle

- Thêm lệnh vào cuối file httpd.conf tại đường dẫn /etc/httpd/conf/httpd.conf
![image](./image/SSLs%209.png)
Với ```SSLUseStapling on``` và ```SSLStaplingCache shmcb:/tmp/stapling_cache(128000)``` giúp cải thiện hiệu năng bằng cách cung cấp cập nhật trạng thái của chứng chỉ tới client

- Khởi động lại apache bằng lệnh
```sh
systemctl restart httpd
```

- Kết quả tương tự như khi cài với NGINX server

##### Cài đặt trên Windows Server với IIS
- Truy cập địa chỉ
```sh
https://decoder.link/converter
```
để chuyển đổi file PKCS#7 thành PKCS#12 (.pfx) dùng để cài đặt chứng chỉ trên Windows

![image](./image/SSLs%2010.png)

- Giải nén file vừa tải được 1 file .pfx

![image](./image/SSLs%2011.png)

- Mở IIS Manager chọn tên máy tính rồi chọn Server Certificates

![image](./image/SSLs%2012.png)

- Chọn Import

![image](./image/SSLs%2013.png)

- Chọn file chứng chỉ đã giải nén trước đó và nhập mật khẩu

![image](./image/SSLs%2014.png)

- Chọn trang web cần cài chứng chỉ SSL, chuột phải chọn Edit Bindings...

![image](./image/SSLs%2015.png)

- Chọn Add

![image](./image/SSLs%2016.png)

- Chọn https, nhập tên host name và chọn chứng chỉ vừa được nhập vào

![image](./image/SSLs%2017.png)

- Kết quả

![image](./image/SSLs%2018.png)