# VLAN
### Sơ lược về VLAN
VLAN viết tắt của Virtual Local Area Network là một kỹ thuật cho phép tạo lập các mạng LAN độc lập một cách logic trên cùng một kiến trúc hạ tầng vật lý
VLAN giúp giảm thiểu miền quảng bá (broadcast domain) cũng như tạo thuận lợi cho việc quản lý một mạng cục bộ lớn

### Phân loại VLAN
- Port-based VLAN: đây là cách cấu hình đơn giản và phổ biến nhất. Mỗi cổng trên Switch được gán với một VLAN xác định, dó đó, mỗi thiết bị host gắn vào cổng mạng đều thuộc một VLAN nào đó
- MAC ddress-based VLAN: Mỗi địa chỉ MAC được đánh dấu với một VLAN xác định. Cách cấu hình này ít được sử dụng
- Protocol-based VLAN: tương tự như MAC address-based VLAN nhưng thay vì dùng địa chỉ MAC thì dùng địa chỉ IP

### Cách thức hoạt động
VLAN được tạo bằng cách thêm tag hoặc header vào mỗi frame. Tag này cho mạng biết frame sẽ được gửi đến VLAN nào. Các thiết bị trong những VLAN khác nhau không thể nhìn thấy lưu lượng của nhau trừ khi chúng đều kết nối với router được cấu hình cho phép việc này

### Các chế độ VLAN
##### Trunking mode
Trunking mode cho phép tập hợp lưu lượng từ nhiều VLAN thông qua cùng một cổng vật lý đơn
Các kết nối trunking thường được sử dụng để kết nối giữa các switch với nhau

##### Access mode
Giao diện này thuộc về một và chỉ một VLAN. Thông thường một cổng của switch gắn tới một thiết bị của người dùng đầu cuối hoặc một server

### Ưu và nhược điểm
##### Ưu điểm
- Hiệu năng cao hơn và độ trễ mạng thấp hơn
- Giảm thiểu việc cần nhiều router trong mạng
- Thông tin được an toàn hơn do không bị nhìn thấy bởi những người dùng không mong muốn

##### Nhược điểm
- Phức tạp trong việc quản lý
- Có khả năng gặp lỗi trong quá trình tương tác với nhau
- Không thể chuyển tiếp luồng dữ liệu giữa các VLAN (cần router để giao tiếp giữa các VLAN)

### Các ứng dụng của VLAN
- Tạo các mạng LAN khác nhau của nhiều máy tính trong văn phòng
- Tạo mạng dữ liệu ảo