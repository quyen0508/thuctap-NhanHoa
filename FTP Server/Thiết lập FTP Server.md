# Thiết lập FTP Server trên CentOS 7
### Cài đặt FTP Server
- Cập nhật trình quản lý gói
```sh
yum update -y
```

- Cài đặt VSFTPD
```sh
yum install -y vsftpd
```

- Khởi động và thiết lập khởi động cùng hệ thống
```sh
systemctl start vsftpd
systemctl enable vsftpd
```

- Cấu hình cho phép dịch vụ FTP và port 21 tuỳ theo ứng dụng firewall

- Backup file cấu hình của VSFTPD
```sh
cp /etc/vsftpd/vsftpd.conf /etc/vsftpd/vsftpd.conf.bak
```

### Cấu hình FTP Server
- Chỉnh sửa file cấu hình của VSFTPD với các thông số
    - ```anonymous_enable=NO```: không cho phép các kết nối ẩn danh (dòng 12)
    - ```local_enable=YES```: cho phép các kết nối trong mạng nội bộ (dòng 16)
    - ```write_enable=YES```: cho phép ghi file vào server (dòng 19)
    - ```chroot_local_user=YES``` (101), ```allow_writeable_chroot=YES```(+), ```chroot_list_enable=YES```(103), ```chroot_list_file=/etc/vsftpd/chroot_list``` (105): chỉ cho phép truy cập trong thư mục của chính mình của mỗi user
    - ```ftpd_banner=Welcome to blah FTP service!``` (87): Thông điệp xuất hiện khi người dùng truy cập FTP Server
    - ```pasv_min_port=30000``` (+), ```pasv_max_port=31000``` (+): Giới hạn khoảng cổng cho FTP passive
    - ```userlist_enable=YES``` (128), ```userlist_file=/etc/vsftpd/user_list``` (+), ```userlist_deny=NO``` (+): Giới hạn user truy cập vào server
    - ```use_localtime=YES``` (+): Cấu hình sử dụng thời gian localtime
    - ```listen=YES``` (116), ```listen_ipv6=NO``` (125)

- Khởi động lại dịch vụ ```vsftpd```
```sh
systemctl restart vsftpd
```

### Thiết lập sử dụng FTP Server
- Tạo user
```sh
useradd quyen1
passwd quyen1
useradd quyen2
passwd quyen2
```

Thư mục mặc định của các user trên là /home/<tên-user>

- Tạo file ```chroot_list``` tại đường dẫn ```/etc/vsftpd/``` và thêm tên các user đã tạo phía trên

![image](./image/FTP%20Server%201.png)

- Thêm 2 user vừa tạo vào file ```user_list``` tại đường dẫn ```/etc/vsftpd/```

- Tạo đường dẫn mặc định và cấp quyền cho user
```sh
mkdir -p /var/www/quyen1/upload
chmod 550 /var/www/quyen1
chmod 750 /var/www/quyen1/upload
chown -R quyen1: /var/www/quyen1
```

- Khởi động lại dịch vụ ```vsftpd```
```sh
systemctl restart vsftpd
```

- Sử dụng phần mềm FileZilla để truy cập FTP Server: Nhập thông tin về host, username, password, port

![image](./image/FTP%20Server%202.png)

![image](./image/FTP%20Server%203.png)

- Để upload/download file với FTP Server, kéo thả file từ thư mục chứa vào FileZilla, hay trong FileZilla từ vị trí hiện tại của file tới server hoặc client

![image](./image/FTP%20Server%204.png)

![image](./image/FTP%20Server%205.png)