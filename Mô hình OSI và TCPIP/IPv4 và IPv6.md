# Giao thức IPv4 và IPv6
## IPv4
### Sơ lược về giao thức
IPv4 viết tắt của Internet Protocol version 4 là giao thức mang tính hướng không kết nối và được sử dụng trong hệ thống chuyển mạch gói
IPv4 tuân theo chuẩn RFC 791

### Cấu trúc địa chỉ IPv4
Địa chỉ IPv4 có độ dài 32-bit, được chia thành 4 octet, mỗi octet gồm 8-bit
Không gian địa chỉ là 2^32 tương đương khoảng 4 tỉ địa chỉ
Mỗi giao diện mạng bao gồm card mạng hay router đều có địa chỉ IP riêng biệt
![image](https://www.tutorialspoint.com/ipv4/images/ip_decimal_notation.jpg)

### Phân lớp địa chỉ IP
##### Lớp A
Cấu trúc địa chỉ:
NetworkID.HostID.HostID.HostID
8-bit đầu tiên là địa chỉ phần mạng và 24-bit sau là địa chỉ phần host
Bit đầu tiên của phần mạng luôn là bit 0
Dải địa chỉ mạng của lớp A: 1.0.0.0 đến 126.0.0.0

##### Lớp B
Cấu trúc địa chỉ:
NetworkID.NetworkID.HostID.HostID
16-bit đầu tiên là địa chỉ phần mạng và 16-bit sau là địa chỉ phần host
Hai bit đầu tiên của phần mạng luôn là 10
Dải địa chỉ mạng: 128.0.0.0 đến 191.255.0.0

##### Lớp C
Cấu trúc địa chỉ:
NetworkID.NetworkID.NetworkID.HostID
24-bit đàu tiên là địa chỉ phần mạng và 8-bit sau là địa chỉ phần host
Ba bit đầu tiên của phần mạng luôn là 110
Dải địa chỉ mạng: 192.0.0.0 đến 223.255.255.0

##### Lớp D
Bốn bit đầu tien của phần mạng luôn là 1110
Được sử dụng làm các địa chỉ multicast

##### Lớp E
Năm bit đầu tien của phần mạng luôn là 11110

### Cấu trúc của một gói tin IPv4
![image](https://electronicspost.com/wp-content/uploads/2016/05/4.13.png)
- Version number: gồm 4-bit dùng để xác định phiên bản của giao thức IP. Khi xác định được phiên bản của giao thức, bộ định tuyến (router) có thể xác định được cách diễn giải phần còn lại của gói tin
- Header length: gồm 4-bit dùng để xác định chỗ dữ liệu (data) thực sự bắt đầu
- Type of service: Dùng để phân biệt các kiểu gói tin khác nhau
- Datagram length: là tổng độ dài của gói dữ liệu IP (bao gồm phần header và data) được tính bằng bytes
- Identifier, flags, fragmentation offset: được sử dụng trong phân mảnh gói tin
- Time-to-live: thời gian gói tin có thể tồn tại trong khi di chuyển qua các nút mạng (router), mỗi khi qua 1 nút mạng (router) thì giá trị sẽ giảm đi 1, khi TTL về 0 thì gói tin sẽ bị bỏ đi
- Protocol: chỉ được sử dụng khi gói tin tới được đích cuối cùng
- Header checksum: giúp phát hiện lỗi trong phần header của gói tin được gửi đến
- Source and destination IP address: là địa chỉ nguồn và địa chỉ đích mà gói tin cần tới
- Options: cho phép mở rộng header
- Data: là phần dữ liệu của gói tin

### Các loại địa chỉ IPv4
- Unicast: địa chỉ IP cho phép thiết bị gửi dữ liệu đến một nơi nhận duy nhất
- Broadcast: cho phép gửi dữ liệu đến các host trong một mạng con
- Multicast: cho phép thiết bị gửi dữ liệu đến một tập xác định trước các host

### Hạn chế của IPv4
- Không bảo mật trên kênh truyền
- Thiếu hụt không gian địa chỉ khi hiện nay đã gần như cạn kiệt nguồn địa chỉ IPv4

## IPv6
### Sơ lược về giao thức
IPv6 viết tắt của Internet Protocol version 6 là phiên bản mới nhất của giao thức IP dần thay thế cho IPv4 do đang dần cạn kiệt địa chi

### Cấu trúc địa chỉ IPv6
IPv6 có chiều dài 128-bit, đươc biểu diễn dưới dạng hexa và phân cách bởi dấu ":"

### Cấu trúc của một gói tin IPv6
![image](https://electronicspost.com/wp-content/uploads/2016/05/4.24.png)
- Version: gồm 4-bit dùng để xác định phiên bản IP
- Traffic class: gồm 8-bit tương tự trường TOS của IPv4
- Flow label: gồm 20-bit dùng để xác định luồng dữ liệu
- Payload length: gồm 16-bit là độ lớn của phần dữ liệu không tính phần tiêu đề
- Next header: dùng để xác định giao thức ở tầng trên sẽ nhận dữ liệu (ví dụ như TCP hoặc UDP) tương tự trường Protocol trong IPv4
- Hop limit: tương tự như TTL trong IPv4, khi giá trị về 0 thì gói tin sẽ bị bỏ
- Source and destination addresses: mỗi trường gồm 128-bit chứa địa chỉ của nguồn và địa chỉ dích
- Data: là phần chứa dữ liệu