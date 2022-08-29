# Các thao tác với DLEMP
### Tạo một website thông thường
- Sử dụng lệnh ```dlemp``` để truy cập các công cụ cài đặt của DLEMP
- Chọn 1 để tạo website

![image](./image/DLEMP%206.png)

- Chọn 1 tiếp để tạo một trang web thông thường

![image](./image/DLEMP%207.png)

- Nhập tên miền và nhập **y** để DLEMP tự động tạo CSDL cho tên miền. Trang web được tạo thành công có thể chỉnh sửa code tại đường dẫn /home/tên-miền/public_html

![image](./image/DLEMP%208.png)

- Kết quả trên trình duyệt

![image](./image/DLEMP%209.png)

### Tạo một trang WordPress
- Sử dụng lệnh ```dlemp``` để truy cập các công cụ cài đặt của DLEMP
- Chọn 1 để tạo website

![image](./image/DLEMP%206.png)

- Chọn 3 để tạo website WordPress tự động

![image](./image/DLEMP%2010.png)

- Chọn loại cache cho WP

![image](./image/DLEMP%2011.png)

- Nhập các thông tin: tên miền, tên user cho quản trị WP, mật khẩu cho tài khoản admin và cuối cùng là email

![image](./image/DLEMP%2012.png)

- Cài đặt thành công

![image](./image/DLEMP%2013.png)

- Đăng nhập trang quản trị của WP (http://tên-miền/wp-admin) với tài khoản và mật khẩu vừa tạo

![image](./image/DLEMP%2014.png)

- Trang Dashboard của WP

![image](./image/DLEMP%2015.png)

### Cài chứng chỉ SSL miễn phí Let's Encrypt
- Trước tiên cần cài acme và thêm địa chỉ email vào ứng dụng
```sh
curl https://get.acme.sh | sh -s email="quyen05082000@gmail.com"
```

- Chọn 24 để cài đặt chứng chỉ SSL miễn phí

![image](./image/DLEMP%2016.png)

- Chọn 1 hoặc 2 tuỳ thuộc vào loại tên miền

![image](./image/DLEMP%2017.png)

- Chọn **y** để xem danh sách các tên miền đang có trên server và nhập tên miền cần cài SSL

![image](./image/DLEMP%2018.png)

- Nếu báo DLEMP không thể cài đặt SSL cho tên miền, chọn **y** để cài đặt SSL cho tên miền

![image](./image/DLEMP%2019.png)

- Cài đặt thành công

![image](./image/DLEMP%2020.png)

- Kiểm tra trên trang web

![image](./image/DLEMP%2021.png)

- Ngoài ra, đối với WP còn có thể cài plugin **Really simple SSL** để quản lý SSL dê dàng hơn

### Xoá trang web
- Để xoá trang web, chọn **2**

![image](./image/DLEMP%2022.png)

- Chọn **y** để hiện danh sách tên miền hiện có trên server, nhập tên miền cần xoá và xác nhận xoá bằng **y**

![image](./image/DLEMP%2023.png)

### Backup code
- Để backup và restore code, chọn mục **3**

![image](./image/DLEMP%2024.png)

- Chọn **4** để tự động backup tất cả website

![image](./image/DLEMP%2025.png)

- Chọn **y** để mở tính năng này, chọn tần suất cập nhật, thời gian cạp nhật, chọn thời gian tự động xoá các bản backup sau 1 khoảng thời gian xác định và cuối cùng xác nhận lại cấu hình

![image](./image/DLEMP%2026.png)

- Tuy nhiên, tính năng này chỉ có trên bản Bussiness

### Backup database
- Để backup database, chọn **4**

![image](./image/DLEMP%2027.png)

- Chọn **y** để mở tính năng này, chọn tần suất cập nhật, thời gian cạp nhật, chọn thời gian tự động xoá các bản backup sau 1 khoảng thời gian xác định và cuối cùng xác nhận lại cấu hình

![image](./image/DLEMP%2028.png)

### Tạo Cronjob
- Để tạo Cronjob, chọn **11** (Cronjob Manage)

![image](./image/DLEMP%2029.png)

- Chọn **1** để tạo Cronjob, sau đó nhập lệnh Cronjob và nhấn Enter để thêm

![image](./image/DLEMP%2030.png)

### Quản lý Log File
- Để truy cập quản lý log file, chọn **12**

![image](./image/DLEMP%2031.png)

- Các chức năng dùng để quản lý: tải về file log, xem 100 dòng cuối của file log, xoá tất cả log,...

![image](./image/DLEMP%2032.png)

### Thay đổi cài đặt PHP
- Để thay đổi cài đặt PHP, chọn **14**
- Trong phần cài đặt có các tuỳ chọn như: Thời gian thực thi tối đa, thời gian nhập tối đa, bật/tắt hiển thị lỗi, giới hạn bộ nhớ, bật/tắt tải file lên, kích thước tối đa khi tải file lên, cài đặt/gỡ cài đặt Imagick, Ioncube, Suhosin,...

![image](./image/DLEMP%2033.png)

### Công cụ quản lý WordPress
- Để truy cập các công cụ quản lý WP, chọn **15**
- Tại đây có các chức năng như: cập nhật an toàn cho WP, cập nhật theme và plugin, bật/tắt tự động cập nhật, sao lưu/khôi phục CSDL, sao lưu/khôi phục toàn bộ trang web, xem thông tin của CSDL,...

![image](./image/DLEMP%2034.png)

### Bảo mật cho server và website
- Để vào trang quản lý bảo mật, chọn **16**
- Trang quản lý bảo mật có các tính năng: quản lý các loại tường lửa, kiểm tra và chặn IP DOS, thay đổi cổng SSH, bảo vệ bằng mật khẩu cho đường dẫn, website và trang wp-login.php, thay đổi mật khẩu cho tài khoản root,...

![image](./image/DLEMP%2035.png)

### Tools - Addons (26)
- Các công cụ có thể kể đến như: Tìm nhưng file hoặc thư mục lớn nhất, kiểm tra IP hoặc nameserver của website, sao lưu file cấu hình (config) và Vhost, cấu hình SSH Timeout, cảnh báo dung lượng trống của ổ đĩa thấp,...

![image](./image/DLEMP%2036.png)

### Update System (27)
- Cập nhật hệ thống, Nginx
- Thay đổi phiên bản của phpMyAdmin, MariaDB, PHP

![image](./image/DLEMP%2037.png)

### Check Server Status & Info (31)
- Kiểm trạng thái của server, thông tin về các server đang chạy và lượng RAM sử dụng và kiểm tra thông tin và tài nguyên của server

![image](./image/DLEMP%2038.png)