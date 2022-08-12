# DNS và Domain
### DNS
Tham khảo tại bản báo cáo DNS đã thực hiện
```sh
https://github.com/quyen0508/thuctap-NhanHoa/blob/main/M%C3%B4%20h%C3%ACnh%20OSI%20v%C3%A0%20TCPIP/DNS.md
```
Ngoài ra, bổ sung thêm:
##### Các bước để truy vấn DNS
- Người dùng nhập tên miền, ví dụ như nhanhoa.com vào trình duyệt web. Một truy vấn sẽ được tạo ra và được nhận bởi trình phân giải đệ quy - DNS Recursive Resolver
- Trình phân giải này sẽ truy vấn tới một root NameServer
- Root server sẽ phản hồi resolver một địa chỉ của Top-Level Domain server, tùy vào tên miền mà sẽ chuyển đến các server Top-Level Domain khác nhau, trong ví dụ thì ở đây là .com Top-Level Domain
- Resolver sẽ tạo một request đến .com Top-Level Domain
- Top-Level Domain server sẽ phản hồi với một địa chỉ NameServer của tên miền
- Resolver sẽ gửi truy vấn đến địa chỉ NameServer của tên miền
- Một địa chỉ IP sẽ được trả lại cho resolver từ NameServer
- Resolver sẽ phản hồi lại cho trình duyệt web địa chỉ IP của tên miền

*Resolver - hệ thống phân giải tên miền*

##### DNS Server
- Là một cơ sở dữ liệu chứa các thông tin về vị trí của các DNS Domain và phân giải các truy vấn xuất phát từ các client
- DNS Server có thể cung cấp các thông tin do client yêu cầu và chuyển đến một DNS Server khác để nhờ phân giải hộ trong trường hợp không thể trả lời được các truy vấn về những tên miền không thuộc quản lý và cũng luôn sẵn sàng trả lời các máy chủ khác về tên miền mà nó quản lý. DNS Server lưu thông tin của Zone, truy vấn và trả kết quá cho DNS Client
- Máy chủ Root Server do tổ chức ICANN quản lý:
    - Là Server quản lý toàn bộ cấu trúc của hệ thống tên miền
    - Root Server không chứa dữ liệu thông tin về cấu trúc hệ thống DNS mà nó chỉ chuyển quyền quản lý xuống cho các Server cấp thấp hơn, do đó Root Server có khả năng định đường đến một domain tại bất kỳ đâu trên Internet
- Primary Server:
    - Được tạo ra khi thêm một Primary Zone mới
    - Thông tin về tên miền do nó quản lý được lưu trữ tại đây và sau đó chuyển sang cho các Secondary Server
- Secondary Server:
    - Là các DNS Server phụ, được dùng khi Primary Server không khả dụng
    - Thông tin tên miền được cập nhật mỗi khi có sự thay đổi dữ liệu ở các bản ghi trên Primary Server

### Tên miền (Domain)
##### Định nghĩa
Tên miền là địa chỉ của trang web, được dùng để thay thế cho đia chỉ IP vốn khó nhớ hơn

##### Cấu trúc của một tên miền
Tham khảo tại báo cáo DNS
```sh
https://github.com/quyen0508/thuctap-NhanHoa/blob/main/M%C3%B4%20h%C3%ACnh%20OSI%20v%C3%A0%20TCPIP/DNS.md#c%E1%BA%A5u-tr%C3%BAc-c%E1%BB%A7a-m%E1%BB%99t-t%C3%AAn-mi%E1%BB%81n
```

##### Một số tên miền theo quy định quốc tế
| Tên miền | Ý nghĩa |
| - | - |
| .aero | Tên miền dành cho ngành hàng không |
| .asia | Tên miền dành cho châu Á |
| .biz | Tên miền dùng cho thương mại trực tuyến |
| .com | Tên miền website thương mại |
| .coop | Tên miền dành cho các liên hiệp, liên đoàn, hợp tác xã |
| .edu | Tên miền lĩnh vực giáo dục |
| .eu | Tên miền dành cho khối liên minh châu Âu |
| .gov | Tên miền sử dụng cho các tổ chức chính phủ |
| .health | Tên miền website về sức khỏe y tế |
| .info | Tên miền website thông tin |
| .mobi | Tên miền dành cho lĩnh vực điện thoại |
| .museum | Tên miền dành cho các bảo tàng |
| .name | Tên miền dành cho các trang cá nhân |
| .net | Tên miền của các công ty về Network hay nhà cung cấp dịch vụ mạng |
| .mil | Tên miền sử dụng cho quân đội |
| .org | Tên miền dùng cho chính phủ hay các tổ chức và nhóm |
| .pro | Tên miền dành cho các tổ chức nghề nghiệp |
| .tv | Tên miền sử dụng cho website truyền hình trực tuyến |
| .ws | Tên miền sử dụng cho các tổ chức thương mại hay cá nhân (Samoa)

##### Subdomain
- Là phần mở rộng của tên miền, có thể được sử dụng như một tên miền thực thụ.
- Ví dụ:
    - ```daotao.nuce.edu.vn```
    - ```cms.nuce.edu.vn```