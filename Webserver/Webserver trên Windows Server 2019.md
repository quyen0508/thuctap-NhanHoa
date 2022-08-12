# Webserver trên Windows Server 2019
## Internet Information Services (IIS)
### Cài đặt IIS
- Sử dụng tính năng "Add roles and features" để cài đặt IIS

![image](./image/Windows%20IIS%201.png)
- Chọn ```Web Server (IIS)``` ở mục Server Roles

![image](./image/Windows%20IIS%202.png)
- Tiếp tục chọn Next tới mục Confirmation thì chọn Install

![image](./image/Windows%20IIS%203.png)
- Tạo file index.html tại đường dẫn C:\inetpub\wwwroot\ có nội dung

![image](./image/Windows%20IIS%204.png)

### Kết quả
- Truy cập thông qua máy ảo Windows 10 Pro phải chỉnh sửa file host:

![image](./image/Windows%20IIS%205.png)
- Truy cập trang web:

![image](./image/Windows%20IIS%206.png)

### Multi-web trên IIS
#### Tạo các website
- Sử dụng Add Website để tạo ra 3 trang web có tên miền là www.nxqweb1.com, www.nxqweb2.com và www.nxqweb3.com

![image](./image/Windows%20IIS%207.png)

##### Cấu hình trang web1

![image](./image/Windows%20IIS%208.png)
Tạo file index.html tại thư mục của trang web:

![image](./image/Windows%20IIS%209.png)

##### Cấu hình trang web2

![image](./image/Windows%20IIS%2010.png)
Tạo file index.html tại thư mục của trang web:

![image](./image/Windows%20IIS%2011.png)

##### Cấu hình trang web3

![image](./image/Windows%20IIS%2012.png)
Tạo file index.html tại thư mục của trang web:

![image](./image/Windows%20IIS%2013.png)

##### Kết quả
- Trước tiên phải cấu hình file hosts trên máy ảo Windows 10 Pro:

![image](./image/Windows%20IIS%2014.png)
- Trang web1:

![image](./image/Windows%20IIS%2015.png)
- Trang web2:

![image](./image/Windows%20IIS%2016.png)
- Trang web3:

![image](./image/Windows%20IIS%2017.png)