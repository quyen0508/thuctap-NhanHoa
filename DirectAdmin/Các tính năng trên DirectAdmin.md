# Các tính năng trên DirectAdmin
### Thiết lập Package cho Reseller
Package được thiết lập dưới quyền cấp Admin
##### Tạo Package
- Chọn **Manage Reseller Packages** rồi chọn **Add Packet** 

![image](./image/DA%201.png)

![image](./image/DA%202.png)

- Thiết lập thông số cho Package, chú ý một vài thông số:
    - **Bandwidth**: băng thông được cấp phát cho User
    - **Disk space**: dung lượng ổ cứng cấp phát cho User
    - **Inodes**: số file tối đa được phép tạo
    - **Domains**: số lượng tên miền website được tạo trên User
    - **Email Accounts**: số lượng email mà User có thể tạo
- Đặt tên cho Package vào nhấn **Save** để tạo Package

![image](./image/DA%203.png)

##### Sửa Package
- Tại màn hình Manage Reseller Packages, nhấn vào tên của package để bắt đầu chỉnh sửa các thông số
- Sau khi thay đổi thiết lập package, chọn **Save** để lưu thay đổi

![image](./image/DA%204.png)

##### Xóa Package
- Để xóa package, tại màn hình Manage Reseller Packages, đánh dấu vào cột **Select** ở package muốn xóa rồi chọn **Delete Selected**

![image](./image/DA%205.png)

### Thiết lập Reseller
Reseller được thiết lập dưới quyền cấp Admin
##### Tạo Reseller
- Tại màn hình trang chính, chọn **Create Reseller**

![image](./image/DA%201.png)

- Nhập thông tin cho Reseller và chọn **Submit** để tạo Reseller

![image](./image/DA%206.png)

- Tạo thành công

![image](./image/DA%207.png)

##### Sửa Reseller
- Tại màn hình trang chính, chọn **List Resellers** để mở danh sách Reseller hiện có

![image](./image/DA%201.png)

- Chọn tên Reseller cần sửa đổi thông tin

![image](./image/DA%208.png)

- Chọn **Modify Reseller reseller1** để bắt đầu sửa đổi thông tin

![image](./image/DA%209.png)

- Sau khi thay đổi thông tin, chọn **Save** để lưu thay đổi

![image](./image/DA%2010.png)

##### Xóa Reseller
- Tại trang **List Resellers**, đánh dấu vào ô **Select** và chọn **Delete** để xóa Reseller

![image](./image/DA%2011.png)

- Nhấn **Confirm** để xác nhận xóa

![image](./image/DA%2012.png)

- Xóa thành công

![image](./image/DA%2013.png)

### Thiết lập Package cho User
User được thiết lập dưới quyền cấp Reseller
##### Tạo Package
- Ở trang chính, chọn **Add Package**

![image](./image/DA%2014.png)

- Tùy chỉnh thông số và đặt tên package rồi nhấn **Save** để tạo package mới

![image](./image/DA%2026.png)

##### Chỉnh sửa Package
- Ở trang chính, chọn **Manage User Packages**

![image](./image/DA%2014.png)

- Chọn tên package cần chỉnh sửa

![image](./image/DA%2027.png)

- Thay đổi thông tin và chọn **Submit** để xác nhận thay đổi thông tin

![image](./image/DA%2015.png)

##### Xóa Package
- Tại tràng **Manage User Packages**, đánh dấu vào cột **Select** tại package cần xóa và chọn **Delete**

![image](./image/DA%2016.png)

### Thiết lập User
##### Tạo User
- Tạo màn hình chính, chọn **Add New User**

![image](./image/DA%2014.png)

- Nhập thông tin cho User và chọn **Submit** để tạo User

![image](./image/DA%2017.png)

- Tạo thành công

![image](./image/DA%2018.png)

##### Chỉnh sửa User
- Tại màn hình chính, chọn **List Users**

![image](./image/DA%2014.png)

- Chọn User cần thay đổi thông tin

![image](./image/DA%2019.png)

- Chọn **Modify User user1**

![image](./image/DA%2020.png)

- Chỉnh sửa thông tin sau đó nhấn **Save** để lưu thay đổi

![image](./image/DA%2021.png)

- Chỉnh sửa thành công

![image](./image/DA%2022.png)

##### Xóa User
- Tại trang **List Users**, đánh dấu vào cột **Select** ở User muốn xóa rồi chọn **Delete**

![image](./image/DA%2023.png)

- Chọn **Confirm** để xác nhận xóa

![image](./image/DA%2024.png)

- Xóa thành công

![image](./image/DA%2025.png)

