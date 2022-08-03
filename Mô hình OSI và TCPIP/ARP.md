# Giao thức ARP
### Sơ lược về ARP
ARP viết tắt của Address Resolution Protocol là một giao thức quan trọng của tầng mạng trong mô hình OSI
ARP dùng để chuyển đổi địa chỉ IP thành địa chỉ MAC (địa chỉ vật lý) tương ứng

### Cách thức hoạt động
Trước khi gửi bất kỳ dữ liệu nào đến các thiết bị khác, các thiết bị phải xác định được địa chỉ MAC vầ địa chỉ IP của thiết bị nhận. Quá trình ánh xạ địa chỉ IP thành địa chỉ MAC này được lấy từ ARP cache ở trên thiết bị đó
Nếu địa chỉ IP không xuất hiện trong ARP cache thì thiết bị đó không thể chuyển hướng đến thiết bị đích cho tới khi nhận được bản cập nhật ánh xạ mới. Vì vậy, trước tiên, mỗi thiết bị sẽ gửi một bản tin yêu cầu ARP trên mạng nội bộ. Các host có địa chỉ IP khi nhận được sẽ gửi lại phản hồi ARP, thiết bị sử dụng phản hồi đó để cập nhật vào ARP cache và gửi thông báo đến host

### Các loại ARP khác
##### Reverse ARP (RARP)
Host sử dụng gói tin quảng bá (broadcast) RARP để lấy địa chỉ IP của mình khi thiết bị mới được cài đặt hoặc không còn bộ nhớ để lưu trữ địa chỉ IP. ARP server khi nhận được gói tin sẽ kiểm tra trong bảng địa chỉ, nếu trùng khớp thông tin thì ARP server sẽ gửi gói tin phản hồi địa chỉ IP tới thiết bị yêu cầu.
Ngày nay, giao thức RARP này không còn được sử dụng do đã có các giao thức có tính năng tốt hơn như là BOOTP (Bootstrap Protocol) và DHCP (Dynamic Host Configuration Protocol)

##### Inverse ARP (InARP)
Ngược lại so với ARP, giao thức InARP dùng để ánh xạ địa chỉ MAC thành địa chỉ IP

##### Proxy ARP
Proxy ARP sử dụng một thiết bị trung gian để liên lạc giữa hai thiết bị (thường là router) bằng cách "làm giả" danh tính, lưu lượng mạng sẽ được di chuyển qua thiết bị trung gian tới đích thực sự
Giao thức này giúp kết nối các thiết bị trong một mạng con truy cập tới các mạng con từ xa (mạng con khác) mà không cần cấu hình lại điều hướng (routing) hay là default gateway
Giao thức này tuân theo chuẩn RFC 1027

##### Gratuitous ARP
Gratuitous ARP được dùng để thông báo địa chỉ MAC tới mạng hiện tại mỗi khi thiết bị được khởi động
Giao thức này dùng để tránh việc xung đột địa chỉ IP và cập nhật bảng ARP và bảng địa chỉ MAC trên Switch

### Tấn công ARP
Giả mạo ARP (ARP spoofing) là hình thức tấn công ARP chủ yếu.
Trong phương thức giả mạo ARP, kẻ tấn công gửi yêu cầu ARP gia mạo trong mạng nội bộ, kết quả là địa chỉ MAC của kẻ tấn công sẽ đánh lừa địa chỉ MAC giữa các host, lúc này, thay vì các host trao đổi trực tiếp với nhau thì sẽ trao đổi thông qua trung gian là máy của kẻ tấn công. Khi đó, kẻ tấn công có thể theo dõi lưu lượng mạng hoặc có thể chặn lưu lượng mạng giữa hai thiết bị mạng. Hình thức tấn công này gọi là Man in the middle.