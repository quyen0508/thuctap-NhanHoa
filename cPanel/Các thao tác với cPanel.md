# Các thao tác với cPanel
### Tạo Package
- Tại tab **Packages**, chọn **Add a Package** và nhập các thông số như tên package, giới hạn dung lượng ổ đĩa, giới hạn lưu lượng băng thông mạng hàng tháng, số tài khoản FTP, email,... và nhấn **Add** để thêm

![image](./image/cPanel%208.png)

### Chỉnh sửa Package
- Tại tab **Packages**, chọn **Edit a Package**, chọn package cần chỉnh sửa rồi chọn **Edit**

![image](./image/cPanel%209.png)

- Sửa lại các thông số rồi chọn **Save changes** để lưu thay đổi

![image](./image/cPanel%2010.png)

### Xoá Package
- Tại tab **Package**, chọn **Delete a Package** và chọn package cần xoá, sau đó nhấn **Delete** để xoá package

![image](./image/cPanel%2011.png)

- Xoá thành công

![image](./image/cPanel%2012.png)

### Tạo Account
- Mỗi account tương ứng với một domain
- Tại tab **Account Functions**, chọn **Create a New Account** và nhập các thông số như tên miền, usernane, password địa chỉ email và chọn gói package, sau đó **Create** để tạo mới account

![image](./image/cPanel%2013.png)

### Chỉnh sửa Account
- Tại tab **Account Functions**, chọn **Modify an Account** và chọn tài khoản muốn chỉnh sửa rồi nhấn **Modify**

![image](./image/cPanel%2014.png)

- Chỉnh sửa thông tin và chọn **Save** để lưu thay đổi

![image](./image/cPanel%2015.png)

### Xoá Account
- Tại tab **Account Infomation**, chọn **List Accounts** và nhấn dấu "+" ở đầu dòng account cần xoá để mở rộng thanh tuỳ chọn, sau đó chọn **Terminate Account**

![image](./image/cPanel%2016.png)

- Chọn **Yes, remove this account** để xác nhận xoá account

![image](./image/cPanel%2017.png)

### Cài đặt chứng chỉ SSL Let's Encrypt
- Truy cập trang quản lý website của cPanel qua cổng 2083 và đăng nhập vào tài khoản tương ứng với tên miền cần cài

![image](./image/cPanel%2018.png)

- Trước tiên cần gỡ chứng chỉ SSL self-sign có sẵn trên tên miền

- Tại tab **Security**, chọn **SSL/TLS**

![image](./image/cPanel%2019.png)

- Chọn **Manage SSL site**

![image](./image/cPanel%2020.png)

- Chọn **Uninstall** để gỡ cài đặt các chứng chỉ cũ

![image](./image/cPanel%2021.png)

- Quay trở về trang chính, vẫn tại tab **Security**, chọn **SSL/TLS Status**

![image](./image/cPanel%2019.png)

- Chọn tất cả các tên miền cần được cấp chứng chỉ SSL và chọn **Run AutoSSL**

![image](./image/cPanel%2022.png)

- SSL tạo thành công

![image](./image/cPanel%2023.png)

- Kết quả trên trang web

![image](./image/cPanel%2024.png)

### Cài đặt trang web WordPress
- Tại tab **Plugins**, chọn **WordPress Toolkit**
- Chọn **Install** hoặc **Install WordPress**

![image](./image/cPanel%2025.png)

- Nhập các thông số của trang web và chọn **Install** sau khi hoàn tất

![image](./image/cPanel%2026.png)

- Chọn **Install Plugins** nếu muốn cài đặt các plugin luôn hoặc **No, thanks** để cài đặt sau

![image](./image/cPanel%2027.png)

- Truy cập trang web bằng trình duyệt

![image](./image/cPanel%2028.png)

### Tạo Addon Domain
- cPanel cho phép người dùng tạo nhiều domain trên cùng một tài khoản (account) giúp quản lý đa tên miền tốt hơn
- Để cài đặt, đăng nhập vào trang cPanel của người dùng, tại tab **DOMAINS** chọn **Addon Domains**

![image](./image/cPanel%2029.png)

- Nhập tên miền của trang web, mặc định, cPanel sẽ tự động điền Subdomain và Document Root, sau đó chọn **Add Domain** khi đã hoàn tất

![image](./image/cPanel%2030.png)

- Trong trường hợp báo lỗi không thể tạo Addon Domain, truy cập trang WHM, trong **Server Configuration**, chọn **Tweak Settings**, trỏ đến tab **Domains** và bật 2 tuỳ chọn sau

![image](./image/cPanel%2031.png)

### Tạo Subdomain
- Để cài đặt, đăng nhập vào trang cPanel của người dùng, tại tab **DOMAINS** chọn **Subdomains**

![image](./image/cPanel%2029.png)

- Nhập tên subdomain và chọn thêm cho domain tương ứng sau đó chọn **Create** để thêm subdomain

![image](./image/cPanel%2032.png)

### Quản lý Domain
- Để quản lý, chọn **Domains** trong tab **DOMAINS**

![image](./image/cPanel%2029.png)

- Tại đây có thể yêu cầu bắt buộc chuyển hướng HTTPS (Force HTTPS Redirect), tại email hay quản lý chi tiết hơn cho từng domain

![image](./image/cPanel%2033.png)

