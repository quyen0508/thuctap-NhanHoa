# NAT
### Sơ lược về NAT
NAT viết tắt của Network Address Translation là một kỹ thuật cho phép chuyển đổi từ một địa chỉ IP này thành một địa chỉ IP khác
Thông thường, NAT được dùng phổ biến trong mạng sử dụng địa chỉ cục bộ (private) cần truy cập đến mạng công cộng (Internet/public)
Vị trí dùng NAT là router biên giữa hai mạng

### Chức năng của NAT
- Chuyển đổi địa chỉ IPv4 private sang địa chỉ IPv4 public và ngược lại
- Có thể đóng vai trò như một tường lửa cơ bản

### Địa chỉ private và địa chỉ public
- Địa chỉ private được định nghĩa trong RFC 1918 là các dải địa chỉ:
    - 10.0.0.0 - 10.255.255.255
    - 172.16.0.0 - 172.31.255.255
    - 192.168.0.0 - 192.168.255.255
- Địa chỉ public là các địa chỉ còn lại. Các địa chỉ public là các địa chỉ được cung cấp bởi các tổ chức có thẩm quyền

### Một số thuật ngữ
- Địa chỉ ```inside local```: là địa chỉ IP gán cho một thiết bị ở mạng bên trong. Địa chỉ này hầu như không phải địa chỉ được cấp bởi NIC (Network Information Center) hay nhà cung cấp dịch vụ
- Địa chỉ ```inside global```: là địa chỉ đã được đăng ký với NIC, dùng để thay thế một hay nhiều địa chỉ IP ```inside local```
- Địa chỉ ```outside local```: là địa chỉ IP của một thiết bị bên ngoài khi nó xuất hiện bên trong mạng. Địa chỉ này không nhất thiết là địa chỉ được đăng ký, nó được lấy từ không gian địa chỉ bên trong
- Địa chỉ ```outside global```: là địa chỉ IP gán cho một thiết bị ở mạng bên ngoài. Địa chỉ này được lấy từ địa chỉ có thể dùng để định tuyến toàn cầu hay từ không gian địa chỉ mạng

### Phân loại NAT
##### NAT tĩnh (Static NAT)
- Static NAT được dùng để chuyển đổi một địa chỉ IP này sang một địa chỉ IP khác một cách cố định, thông thường là từ một địa chỉ cục bộ sang một địa chỉ công cộng và quá trình này được cài đặt thử công, nghĩa là địa chỉ ánh xạ và địa chỉ được ánh xạ được chỉ định rõ ràng tương ứng duy nhất
- Static NAT rất hữu ích trong trường hợp những thiết bị cần phải có địa chỉ cố định để có thể truy cập từ bên ngoài Internet như là những Server như Web, Mail,...
- Cấu hình Static NAT:
    - Thiết lập mối quan hệ chuyển đổi giữa địa chỉ nội bộ bên trong và địa chỉ đại diện bên ngoài:
    ```ip nat inside source static local-ip global-ip```
    - Xác định các cổng kết nối vào mạng bên trong và thực hiện lệnh:
    ```ip nat inside```
    - Xác định các cổng kết nối ra mạng công cộng bên ngoài và thực hiện lệnh:
    ```ip nat outside```

##### NAT động (Dynamic NAT)
- Dynamic NAT được dùng để ánh xạ một địa chỉ IP này sang một địa chỉ IP khác một cách tự động, thông thường là ánh xạ từ một địa chỉ cục bộ sang một địa chỉ được đăng ký. Bất kỳ một địa chỉ IP nào nằm trong dải địa chỉ IP công cộng đã được định trước đều có thể được gán cho một thiết bị bên trong mạng
- Cấu hình Dynamic NAT:
    - Xác định dải địa chỉ đại diện bên ngoài (public): các địa chỉ NAT
    ```ip nat pool name start-ip end-ip [netmask netmask/prefix-length prefix-length]```
    - Thiết lập ACL cho phép những địa chỉ nội bộ bên trong nào được chuyển đổi: các địa chỉ được NAT
    ```access-list access-list-number permit source [source-wildcard]```
    - Thiết lập mối quan hệ giữa địa chỉ nguồn đã được xác định trong ACL với dải địa chỉ đại diện ra bên ngoài
    ```ip nat inside source list <acl-number> pool <name>```
    - Xác định các cổng kết nối vào mạng nội bộ
    ```ip nat inside```
    - Xác định các cổng kết nối ra bên ngoài
    ```ip nat outside```

##### NAT Overload
- NAT Overload là một dạng của Dynamic NAT, nó thực hiện ánh xạ nhiều địa chỉ IP thành một địa chỉ (many-to-one) và sử dụng các chỉ số cổng (port) khác nhau để phân biệt cho từng chuyển đổi. NAT Overload còn có tên gọi khác là PAT (Port Address Translation)
- Chỉ số cổng (port) được mã hóa 16-bit, do đó có tới 65536 địa chỉ nội bộ có thể được chuyển đổi sang một địa chỉ công cộng
- Cấu hình NAT Overload:
    - Xác định dãy địa chỉ bên trong cần chuyển dịch ra ngoài (private ip addresses range)
    ```access-list <ACL-number> permit <source> <wildcard>```
    - Cấu hình chuyển đổi địa chỉ IP sang cổng nối ra ngoài
    ```ip nat inside source list <ACL-number> interface <interface> overload```
    - Xác định các cổng kết nối vào mạng nội bộ
    ```ip nat inside```
    - Xác định các cổng kết nối ra bên ngoài
    ```ip nat outside```

### Ưu và nhược điểm của NAT
##### Ưu điểm
- Tiết kiệm không gian địa chỉ IPv4
- Tăng cường bảo mật khi NAT đóng vai trò là một tường lửa cơ bản giúp lọc các gói tin
- Kết nối linh hoạt
##### Nhược điểm
- Ảnh hưởng hiệu năng tới router
- Khó khăn khi sử dụng một vài giao thức đường hầm (tunnel) như là IPsec