# Giao thức HTTP
### Giới thiệu chung
HTTP viết tắt của Hyper Text Transfer Protocol (Giao thức truyền tải siêu văn bản) là giao thức tầng ứng dụng của trang web. HTTP tuân theo chuẩn RFC 1945 và RFC 2616. Nó được sử dụng trong mô hình Server/Client, Server và Client trao đổi thông tin với nhau thông qua việc trao đổi các bản tin HTTP. HTTP định nghĩa cấu trúc các bản tin đó và cách trao đổi các bản tin.
HTTP là giao thức không lưu trạng thái.
### Cách thức hoạt động
HTTP sử dụng TCP làm giao thức truyền tải cơ bản. HTTP client ban đầu sẽ khởi tạo một kết nối TCP với server. Khi kết nối được thiết lập, trình duyệt và server xử lý việc truy cập TCP thông qua giao diện socket. Client gửi bản tin yêu cầu và nhận bản tin phản hồi thông qua giao diện socket. Tương tự như vậy, Server nhận bản tin yêu cầu và gửi bản bản tin phản hồi thông qua giao diện socket.
### Non-Persistent và Persistent
RTT: Thời gian để một gói tin nhỏ di chuyển từ client tới server và quay trở lại client.
##### Non-Persistent (Không duy trì kết nối)
- Mỗi kết nối TCP giữa client và server chỉ sử dụng để vận chuyển nhiều nhất một đối tượng.
- Một kết nối bao gồm một yêu cầu và một phản hồi

##### Persistent (Duy trì kết nối)
- Nhiều đối tượng có thể được tải về thông qua một lần kết nối duy nhất
- Một kết nối có thể có nhiều yêu cầu và phản hồi

##### So sánh Non-Persistent và Persistent
| Non-Persistent | Persistent |
| - | - |
| Kết nối sẽ đóng sau khi Server gửi phản hồi cho client | Server và Client vẫn duy trì kết nối sau mỗi yêu cầu hoặc phản hồi |
| Tốn thời gian để OS lập kết nối TCP | Các bản tin tiếp theo sẽ gửi và nhận qua kết nối mạng đang mở đó |
| Trình duyệt thường phải mở song song nhiều kết nối TCP | Client sẽ gửi yêu ngay khi cần |
| Tốn 2 RTT cộng với mỗi lần truyền file | Chỉ mất 1 RTT để thiết lập kết nối và 1 RTT với mỗi lần truyền file |

### Bản tin yêu cầu (HTTP request)
Bản tin request có dạng text, chia thành dòng và có thể đọc được.
Ví dụ về cú pháp của bản tin:
GET /ktht/index.html HTTP\1.1
Host: www.nuce.edu.vn
User-agent: Mozilla/4.0
Connection: close
Accept-language:VN
(extra CR,LF)

Trong đó:
> GET /ktht/index.html HTTP\1.1

là dòng yêu cầu chưa lệnh

> Host: www.nuce.edu.vn
User-agent: Mozilla/4.0
Connection: close
Accept-language:VN

là phần tiêu đề (header) của bản tin

> (extra CR,LF)

là ký tự xuống dòng và về đầu dòng, đánh dấu kết thúc bản tin

### Các phương thức của các phiên bản HTTP
##### HTTP/1.0
- GET: lấy thông tin được xác định bởi Request-URL
- HEAD: tương tự như GET nhưng thông tin trả về không chứa phần thân (Entity-Body)
- POST: yêu cầu server chấp nhận thực thể được kèm theo trong bản tin yêu cầu được xác định bởi Request-URL

##### HTTP/1.1
- HTTP/1.1 cũng bao gồm GET, HEAD, POSt, ngoài ra còn thêm một vài phương thức khác
- PUT: yêu cầu một thực thể được kèm theo trong bản tin yêu cầu được lưu trữ được xác định bởi Request-URL. Nếu đối tượng đã tồn tại thì thay đổi dối tượng đó, nếu không thì tạo một đối tượng mới
- DELETE: yêu cầu xóa một đối tượng được xác định bởi Request-URL. Thường thì đối tượng sẽ không được xóa hẳn mà được chuyển sang vị trí không thể truy cập

### Bản tin phản hồi
Ví dụ về cú pháp bản tin:
HTTP/1.1 200 OK
Connection close
Date: Thu, 06 Aug 1998 12:00:15 GMT
Server: Apache/1.3.0 (Unix)
Last-Modified: Mon, 22 Jan 1998 14:30:00 GMT
Content-Length: 6821
COntent-Type: text/html

data data data data data data ...

Trong đó:
> HTTP/1.1 200 OK

là dòng trạng thái của giao thức (chứa mã trạng thái)

> Connection close
Date: Thu, 06 Aug 1998 12:00:15 GMT
Server: Apache/1.3.0 (Unix)
Last-Modified: Mon, 22 Jan 1998 14:30:00 GMT
Content-Length: 6821
COntent-Type: text/html

là tiêu đề (header)

> data data data data data data ...

là phần thân (body), chứa dữ liệu, ví dụ như nội dung của file HTML

### Các mã trạng thái thường gặp trong bản tin phản hồi
200 OK
201 Created
204 No Content
301 Move Permanently
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
408 Request Timeout
415 Unsupported Media Type
500 Internal Server Error
502 Bad Gateway