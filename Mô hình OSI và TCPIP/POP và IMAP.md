# Giao thức POP và IMAP
## POP
### Sơ lược về giao thức
POP viết tắt của Post Office Protocol là một giao thức đơn giản trong việc truy cập email từ máy chủ về máy tính
POP tuân theo RFC 1939
POP hoạt động trên cổng (port) 110
POP trải qua 3 phiên bản, hiện tại đang là POP3 giúp hoàn thiện giao thức

### Chức năng của POP
Cho phép người dùng tải thử từ Mail Server về máy tính
Xóa thư sau khi lấy từ Mail Server
Kiểm tra hòm thư

### Cách thức hoạt động
Email được lưu trữ tại Mail Server cho đến khi người dùng đăng nhập và tải thư xuống máy tính

### Mô tả một phiên của POP3
Một phiên POP3 trải qua 3 giai đoạn:
- Giai đoạn authorization: Người dùng gửi username và password để xác thực người dùng
- Giai đoạn transaction: Người dùng có thể lấy mail, đánh dấu xóa mail, bỏ đánh dấu xóa và lấy số liệu thống kê mail
- Giai đoạn update: Mail Server xóa mail được đánh dấu xóa và kết thúc phiên

### Các lệnh cơ bản của POP3
##### Lệnh ```USER```
Dùng để xác thực người dùng
Cú pháp:

```USER name```

Phản hồi:

```+OK name is a valid mailbox```

hoặc

```-ERR never heard of mailbox name```

##### Lệnh ```PASS```
Dùng để xác thực người dùng (dùng kèm với lệnh ```USER```)
Cú pháp:

```PASS string```

Phản hồi:

```+OK maildrop locked and ready```

hoặc

```-ERR invalid password```

hoặc

```-ERR unable to lock maildrop```

##### Lệnh ```LIST```
Dùng để lấy dang sách email trong hộp thư hoặc kiểm tra xem có thư với chỉ số tương ứng hay không
CÚ pháp:
```LIST [msg]```
Với ```[msg]``` là chỉ số của tin nhắn, nếu không có thì liệt kê tất cả email
Phản hồi:

```+OK scan listing follows```

hoặc

```-ERR no such message```

##### Lệnh ```STAT```
Dùng để lấy thống kê của hộp thư
Cú pháp:

```STAT```

Phản hồi:

```+OK nn mm```

##### Lệnh ```RETR```
Dùng để tải thư cụ thể từ Mail Server
Cú pháp:

```RETR msg```
Với ```msg``` là chỉ số của email

Phản hồi:

```+OK message follows```
```(nội dung email)```
```.(CLRF)```

hoặc

```-ERR no such message```

##### Lệnh ```DELE```
Dùng để đánh dấu xóa email
Cú pháp:

```DELE msg```
Với ```msg``` là chỉ số của email

Phản hồi:

```+OK message deleted```

hoặc

```-ERR no such message```

##### Lệnh ```QUIT```
Dùng để xóa email nếu được đánh dấu xóa và kết thúc phiên
Cú pháp:

```QUIT```

Phản hồi:

```+OK```

hoặc

```-ERR some deleted messages not removed```

### Ưu và nhược điểm
##### Ưu điểm
- Kết nối Internet chỉ dùng để gửi và nhận mail
- Tiết kiệm không gian lưu trữ cho Mail Server
- Có lựa chọn để lại bản sao mail trên server
- Hợp nhất nhiều tài khoản email và nhiều server vào một hộp thư

##### Nhược điểm
- Không thể truy cập cùng một tài khoản email từ nhiều thiết bị

## IMAP
### Sơ lược về giao thức
IMAP viết tắt của Internet Message Access Protocol là giao thức dùng để nhận email tương tự như POP3 nhưng phức tạp hơn. Email được lưu trữ trên Mail Server.
IMAP tuân theo RFC 3501
IMAP hoạt động trên cổng 143

### Chức năng của IMAP
Cho phép truy cập cùng một tải khoản trên nhiều thiết bị
Cho phép truy cập email trực tiếp trên server mà không cần tải xuống
Có khả năng lưu nháp tin nhắn trên server

### Ưu và nhược điểm
##### Ưu điểm
- Mail được lưu trên server nên có truy cập từ nhiều thiết bị khác nhau
- Có thể xem trước một phần của mail để quyết định có tải về hay không
- Tiết kiệm không gian lưu trữ nội bộ nhưng vẫn có tùy chọn lưu mail cục bộ

##### Nhược điểm
- Bắt buộc phải có kết nối Internet để thao tác với mail

## So sánh POP3 và IMAP
| Tiêu chí | POP3 | IMAP |
| - | - | - |
| Cơ bản | POP3 cần phải tải thu để có thể đọc | Nội dung mail có thể được kiểm tra một phần trước khi tải về |
| Cách tổ chức | Không thể tổ chức mail trong hộp thư trên Mail Server | Có khả năng tổ chức mail trên server |
| Thư mục | Người dùng không thể tạo, xóa hoặc sửa tên hộp thử trên Mail Server | Người dùng có thể tạo, xóa hoặc sửa tên hộp thư trên Mail Server |
| Nội dung | Người dùng không thể tìm kiểm nội dung của mail trước khi tải về | Người dùng có thể tìm kiếm nội dung của mail trước khi tải xuống |
| Tải xuống một phần | Không | Có |
| Các tính năng | POP3 đơn giản và bị giới hạn về tính năng | IMAP mạnh hơn, phức tạp hơn và nhiều tính năng hơn so với POP3 |