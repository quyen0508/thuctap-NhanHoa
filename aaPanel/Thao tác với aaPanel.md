# Thao tác với aaPanel
### Đăng nhập
- Giao diện đăng nhập

![image](./image/aaPanel%203.png)

### Trang chính
- Lần đầu đăng nhập vào aaPanel sẽ được gợi ý cài LEMP hoặc LAMP, chọn 1 trong 2 bằng cách đánh dấu các phần mềm cần cài vào cột tương ứng và chọn **One-click** để tiến hành cài đặt

![image](./image/aaPanel%204.png)

- Giao diện trang chính

![image](./image/aaPanel%205.png)

##### Status
- Status hiển thị thông tin trạng thái tài nguyên của hệ thống

![image](./image/aaPanel%206.png)

##### Overview
- Overview hiển thị các thông báo đang chú ý của các dịch vụ đang chạy

![image](./image/aaPanel%207.png)

- Khi bấm vào mục Security sẽ có 3 mức cảnh báo giảm dần: Risk, Security, Ignore

![image](./image/aaPanel%2011.png)

##### Software
- Software hiển thị trạng thái các phần mềm đã được cài đặt

![image](./image/aaPanel%208.png)

##### Traffic
- Traffic giúp theo dõi, giám sát lưu lượng mạng của server

![image](./image/aaPanel%209.png)

##### Disk IO
- Disk IO giúp giám sát hoạt động của ổ đĩa

![image](./image/aaPanel%2010.png)

### Thiết lập trang web
##### Tạo trang web
- Truy cập vào tab **Website** và chọn **Add site**

![image](./image/aaPanel%2012.png)

- Điền các thông tin để tạo trang web, có thể tạo tài khoản FTP và MySQL đồng thời

![image](./image/aaPanel%2013.png)

![image](./image/aaPanel%2014.png)

- Tạo thành công

![image](./image/aaPanel%2015.png)

##### Chỉnh sửa nội dung trang web
- Truy cập vào tab **Website**, nhấn vào đường dẫn **Document Root** của website đã tạo

![image](./image/aaPanel%2016.png)

- Nhấn đúp vào file index.html để bắt đầu sửa nội dung

![image](./image/aaPanel%2017.png)

- Viết nội dung cho file và chọn **Save** để lưu thay đổi nội dung file

![image](./image/aaPanel%2018.png)

- Kiểm tra tại trang web

![image](./image/aaPanel%2019.png)

##### Cài đặt chứng chỉ SSL
- Chọn tên miền tại trang quản lý website, chọn mục **SSL**, chọn tên miền cần cấp chứng chỉ SSL trong mục **Domain name** và chọn **Apply** để tiến hành đăng ký và cài đặt chứng chỉ

![image](./image/aaPanel%2020.png)

- Cài đặt chứng chỉ thành công

![image](./image/aaPanel%2021.png)

- Kiểm tra trên trang web

![image](./image/aaPanel%2022.png)

### FTP
- FTP sử dụng để truy nhập file từ xa, có thể dùng để upload source code của mỗi trang web với user tương ứng
- Để truy cập vào trang quản lý, chọn tab **FTP**

![image](./image/aaPanel%2023.png)

- Với mỗi user có thể sửa lại đường dẫn được phép truy cập, thay đổi mật khẩu và khóa tài khoản đi

- Để truy cập từ xa, ví dụ dùng Windows File Explorer để truy cập, nhập đường dẫn ```ftp://địa-chỉ-ip-của-server:21```

![image](./image/aaPanel%2024.png)

- Đăng nhập bằng tài khoản đã tạo (web1)

![image](./image/aaPanel%2025.png)

- Giao diện sau khi đăng nhập thành công, người dùng có thể thao tác với file trong thư mục của trang web ```web1.quyennx.xyz```

![image](./image/aaPanel%2026.png)

- Các thao tác có thể thực hiện trên File Explorer: sao chép (2 chiều), xóa và đổi tên file

- Ngoài ra còn có thể đổi cổng truy cập FTP thông qua nút **Change FTP Port**

![image](./image/aaPanel%2027.png)

### Databases
- Để quản lý các CSDL, sử dụng tab **Databases**
- Giao diện chính

![image](./image/aaPanel%2028.png)

- Mỗi CSDL đều có thể quản lý bằng các chức năng: sao lưu/khôi phục, truy xuất và thay đổi dữ liệu (thông qua phpMyAdmin), cấp quyền truy cập CSDL cho người khác, thay đổi mật khẩu và xóa CSDL

### Quản lý Files
- Files trên server có thể được quản lý ngay trên giao diện web của aaPanel
- Để truy cập, chọn tab **Files**

![image](./image/aaPanel%2029.png)

- Các chức năng của **Files**:
##### Upload từ máy tính
- Sử dụng để upload file từ máy tính chạy trang web quản lý của aaPanel để upload vào server

![image](./image/aaPanel%2030.png)

- Có thể kéo thả file vào hoặc chọn từ hộp thoại rồi chọn **Upload** để tải file lên server

##### Remote Download
- Dùng để tải file từ một trang web khác và lưu vào server
- Nhập các thông tin tải file và chọn **Confirm** để xác nhận và bắt đầu tải xuống

![image](./image/aaPanel%2031.png)

##### New
- Dùng để tạo mới thư mục, file hoặc đường dẫn (softlink/shortcut)

![image](./image/aaPanel%2032.png)

##### Search Files Content
- Dùng để tìm kiếm tên file theo 2 cách: theo từ hoặc theo biểu thức chính quy

![image](./image/aaPanel%2033.png)

##### Terminal
- Dùng để mở terminal tại thư mục đang làm việc

![image](./image/aaPanel%2034.png)

##### Recycle Bin
- Là nơi chứa những file/thư mục đã bị xóa
- Có 2 tùy chọn là: khôi phục hoặc xóa file

![image](./image/aaPanel%2035.png)

### Cron job
- Cron Job là phần mềm xử lý các tác vụ lặp đi lặp lại theo một điều kiện thời gian nhất định
- Để quản lý Cron Jon, chọn tab **Cron**
- Các tác vụ có thể tạo: Shell Script, Backup Site, Backup Database, Cut Log, Backup Directory, Free RAM, Access URL

![image](./image/aaPanel%2036.png)

- Ví dụ khi tạo tác vụ sao lưu CSDL với thời gian thứ 2 hàng tuần vào lúc 4h30

![image](./image/aaPanel%2037.png)

- Ở danh sách tác vụ, các hành động có thể thực hiện với các tác vụ như: thực thi, sửa, log và xóa tác vụ

![image](./image/aaPanel%2038.png)

### Giao diện CLI
- aaPanel có thể được quản lý dưới dạng giao diện dòng lệnh với các lệnh quản trị cho hệ thống Panel như khởi động, dừng, khởi động lại panel hay sửa lỗi cho panel, hiện danh sách lỗi, thay đổi username, password,...

![image](./image/aaPanel%2039.png)

### App Store
- App Store bao gồm danh sách các ứng dụng đã cài và có thể cài lên server

![image](./image/aaPanel%2040.png)