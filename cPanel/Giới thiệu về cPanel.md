# Giới thiệu về cPanel
- cPanel là web hosting control panel trên nền tảng Linux phổ biến nhất hiện nay
- cPanel có giao diện đơn giản, linh hoạt, giúp người dùng quản lý tất cả các dịch vụ của web hosting một cách dễ dàng
- Có hệ thống phân cấp ba lớp:
    - Hosting Company
    - Reseller
    - End User
- Hosting Company và Reseller đều sử dụng giao diện Web Host Manager (WHM). Trong đó, Hosting Company có quyền quản trị cao nhất và có thể hạn chế quyền truy cập vào một số tính năng nhất định trong Reseller
- End User có quyền truy cập trực tiếp vào cPanel Interface để có thể thực hiện các tác vụ cho trang web của họ
- Ngoài ra, cPanel cũng cho phép các nhà cung cấp bên thứ ba tích hợp dịch vụ của họ để khách hàng có thể sử dụng dịch vụ ngay trên giao diện cPanel
- cPanel có thể được cài đặt trên các hệ điều hành như CentOS, RedHat Enterprise Linux (RHEL), CloudLinux hay FreeBSD
- cPanel hỗ trợ Apache, MySQL và PHP cũng như các giao thức email phổ biến gồm POP3, IMAP và SMTP
- End User sử dụng hosting cPanel bằng cách truy cập qua cổng 2083

### Các tính năng chính của cPanel
##### Quản lý tập tin
- **File Manager**: Truy cập và quản lý file nhanh chóng (thêm, sửa, xoá) mà không cần FTP
- **Disk Usage**: Các giao diện đồ hoạ thể hiện tình trạng sử dụng ổ cứng để hiểu và quản lý ổ cứng tốt hơn
- **FTP Connection**: Cung cấp tổng quan về các phiên kết nối FTP
- **BackUp** và **Backup Wizard**: Sao lưu các tệp tin trên web hosting dễ dàng
- **Image**: Cho phép người dùng thay đổi kích thước, chuyển đổi và xem hình ảnh
- **Web Disk**: Cho phép quản trị viên web xem và quản lý không gian ổ cứng (chỉnh sửa, di chuyển, upload hay download file)
- **Anonymous FTP**: Dùng để tải xuống file từ các nguồn công khai
- **Directory Privacy**: Thư mục được bảo vệ bằng mật khẩu để bảo mật tốt hơn
- **FTP Account**: Quản lý tài khoản FTP

##### Quản lý cơ sở dữ liệu
- **phpMyAdmin**: Giao diện của bên thứ ba dùng để quản trị cơ sở dữ liệu MySQL
- **Remote SQL**: Cho phép truy cập cơ sở dữ liệu từ xa
- **MySQL**: Cơ sở dữ liệu để các ứng dụng web chạy
- **PostgreSQL Database**: Cơ sở dữ liệu thay thế cho MySQL
- **MySQL Database Wizard**: Trình tạo và quản lý cơ sở dữ liệu MySQL
- **PostgreSQL Database Wizard**: Trình tạo và quản lý cơ sở dữ liệu PostgreSQL

##### Quản lý tên miền
- **Site Publisher**: Tạo trang web cơ bản hoặc trang giữ để chuẩn bị cho một trang web mới
- **Alias**: Chuyển hướng tên miền đến các trang web khác nhau
- **Advanced & Simple Zone Editor**: Quản lý các bản ghi DNS
- **Addon Domain**: Giảm chi phí bằng cách thêm tên miền và tạo trang web với địa chỉ email mới cho mỗi tên miền mà không cần phải mua hosting mới cho mỗi tên miền
- **Redirect**: Thiết lập chuyển hướng từ một trang cụ thể sang một trang khác
- **Subdomain**: Tạo các phần phụ của trang web cho mục đích cụ thể như blog của công ty hoặc cơ sở tri thức

