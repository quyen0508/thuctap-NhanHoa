# Giới thiệu về CSF
- CSF viết tắt của Config Server & Firewall là một gói ứng dụng hoạt động trên Linux như một Firewall được phát hành miễn phí nhằm tăng tính bảo mật cho server (VPS và Dedicated)
- CSF hoạt động dựa trên iptables và tiến trình ldf để giải quyết các file log để phát hiện các dấu hiệu tấn công bất thường

### Các tính năng chính của CSF
- Chống DoS các loại
- Chống Scan Port
- Đưa ra các khuyến nghị về việc cấu hình server (ví dụ như gợi ý nâng cấp MySQL lên bản mới hơn)
- Chống Brute Force Attack vào các dịch vụ server hay Control Panel,...
- Chống Syn Flood
- Chống Ping Flood
- Cho phép ngăn chặn truy cập từ một quốc qua cụ thể
- Hỗ trợ cả IPv4 và IPv6
- Cho phép khoá IP tạm thời và vĩnh viễn ở tầng mạng (an toàn hơn ở tầng ứng dụng) giúp giảm tải cho webserver
- Cho phép chuyển hướng yêu cầu từ các địa chỉ IP bị khoá sang trang web html để thông báo cho người dùng biết địa chỉ IP của họ đang bị khoá

### Các thao tác với CSF
#### Cài đặt CSF
- Cài đặt module Perl cho CSF script
```sh
yum install -y perl-libwww-perl
```

- Tải CSF
```sh
cd /tmp
wget https://download.configserver.com/csf.tgz
```

- Giải nén và cài đặt
```sh
tar -xzf csf.tgz
cd csf
sh install.sh
```

#### Cấu hình CSF
- Mặc định, CSF sẽ chạy ở chế độ "Testing", do đó server chưa được bảo vệ toàn diện.
- Để tắt chế độ này, trước tiên cần thiết lập các thông số TCP_IN, TCP_OUT, UDP_IN và UDP_OUT theo nhu cầu sử dụng
- Để chỉnh sửa, mở file cấu hình
```sh
nano /etc/csf/csf.conf
```

![image](./image/CSF%201.png)

![image](./image/CSF%202.png)

- Khởi động và cài đặt khởi động cùng hệ thống
```sh
systemctl start csf
systemctl enable csf
```

##### Các file cấu hình của CSF
- Các file cấu hình của CSF đều được đặt tại thư mục /etc/csf
    - ```csf.conf```: File cấu hình chính dùng để quản lý CSF
    - ```csf.allow```: Danh sách địa chỉ IP cho phép qua firewall
    - ```csf.deny```: Danh sách địa chỉ IP từ chối qua firewall
    - ```csf.ignore```: Danh sách địa chỉ IP cho phép firewall và không bị block nếu có vấn đề
    - ```csf.*ignore```: Danh sách user, IP, chương trình,... được bỏ qua

##### Một số lệnh thông dụng
- Chặn 1 địa chỉ IP
```sh
csf -d 192.168.1.100
```

- Bỏ chặn 1 địa chỉ IP
```sh
csf -dr 192.168.1.100
```

- Cho phép 1 địa chỉ IP
```sh
csf -a 192.168.1.100
```

- Bỏ cho phép 1 địa chỉ IP
```sh
csf -ar 192.168.1.100
```

- Kiểm tra địa chỉ IP có bị chặn hay không
```sh
csf -g 192.168.1.100
```

- Mở CSF
```sh
csf -e
```

- Tắt CSF
```sh
csf -x
```

- Khởi động lại CSF
```sh
csf -r
```

#### Gỡ cài đặt CSF
- Sử dụng lệnh
```sh
/etc/csf/uninstall.sh
```