### Chỉnh sửa source code tên miền của user
- Source code của tên miền nằm trong thư mục public_html truy cập thông qua tab Files (FileManager)

![image](./image/DA%2028.png)

![image](./image/DA%2029.png)

- Source code của tên miền là file index.html, để thay đổi source code, có 2 cách:

##### Sửa trực tiếp file index.html thông qua trình chỉnh sửa trực tiếp trên DirectAdmin
- Chọn **Edit** ở cột **Action** của file index.html để truy cập giao diện chỉnh sửa, nếu chưa có, tại tab **Filesystem Tools** ở mục **Create New File** đặt tên file là index.html rồi chọn **Create** để tạo file

![image](./image/DA%2030.png)

- Trong text box, chỉnh sửa nội dung trang web, chọn **Preview Html** để xem trước nội dung của trang trước khi lưu

- Sau khi chỉnh sửa xong, chọn **Save As** để lưu file index.html

![image](./image/DA%2031.png)

- Kết quả hiển thị trên trang web

![image](./image/DA%2032.png)

##### Upload file index.html thông qua FileManager trên DirectAdmin
- Tại thư mục gốc của trang web (/domain/quyennx.xyz/public_html), chọn **Upload files to current directory** để tải file lên

![image](./image/DA%2029.png)

- Chọn file cần upload và chọn **Upload Files**

![image](./image/DA%2033.png)

- Tải file thành công

![image](./image/DA%2034.png)

- Kết quả hiển thị trên trang web

![image](./image/DA%2035.png)

### Thiết lập database
##### Tạo database
- Từ trang chính của User, chọn **MySQL Management**

![image](./image/DA%2036.png)

- Chọn **Create new Database** để truy cập trang tạo mới CSDL

![image](./image/DA%2037.png)

- Nhập các thông tin cho CSDL và chọn **Create** để tạo CSDL

![image](./image/DA%2038.png)

- Tạo thành công

![image](./image/DA%2039.png)

### Cài đặt SSL lên tên miền
##### Sử dụng SSL trả phí
- Đăng ký chứng chỉ SSL tại trang web ssls.com
- Ở trang chính của User, chọn **SSL Certificates** tại **Advanced Features**

![image](./image/DA%2040.png)

- Chọn **Paste a pre-generated certificate and key** và dán theo thứ tự private key -> certificate vào text box rồi chọn **Save** để lưu lại chứng chỉ

![image](./image/DA%2041.png)

- Kiểm tra kết quả trên trang web

![image](./image/DA%2042.png)

### Thiết lập CustomBuild
- Để truy cập CustomBuild, chọn **CustomBuild 2.0** tại trang chính của Admin Level

![image](./image/DA%2043.png)

#### Thiết lập bằng giao diện
##### Update các phần mềm đã cài đặt
- Tại tab **Update Software**, danh sách các phần mềm đang có bản cập nhật sẽ xuất hiện tại đây, chọn **Update** để cập nhật cho phần mềm đó

![image](./image/DA%2044.png)

- Quá trình cập nhật

![image](./image/DA%2045.png)

##### Cài đặt các phần mềm mới
- Tại tab **Build Software**, danh sách các phần mềm có thể cài đặt được trên server sẽ xuất hiện tại đây

- Để cài đặt/cập nhật các phần mềm, chọn **Build** ở phần mềm muốn được cài đặt

![image](./image/DA%2046.png)

- Quá trình cài đặt

![image](./image/DA%2047.png)

#### Thiết lập bằng dòng lệnh
##### Build PHP
- Trỏ đường dẫn tới thư mục /usr/local/directadmin/custombuild
- Tạo 4 cấu hình PHP với mode là php-fpm
```sh
./build set php1_mode php-fpm
./build set php2_mode php-fpm
./build set php3_mode php-fpm
./build set php4_mode php-fpm
```

- Gán từng phiên bản PHP cho từng cấu hình
```sh
./build set php1_release 5.6
./build set php2_release 7.0
./build set php3_release 7.3
./build set php4_release 7.4
```

- Build PHP
```sh
./build php n
```

- Nếu gặp thông báo ```Your DirectAdmin version (1.61) is older than minimal required for this version of CustomBuild (1.63)``` thì chạy lệnh để hạ phiên bản DirectAdmin xuống thành 1.61
```sh
sed -i 's/1.63/1.61/g'  /usr/local/directadmin/custombuild/build
```

- Lưu lại cấu hình
```sh
./build rewrite_confs
```

- Để chọn phiên bản PHP, truy cập **Domain Setup** dưới **User Level**

![image](./image/DA%2048.png)

