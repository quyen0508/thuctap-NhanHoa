# Giao thức SMTP
### Sơ lược về giao thức
SMTP viết tắt của Simple Mail Transfer Protocol là giao thức dùng để truyền email tin cậy và hiệu quả từ người gửi đến người nhận. Giao thức không phụ thuộc vào hệ thống cụ thể của các bên tham gia vào giao thức, chỉ cần các bên có kết nối qua một kênh truyền dữ liệu tin cậy (sử dụng TCP)
SMTP hoạt động trên cổng (port) 25 và tuân theo tài liệu RFC 821
SMTP cho phép chuyển tiếp email từ một User Agent qua các hệ thống Mail Server trung gian tới Mail Server của địa chỉ người nhận

### Mô hình hoạt động của giao thức
![image](https://www.codeproject.com/KB/IP/smtp-server/smtp-model.gif)
- Sender-SMTP là chương trình Client. Khi người dùng có yêu cầu gửi email, Client sẽ thiết lập một kết nối TCP đến Receiver-SMTP
- SMTP Server có thể là điểm đến cuối cùng của email hoặc một điểm trung chuyển
- Client sẽ tạo các bản tin request chứa các lệnh SMTP và gửi đến Server
- Server xử lý lệnh và trả lời bằng cách gửi bản tin phản hồi cho Client

### Mô tả một phiên truyền email giữa Client và Server
- Sau khi kết nối được thiết lập, Server gửi một bản tin thông báo trạng thái hiện tại của Server
- Client gửi lệnh HELO và thông báo tên Client. Server gửi phản hồi thông báo tên của Server
- Nếu trạng thái của Server là sẵn sàng phục vụ và Server trả lời OK với lệnh HELO của Client. Client gửi lệnh MAIL để bắt đầu phiên giao dịch email và báo cho Server địa chỉ người gửi mail (có thể bao gồm cả tên và địa chỉ mail của người gửi)
- Nếu Server chấp nhận người gửi đó thì sẽ gửi một phản hồi thông báo đồng ý
- Client sau đó gửi lệnh RCPT để báo cho Server địa chỉ người nhận email (có thể bao gồm cả tên và địa chỉ mail của người nhận)
- Server có thể trả lời đồng ý nếu chấp nhận hoặc từ chối nếu không chấp nhận. Lý do không chấp nhận là vì Server không trực tiếp quản lý địa chỉ email của người nhận hoặc không thể chuyển tiếp email cho người nhận đó
- Client và Server có thể tiếp tục trao đổi thỏa thuận về nhừng người nhận tiếp theo (Một email có thể gửi đến cho nhiều người nhận)
- Sau khi đã hoàn thành việc cung cấp địa chỉ người nhận cho Server, Client sẽ chuyển nội dung email cho Server, kết thúc bằng một chuỗi ký hiệu đặc biệt
- Server nhận xong email sẽ lưu thành file vào thư mục email của người nhận trên ổ đĩa của Server. Sau khi xử lý thành công, Server gửi phản hồi đã hoàn thành cho Client

### Các lệnh trong giao thức SMTP
##### Lệnh ```HELO```
- Lệnh dùng để xác định người gửi (Client) và người nhận (Server)
- Cú pháp:
```HELO client-name (CLRF)```
- Phản hồi:
```250 server-name is ready```

##### Lệnh ```MAIL```
- Lệnh dùng để báo cho Server biết một giao dịch truyền email mới bắt đầu để Server thiết lập lại các bảng trạng thái phiên, các vùng đệm chứa dữ liệu, các danh sách địa chỉ email người gửi và người nhận mà Server quản lý trong phiên này. Nếu chấp nhận lệnh này, Server sẽ gửi trả lời với mã 250
- Cú pháp:
```MAIL FROM:<(email-address)> (CLRF)```
- Phản hồi:
```250 (email-address) is ok (CLRF)```

##### Lệnh ```RCPT```
- Lệnh này sẽ báo cho Server biết một địa chỉ email của một người nhận đối với giao dịch mail này. Nếu chấp nhận, Server sẽ gửi trả lời với mã 250. Nếu khồng biết (hoặc không quản lý) địa chỉ người nhận, Server sẽ gửi trả lời với mã 550 (có lỗi xảy ra với ;lệnh RCPT). Lệnh RCPT có thể lặp lại nhiều lần cho nhiều người nhận email
- Cú pháp:
```RCPT TO:<(email-address)> (CLRF)```
- Phản hồi:
```250 (email-address) is ok (CLRF)```

##### Lệnh ```DATA```
- Lệnh này dùng để thực hiện truyền nội dung email từ Client đến Server. Nếu chấp nhận lệnh, Server sẽ trả lời với mã 354 và sau đó coi những dữ liệu nhận được sau đó từ Client là nội dung của email. Trong quá trình nhận, Server sẽ lưu trữ dữ liệu email vào file trong thư mục hộp thư của người nhận. Khi hoàn thành nhận nội dung email, Server sẽ trả lời với mã 250. Do dữ liệu email được gửi trên cùng một kênh truyền TCP với lệnh và phản hồi, Client phải chỉ báo cho Server biết kết thúc của nội dung email bằng một chuỗi ký tự đặc biệt là ```(CLRF).(CLRF)```
- Cú pháp:
```DATA (CLRF)```
- Phản hồi:
```354 End data with CLRF.CLRF (CLRF)```
- Sau khi nhận xong dữ liệu của email, Server phản hồi:
```250 Received email successfully (CLRF)```

##### Lệnh ```QUIT```
- Lệnh dùng để kết thúc phiên và đóng kết nối
- Cú pháp:
```QUIT (CLRF)```
- Phản hồi:
``` 221 Bye (CLRF)```