# Mô hình OSI và TCP/IP
## Mô hình OSI
| Mô hình OSI |
| - |
| Application |
| Presentation |
| Session |
| Transport |
| Network |
| Data Link |
| Physical |
### Vai trò của các tầng trong mô hình
##### Tầng Physical (Tầng Vật lý)
- Quản lý trạng thái kết nối đường truyền
- Quản lý truy cập đường truyền
- Chuyển đổi dữ liệu thành tín hiệu và phát trên đường truyền
- Chuyển tin hiệu thu được từ đường truyền thành frame dữ liệu

##### Tầng Data Link (Tầng Liên kết dữ liệu)
- Truyền dữ liệu giữa các thiết bị có kết nối vật lý
- Quản lý địa chỉ vật lý MAC
- Đóng gói dữ liệu tầng trên gửi xuống vào trong frame
- Chuyển dữ liệu trong frame lên tầng trên
- Kiểm tra lỗi frame dữ liệu

##### Tầng Network (Tầng Mạng)
- Triển khai một phương thức đánh địa chỉ mạng ở mức logic
- Định tuyến gói dữ liệu đến địa chỉ đích
- Đóng gói dữ liệu của tầng Giao vận chuyển xuống
- Chuyển giao dữ liệu cho tầng Giao vận

##### Tầng Transport (Tầng Giao vận)
- Trao đổi dữ liệu giữa các chương trình ứng dụng
- Cung cấp dịch vụ giao vận dữ liệu tin cậy end-to-end
- Đóng gói dữ liệu của ứng dụng chuyển xuống
- Chuyển giao dữ liệu nhận được lên tầng Phiên (Session)

##### Tầng Session (Tầng Phiên)
- Thiết lập, duy trì và kết thúc phiên trao đổi dữ liệu
- Lựa chọn dịch vụ và giao thức giao vận dữ liệu thích hợp

##### Tầng Presentation (Tầng Trình diễn)
- Định dạng và mã hóa dữ liệu
- Đảm bảo tính tương thích về mặt dữ liệu bằng cách lựa chọn các cú pháp dữ liệu thích hợp

##### Tầng Appliication (Tầng Ứng dụng)
- Định danh máy trạm (sử dụng hệ thống tên minề hoặc dịch vụ truy vấn tên trong mạng)
- Xác định các tài nguyên trong hệ thống
- Đồng bộ hóa trao đổi dữ liệu

## Mô hình TCP/IP
| Mô hình TCP/IP |
| - |
| Application |
| Transport |
| Internet |
| Network Access |
### Vai trò của các tầng trong mô hình
##### Tầng Network Access
- Dùng để truyền gói tin từ tầng mạng đến các host
- Các thiết bị vật lý như switch, cáp mạng, card mạng HBA - Host Bus Adapter là các thánh phần truy cập

##### Tầng Internet
- Giải quyết vấn đề dẫn đến các gói tin đi qua các mạng để đến đúng đích

##### Tầng Transport
- Phân nhỏ các gói tin có kích thước lớn khi gửi và tập hợp lại khi nhận
- Đảm bảo tính toàn vẹn cho dữ liệu

##### Tầng Application
- Đóng vai trò cho các ứng dụng liên lạc giữa các node trong mạng

## Mối tương quan giữa hai mô hình
| Tiêu chí | OSI | TCP/IP |
| - | - | - |
| Số tầng | 7 | 4 |
| Cách tiếp cận | Theo chiều dọc | Theo chiều ngàng |