- Chọn tên miền cần thay đổi phiên bản PHP

![image](./image/DA%2049.png)

- Tại mục **PHP Version Selector**, chọn phiên bản PHP tại cột **Handler** của **First PHP** và chọn **Save** để thay đổi phiên bản

![image](./image/DA%2050.png)

- Thay đổi thành công

![image](./image/DA%2051.png)

- Để kiểm tra phiên bản PHP, tạo file info.php tại thư mục public_html của tên miền

![image](./image/DA%2052.png)

- Nội dung file info.php

![image](./image/DA%2053.png)

- Kiểm tra trên trình duyệt bằng đường dẫn ```tên-miền/info.php```

![image](./image/DA%2054.png)

#### Build webserver chuyển đổi giữa Apache và NGINX
- Chuyển thư mục làm việc về /usr/local/directadmin/custombuild/ để dễ dàng thao tác hơn bằng lệnh
```sh
cd /usr/local/directadmin/custombuild/
```

- Kiểm tra webserver đang được sử dụng tại file options.conf bằng lệnh
```sh
vi options.conf
```

- Tại dòng 27, webserver hiện tại đang là apache

![image](./image/DA%2055.png)

- Để chuyển đổi sang nginx, sửa apache thành nginx và lưu file lại

- Chạy lệnh ```./build update``` để cập nhật danh sách build

- Chạy lệnh ```./build nginx``` để CustomBuild thực hiện thay thế Apache bằng NGINX

- Nếu gặp thông báo ```Your DirectAdmin version (1.61) is older than minimal required for this version of CustomBuild (1.63)``` thì chạy lệnh để hạ phiên bản DirectAdmin xuống thành 1.61
```sh
sed -i 's/1.63/1.61/g'  /usr/local/directadmin/custombuild/build
```

- Sau khi build xong, lưu lại thiết lập file config bằng lệnh
```sh
./build rewrite_confs
```

- Để chuyển ngược lại từ NGINX sang Apache, cần sửa lại dòng 27 của file options.conf từ nginx thành apache sau đó chạy các lệnh tương tự như khi chuyển từ Apache sang NGINX

#### Kết hợp NGINX và Apache
- Apache có ưu điểm tốt hơn NGINX trong việc xử lý các web động, ngược lại, NGINX lại tốt hơn Apache trong việc xử lý web tĩnh
- Do đó, kết hợp cả 2 sẽ giúp tận dụng được hết khả năng của 2 loại webserver này
- NGINX được sử dụng như một reverse proxy của Apache. Đối với các nội dung tĩnh, NGINX xử lý nhanh chóng và trực tiếp cho client, còn đối với nội dung động, NGINX sẽ chuyển cho Apache thực hiện rồi gửi kết quả ngược về NGINX để trả về cho client
- Đơn giản hơn thì NGINX xử lý các nội dung tĩnh như HTML, CSS, JS,... còn Apache xử lý các nội dung động như PHP,...
- Để build reverse proxy NGINX-Apache sửa file cấu hình options.conf tại đường dẫn /usr/local/directadmin/custombuild/
```sh
cd /usr/local/directadmin/custombuild
vi options.conf
```

- Sửa giá trị webserver tại dòng 27 thành nginx_apache

![image](./image/DA%2056.png)

- Chạy lệnh ```./build update``` để cập nhật danh sách build

- Chạy lệnh ```./build nginx_apache``` để CustomBuild thực hiện build nginx_apache

- Nếu gặp thông báo ```Your DirectAdmin version (1.61) is older than minimal required for this version of CustomBuild (1.63)``` thì chạy lệnh để hạ phiên bản DirectAdmin xuống thành 1.61
```sh
sed -i 's/1.63/1.61/g'  /usr/local/directadmin/custombuild/build
```

- Sau khi build xong, lưu lại thiết lập file config bằng lệnh
```sh
./build rewrite_confs
```

#### Cài đặt OpenLiteSpeed
- OpenLiteSpeed là phiên bản mã nguồn mở và miễn phí của phiên bản LiteSpeed Web Server Enterprise. OpenLiteSpeed chứa gần hết các tính năng cần thiết có trong LiteSpeed EnterPrise, bao gồm LSCache - là một plugin cần thiết cho WordPress
- Chuyển thư mục làm việc về /usr/local/directadmin/custombuild/ để dễ dàng thao tác hơn bằng lệnh
```sh
cd /usr/local/directadmin/custombuild/
```

- Cập nhật lại tập lệnh CustomBuild bằng lệnh
```sh
./build update
```