- Để xoá một domain, chọn **Manage** tương ứng với domain cần xoá
- Chọn **Remove Domain** để tiến hành xoá

![image](./image/cPanel%2034.png)

- Chọn **Yes, Remove This Domain** để xác nhận xoá

![image](./image/cPanel%2035.png)

### Quản lý Aliases
- Alias Domain là tên miền bí danh, hoạt động đồng thời với tên miền chính. Khi truy cập vào tên miền bí danh, nội dung trang web sẽ trỏ về tên miền chính
- Để tạo một tên miền bí danh trong cPanel, truy cập trang quản lý cPanel, chọn **Aliases** tại **DOMAINS**

![image](./image/cPanel%2029.png)

- Nhập tên miền vào mục **Domain** và chọn **Add Domain** để tiến hành tạo tên miền bí danh

![image](./image/cPanel%2049.png)

- Kiểm tra bằng trình duyệt
    - Trang tên miền chính

    ![image](./image/cPanel%2050.png)

    - Trang tên miền bí danh (Alias)

    ![image](./image/cPanel%2051.png)

- Để xoá Alias đã tạo, ở mục **Remove Aliases**, chọn **Remove** tại tên miền bí danh cần xoá

![image](./image/cPanel%2057.png)

### Quản lý Redirects
- Redirects là chức năng cho phép chuyển hướng từ 1 trang web sang 1 trang web khác
- Để sử dụng, truy cập **Redirects** tại **DOMAINS**

![image](./image/cPanel%2029.png)

- Nhập thông tin cho việc chuyển hướng như loại Redirect (301 - Permanent hay 302 - Temporary), trang web cần chuyển hướng, thực hiện việc chuyển hướng khi gặp đường dẫn được thiết lập và trang web được chuyển hướng tới
- Sau khi hoàn tất, chọn **Add** để thêm Redirect

![image](./image/cPanel%2055.png)

- Để xoá Redirect đã tạo, chọn **Delete** tương ứng với tên miền cần xoá

![image](./image/cPanel%2056.png)

### Quản lý Cron Jobs
- Cron Jobs giúp thực thi các lệnh một cách tự động khi đạt tới điều kiện thời gian đã thiết lập trước
- Để mở trang quản lý Cron Jobs, truy cập trang cPanel, ở tab **ADVANCED**, chọn **Cron Job**

![image](./image/cPanel%2036.png)

- Lựa chọn thời gian và nhập lệnh (command) sau đó chọn **Add New Cron Job** để thêm cron job

![image](./image/cPanel%2037.png)

- Tab **Current Cron Job** dùng để quản lý các cron job hiện có, có thể thực hiện các hành động như sửa hoặc xoá các cron job

![image](./image/cPanel%2038.png)

- Để sửa một cron job, chọn **Edit** tương ứng với cron job đó, sau đó sửa thông tin của cron job và nhấn **Edit Line** để lưu thay đổi

![image](./image/cPanel%2039.png)

- Để xoá một cron job, chọn **Delete** tương ứng với cron job đó, sau đó chọn **Delete** để xác nhận xoá

![image](./image/cPanel%2040.png)

### Backup/Restore
- cPanel cung cấp các tuỳ chọn để sao lưu và khôi phục lại dữ liệu
- Để truy cập, chọn **Backup** trong mục **FILES**

![image](./image/cPanel%2041.png)

- Tại đây có các tuỳ chọn sao lưu như: sao lưu toàn bộ, sao lưu từng phần (sao lưu Home Directory, MySQL Database, Email Forwarders và Email Filters)

![image](./image/cPanel%2042.png)

![image](./image/cPanel%2043.png)


##### Sao lưu toàn bộ
- Để sao lưu toàn bộ, chọn **Download a Full Account Backup**, chọn vị trí sao lưu đích, lựa chọn thông báo và chọn **Generate Backup** để tiến hành sao lưu

![image](./image/cPanel%2044.png)

- Sau khi sao lưu thành công, file sẽ được hiển thị tại mục **Backup Availabel for Download**, từ đây có thể tải xuống file

![image](./image/cPanel%2045.png)

##### Sao lưu/Khôi phục một phần
- Để sao lưu Home Directory, chọn **Home Directory** dưới mục **Download a Home Directory Backup**
- Để khôi phục, chọn file sao lưu tương ứng và chọn **Upload**

![image](./image/cPanel%2046.png)

![image](./image/cPanel%2047.png)

### Quản lý file
- cPanel tích hợp sẵn trình quản lý file với đường dẫn tương ứng với từng tài khoản (tên miền) được tách biệt với nhau
- Các chức năng của File Manager: Tạo File/Folder, Sao chép (Copy), Di chuyển (Move), Tải file lên từ máy tính (Upload), Tải file về máy tính (Download), Xoá File/Folder (Delete), Khôi phục (Restore), Đổi tên (Rename), Sửa File (Edit), Cài đặt quyền cho file (Permission),...

![image](./image/cPanel%2048.png)

### Quản lý phiên bản PHP của các trang web
- Truy cập **MultiPHP Manager** trong **SOFTWARE**

![image](./image/cPanel%2052.png)

- Lựa chọn phiên bản muốn thay đổi và chọn trang web muốn thay đổi, sau đó chọn **Apply** để tiến hành thay đổi phiên bản

![image](./image/cPanel%2053.png)

- Trang web đã được thay đổi phiên bản PHP

![image](./image/cPanel%2054.png)

