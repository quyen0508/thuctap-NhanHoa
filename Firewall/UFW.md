# Giới thiệu về UFW
- UFW viết tắt của Uncomplicated Firewall
- UFW là giao diện của iptables nhằm mục đích làm đơn giản hoá cấu hình tường lửa
- Vì iptables là công cụ có độ linh hoạt cao nên không phù hợp cho người mới dử dụng

### Các thao tác với UFW
#### Cài đặt UFW
- Cài đặt bằng lệnh
```sh
yum install -y ufw
```

- Khởi chạy UFW
```sh
ufw enable
```

- Kiểm tra hoạt động của UFW và bảng các rule
```sh
ufw status
```
- Tắt UFW
```sh
ufw disable
```

#### Cấu hình UFW
##### Chặn địa chỉ IP
Sử dụng lệnh theo cú pháp
```sh
ufw deny from <địa-chỉ-ip>
```

Ví dụ
```sh
ufw deny from 192.168.1.100
```

##### Chặn một dải mạng
Sử dụng lệnh
```sh
ufw deny from <địa-chỉ-dải-mạng>/<subnet-mask>
```

Ví dụ
```sh
ufw deny from 192.168.1.0/24
```

##### Cho phép địa chỉ IP kết nối đến
Sử dụng lệnh
```sh
ufw allow from <địa-chỉ-ip>
```

Ví dụ
```sh
ufw allow from 192.168.1.100
```

##### Cho phép kết nối tới các giao diện mạng (interface)
Sử dụng lệnh
```sh
ufw allow in on <interface> from <địa-chỉ-ip>
```

Ví dụ
```sh
ufw allow in on eth0 from 192.168.1.100
```

##### Xoá rule
- Trước tiên, phải liệt kê danh sách rule có đánh số thứ tự
```sh
ufw status numbered
```

- Xoá rule bằng lệnh
```sh
ufw delete <chỉ-số-của-rule>
```

##### Cho phép kết nối đến port từ tất cả các địa chỉ IP
Sử dụng lệnh
```sh
ufw allow <port>
```

Ví dụ, mở port 110
```sh
ufw allow 110
```

##### Chặn kết nối đến port từ tất cả các địa chỉ IP
Sử dụng lệnh
```sh
ufw deny <port>
```

Ví dụ, chặn cổng 143
```sh
ufw deny 143
```

##### Cho phép ứng dụng cụ thể
Sử dụng lệnh
```sh
ufw allow <tên-ứng-dụng>
```

Ví dụ
```sh
ufw allow VNC
```

##### Chặn ứng dụng cụ thể
Sử dụng lệnh
```sh
ufw deny <tên-ứng-dụng>
```

Ví dụ
```sh
ufw deny VNC
```

##### Cho phép địa chỉ IP truy cập tới ứng dụng
Sử dụng lệnh
```sh
ufw allow from <địa-chỉ-ip> to any app <tên-app-profile>
```

Ví dụ
```sh
ufw allow from 192.168.1.100 to any app VNC
```

##### Chặn địa chỉ IP truy cập tới ứng dụng
Sử dụng lệnh
```sh
ufw deny from <địa-chỉ-ip> to any app <tên-app-profile>
```

Ví dụ
```sh
ufw deny from 192.168.1.100 to any app VNC
```

##### Cho phép kết nối tới dịch vụ cụ thể
```sh
ufw allow <tên-dịch-vụ>
```

Ví dụ
```sh
ufw allow imap
```

##### Chặn kết nối tới dịch vụ cụ thể
```sh
ufw deny <tên-dịch-vụ>
```

Ví dụ
```sh
ufw deny imap
```