- Thay đổi cấu hình webserver thành OpenLiteSpeed
```sh
./build set webserver openlitespeed
```

- Tắt mod_ruid2 vì mod_ruid2 chỉ hoạt động với Apache
```sh
./build set mod_ruid2 no
```

- Chỉnh mode của các phiên bản PHP thành lsphp
```sh
./build set php1_mode lsphp
./build set php2_mode lsphp
./build set php3_mode lsphp
./build set php4_mode lsphp
```

- Thực hiện build OpenLiteSpeed
```sh
./build openlitespeed
```

- Nếu gặp thông báo ```Your DirectAdmin version (1.61) is older than minimal required for this version of CustomBuild (1.63)``` thì chạy lệnh để hạ phiên bản DirectAdmin xuống thành 1.61
```sh
sed -i 's/1.63/1.61/g'  /usr/local/directadmin/custombuild/build
```

- Build lại các phiên bản PHP để tương thích với OpenLiteSpeed
```sh
./build php n
```

- Lưu lại các thiết lập
```sh
./build rewrite_confs
```

- Lưu ý: Dashboard của OpenLiteSpeed chạy trên cổng 7080, vì vậy cần mở cổng trong firewall để có thể truy cập

#### Cài đặt ImunifyAV
- ImunifyAV là một phần mềm miễn phí có thể quét hầu hết các mã nguồn PHP nhằm giúp phát hiện các phần mềm độc hại
- Để cài đặt, thực hiện lệnh tải file cài và tiến hành chạy file cài bằng lệnh
```sh
wget https://repo.imunify360.cloudlinux.com/defence360/imav-deploy.sh
bash imav-deploy.sh
```

- Để cập nhật cơ sở dữ liệu và phiên bản mới nhất của ImunifyAV, sử dụng lệnh
```sh
yum update imunify-antivirus
```

- ImunifyAV có thể được tìm thấy trong trang chính của Admin Level tại mục **Extra Features**

![image](./image/DA%2057.png)

- Giao diện chính của ImunifyAV

![image](./image/DA%2058.png)

#### Cài đặt Imagick
- Imagick là bộ phần mềm xử lý các file ảnh, dùng để tạo và sửa đổi các hình ảnh sử dụng Imagick API
- Imagick có khả năng đọc, ghi và chuyển đổi nhiều định dạng file ảnh như JPEG, GIF, PNG, TIFF, PDF, PostScript và SVG,...
- Imagick có thể dùng để thực hiên các thao tác đơn giản với hình ảnh như dịch chuyển, xoay hình, lật hình, thu phóng, kéo xiên hình, hiệu chỉnh màu sắc hoặc vẽ thêm chữ và các khối hình vào file hình ảnh sẵn có
- Để cài đặt Imagick, chuyển thư mục làm việc về /usr/local/directadmin/custombuild/ để dễ dàng thao tác hơn bằng lệnh
```sh
cd /usr/local/directadmin/custombuild/
```

- Sử dụng lệnh ```./build update``` để cập nhật CustomBui;d

- Sử dụng lệnh ```./build set imagick yes``` để sửa để thay đổi cài đặt trong file options.conf

- Sử dụng lệnh để cài đặt bản build
```sh
./build imagick
```

- Nếu gặp thông báo ```Your DirectAdmin version (1.61) is older than minimal required for this version of CustomBuild (1.63)``` thì chạy lệnh để hạ phiên bản DirectAdmin xuống thành 1.61
```sh
sed -i 's/1.63/1.61/g'  /usr/local/directadmin/custombuild/build
```

- Build lại các phiên bản PHP để tương thích với OpenLiteSpeed
```sh
./build php n
```

- Kiểm tra việc cài đặt thành công trên trang tên-miền/info.php

![image](./image/DA%2063.png)

### Backup/Restore User
- Để backup và restore cho User, truy cập trang chính của User Level chọn **Create/Restore Backups** tại **Your Account**

![image](./image/DA%2059.png)

- Chọn những mục muốn sao lưu và chọn **Create Backup** để tiến hành sao lưu, quá trình sao lưu có thể mất nhiều thời gian tùy thuộc vào lượng dữ liệu cần sao lưu

![image](./image/DA%2060.png)

- Để khôi phục lại các bản sao lưu, chọn phiên bản đã được sao lưu ở dưới tùy chọn sao lưu và chọn **Select Restore Options**

![image](./image/DA%2061.png)

- Chọn các mục muốn khôi phục từ bản sao lưu và chọn **Restore Selected Items**, quá trình có thể mất nhiều thời gian tùy thuộc vào lượng dữ liệu cần khôi phục

![image](./image/DA%2062.png)