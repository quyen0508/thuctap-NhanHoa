# Giao thức DNS
### Giới thiệu chung
DNS viết tắt của Domain Name  System là hệ thống phân giải tên miền được phát minh vào năm 1984 nhằm mục đích chính là phân giải tên miền thành địa chỉ IP
### Phân loại máy chủ
- Primary server DNS: là server DNS chính
- Secondary server DNS: là server DNS phụ, được cập nhật thông tin định kỳ qua server chính
- Cả hai đều có chức năng tương đương nhau

### Cấu trúc của một tên miền
- Gồm 4 phần:
    - Root Domain
    - Top-Level Domain
    - Second-Level Domain
    - Subdomain
- Ví dụ về tên miền ```ktht.nuce.edu.vn```:
    - Root Domain: là phần sau phần ```vn```, bao gồm một đấu chấm ".", thông thường khi sử dụng trình duyệt thì thành phần này thường được bỏ qua
    - Top-Level Domain: ```vn```
    - Second-Level Domain: ```edu```
    - Subdomain: ```nuce```
    - Host: ```ktht```

### Các bản ghi của DNS
##### Bản ghi SOA
Dùng để chỉ ra máy chủ Name Server là nơi cung cấp thông tin tin cậy từ dữ liệu có trong Zone. Tất cả các DNS Zone đều cần một bản ghi SOA để tuân theo tiêu chuẩn của IETF, các bản ghi SOA cũng rất quan trọng trong việc chuyển vùng Zone
Cú pháp:
```[tiên-miền] IN SOA [tên-server-dns] [địa-chỉ-email] (serial number;refresh number;retry number;expire number;TTL number)```
Trong đó:
- ```serial``` là số phiên bản của bản ghi SOA, khi số này thay đổi thì sẽ cảnh báo cho các server phụ rằng chúng nên cập nhật các bản sao của file zone thông qua chuyển vùng zone
- ```refresh``` là khoảng thời gian tính bằng giây để server phụ phải đợi trước khi yêu cầu server chính cung cấp SOA record xem nó đã được cập nhật hay chưa
- ```retry``` là khoảng thời gian server phải đợi để yêu cẩu nếu một Name Server không phản hồi cập nhật lại
- ```expire``` là khoảng thời gian server phụ sẽ ngừng phản hồi cho zone nếu không nhận được phản hồi từ server chính
- ```TTL``` là khoảng thời gian cache của bản ghi

Chuyển vùng Zone: là quá trình gửi dữ liệu bản ghi DNS từ Name Server chính đến Name Server phụ

##### Bản ghi NS
Chức năng: chỉ ra các máy chủ DNS quản lý tên miền của hệ thống. Một tên miền thường có nhiều bản ghi NS để chỉ ra các server đích danh chính và dự phòng cho tên miền đó. Nếu không cấu hình đúng bản ghi NS thì sẽ không thể tải trang web khi sử dụng bằng tên miền
Cú pháp: ```[tên miền] IN NS [tên-server-dns]```
Ví dụ:
- ```ktht.nuce.edu.vn IN NS server1.ktht.nuce.edu.vn```
- ```ktht.nuce.edu.vn IN NS server2.ktht.nuce.edu.vn```

##### Bản ghi A
Chức năng: 
- Dùng để ánh xạ tên máy hoặc tên miền thành địa chỉ IPv4
- Vận hành danh sách danh sách lỗ hổng bảo mật dựa trên hệ thống tên miền DNSBL. DNSBL có thể giúp máy chủ email xác định và chặn mail từ các tên miền gửi mail rác đã biết

Cú pháp: ```[tên-máy-tính] IN A [địa-chỉ-IP]```
Ví dụ:
- ```server1 IN A 10.0.0.1```
- ```server2 IN A 10.0.0.2```

##### Bản ghi AAAA
Chức năng:
- Dùng để ánh xạ tên máy hoặc tên miền thành địa chỉ IPv6
- Một tên miền có thể có một hoặc nhiều địa chỉ IPv4 và các bản ghi A đi kèm nhưng không phải tất cả đều có địa chỉ IPv6 và các thiết bị của người dùng đều được cấu hình IPv6

