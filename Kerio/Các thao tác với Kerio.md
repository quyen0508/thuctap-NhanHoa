# Các thao tác với Kerio
### Cài đặt SSL Let's Encrypt cho Kerio Connect
- Truy cập trang web quản trị của Kerio, chọn tab **Configuration** rồi chọn **SSL Certificates**
- Tại giao diện quả lý chứng chỉ SSL, chọn **New** rồi chọn **New let's Encrypt Certificate**

![image](./image/Kerio%2013.png)

- Nhập tên miền cần được cấp chứng chỉ và chọn **Ok** để tiến hành cấp chứng chỉ tự động vào tạo gia hạn tự động

![image](./image/Kerio%2014.png)

![image](./image/Kerio%2015.png)

- Trở lại trang quản lý chứng chỉ, chuột phải vào chứng chỉ tên miền chính và chọn **Set as Default** để đặt làm chứng chỉ mặc định cho server

![image](./image/Kerio%2016.png)

- Kiểm tra chứng chỉ của trang web

![image](./image/Kerio%2017.png)

### Giao diện trang quản trị
- Gồm 4 tab: Accounts, Status, Configuration, Logs