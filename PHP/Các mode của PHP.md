# Các PHP mode
- PHP mode nói chung là các chương trình có chức năng phiên dịch PHP khi chạy trang web cho web server

### CGI
- CGI viết tắt của Common Gateway Interface
- CGI phù hợp với các trang web có dữ liệu tĩnh hoặc ít khi phải thực thi PHP
- CGI sử dụng ít RAM hơn do PHP chỉ được thực thi nếu được yêu cầu. Nhưng sẽ chậm hơn so với các trình thông dịch khác do mỗi khi thực thi PHP phải mất thời gian tải về RAN
##### Ưu điểm
- Bất kỳ user nào của hệ thống đều có khả năng chạy CGI với ứng dụng ```suEXEC```
- Mỗi user đều có thể tùy chỉnh cấu hình PHP dựa theo nhu cầu của mình
- RAM chỉ được sử dụng để chạy CGI khi cần
- Ở mode này, PHP chạy thành các tiến trình khác nhau, vì vậy sẽ giảm thiểu khả năng các đoạn mã sẽ gây crash cả webserver
- Các máy client khác nhau có thể chạy các phiên bản PHP khác nhau

##### Nhược điểm
- Gây năng suất thấp
- Lệnh ```Header``` bị hạn chế trong việc tạo xác thực của PHP. Giới hạn này là do đoạn mã không có khả năng nhận một vài biến của server

### PHP-FPM
- PHP-FPM viết tắt của FastCGI Process Manager
- PHP-FPM có đặc điểm tối ưu quá trình xử lý thông tin của các máy chủ web vì vậy phù hợp với các trang web có kích thước lớn

##### Ưu điểm
- Tùy chỉnh cache sẽ tăng năng suất
- Chỉ người sở hữu đoạn mã mới có thể chạy nó
- FastCGI có một biến hướng tới việc giảm thiểu rủi ro trong việc chờ đợi bằng cách xác định trước số yêu cầu trước khi khởi động lại trình thông dịch

##### Nhược điểm
- Luôn luôn chạy tiến trình *php-cgi* ngốn nhiều RAM bất kể có yêu cầu (request) hay không

### DSO (mod_php)
- DSO được chạy như là một Apache module hay mod_php
- DSO là mode chạy nhanh nhất so với các mode hiện có
- Phù hợp với những trang web nhỏ không nhiều người truy cập

##### Ưu điểm
- Các đoạn mã chạy ở tốc độ cao do được chạy dưới quyền của Apache user
- Tùy biến cache sẽ tăng hiệu quả

##### Nhược điểm
- Chỉ có thể sử dụng file ```php.ini``` để cấu hình toàn cục cho tất cả các trang web. Một số ít các tham số có thể được định nghĩa lại trong file ```.htaccess```
- Mode này không đủ an toàn vì nó sử hữu quyền Apache. Chỉ có ```mod_ruin``` có thể chạy như là các user riêng lẻ dù PHP dưới nó được thực thi như một module
- Bất kể người dùng có gửi yêu cầu hay không, module này sẽ được chạy với mỗi tiến trình webserver. Kết quả là server và nguồn tài nguyên có thể bị quá tải
- Wevserver crash trở thành một trong các lỗi của đoạn mã (script)
- Khó có thể xác định người dùng chạy phần mềm bên thứ ba thông qua đoạn mã (script)
- Multithread Apache running (MPM Worker) có thể không hỗ trợ một vào module PHP

### SuPHP
- SuPHP cũng chạy PHP như CGI module
- SuPHP khác với CGI ở chỗ PHP scripts được gọi từ wevserver sẽ được chạy dưới quyền của user sở hữu PHP scripts đó

##### Ưu điểm
- Có thể xác định người chạy PHP script khi chủ sở hữu chạy chúng
- Nếu không phải là chủ sở hữu thì sẽ không chạy được, vì vậy sẽ bảo mật hơn DSO hay CGI. Khi một tài khoản nào đó bị đánh cắp, các scripts cũng không thể nào lây lan sang các tài khoản khác được
- Trong quá trình chạy file trên server, người dùng có thể truyền đạt quyền lại cho chúng

##### Nhược điểm
- Mode này sử dụng nhiều CPU hơn so với CGI dù vẫn khá ít
- Các tùy chọn cache như ```APC```, ```XCache```,... đều không có sẵn

### So sánh các PHP mode
| Tiêu chí | CGI | PHP-FPM | DSO | SuPHP |
| - | - | - | - | - |
| Tài nguyên CPU | Tốn nhiều | Tốn ít | Tốn ít | Tốn nhiều |
| Tài nguyên RAM | Tốn ít | Tốn nhiều | Tốn ít | Tốn ít |
| Chạy scripts với quyền sở hữu của owner | Có (với SuEXEC) | Có | Không | Có |
| Bảo mật tốt | Không | Có | Không | Có |