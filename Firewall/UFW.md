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

- Kiểm tra hoạt động
```sh
ufw status
```
- Tắt UFW
```sh
ufw disable
```

#### Cấu hình UFW