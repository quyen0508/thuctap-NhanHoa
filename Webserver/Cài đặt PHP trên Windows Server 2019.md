# Cài đặt PHP trên Windows Server 2019
### Tải xuống các phần mềm
- Tại xuống PHP tại đường dẫn
```sh
https://windows.php.net/download/
```
Chọn phiên bản VS16 x64 Non Thread Safe và tải file zip
- Tải xuống Wincache tại đường dẫn
```sh
https://sourceforge.net/projects/wincache/files/
```

### Giải nén phần mềm
- Tạo thư mục PHP tại thư mục gốc của ổ C và giải nén file PHP vừa tải vào thư mục
- Tạo một thư mục con tại thư mục này tên là ext và giải nén Wincache vào đó

### Cấu hình để PHP
- Để sử dụng PHP cần cấu hình biến hệ thống (Environment Variables) bằng cách tìm kiếm "Edit the system enviroment variables"
![image](./image/PHP%201.png)
- Nhấn đúp chuột vào Path để vào mục thay đổi biến hệ thống
![image](./image/PHP%202.png)
- Chọn New và nhập đường dẫn chứa PHP ("C:\PHP") rồi nhấn Ok các hộp thoại để lưu cấu hình
![image](./image/PHP%203.png)
- Kiểm tra bằng cách mở Command Prompt và chạy lệnh ```php -v```
![image](./image/PHP%204.png)
- Truy cập trang quản lý IIS Manager chọn tên máy tính ở khu vực panel bên trái
![image](./image/PHP%205.png)
- Chọn Handler Mappings
![image](./image/PHP%206.png)
- Chọn Add Module Mapping và nhập các thông tin
![image](./image/PHP%207.png)
![image](./image/PHP%208.png)
- Nếu báo chưa có CgiModule, cài đặt CGI thông qua tính năng Add roles and features của Windows Server
![image](./image/PHP%209.png)
- Quay trở về màn hình Home và chọn Default Documents
![image](./image/PHP%2010.png)
- Thêm Default.php và index.php vào danh sách
![image](./image/PHP%2011.png)
- Trở lại thư mục C:\PHP sửa tên file php.ini-production thành php.ini và sửa nội dung trong file (sử dụng tính năng Find để thuận tiện trong việc tìm thông số cấu hình)
```sh
max_execution_time =300
extension_dir ="./"
```
và thêm các dòng sau
```sh
upload_tmp_dir="C:\Windows\Temp"
session.save_path="C:\Windows\Temp"
error_log="C:\Windows\temp\php-errors.log"
cgi.force_redirect=0
fastcgi.impersonate=1
fastcgi.logging=0
```
- Tạo file index.php tại đường dẫn C:\inetpub\wwwroot với nội dung
```sh
<?php phpinfo(); ?>
```
- Kiểm tra kết quả
![image](./image/PHP%2012.png)