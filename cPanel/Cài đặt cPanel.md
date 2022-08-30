# Cài đặt cPanel
- Cập nhật hệ thống trước khi cài đặt
```sh
yum update -y
```

- Cài đặt ```perl``` và ```curl```
```sh
yum install perl curl -y
```

- Cài đặt cPanel
```sh
cd /home && curl -o latest -L https://securedownloads.cpanel.net/latest && sh latest
```

- Sử dụng trình duyệt để đăng nhập trang quản lý của cPanel tại cổng 2087

- Đăng nhập bằng tên và mật khẩu của tài khoảng root trên server

![image](./image/cPanel%201.png)

- Chấp nhận điều khoản

![image](./image/cPanel%202.png)

- Đăng nhập vào tài khoản cPanel Free Trial hoặc bản quyền

![image](./image/cPanel%203.png)

![image](./image/cPanel%204.png)

- Kích hoạt bản quyền dùng thử

![image](./image/cPanel%205.png)

- Nhập thông tin về email để cập nhật trạng thái và báo lỗi và sửa Nameserver nếu cần thiết

![image](./image/cPanel%206.png)

- Trang chính của WHM

![image](./image/cPanel%207.png)