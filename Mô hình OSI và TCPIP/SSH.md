# Giao thức SSH
### Giới thiệu chung
SSH viết tắt của Secure Shell là một phương thức đăng nhập bảo mật từ xa từ một máy tính đến một máy tính khác. Giao thức này được tạo ra để thay thế giao thức kém bảo mật hơn là Telnet và FTP

### Các chức năng chính
- Cung cấp việc truy cập bảo mật cho người dùng và các thao tac xử lý tự động
- Truyền file tự động hoặc có thao tác
- Thực thi lệnh từ xa
- Quản lý cơ sở hạ tầng mạng và các thành phần quan trọng khác của hệ thống

### Cách thức hoạt động
Giao thức được sử dụng trong mô hình Client/Server, tức là kết nối được thiết lập khi SSH client kết nối tới SSH server. SSH client điều hướng vào quá trình thiết lập và sử dụng mật mã khóa công khai để xác minh danh tính của SSH server. Sau bước thiết lập, giao thức SSH sử dụng mã hóa đối xứng và thuật toán hàm băm để dảm bảo tính bảo mật và toàn vẹn của dữ liệu được trao đổi giữa client và server
![image](https://www.ssh.com/hs-fs/hubfs/SSH_Client_Server.png?width=556&name=SSH_Client_Server.png)

### Đặc điểm của SSH
SSH cung cấp khả năng mã hóa mạnh mẽ và bảo toàn dữ liệu:
- Một khi kết nối được thiết lập giữa client và server, dữ liệu được truyền mã hóa theo tham số quy định trong lúc cài đặt
- Trong quá trình quyết định, client và server chấp nhận thuật toán mã hóa đối xứng để được sử dụng và sinh khóa mã hóa sẽ được sử dụng
- Lưu lượng  giữa các bên sẽ được bảo vệ bởi thuật toán mã hóa mạnh tiêu chuẩn công nghiệp như là AES (Advanced Encryption Standard) và giao thức SSH cũng bao gồm một cơ chế giúp bảo toàn trong việc truyền dữ liệu bằng việc sử dụng thuật toán hàm băm tiêu chuẩn như là SHA-2 (Standard Hashing Algorithm)

### SFTP
SFTP là giao thức phổ biến trong việc bảo mật truyền file được sử dụng dựa trên SSH

### Các câu lệnh trong SSH
- ```ssh-keygen```: tạo một cặp khóa cho xác thực khóa công khai
- ```ssh-copy-id```: cấu hình một khóa công khai được ủy quyền trên một server
- ```ssh-agent```: giúp quản lý việc truy cập vào các máy tính sử dụng khóa private
- ```ssh-add```: công cụ để thêm khóa vào kho quản lý
- ```scp```: client truyền file với giao diện dòng lệnh giống với RCP
- ```sftp```: client truyền file với giao diện dòng lệnh giống với FTP
- ```sshd```: OpenSSH server

### So sánh SSH với Telnet
| Tiêu chí | SSH | Telnet |
| - | - | - |
| Hoạt động trên port | 22 | 23 |
} Mức độ bảo mật | An toàn | Kém an toàn |
| Cơ chế mã hóa | Sử dụng Public Key | Truyền văn bản đơn thuần |
| Hệ thống phù hợp | Public Network | Private Network |
| Hệ điều hành tương thích | Tất cả hệ điều hành | Windows và Linux |