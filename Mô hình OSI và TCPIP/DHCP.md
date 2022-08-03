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

##### Bản tin DHCP Discover
Bản tin được sinh ra đầu tiên trong quá trình giao tiếp giữa client và server. Bản tin này được gửi từ host để kiểm tra xem liệu có DHCP server trong mạng hay không

##### Bản tin DHCP Offer
Bản tin này được server dùng để phản hồi lại client các thông tin về các địa chỉ chưa được cấp phát và các thông số cài đặt TCP khác

##### Bản tin DHCP Request
Bản tin này được client sử dụng sau khi nhận được bản tin Offer để gửi cho toàn mạng tín hiệu broadcasr để kiểm tra xem có host nào trùng địa chỉ IP không, nếu không có thì gửi một bản tin tới server để yêu cầu cấp phát địa chỉ IP đó

##### Bản tin DHCP ACK
Server dùng bản tin này để gửi cho client sau khi nhận được yêu cầu, bản tin bao gồm thời gian thuê bao cho client

### Các thành phần chính của DHCP server
- Options: Cấu hình các thông số mặc định của DHCP
- Scope: Một đoạn địa chỉ IP được quy định trước trên DHCP server dùng để gán cho các máy client
- Reservation: Là nhưng đoạn địa chirdufng để "để dành" dành riêng cho một số máy tính trong một scope
- Lease: Thời gian "cho thuê" địa chỉ IP đối với mỗi client

### Ưu và nhược điểm của giao thức DHCP
##### Ưu điểm
- Quản lý tập trung các địa chỉ IP
- Dễ dàng trong việc thêm các client mới vào mạng
- Sử dụng lại các địa chỉ IP để giảm tổng số lượng địa chỉ IP cần thiết
- Đơn giản trong việc cấu hình lại không gian địa chỉ IP bằng DHCP server mà không cần cấu hình lại trên từng client

##### Nhược điểm
- Có thể bị xung đột địa chỉ IP