##### Email
- **Email Account**: Thiết lập và quản lý tất cả các khía cạnh của tài khoản email một cách nhanh chóng và dễ dàng
- **Autoresponder**: Trả lời tự động tới các email nhận được
- **Track Delivery**: Theo dõi các email đã gửi
- **Authentication**: Gửi email đã được xác thực
- **Archive**: Lưu trữ email gửi và nhận trong một khoảng thời gian xác định
- **Calendar and Contact**: Cập nhật thông tin về lịch và danh bạ
- **Forwarder**: Thiểt lập chuyển tiếp email cho các địa chỉ email cụ thể
- **Default Address**: Bất kỳ email nào nhận được địa chỉ chính xác đều được gửi đến địa chỉ mặc định
- **Global Filter**: Thiết lập bộ lọc email
- **Encryption**: Tạo khoá công khai (public key) để liên lạc qua email an toàn hơn
- **Configure Greylisting**: Biện pháp ngăn chặn thư rác cơ bản
- **MX Entry**: Định tuyến lại email đến một máy chủ khác
- **Mailing List**: Tạo một email gửi cho nhiều người
- **Email Filter**: Chuyển hướng email, ngăn chặn thư rác hoặc chuyển email đến các ứng dụng
- **Apache SpamAssassin**: Ứng dụng chống thư rác
- **BoxTrapper**: Ngăn chặn các email không xác định vào gộp thư đến

##### Thống kê số liệu và phân tích
- **Visitor**: Bản ghi đầy đủ về lượng khách truy cập trong file log Apache
- **Raw Access**: Phiên bản nén của nhật ký khách truy cập vào máy chủ
- **Webalizer**: Công cụ phân tích khách truy cập trang web
- **Error**: Tập hợp các lỗi gần đây trên trang web
- **AWStat**: Công cụ đo lường thể hiện lượng khách truy cập vào trang web
- **Webalizer FTP**: Công cụ đo lường để hiển thị thông tin khách truy cập FTP vào trang web
- **Bandwidth**: Hiển thị mức sử dụng băng thông
- **Analog Stat**: Chế độ xem đơn giản các lượt truy cập trang web
- **Metric Editor**: Chọn số liệu để chạy trên các miền

##### Tính năng bảo mật
- **SSH Access - Secure**: Xác thực tới máy chủ thông qua dòng lệnh
- **Hotlink Protection**: Ngăn chặn hành vi chiếm băng thông khi nội dung được nhúng trên một trang web khác
- **ModSecurity Domain Manager**: Kích hoạt hoặc vô hiệu hoá ModSecurity
- **IP Blocker**: Quản lý chặn một số IP nhất định truy cập trang web
- **Leech Protection**: Hạn chế số lần đăng nhập
- **Two-Factor Authentication**: Bảo mật 2 lớp
- **SSL/TLS**: Bảo mật nâng cao khi quản lý SSL/TLS
- **Security Policy**: Chính sách bảo mật cho cácn IP không xác định
- **SSL/TLS Wizard**: Tự động hoá quy trình cung cấp SSL

##### Các ứng dụng phần mềm
- **PHP**: Kiểm tra cấu hình PHP của server
- **RubyGem**: Quản lý Ruby
- **Optimize Website**: Tối ưu thời gian phản hồi của web server Apache
- **PHP Pear Package**: Gói Pear để có thể chạy trên PHP
- **Ruby On Rail**: Triển khai các ứng dụng Ruby On Rail
- **MultiPHP Manager**: Lựa chọn các phiên bản PHP khác nhau cho từng website
- **PERL Module**: Tạo module PERL để tạo các tác vụ với PERL
- **Site Software**: Thêm phần mềm bổ sung như Bảng thương mại điện tử và Bảng tin
- **MultiPHP INI Editor**: Quản lý cấu hình PHP của nhiều phiên bản khác nhau

##### Các cài đặt nâng cao
- **Index**: Tuỳ chỉnh trang mục Apache mặc định
- **MIME Type**: Đặt hướng dẫn xử lý các phần mở rộng tệp khác nhau như .html, .htm
- **Cron Job**: Tự động hoá các nhiệm vụ lặp đi lặp lại vào thời gian đã lên lịch
- **Error Page**: Định cấu hình cách các trang lỗi xuất hiện khi khách truy cập
- **Virus Scanner**: Quét các mối đe doạ, phần mềm độc hại
- **Track DNS**: Kiểm tra cài đặt DNS bằng cách truy tìm tuyến đường từ PC đến máy chủ
- **Apache Handler**: Các lựa chọn xử lý của Apache
- **API Shell**: Chạy các lệnh gọi API cPanel

##### Các tuỳ chọn người dùng
- **User Preference**: Đặt tuỳ chọn người dùng
- **User Manager**: Đặt và chỉnh sửa quyền và quyền của người dùng