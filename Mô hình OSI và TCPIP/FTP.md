# Giao thức FTP
### Giới thiệu chung
FTP viết tắt của File Transfer Protocol là giao thức cung cấp cho người dùng khả năng chuyển file giữa các máy tính, được đặc tả trong RFC 959
Giao thức hoạt động trên mô
Khác với HTTP, server FTP duy trì các trạng thái (state) lệnh trong một phiên
### Mô tả giao thức FTP
- Khi người dùng bắt đầu một phiên FTP, FTp ở phía client sẽ khởi tạo một kết nối TCP với phía server trên cổng 21
- Phía client gửi thông tin định danh người dùng và mật khẩu thông qua đường kết nối điều khiển này
- Client sẽ làm việc với hệ thống tệp tin trên server
- Server nhận lệnh, đáp ứng yêu cầu
- Client và Server giao tiếp với nhau thông qua kết nối điều khiển (cổng 21) nhưng việc giao vận dữ liệu lại trên một kết nối riêng khác (cổng 20)

### Các phương thức (lệnh) của FTP
- ```USER username```: Dùng để xác định tên user
- ```PASS password```: Gửi password cho server với user tương ứng
- ```CWD pathname```: Dùng để thay đổi thư mục làm việc
- ```MKD pathname```: Dùng để tạo đường dẫn mới
- ```LIST [pathname]```: Dùng để trả về danh sách các file trong thư mục làm việc hoặc được chỉ định
- ```RETR pathname```: Dùng để tải file về client từ thư mục hiện tại
- ```STOR pathname```: Dùng để tải file vào thư mục hiện tại

### Các mã phản hồi của FTP
- 331 User name ok
- 125 Data connection already open; transfer starting
- 425 Can't open data connection
- 452 Requested action not taken. Insufficient storage space in system.