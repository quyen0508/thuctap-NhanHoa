# Giới thiệu về iptables
- Iptables là một hệ thống tưởng lửa tiêu chuẩn, được cấu hình, tích hợp mặc định trong hầu hết các bản phân phối của hệ điều hành Linux (CentOS, Ubuntu,...)
- Iptables hoạt động dựa trên việc phân loại và thực thi các package ra/vào theo các quy tắc được thiết lập từ trước

### Các thao tác với iptables
#### Cài đặt iptables
- Cài đặt gói ```iptables```
```sh
yum install -y iptables-services
```

- Kiểm tra phiên bản và trạng thái của ```iptables```
```sh
rpm -q iptables
service iptables
```

- Khởi động dịch vụ và thiết lập khởi động cùng hệ điều hành
```sh
systemctl start iptables
systemctl enable iptables
systemctl start ip6tables
systemctl enable ip6tables
```

#### Cấu hình iptables
##### Mở port
- Để mở port trong iptables, sử dụng lệnh
```sh
iptables -A INPUT -p <tcp/udp> -m <tcp/udp> --dport <port> -j ACCEPT
```

hoặc

```sh
iptables -I INPUT -p <tcp/udp> -m <tcp/udp> --dport <port> -j ACCEPT
```

Trong đó:
- ```-A```: chèn chuỗi INPUT vào cuối chuỗi luật
- ```-I```: chèn chuỗi INPUT vào dòng chỉ định, nếu không được chỉ định dòng, iptables sẽ mặc định đặt trên đầu chuỗi
- ```-p```: protocol, xác định giao thức
- ```-m```: Match Extensions

- Nên sử dụng tuỳ chọn ```-I``` để tránh xung đột với chuỗi rule gốc

##### Chặn IP truy cập
- Thêm luật chặn bằng lệnh
```sh
iptables -A INPUT -s <địa-chỉ-IP> -j DROP
```

- Để chặn 1 IP truy cập 1 port cụ thể, sử dụng lệnh
```sh
iptables -A INPUT -p tcp -s <địa-chỉ-IP> -dport <port> -j DROP
```

- Chặn kết nối đến từ địa chỉ IP bị chặn mà vẫn có thể kết nối đến địa chỉ IP đó
```sh
iptables -P OUTPUT ACCEPT
iptables -P INPUT DROP
```

- Khởi động lại dịch vụ để bắt đầu có hiệu lực
```sh
systemctl restart iptables
```

##### Xoá rule
- Hiện thị danh sách luật kèm theo chỉ số dòng của luật
```sh
iptables -L INPUT --line-numbers
```

- Xoá luật theo chỉ số dòng của luật
```sh
iptables -D INPUT <chỉ-số-dòng>
```