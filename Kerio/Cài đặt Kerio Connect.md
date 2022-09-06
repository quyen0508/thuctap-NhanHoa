# Cài đặt Kerio Connect
- [Tải xuống](https://www.gfi.com/products-and-solutions/email-and-messaging-solutions/kerio-connect/download) bản dùng thử của Kerio Connect
- Sao chép file cài vào VPS

![image](./image/Kerio%201.png)

- Kiểm tra và tắt các dịch vụ mail nếu đã cài trước đó
```sh
/etc/init.d/sendmail stop && /sbin/chkconfig sendmail off
/etc/init.d/postfix stop && /sbin/chkconfig postfix off
```

- Di chuyển tới thư mục chứa file cài Kerio và tiến hành cài đặt
```sh
yum install kerio-connect-9.4.2-6498-linux-x86_64.rpm
```

- Truy cập trang web ```địa-chỉ-ip-của-vps:4040``` (103.159.51.14:4040) để tiếp tục cấu hình Kerio (có thể cần mở cổng 4040 nếu đang sử dụng tưởng lửa)

- Chọn ngôn ngữ

![image](./image/Kerio%202.png)

- Chấp nhận điều khoản

![image](./image/Kerio%203.png)

- Nhập thông tin về hostname và email domain

![image](./image/Kerio%204.png)

- Đặt tên tài khoản và mật khẩu cho tài khoản admin

![image](./image/Kerio%205.png)

- Lựa chọn các tuỳ chọn
    - **Allow remote administration from MyKerio cloud service**: quản lý Kerio Connect từ dịch vụ dám mây MyKerio
    - **Open MyKerio and add this appliance afrer you finish thí wizard**: chuyển hướng tới trang MyKerio sau khi cài đặt xong

![image](./image/Kerio%206.png)

- Chọn nơi lưu trữ trên VPS

![image](./image/Kerio%207.png)

- Chọn loại bản quyền

![image](./image/Kerio%208.png)

- Nhập mã kích hoạt

![image](./image/Kerio%209.png)

- Xác nhận chia sẻ thông tin  và chọn **Finish** khi xem xong lại cấu hình đã thiết lập trước đó

![image](./image/Kerio%2010.png)

- Sau khi cài đặt thành công, truy cập trang web ```địa-chỉ-ip-của-vps:4040``` để truy cập trang quản lý lý Kerio

![image](./image/Kerio%2011.png)

- Giao diện chính của trang quản lý

![image](./image/Kerio%2012.png)