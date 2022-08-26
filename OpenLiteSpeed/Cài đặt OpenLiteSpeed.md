# Cài đặt OpenLiteSpeed
- Cập nhật các gói phần mềm lên phiên bản mới nhất bằng lệnh

```sh
yum install epel-release -y
yum update -y
```

- Cài đặt mã nguồn OpenLiteSpeed

```sh
rpm -ivh http://rpms.litespeedtech.com/centos/litespeed-repo-1.1-1.el7.noarch.rpm
yum install openlitespeed -y
```

- Cài đặt PHP 7.4

```sh
yum install lsphp74 lsphp74-gd lsphp74-json lsphp74-common lsphp74-process lsphp74-mbstring lsphp74-mysqlnd lsphp74-xml lsphp74-opcache lsphp74-mcrypt lsphp74-pdo lsphp74-imap lsphp74-bcmath lsphp74-pecl-memcache lsphp74-pecl-memcached lsphp74-pecl-redis lsphp74-pgsql lsphp74-zip -y
```

- Thiết lập tài khoản Admin cho OpenLiteSpeed WebAdmin GUI: Nhập thông tin đăng ký tài khoản

```sh
/usr/local/lsws/admin/misc/admpass.sh
```

![image](./image/OLS%201.png)

- Mở port cho OpenLiteSpeed: OpenLiteSpeed hoạt động trên cổng 7080

```sh
firewall-cmd --zone=public --add-port=7080/tcp --permanent
firewall-cmd --reload
```

- Cài đặt MySQL: Tham khảo tại [cài đặt MySQL](https://github.com/quyen0508/thuctap-NhanHoa/blob/main/LAMP/LAMP.md#c%C3%A0i-%C4%91%E1%BA%B7t-mysql)

- Truy cập trang web và đăng nhập

![image](./image/OLS%202.png)

- Giao diện chính

![image](./image/OLS%203.png)

- Cấu hình OpenLiteSpeed trông WebAdmin GUI
    - Mặc định OpenLiteSpeed sẽ sử dụng PHP 5.6, vì vậy cần cấu hình lại thành PHP 7.4
    - Truy cập **External App** tại **Server Configuration** và chọn **Add**
    
    ![image](./image/OLS%204.png)
    - Tại mục **Type**, chọn **LiteSpeed SAPI App**

    ![image](./image/OLS%205.png)
    - Nhập thông tin cho **LiteSpeed SAPI App**

    ![image](./image/OLS%206.png)
    - Chuyển sang **Script Handler**, chọn **Edit** để sửa thành PHP 7.4
    - Ở **Handler Name**, chọn **lsphp74** và chọn **Save** để lưu lại

- Cấu hình OpenLiteSpeed sử dụng port 80
    - Vì mặc định OpenLiteSpeed lắng nghe trên port 8088 nên sẽ phải cấu hình lại thành port 80
    - Truy cập **Listeners**, chọn **View** tại port 8088

    ![image](./image/OLS%207.png)
    - Chọn **Edit** để sửa port

    ![image](./image/OLS%208.png)
    - Sửa giá trị tại mục **Port** và chọn **Save** để lưu cấu hình

    ![image](./image/OLS%209.png)
    - Để áp dụng tất cả các thay đổi trên, chọn **Graceful Restart**

    ![image](./image/OLS%2010.png)

- Kiểm tra kết quả bằng cách truy cập trang web tại cổng 80

![image](./image/OLS%2011.png)

- Để kiểm tra phiên bản PHP, tại mục **Test PHP**, chọn **Click Here >>**

![image](./image/OLS%2012.png)

![image](./image/OLS%2013.png)