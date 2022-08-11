# WISA
### Giới thiệu về WISA
WISA là một bộ ứng dụng và hệ điều hành tạo môi trường cho webserver bao gồm W - Windows, I - IIS, S - SQL và A - ASP.NET

### Các thành phần của WISA
- Windows: là hệ điều hành làm cơ sở nên tảng cho các ứng dụng chạy trên nó
- IIS: là phần mềm web server
- SQL: là hệ quản trị cơ sử dữ liệu giúp lưu trữ thông tin của website
- ASP.NET: là nền tảng lập trình

### Cài đặt các thành phần của WISA
Cài đặt IIS, SQL và ASP.NET trên Windows Server 2019
##### Cài đặt IIS
Tham khảo tại Webserver trên Windows Server 2019
```sh
https://github.com/quyen0508/thuctap-NhanHoa/blob/main/Webserver/Webserver%20tr%C3%AAn%20Windows%20Server%202019.md
```

##### Cài đặt SQL
- Tải SQL Server Express tại trang web https://www.microsoft.com/en-us/sql-server/sql-server-downloads
- Mở phần mềm cài đặt và chọn kiểu cài đặt đơn giản (Basic)
![image](./image/WISA%201.png)
- Chấp nhận điều khoản
![image](./image/WISA%202.png)
- Chọn vị trí lưu trữ cài đặt rồi chọn Install
![image](./image/WISA%203.png)
- Để thuận tiện quản lý cơ sở dữ liệu, cài đặt SSMS (SQL Server Management Studio) tại trang web https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?redirectedfrom=MSDN&view=sql-server-ver16
    - Mở ứng dụng vừa tải, chọn ví trí cài đặt ứng dụng và chọn Install
![image](./image/WISA%204.png)

##### Cài đặt ASP.NET
- Sử dụng tính năng Add roles and features của Server Manager trong Windows Server để cài đặt ASP.NET 4.7
![image](./image/WISA%205.png)
![image](./image/WISA%206.png)
- Tạo một trang web mới có địa chỉ www.nxqweb4.com
![ìmage](./image/WISA%207.png)
- Chọn Add Application
![image](./image/WISA%208.png)
- Cài đặt Alias, Application pool và Physical path
![image](./image/WISA%209.png)
- Tạo một file index.html tại đường dẫn của web4 (C:\inetpub\wwwroot\web4) với nội dung
![image](./image/WISA%2010.png)
- Truy cập trang web www.nxqweb4.com/asp
![image](./image/WISA%2011.png)