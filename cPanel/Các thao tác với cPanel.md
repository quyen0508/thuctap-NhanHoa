# Các thao tác với cPanel
### Tạo Package
- Tại tab **Packages**, chọn **Add a Package** và nhập các thông số như tên package, giới hạn dung lượng ổ đĩa, giới hạn lưu lượng băng thông mạng hàng tháng, số tài khoản FTP, email,... và nhấn **Add** để thêm

![image](./image/cPanel%208.png)

### Chỉnh sửa Package
- Tại tab **Packages**, chọn **Edit a Package**, chọn package cần chỉnh sửa rồi chọn **Edit**

![image](./image/cPanel%209.png)

- Sửa lại các thông số rồi chọn **Save changes** để lưu thay đổi

![image](./image/cPanel%2010.png)

### Xoá Package
- Tại tab **Package**, chọn **Delete a Package** và chọn package cần xoá, sau đó nhấn **Delete** để xoá package

![image](./image/cPanel%2011.png)

- Xoá thành công

![image](./image/cPanel%2012.png)

### Tạo Account
- Mỗi account tương ứng với một domain
- Tại tab **Account Functions**, chọn **Create a New Account** và nhập các thông số như tên miền, usernane, password địa chỉ email và chọn gói package, sau đó **Create** để tạo mới account

![image](./image/cPanel%2013.png)

### Chỉnh sửa Account
- Tại tab **Account Functions**, chọn **Modify an Account** và chọn tài khoản muốn chỉnh sửa rồi nhấn **Modify**

![image](./image/cPanel%2014.png)

- Chỉnh sửa thông tin và chọn **Save** để lưu thay đổi

![image](./image/cPanel%2015.png)

### Xoá Account
- Tại tab **Account Infomation**, chọn **List Accounts** và nhấn dấu "+" ở đầu dòng account cần xoá để mở rộng thanh tuỳ chọn, sau đó chọn **Terminate Account**

![image](./image/cPanel%2016.png)

- Chọn **Yes, remove this account** để xác nhận xoá account

![image](./image/cPanel%2017.png)

### Cài đặt chứng chỉ SSL Let's Encrypt
- Truy cập trang quản lý website của cPanel qua cổng 2083 và đăng nhập vào tài khoản tương ứng với tên miền cần cài

![image](./image/cPanel%2018.png)

- Trước tiên cần gỡ chứng chỉ SSL self-sign có sẵn trên tên miền

- Tại tab **Security**, chọn **SSL/TLS**

![image](./image/cPanel%2019.png)

- Chọn **Manage SSL site**

![image](./image/cPanel%2020.png)

- Chọn **Uninstall** để gỡ cài đặt các chứng chỉ cũ

![image](./image/cPanel%2021.png)

- Quay trở về trang chính, vẫn tại tab **Security**, chọn **SSL/TLS Status**

![image](./image/cPanel%2019.png)

- Chọn tất cả các tên miền cần được cấp chứng chỉ SSL và chọn **Run AutoSSL**

![image](./image/cPanel%2022.png)

- SSL tạo thành công

![image](./image/cPanel%2023.png)

- Kết quả trên trang web

![image](./image/cPanel%2024.png)