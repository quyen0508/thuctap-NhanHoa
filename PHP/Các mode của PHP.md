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
- Có ít RAM 