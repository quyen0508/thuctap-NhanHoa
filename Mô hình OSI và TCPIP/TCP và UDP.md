# Giao thức TCP và UDP
## TCP
### Sơ lược về giao thức
- TCP viết tắt của Tranmission Control Protocol là giao thức truyền tải hướng kết nối, nghĩa là phải thiết lập kết nối trước khi bắt đầu truyền dữ liệu. Tiến trình này được gọi là tiến trình bắt tay 3 bước
- TCP cung cấp cơ chế báo nhận: Khi A gửi dữ liệu cho B, B nhận được thì gửi gói tin cho A là đã nhận được, nếu không thì A sẽ gửi lại gói tin cho đến khi B báo nhận thì thôi.
- Có cơ chế đánh số thứ tự gói tin cho các đơn vị dữ liệu được truyền, sử dụng để ráp các gói tin chính xác ở điểm nhận và loại bỏ gói tin trùng lặp
- Có các cơ chế điều khiển luồng thích hợp (flow control) để tránh tắc nghẽn xảy ra
- Hỗ trợ cơ chế full-duplex (song công)

### Cấu trúc gói tin
![image](https://images.viblo.asia/ca199b5e-2deb-42b0-ac36-33dbf30f3e20.png)
- Source port và destination port (16-bit): Dùng để ghép kênh/phân kênh dữ liệu đến/đi từ các ứng dụng tầng cao hơn
- Sequence number (32-bit): Dùng để đánh số thứ tự gói tin
- Acknowledge number (32-bit): Dùng để báo đã nhận gói tin có số thứ tự bao nhiêu và mong muốn nhận được byte mang số thứ tự nào tiếp theo
- Head lendth (4-bit): cho biết toàn bộ header dài bao nhiêu tính theo đơn vị word (1-word = 4-byte)
- Các bit reserved (4-bit): đều được thiết lập bằng 0
- Các bit control (9-bit): các bit dùng để điều khiển cờ ACK, cờ Sequence,...
- Window size (16-bit): chỉ số số lượng bytes bên nhận chấp nhận
- Checksum (16-bit): kiểm tra lỗi của toàn bộ TCP segment
- Urgent pointer (16-bit): sử dụng trong trường hợp cần ưu tiên dữ liệu
- Options (tối đa 32-bit): là trường tùy chọn, có thể thay đổi tùy ý. Trường này được sử dụng khi bên gửi và bên nhận thương lượng với nhau về kích thước phân đoạn tối đa (MSS) hay là hệ số mở rộng window cho mục đích sử dụng mạng tốc độ cao

### Cách thức hoạt động
##### Tiến trình bắt tay 3 bước
![image](https://f002.backblazeb2.com/b2api/v1/b2_download_file_by_id?fileId=4_za8a2358db1d7f91b68b30916_f109804476cef7824_d20190911_m064720_c002_v0001127_t0001)
- Bước 1: Host A gửi cho host B một gói tin có cờ SYN được bật lên, với số thứ tự được đánh là 100. Segment đầu tiên này không chứa phần dữ liệu nên không có phần data, tuy nhiên số lượng byte dữ liệu vẫn được tính là một byte cho hoạt động gửi cờ SYN
- Bước 2: Host B nhận được gói tin thì B gửi lại gói tin có cờ SYN được bật lên, kèm theo đó là cờ ACK để xác nhận
- Bước 3: Sau khi kết nối đã được thiết lập thì A gửi lại gói tin để đáp ứng nhu cầu của B. ACK = 301 dùng để báo là đã nhận được gói tin có SEQ = 300
- Sau khi 3 bước được hoàn tất, kết nối TCP được thiết lập giữa host A và B, lúc này hai host đã có thể truyền dữ liệu được cho nhau

## UDP
### Sơ lược về giao thức
- UDP viết tắt của User Datagram Protocol là giao thức truyền tải hướng phi kết nối vì không đòi hỏi bên gửi và bên nhận phải liên kết trước khi trao đổi dữ liệu
### Ưu, nhược điểm của UDP
##### Ưu điểm
- Truyền tải nhanh dữ liệu của tầng ứng dụng
- Truyền tải nhanh và hiệu quả đối với các đữ liệu có kích thước nhỏ và yêu cầu khắt khe về thời gian
- Thích hợp cho việc trả lời các truy vấn nhỏ với số lượng người yêu cầu lớn

##### Nhược điểm
- Dễ bị lỗi do không quan tâm đến gói tin có bị mất mát khi truyền dữ liệu hay không

### Cấu trúc gói tin UDP
![image](https://images.viblo.asia/804e5295-cc37-49a4-9029-bac0b28402d3.png)
- Source port và destination port (16-bit): cho phép định danh một phiên của một ứng dụng nào đó chạy trên UDP, có thể coi port là địa chỉ của tầng Transport (Giao vận)
- UDP length (16-bit): cho biết chiều dài của toàn bộ UDP datagram tổng cộng bao nhiêu byte
- UDP checksum (16-bit): sử dụng thuật toán mã vòng CRC để kiểm tra lỗi cho toàn bộ UDP datagram và chỉ kiểm tra một cách hạn chế
- Data: dữ liệu tầng trên được đóng gói vào UDP datagram đang xét

### Cách thức hoạt động
- UDP hoạt động tương tự như TCP nhưng nó không cung cấp kiểm tra lỗi khi truyền gói tin

## So sánh TCP và UDP
### Điểm chung
Đều là các giao thức mạng TCP/IP, có chức năng kết nối và gửi nhận dữ liệu giữa các thiết bị mạng với nhau
### Điểm khác
| TCP | UDP |
| - | - |
| Hướng kết nối | Hướng không kết nối |
| Độ tin cậy cao | Độ tin cậy thấp |
| Gửi dữ liệu dạng luồng byte | Gửi đi Datagram |
| Không cho phép mất gói tin | Cho phép mất gói tin |
| Đảm bảo việc truyền dữ liệu | Không đảm bảo việc truyền dữ liệu |
| Có sắp xếp thứ tự các gói tin | Không sắp xếp thứ tự các gói tin |
| Tốc độ truyền thấp hơn UDP | Tốc độ truyền cao |