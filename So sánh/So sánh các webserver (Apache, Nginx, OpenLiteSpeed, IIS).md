# So sánh các webserver (Apache, Nginx, OpenLiteSpeed, IIS)
### Giới thiệu sơ lược
##### Apache
- Apache là webserver được sử dụng nhiều nhất
- Được tạo vào năm 1995 bởi Rob McCool và Brian Behlendorf
- Theo W3Techs, Apache chiếm 36% thị phần tính tới 1/9/2020
- Lý do Apache phổ biến là vì được cài sẵn trên hầu hết các bản phân phối của hệ điều hành Linux

##### Nginx
- Được tạo bởi Igor Sysoev và ra mắt vào năm 2004
- Nginx được tạo ra với mục tiêu chạy với hiệu năng vượt trội so với Apache
- Hiện tại, Nginx đang chiếm 32,5% thị phần

##### OpenLiteSpeed
- OpenLiteSpeed là phiên bản mã nguồn mở của LiteSpeed Web Server Enterprise ra năm 2013 (LiteSpeed Web Server Enterprise ra mắt năm 2003)
- Được sử dụng bởi nhiều công ty web hosting bởi tính hiệu quả của nó

##### IIS
- IIS (Internet Infomation Services) là web server chạy trên nền tảng Windows được phát hành đầu tiên vào năm 1995
- Thường dùng để chạy ASP.NET

### So sánh giữa các webserver
##### Ưu điểm
###### Apache
- Apache xử lý tốt các trang web động hơn so với Nginx
- Có khả năng thêm các tính năng hoặc module
- Có độ tin cậy cao
- Có thể được cài đặt dễ dàng
- Thay đổi được áp dụng ngay lập tức mà không cần khởi động lại server
- Chạy được trên nhiều loại hệ điều (Windows, Linux,...)
- Được cập nhật thường xuyên
- Cộng đồng lớn
- Cho phép cấu hình bằng file ```.htaccess```

###### Nginx
- Nginx xử lý vượt trội các trang web tĩnh so với Apache
- Nhẹ hơn - yêu cầu ít nguồn tài nguyên và bộ nhớ hơn
- Tốt trong việc mở rộng
- Xử lý được nhiều client với ít số tiến trình hơn
- Được khuyến nghị chạy website chạy trên VPS


###### OpenLiteSpeed
- OpenLiteSpeed có hiệu năng vượt trội so với Apache hay Nginx
- Hỗ trợ hầu hết các module của Apache
- Có cấu trúc hướng sự kiện đem lại hiệu năng cao
- Có thể được quản lý thông qua giao diện đồ hoạ

##### Nhược điểm
###### Apache
- Chiếm nhiều RAM hơn khi chạy nặng
- Phát sinh ra tiến trình mới với mỗi yêu cầu khiến cho Apache chạy ít hiệu quả hơn so với các webserver khác
- Là server dựa trên tiến trình
- Cần phải xác định và tắt các module và service không mong muốn vì có thể gây ra các rủi ro bảo mật nghiêm trọng
- Chỉ có dựa theo cộng đồng hỗ trợ

###### Nginx
- Ít module
- Cộng đồng hỗ trợ thấp
- Không hỗ trợ file htaccess

###### IIS
- Không thể cấu hình từ xa
- Chỉ có trên nền tảng Windows
- IIS có thể bị treo, khi đó phải khởi động lại hệ thống mới có thể khôi phục lại được
- Không hỗ trợ file htaccess
- Chi phí hỗ trợ kỹ thuật đắt đỏ

###### OpenLiteSpeed
- Phí bản quyền cao hơn so với Apache và Nginx