# Cài đặt Plesk trên Windows Server 2019
### Tải file cài Plesk
Tải tại trang web [Plesk Web Installer](https://get.plesk.com/)

### Cài đặt Plesk
- Truy cập bằng trình duyệt với địa chỉ localhost:8447
- Chọn ngôn ngữ và đăng nhập bằng tài khoản admin của Windows Server

![image](./image/Plesk%201.png)
- Lựa chọn **Cài đặt hoặc Nâng cấp sản phẩm**

![image](./image/Plesk%202.png)
- Chọn **Tiếp tục**

![image](./image/Plesk%203.png)

![image](./image/Plesk%204.png)

- Nhập mật khẩu admin giống với lúc đăng nhập và chọn **Tiếp tục**

![image](./image/Plesk%205.png)

- Cài đặt hoàn tất

![image](./image/Plesk%206.png)

- Đăng nhập vào Plesk bằng địa chỉ localhost:8443

![image](./image/Plesk%207.png)

- Đăng ký thông tin liên hệ

![image](./image/Plesk%208.png)

- Giao diện trang chính

![image](./image/Plesk%209.png)

### Thêm khách hàng
- Để thêm khách hàng mới, vào tab **Khách hàng** và chọn **Thêm khách hàng**

![image](./image/Plesk%2010.png)

- Nhập các thông tin thiết lập và đồng thời tạo thông tin thuê bao

![image](./image/Plesk%2011.png)

![image](./image/Plesk%2012.png)

### Cài đặt SSL trả phí cho website
- Tham khảo bước đăng ký chứng chỉ trên website của SSLs
```sh
https://github.com/quyen0508/thuctap-NhanHoa/blob/main/SSL/C%C3%A0i%20%C4%91%E1%BA%B7t%20ch%E1%BB%A9ng%20ch%E1%BB%89%20SSL%20c%C3%B3%20tr%E1%BA%A3%20ph%C3%AD.md#%C4%91%C4%83ng-k%C3%BD-ch%E1%BB%A9ng-ch%E1%BB%89-ssl-tr%C3%AAn-sslscom
```

- Tại tab **Trang Web & Tên Miền**, chọn tên miền cần cài đặt SSL, chọn **Chứng nhận SSL/TLS**

![image](./image/Plesk%2013.png)

- Kéo xuống cuối chọn nút **Quản lý**

![image](./image/Plesk%2014.png)

- Chọn **Thêm chứng nhận SSL/TLS**

![image](./image/Plesk%2015.png)

- Các thông tin cần nhập là **Tên chứng nhận**, **Quốc gia** và các tệp tin chứng nhận đã nhận được khi đăng ký trên trang ssls.com, sau đó chọn **Tải len chứng nhận**

![image](./image/Plesk%2016.png)

- Chứng chỉ sau khi thêm thành công

![image](./image/Plesk%2017.png)

- Để thêm chứng chỉ vào website cần thiết lập chứng chỉ SSL, quay trở về trang chính của tên miền rồi chuyển sang tab **Lưu trữ & DNS**, sau đó chọn **Các thiết lập lưu trữ**

![image](./image/Plesk%2018.png)

- Kéo xuống phần **Bảo mật**, tại mục **Chứng nhận** chọn chứng chỉ SSL vừa được thêm và chọn **Đồng ý**

![image](./image/Plesk%2019.png)

- Kiểm tra chứng chỉ bằng cách vào mục **Chứng nhận SSL/TLS** tại trang chính của tên miền

![image](./image/Plesk%2020.png)

- Kết quả khi truy cập trang web

![image](./image/Plesk%2021.png)

### Chỉnh sửa nội dung trang web
- Để chỉnh sửa nội dung trang web, cần chỉnh sửa file index.html trong thư mục gốc của website
- Chuyển sang tab **Các tập tin**, chọn file index.html nằm tại thư mục gốc để bắt đầu chỉnh sửa file
![image](./image/Plesk%2022.png)

- Sau khi sửa xong nội dung, chọn **Lưu** để cập nhật nội dung trang web

![image](./image/Plesk%2023.png)

- Truy cập vào tên miền bằng trình duyệt để kiểm tra kết quả

![image](./image/Plesk%2024.png)

### Tạo các gói dịch vụ
- Sử dụng tài khoản Administrator để thêm, sửa và xóa các gói dịch vụ
- Chọn tab **Gói dịch vụ** để vào trang chính của các gói dịch vụ

![image](./image/Plesk%2025.png)

- Lựa chọn các tùy chọn phù hợp với người dùng bao gồm các tab như: Tài nguyên, Quyền hạn, Tham số lưu trữ, Các thiết lập PHP, Thư tin, DNS, Hiệu suất, Nhật ký & Thống kê, Ứng dụng, Các dịch vụ bổ sung

![image](./image/Plesk%2026.png)