##### Bản ghi CNAME
Chức năng: dùng để tạo tên gọi khác (bí danh) khác cho một máy chủ hoặc tên miền. Bản ghi này luôn luôn trỏ tới một tên miền, không bao giờ trỏ tới địa chỉ IP
Cú pháp: ```[tên-bí-danh] IN CNAME [địa-chỉ-IP]```
Ví dụ:

```www IN CNAME 10.0.0.1```

##### Bản ghi PTR
Chức năng: dùng để ánh xạ đại chỉ IP thành tên máy (ngược lại với bản ghi A và AAAA)
Cú pháp: ```[địa-chỉ-IP] IN PTR [tên-máy-tính]```
Ví dụ:

```10.0.0.1 IN PTR server1.ktht.nuce.edu.vn```
Một số mục đích chính của bản ghi PTR
- _Chống thư rác_: một số bộ lọc chống thư rác sử dụng bản ghi này để kiểm tra tên miền của địa chỉ email và xem liệu các địa chỉ IP liên kết có khả năng được sử dụng bới các máy chủ hợp pháp hay không
- _Khắc phục sự cố gửi email_: vì các bộ lọc chống thư rác sử dụng bản ghi này, các vấn đề gửi email có thể do bản ghi PTR bị định cấu hình sai hoặc bị thiếu. Nếu một tên miền không có bản ghi PTR hoặc nếu bản ghi PTR chứa tên miền sai, các dịch vụ mail có thể chặn tất cả các email từ tên miển đó
- _Ghi nhật ký_: Nhật ký hệ thống thường chỉ ghi lại địa chỉ IP, bản ghi này có thể chuyển những tên miền này thành tên miền cho nhật ký mà con người dễ đọc hơn

##### Bản ghi MX
Chức năng: dùng trong việc chuyển hướng tới mail server. Bản ghi này chp biết cách gửi mail theo SMTP
Cú pháp: ```[tên-miền] IN MX [thứ-tự-ưu-tiên] [tên-máy-chủ-mail]
Ví dụ:
- ```ktht.nuce.edu.vn IN MX 1 server1.ktht.nuce.edu.vn```
- ```ktht.nuce.edu.vn IN MX 2 server2.ktht.edu.vn```

### DNS Zone
##### Zone thuận
Chức năng: dùng để phân giải tên miền thành địa chỉ IP
Cú pháp:
```sh
zone "[tên-miền]" IN {
    type [tên-kiểu];
    file "[tên-file-cấu-hình]";
}
```
Ví dụ:
```sh
zone "ktht.nuce.edu.vn" IN {
    type master;
    file "ktht.db";
}
```
##### Zone nghịch
Chức năng: dùng để phân giải địa chỉ IP thành tên miền
Cú pháp:
```sh
zone "[địa-chỉ-lớp-mạng.in-addr.arpa]" IN {
    type [tên-kiểu];
    file "[tên-file-cấu-hình]";
}
```
Ví dụ:
```sh
zone "0.0.10.in-addr.arpa" IN {
    type master;
    file "0.0.10.in-addr.arpa.db";
}
```

### Bản tin DNS
![image](https://electronicspost.com/wp-content/uploads/2016/05/2.23.png)
- 12 bytes đầu tiên là header section, trong đó có một số trường như:
    - Identification chiếm 16-bit
    - 1-bit cờ query/reply để đưa ra chỉ dẫn liệu bản tin là query(0) hay reply(1)
    - 1-bit cơ authoritative, 1-bit cờ recursion-desired
    - 1-bit cờ recursion-desired
    - 1-bit trường recursion-available
    - Ngoài ra còn 4 trường, các trường naqfy chỉ dẫn số lần xuất hiện của 4 kiểu dữ liệu trong data section
- Question section bao gồm các thông tin về truy vấn đang được tạo
- Answer section bao gồm bản ghi nguồn cho phần tên miền đã yêu cầu
- Authority section bao gồm các bản ghi của các server authoritative khác
- Additional section bao gồm các bản ghi hữu dụng khác