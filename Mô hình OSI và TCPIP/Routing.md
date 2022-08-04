# Định tuyến (Routing)
## Sơ lược về định tuyến
Định tuyến là quá trình lựa chọn các đường đi trên một mạng máy tính để gửi dữ liệu qua đó
Định tuyến chỉ ra hướng di chuyển của các gói tin được đánh địa chỉ từ mạng nguồn của chúng, hướng đến đích cuối thông qua các nút trung gian là các router
Quá trình định tuyến dựa vào bảng định tuyến (bảng chứa lộ trình tốt nhất đến các đích khác trên mạng)

## Các loại định tuyến
### Định tuyến tĩnh
##### Đặc điểm
Người quản trị phải cấu hình thủ công chỉ ra đường đi đến tất cả các mạng đích trên router trong hệ thống
Kỹ thuật định tuyến tĩnh đơn giản, dễ thực hiện, ít hao tổn tài nguyên mạng và CPU xử lý trên router nhưng không thích hợp trên mạng có quy mô lớn

##### Ưu điểm
- Sử dụng ít băng thông hơn định tuyến động
- Không tiêu tốn tài nguyên để tính toán và phân tích gói tịn định tuyến

##### Nhược điểm
- Không có khả năng tự động cập nhật đường đi
- Phải cấu hình thủ công khi mạng có sự thay đổi
- Phù hợp với mạng nhỏ, rất khó triển khau trên mạng lớn

##### Các trường hợp sử dụng định tuyến tĩnh
- Đường truyền có băng thông thấp
- Người quản trị mạng cần kiểm soát các kết nối
- Kết nối dùng định tuyến tĩnh là đường dự phòng cho đường kết nối dùng giao thức định tuyến động
- Chỉ có một đường duy nhất đi ra mạng bên ngoài
- Router có ít tài nguyên và không thể chạy một giao thức định tuyến động
- Người quản trị mạng cần kiểm soát bảng định tuyến và cho phép các giao thức classful và classless

##### Cấu hình định tuyến tĩnh
Cú pháp:

```ip route <destination-network> <subnet-mask> {next-hop-address|out-bound-interface} [distance]```

Trong đó:
```destination-network```: là địa chỉ mạng đích cần đi tới
```subnet-mask```: subnet-mask của destination-network
```next-hop-address```: địa chỉ IP của cổng trên router kế tiếp có kết nối trực tiếp với router đang xét
```out-bound-interface```: cổng của router sẽ gửi dữ liệu ra
```distance```: thay đổi giá trị AD (Administrative Distance) cho tuyến này. Mặc định các tuyến tĩnh có AD=1

##### Default route
Default router nằm ở cuối bảng định tuyến và được sử dụng để gửi các gói tin đi trong trường hợp mạng đích không tìm thấy trong bảng định tuyến. Nó rất hữu dụng trong các mạng dạng "stub network" như kết nối từ mạng nội bộ ra ngoài Internet

### Định tuyến động
##### Đặc điểm
Các router tự trao đổi thông tin về các địa chỉ mạng trên sơ đồ mạng, tự chạy một phương thức để tính toán đường đi tối ưu

##### Các loại định tuyến động
###### Link state
- Phổ biến nhất là thuật toán Dijkstra
- Thuật toán link state gồm có bước khởi tạo cho vòng lặp. Số các bước bằng tổng số các nút trên mạng

###### Distance vector
- Là thuật toán lặp, không đồng bộ và phân tán
- Thuật toán có tính phân tán vì mỗi nút nhận thông tin từ những nusrt hàng xóm có đường kết nối trực tiếp, thực hiện các bước tính toán và phân tán kết quả tính toán tới tất cả các nút lân cận

###### Classful
Router không gửi kèm theo subnet mask trong bảng định tuyến của mình
Giao thức Classful điển hình: RIPv1

###### Classless
Router gửi kèm theo subnet mask trong bản tin định tuyến
Các giao thức Classless: RIPv2, OSPF, EIGRP