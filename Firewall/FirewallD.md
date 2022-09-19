# Giới thiệu về FirewallD
- FirewallD là giải pháp tường lửa mạnh mẽ tương tự như CSF, được cài mặc định trên RHEL 7 hoặc CentOS 7 nhằm thay thế iptables
- FirewallD sử dụng "zones" và "services" thay vì "chain" và "rule" trong iptables đem lại khả năng dễ dàng cấu hình hơn
- FirewallD quản lý các quy tắc được thiết lập tự động, có tác dụng ngay lập tức mà không làm mất các kết nối và session hiện có

### Zone
- Zone là một nhóm quy tắc nhằm chỉ ra những luồng dữ liệu được cho phép, đựa trên mức độ tin tưởng của điểm xuất phát luồng dữ liệu đó trong hệ thống mạng
- Các zone được xác định trước theo mức độ tin cậy, theo thứ tự từ ít tin cậy nhất đến đáng tin cậy nhất:
    - ```drop```: ít tin cậy nhất - toàn bộ các kết nối đến sẽ bị từ chối mà không phản hồi, chỉ cho phép duy nhất kết nối đi ra
    - ```block```: tương tự với ```drop``` nhưng các kết nối đến sẽ bị từ chối và phản hồi bằng tin nhắn icmp-host-prohibited (hoặc icmp6-adm-prohibited)
    - ```public```: đại diện cho mạng công cộng - không đáng tin cậy, các máy tính/services khác không được tin tưởng trong hệ thống nhưng vẫn cho phép các kết nối đến trên cơ sở cho từng trường hợp cụ thể
    - ```external```: hệ thống mạng bên ngoài trong trường hợp tường lửa được sử dụng làm gateway, được cấu hình giả lập NAT để giữ bảo mật mạng nội bộ mà vẫn có thể truy cập
    - ```internal```: trái lại với external, internal được sử dụng cho phần nội bộ của gateway, các máy tính/services thuộc zone này khá tin cậy
    - ```dmz```: sử dụng cho các máy tính/services ở khu vực DMZ (Demilitarized) - cách ly không cho phép truy cập vào phần còn lại của hệ thống mạng, chỉ cho phép một số kết nối đến nhất định
    - ```work```: sử dụng trong công việc, tin tường hầu hết các máy tính và một vài services được phép hoạt động
    - ```home```: tin tưởng hầu hết các máy tính khác và thêm một vài services được cho phép hoạt động
    - ```trusted```: đáng tin cậy nhất - tin tưởng toàn bộ thiết bị trong hệ thống

- Trong FirewallD, các quy tắc được cấu hình thời gian hiệu lực theo Runtime hoăc Permanent:
    - Runtime (mặc định): các quy tắc được áp dụng ngay lập tức tại phiên hiện tại, khởi động lại dịch vụ hoặc hệ thống sẽ mất hiệu lực
    - Permanent: các quy tắc không được áp dụng tại phiên hiện tại nhưng có hiệu lực vĩnh viễn, chỉ cần khởi động lại dịch vụ hoặc hệ thống là bắt đầu có hiệu lực

- Việc khởi động lại dịch vụ sẽ huỷ toàn bộ các thiết lập Runtime và đồng thời áp dụng thiết lập Permanent mà không phá vỡ các kết nối và session hiện tại

### Các thao tác với FirewallD
#### Cài đặt FirewallD
- Trước tiên, đảm bảo hệ thống cập nhật lên phiên bản mới nhất
```sh
yum -y update
```

- Cài đặt FirewallD nếu chưa có
```sh
yum -y install firewalld
```

- Khởi chạy dịch vụ
```sh
systemctl start firewalld
```

- Khởi chạy dịch vụ cùng hệ thống
```sh
systemctl enable firewalld
```

- Kiểm tra trạng thái dịch vụ
```sh
systemctl status firewalld
```

- Khởi chạy lại dịch vụ FirewallD
```sh
firewall-cmd --reload
```

#### Cấu hình FirewallD
##### Thiết lập Zone
- Kiểm tra toàn bộ quy tắc của tất cả các zone
```sh
firewall-cmd --list-all-zones
```

- Kiểm tra toàn bộ quy tắc của zone mặc định và active zone
```sh
firewall-cmd --list-all
```

- Kiểm tra toàn bộ quy tắc của một zone cụ thể
```sh
firewall-cmd --zone=home --list-all
```

- Kiểm tra danh sách services hoặc ports đã được cho phép của một zone cụ thể
```sh
firewall-cmd --zone=public --list-services
firewall-cmd --zone=public --list-ports
```

##### Thiết lập Service
- Xác định các services có thể thiết lập trên hệ thống
```sh
firewall-cmd --get-services
```

![image](./image/FirewallD%201.png)

- Thiết lập cho phép các dịch vụ trên bằng tham số ```--add-service```
```sh
firewall-cmd --zone=public --add-service=http
firewall-cmd --zone=public --add-service=http --permanent
```

- Dịch vụ ```http``` sẽ được cho phép ngay lập tức với câu lệnh đầu và vẫn có hiệu lực sau khi khởi động lại với câu lệnh sau

- Thiết lập vô hiệu hoá/đóng cổng bằng tham số ```--remove-service```
```sh
firewall-cmd --zone=public --remove-service=http
firewall-cmd --zone=public --remove-service=http --permanent
```

##### Thiết lập Port
- Thiết lập cho phép 1 port với tham số ```--add-port```
```sh
firewall-cmd --zone=public --add-port=7071/tcp
firewall-cmd --zone=public --add-port=7071/tcp --permanent
```

- Thiết lập cho phép 1 dải port với tham số ```--add-port```
```sh
firewall-cmd --zone=public --add-port=7000-8500/tcp
firewall-cmd --zone=public --add-port=7000-8500/tcp --permanent
```

- Thiết lập chặn port với tham số ```--remove-port```
```sh
firewall-cmd --zone=public --remove-port=8450/tcp
firewall-cmd --zone=public --remove-port=8450/tcp --permanent
```

##### Thiết lập địa chỉ IP
- Thiết lập cho phép 1 địa chỉ IP với tham số ```--add-source``` (whitelist)
```sh
firewall-cmd --add-source=192.168.1.100
firewall-cmd --add-source=192.168.1.100 --permanent
```

- Thiết lập xoá địa chỉ IP khỏi whitelist
```sh
firewall-cmd --remove-source=192.168.1.100
firewall-cmd --remove-source=192.168.1.100 --permanent
```

- Thiết lập chặn địa chỉ IP
```sh
firewall-cmd --add-rich-rule='rule family=ipv4 source address=192.168.1.100 reject'
firewall-cmd --add-rich-rule='rule family=ipv4 source address=192.168.1.100 reject' --permanent
```

- Thiết lập bỏ chặn địa chỉ IP
```sh
firewall-cmd --remove-rich-rule='rule family=ipv4 source address=192.168.1.100 reject'
firewall-cmd --remove-rich-rule='rule family=ipv4 source address=192.168.1.100 reject' --permanent
```