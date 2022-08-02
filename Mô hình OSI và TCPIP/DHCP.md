# Giao thức DHCP
### Giới thiệu chung
DHCP viết tắt của Dynamic Host Configuration Protocol là một giao thức client/server cung cấp tự động một địa chỉ IP với các thông tin cấu hình liên quan như là mặt nạ mạng con (subnet mask) và địa chỉ default gateway. DHCP tuân theo chuẩn RFC 2131 và 2132.

### Quy trình cấp phát IP của hệ thống mạng sử dụng DHCP
- Gồm 4 bước:
    - Client gửi gói tin DHCP Discover
    - DHCP server gửi gói tin DHCP Offer
    - Client gửi gói tin DHCP Request
    - DHCP server gửi gói tin DHCP ACK
- Vì tin hiệu truyền đi trong quá trình xin cấp phát IP giữa DHCP client và server là tín hiệu Broadcast, do đó DHCP server chỉ có thể cấp thông số IP cho các máy client nằm trong cùng một dải mạng

### Các thành phần chính của DHCP server
- Options: Cấu hình các thông số mặc định của DHCP
- Scope: Một đoạn địa chỉ IP được quy định trước trên DHCP server dùng để gán cho các máy client
- Reservation: Là nhưng đoạn địa chirdufng để "để dành" dành riêng cho một số máy tính trong một scope
- Lease: Thời gian "cho thuê" địa chỉ IP đối với mỗi client
