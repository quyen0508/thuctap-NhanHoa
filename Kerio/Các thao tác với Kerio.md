# Các thao tác với Kerio
## Cài đặt SSL Let's Encrypt cho Kerio Connect
- Truy cập trang web quản trị của Kerio, chọn tab **Configuration** rồi chọn **SSL Certificates**
- Tại giao diện quả lý chứng chỉ SSL, chọn **New** rồi chọn **New let's Encrypt Certificate**

![image](./image/Kerio%2013.png)

- Nhập tên miền cần được cấp chứng chỉ và chọn **Ok** để tiến hành cấp chứng chỉ tự động vào tạo gia hạn tự động

![image](./image/Kerio%2014.png)

![image](./image/Kerio%2015.png)

- Trở lại trang quản lý chứng chỉ, chuột phải vào chứng chỉ tên miền chính và chọn **Set as Default** để đặt làm chứng chỉ mặc định cho server

![image](./image/Kerio%2016.png)

- Kiểm tra chứng chỉ của trang web

![image](./image/Kerio%2017.png)

## Giao diện trang quản trị
- Gồm 4 tab: Accounts, Status, Configuration, Logs

### Accounts
- Dùng để quản lý các mục liên quan tới tài khoản
- Bao gồm: Users, Groups, Aliases, Mailing Lists, Resources
#### Users
- Người quản trị có thể quản lý user với các thao tác như thêm, sửa và xoá,...
- Tại thao tác thêm, người quản trị có thể cấu hình như:
    - Thiết lập cơ bản cho user

    ![image](./image/Kerio%2018.png)

    - Thiết lập các địa chỉ email cho user

    ![image](./image/Kerio%2019.png)

    - Thiết lập thông tin liên hệ
    - Thiết lập cài đặt chuyển tiếp
    - Thiết lập nhóm người dùng (Group)
    - Thiết lập quyền cho người dùng
    - Thiết lập giới hạn tài nguyên
    - Thiết lập cài đặt cho nội dung của email

#### Groups
- Người quản trị có thể quản lý group với các thao tác thêm, sửa và xoá
- Tại thao tác thêm, người quản trị có thể thiết lập
    - Tên của group

    ![image](./image/Kerio%2020.png)

    - Thêm các địa chỉ email

    ![image](./image/Kerio%2021.png)

    - Thêm các user vào trong group

    ![image](./image/Kerio%2022.png)

    - Quyền cho group

#### Aliases
- Người quản trị có thể quản lý các bí danh (alias) với các thao tác thêm, sửa và xoá
- Tại thao tác thêm, người quản trị thiết lập tên bí danh và địa chỉ email trỏ tới

![image](./image/Kerio%2023.png)

#### Mailing List
- Mailing List dùng để gửi và nhận email theo danh sách cụ thể
- Người quản trị có thể thêm, sửa và xoá các danh sách này
- Tại thao tác thêm, người quản trị có thể thiết lập
    - Đặt tên cho Mailing List

    ![image](./image/Kerio%2024.png)

    - Lời chào hoặc lời nhắn đính kèm khi gửi email
    - Subcription

    ![image](./image/Kerio%2025.png)

    - Posting
    - Quản lý moderator

    ![image](./image/Kerio%2026.png)

    - Quản lý các thành viên của danh sách

    ![image](./image/Kerio%2027.png)

    - Archive

#### Resource
- Người quản trị có thể quản lý liên quan tới nguồn tài nguyên như thêm, sửa và xoá

![image](./image/Kerio%2028.png)

### Status
- Tại tab **Status**, người quản trị có thể theo dõi trạng thái của server

#### Dashboard
- Hiển thị thông tin tổng quát của hệ thống

![image](./image/Kerio%2029.png)

#### Message Queue
- Thống kê các mail trong hàng đợi

![image](./image/Kerio%2030.png)

#### Traffic Charts
- Thống kê lưu lượng mạng

![image](./image/Kerio%2031.png)

#### Statistics
- Thống kê thông số hệ thống

![image](./image/Kerio%2032.png)

#### Active Connections
- Thống kê các kết nối và phiên đang hoạt động

![image](./image/Kerio%2033.png)

#### Opened Folders
- Hiển thị các thư mục đã mở

![image](./image/Kerio%2034.png)

#### System Health
- Thống kê thông số CPU, RAM và Storage

![image](./image/Kerio%2035.png)

### Configuration
#### Services
- Quản lý các dịch vụ đang chạy với các thao tác như: khởi động, dừng lại, khởi động lại và sửa (tên và port)

![image](./image/Kerio%2036.png)

#### Domains
- Quản lý các domain với các thao tác như: thêm, sửa, xoá, đặt làm tên miền chính,...

![image](./image/Kerio%2037.png)

#### SMTP Server
- Quản lý việc gửi thư qua Kerio Connect và quyền của người gửi
- Tại thao tác thêm, người quản trị có thể thiết lập
    - **Users from IP addess group** để chỉ định một nhóm địa chỉ IP mà người dùng có thể gửi đi
    - **User authenticated through SMTP for outgoing mail** để cho phép người dùng đã xác thực có thể gửi email đi
    - **Users previously authenticated through POP3 from the same IP address** cho phép người dùng đã xác thực trước đó qua POP3 có thể gửi thư cùng địa chỉ IP

    ![image](./image/Kerio%2038.png)

    - Ngoài ra, tại tab **Security Options**, người quản trị còn có thể quả lý như giới hạn dựa theo địa chỉ IP hay chặn theo điều kiện nhất định

    ![image](./image/Kerio%2039.png)

    - Tab **SMTP Delivery** dùng để quản lý các relay trung gian

    ![image](./image/Kerio%2040.png)

    - Tab **Queue Options** dùng để giới hạn các thông số liên quan đến relay (number of delivery threads hay retry interval)

    ![image](./image/Kerio%2041.png)

#### Instant Messaging
- Dịch vụ trò chuyện tức thời trên Kerio Connect

![image](./image/Kerio%2042.png)

#### Archiving and Backup
- Archive:
    - Archive dùng để lưu trữ email, XMPP và Chat
    - Có thể thiết lập thư mục lưu trữ nội bộ cho các bản lưu trữ
    
    ![image](./image/Kerio%2043.png)

- Backup:
    - Dùng để sao lưu dữ liệu
    - Có 2 kiểu sao lưu: Full backup - Sao lưu đầy đu và Differential backup - Sao lưu nhưng điểm khác so với lần sao lưu trước
    - Có thể thiết lập thư mục lưu cho các bản sao lưu, thông báo qua email khi tiến hành sao lưu

    ![image](./image/Kerio%2044.png)

#### SSL Certificates
Tham khảo tại
```sh
https://github.com/quyen0508/thuctap-NhanHoa/blob/main/Kerio/C%C3%A1c%20thao%20t%C3%A1c%20v%E1%BB%9Bi%20Kerio.md#c%C3%A0i-%C4%91%E1%BA%B7t-ssl-lets-encrypt-cho-kerio-connect
```

![image](./image/Kerio%2045.png)

#### Advanced Options
- Các tuỳ chọn nầng cao cho Kerio
- Để cấu hình cho Client, chuyển sang tab **Kerio Connect Client**
- Tại đây có thể thiết lập
    - Kích thước của email
    - Thời hạn cho 1 phiên hết hạn
    - Thời hạn tối đa cho 1 phiên
    - Thay đổi logo cho các Kerio Connect client

![image](./image/Kerio%2046.png)

#### Security
- Kerio có các chính sách bảo mật như **Require secure authentication** (yêu cầu xác thực bảo mật) hay **Require encrypted connection** (yêu cầu kết nối được mã hoá)
- Các phương thức bảo mật
    - **CRAM-MD5**
    - **DIGEST-MD5**
    - **LOGIN**
    - **PLAIN**
- **CRAM-MD5** và **DIGEST-MD5** đều xác thực bằng cách yêu cầu và phản hồi bằng mã MD5
- **LOGIN** và **PLAIN** dùng cho xác thực mật khẩu mã hoá bằng SHA
- Khi có nhiều phương thức được chọn, Kerio sẽ chọn phương thức khả dụng đầu tiên
- Ngoài ra, Kerio còn có chính sách cho người gửi (yêu cầu xác thực khi gửi email) và thiết lập phiên bản TLS cho kết nối vào ra

![image](./image/Kerio%2047.png)

#### Administration Settings
- Cho phép thiết lập một tài khoản quản trị được tích hợp sẵn

![image](./image/Kerio%2048.png)

#### MyKerio
- MyKerio là dịch vụ đám mây cho phép quản lý nhiều phiên bản của các thiết bị Kerio Connect thông qua giao diện web tập trung
- Để thiết lập, chọn **add this Kerio Connect** để chuyển sang trang đăng nhập của MyKerio

![image](./image/Kerio%2049.png)

- Nếu chưa có tài khoản, chọn **Register** để đăng ký tài khoản

![image](./image/Kerio%2065.png)

- Tạo một Appliance mới

![image](./image/Kerio%2066.png)

- Để truy cập vào Kerio Connect, chọn Appliance vừa tạo

![image](./image/Kerio%2067.png)

- Kerio Connect được truy cập thông qua trang MyKerio

![image](./image/Kerio%2068.png)

#### Spam Filter
- Để phát hiện và loại thư rác, sử dụng các phương pháp
    - **Spam Rating**: đặt giới hạn cho việc spam
    - **Kerio Anto-spam**: bộ lọc nâng cao tin nhắn spam bằng các dịch vụ quét trực tuyến của Bitdefender
    - **Blacklists**: tạo danh sách địa chỉ IP và đưa vào Blacklists để chặn tất cả các thư từ các địa chỉ đó
    - **Custom Rules**: cấu hình các quy tắc của riêng mình
    - **Call ID** và **SPF**: lọc thư có địa chỉ giả
    - **Greylisting**: chỉ gửi tin nhắn cho những người đã biết
    - **Spam Repellent**: hạn chế các công cụ spam bằng cách đặt độ trễ cho SMTP greeting

##### Spam Rating
- Spam Rating dùng để đặt giới hạn cho việc xác định thư rác
- **Tag Score**: khi đạt tới điểm đã thiết lập, thư được đánh dấu là thư rác
- **Block Score**: khi đạt tới điểm đã thiết lập, thư sẽ bị loại bỏ

![image](./image/Kerio%2050.png)

##### Kerio Anti-spam
- Kerio Anti-spam sử dụng dịch vụ quét trực tuyến của Bitdefender, cung cấp chức năng lọc thư rác nâng cao đối với các thư gửi đến
- Cách thức hoạt động của Kerio Anti-spam
    - Kerio Connect gửi dữ liệu được mã hoá tới dịch vụ quét trực tuyến Bitdefender
    - Bitdefender quét dữ liệu và gửi kết quả cho Kerio Connect thông qua thang điểm
        - 0: Không phải là thư rác
        - 1-9: Các mức độ spam
    - Kerio Connect tính toán điểm thư rác bằng một thuật toán đặc biệt và thêm điểm vào **Spam Rating**
    - Nếu Bitdefender nhận ra phần mềm độc hại hoặc email lừa đảo, Kerio Connect sẽ tự động chặn tin nhắn/phần mềm bất kể Kerio được cấu hình như nào

![image](./image/Kerio%2051.png)

##### Blacklists
- Blacklists dùng để chặn các máy chủ (theo địa chỉ IP) được cho là đang gửi tin nhắn rác
- Để tạo blacklist, trước hết cần biết địa chỉ IP của máy chủ cần chặn
    - Ở mục **Custom blacklist of spammer IP address**, bật tuỳ chọn **Use IP address group** và chọn **Edit** để tạo một nhóm địa chỉ IP mới

    ![image](./image/Kerio%2052.png)

    - Tạo một nhóm địa chỉ IP mới và thêm địa chỉ cần chặn

    ![image](./image/Kerio%2069.png)

    - Có 2 tuỳ chọn khi nhận được thư từ địa chỉ IP nằm trong nhóm địa chỉ IP vừa tạo
        - **Block the message**: chặn thư ngay khi nhận được
        - **Add spam score to the message**: tăng điểm xác định thư rác của thư
    - Chọn nhóm vừa tạo và chọn **Apply** để áp dụng cài đặt

    ![image](./image/Kerio%2070.png)

##### Custom Rules
- Kerio hỗ trợ tạo các luật tuỳ chọn giúp bao quát để xác định các trường hợp thư rác
- Để tạo một luật mới, chọn **Add**
- Tuỳ chỉnh các tuỳ chọn sau đó chọn **Ok** để lưu cài đặt

![image](./image/Kerio%2071.png)

![image](./image/Kerio%2072.png)

- Chọn **Apply** để áp dụng thiết lập

![image](./image/Kerio%2073.png)

##### Caller ID và SPF
- Caller ID & SPF cho phép lọc các thư có địa chỉ người gửi giả
- Spammer muốn gửi thư tới tên miền sé phải dùng địa chỉ thật, vì vậy, nếu gửi thư rác sẽ nhanh chóng bị phát hiện và ngăn chặn nhanh chóng
- Để thiết lập Caller ID, chọn **Check Caller ID of every incoming message** và chuyển sang tab **SPF** chọn **Enable SPF check of every incoming message**
- Có 3 lựa chọn thiết lập
    - **Log this to the security log only**
    - **Black and score to the message**
    - **Add spam score to the message**

![image](./image/Kerio%2053.png)

![image](./image/Kerio%2054.png)

##### Greylisting
- Greylisting là một phương pháp chống thư rác bổ sung cho các phương pháp và cơ chế chống thư rác khác
- Cách thức hoạt động
    - Kerio liên hệ với server Greylisting và cung cấp thông tin về thư. Greylisting server bao gồm  danh sách các địa chỉ IP đáng tin cậy
    - Nếu danh sách chứa địa chỉ IP của người gửi thư, thư sẽ vượt qua kiểm tra của Greylisting ngay lập tức
    - Nếu danh sách không chứa địa chỉ IP của người gửi, server Greylisting sẽ trì hoãn việc gửi thư. Nhưng người gửi thư đang tin cậy sẽ cố gắng gửi lại các thư sao đó trong khi người gửi thư rác thường không làm vậy
    - Sau khi nhận được thư, Kerio Greylisting sẽ thêm địa chỉ IP của người gửi vào whilelist. Vì vậy, thư của người gửi này sẽ luôn vượt qua sự kiểm tra của Greylisting

![image](./image/Kerio%2055.png)

##### Spam Repellent
- Phần lớn các thư rác được tạo ra bởi các công cụ gửi thư hàng loạt chuyên biệt, mục đích của các công cụ này là phân phối càng nhiều thư rác càng tốt trong một khoảng thời gian ngắn
- Spam Repellent hoạt động bằng cách tạo độ trễ của lời chào SMTP. Các mail hợp pháp thường sẽ đợi ít nhất 2 phút trước khi đóng kết nối, trong khi các công cụ thư rác thì thời gian này chỉ là vài giây
- Giá trị mặc định là 25 giây. Khoảng thời gian này làm giảm đáng kể lượng thư rác mà không làm mất email hợp lệ, nhưng đồng thời, thời gian nhận email sẽ bị trễ đi 25 giây

![image](./image/Kerio%2056.png)

#### Antivirus
- Kerio Connect tích hợp Kerio Antivirus giúp bảo vệ chống lại các email độc hại có chứa virus
- **Check for update every [hours]** dùng để đặt chu kỳ cập nhật cơ sở dữ liệu virus
- Nếu virus được tìm thấy trong thư, có thể thực hiện 2 hành động
    - **Discard the message** (Bỏ qua thư)
    - **Deliver the message with the malicious code removed** (Tiếp tục vận chuyển thư sau khi đã loại bỏ thành phần độc hại)
    - Ngoài ra còn có thể chọn 2 tuỳ chọn hành động khác là: **Forward the original message to the administrator address** (Chuyển tiếp thư gốc tới địa chỉ của tài khoản admin) và **Forward the filtered message to the administrator address** (Chuyển tiếp thư đã được xử lý tới địa chỉ của tài khoản admin)
- Nếu một phần của thư không thể quét được, có 2 hành động
    - **Deliver the original message with a warning** (Tiếp tục chuyển thư gốc kèm với cảnh báo)
    - **Reject the message as if it was a virus (use the settings above)** (Coi như thư có chứa virus và thực hiện hành động như phía trên)

![image](./image/Kerio%2057.png)

#### Attachment Filter
- Kerio cung cấp việc kiểm tra các file đính kèm để tránh việc lây nhiễm virus bằng việc vô tình mở file đính kèm có chèn mã độc
- **Attachment Filter** cho phép thêm các luật dùng để chặn/cho phép các file đính kèm

![image](./image/Kerio%2058.png)

- Người quản trị có thể chọn quy tắc cho luật theo tên file hoặc kiểu MIME

![image](./image/Kerio%2074.png)

    - Lọc theo tên file sẽ dựa theo đuôi file để cho phép/chặn các tệp đính kèm

    ![image](./image/Kerio%2075.png)

    - Lọc theo kiểu của MIME (Multipurpose Internet Mail Extensions - là tiêu chuẩn giúp phân loại tập tin được sử dụng trên Internet)

    ![image](./image/Kerio%2076.png)

- Khi gặp thư có chứa điều kiện trên, người quản trị có thể cấu hình để gửi thư gốc hoặc đã được loại bỏ tới địa chỉ chỉ định
- Ngoài ra còn có tuỳ chọn loại bỏ file zip chứa các file có đuôi mở rộng nguy hiểm (ví dụ như file thực thi *.exe)

#### Message Filters
- Kerio cung cấp việc kiểm tra tiêu đề, nội dung thư,... bằng **Message Filters** cho việc gửi và nhận thư

![image](./image/Kerio%2059.png)

- Người quản trị có thể cấu hình điều kiện cho các luật

![image](./image/Kerio%2077.png)

![image](./image/Kerio%2078.png)

- Cùng với đó là các hành động khi thoả mãn điều kiện của luật

![image](./image/Kerio%2079.png)

![image](./image/Kerio%2080.png)

#### Time Ranges
- **Time Ranges** là khoảng thời gian có thể sử dụng các dịch vụ của Kerio

![image](./image/Kerio%2060.png)

- Người quản trị có thể đặt thời gian bắt đầu, thời gian kết thúc và lịch lặp lại theo ngày/tuần

![image](./image/Kerio%2081.png)

#### IP Address Groups
- IP Address Groups giúp gộp nhóm những địa chỉ IP giúp quản lý theo nhóm tốt hơn

![image](./image/Kerio%2061.png)

- Người quản trị có thể thêm địa chỉ IP vào nhóm hiện có hoặc tạo nhóm mới

![image](./image/Kerio%2082.png)

#### User Access Policies
- Cho phép người quản trị thiết lập truy cập một số dịch vụ dành cho người dùng cụ thể

![image](./image/Kerio%2062.png)

- Người quản trị có thể
    - Đặt tên cho chính sách

    ![image](./image/Kerio%2083.png)

    - Chọn dịch vụ

    ![image](./image/Kerio%2084.png)

    - Cho phép hoặc chặn dịch vụ

    ![image](./image/Kerio%2085.png)

#### User Templates
- Người quản trị có thể tạo các mẫu cho user giúp cho việc thiết lập các user có cấu hình tương tự nhau trở nên dễ dàng, nhanh chóng hơn

![image](./image/Kerio%2063.png)

- Việc cấu hình tương tự như khi tạo một user mới

#### Company Locations
- Company Locations giúp thêm thông tin liên hệ về công ty

![image](./image/Kerio%2064.png)

- Người quản trị có thể thêm các thông tin như tên, địa chỉ, số điện thoại, tên miền,...

![image](./image/Kerio%2086.png)

### Logs
- Logs là những file giúp Kerio ghi lại thông tin về những sự kiện, ví dụ như lỗi, cảnh báo và debug, dựa vào đó có thể biết được trạng thái của server cũng như tìm được nguyên nhân dẫn đến lỗi để tìm cách khắc phục

#### Các loại log trong Kerio
##### Config
- Config log lưu trữ các thay đổi cấu hình trên server
- Các loại config log
    - Lưu trữ các thông tin đăng nhập trang quản trị Kerio Connect
    - Lưu trữ các thông tin thay đổi cấu hình trên CSDL
    - Những thay đổi khác trong cấu hình

##### Debug
- Sử dụng để giám sát các loại thông tin nhất định
- Mặc định sẽ hiển thị các thông tin liên quan đến khởi động và dứng dịch vụ, giao thức trên Mailserver Kerio Connect
- Liệt kê các dịch vụ và port kết nối phục vụ cho quá trình vận hành của mail server và các thông tin khác mô tả quá trình xử lế của mail server

##### Error
- Hiển thị những lỗi lớn mà có thể ảnh hưởng đến sự vận hành của mail server
- Điển hình có thể kể đến như là việc khởi tạo dịch vụ bị lỗi, phân phát không gian đĩa, khởi động kiểm tra antivirus, sự xác thực không hợp lệ của người dùng

##### Mail
- Ghi lại tiến trình xử lý mail
    - Mail gửi đến
    - Mail gửi đi
    - Mailing Lists

##### Operations
- Lưu lại những thay đổi như xoá và di chuyển các email, danh bạ, sự kiện, nhiệm vụ hay ghi chú trong hộp thư của người dùng. Trường hợp email bị đánh dấu spam hay di chuyển vào hòm thư spam cũng được ghi lại

##### Security
- Ghi lại thông tin liên quan đến bảo mật của Kerio Connect và chứa các bản ghi về các email không gửi được

##### Spam
- Hiển thị thông tin về tất cả các email spam được lưu trữ hoặc được đánh dấu trong Kerio Connect

##### Warning
- Hiển thị các thông báo cảnh báo về các lỗi có ý nghĩa nhỏ
- Các sự kiện được ghi trong mục này thường không ảnh hưởng lớn đến hoạt động của Kerio Connect

##### Audit
- Lưu trữ các thông tin về các lần xác thực thành công tài khoản Kerio Connect
- Bao gồm: tài khoản quản trị Kerio Connect, Kerio Connect Client, Microsoft Outlook,...

#### Các thao tác với log
##### Lưu file log về máy
- Có thể chọn lưu file log về máy theo dạng văn bản thông thường hoặc kiểu HTML và chọn lưu toàn bộ file hoặc một phần được chỉ định

![image](./image/Kerio%2087.png)

##### Highlighting
- Highlighting làm nổi bật các dòng log đáng chú ý được thiết lập tuỳ ý
- Cài đặt làm nổi bật bằng các từ khoá hoặc biểu thức chính quy (regex)

![image](./image/Kerio%2088.png)

- Các dòng chứa từ khoá đã được thiết lập sẽ có màu vàng

![image](./image/Kerio%2089.png)

##### Log Settings
- Mục **File Logging** có thể thiết lập để tự tạo file log mới theo chu kỳ hoặc đến kích thước giới hạn

![image](./image/Kerio%2090.png)

- Mục **External Logging** dùng để thiết lập Syslog logging

![image](./image/Kerio%2091.png)

## Cấu hình DKIM, DMARC, SPF trên Kerio
### DKIM
- DKIM viết tắt của Domain Keys Identified Mail
- Là một phương thức giúp xác nhận các email thông qua chữ ký số của miền gửi thư dùng để tránh giả mạo
- DKIM ban đầu được thiết kế để người nhận có thể xác định email đến từ miền cụ thể nào, tên miền đó thật không và có được uỷ quyền hay không

### DMARC
- DMARC là một tiêu chuẩn để chặn spammer khỏi sử dụng domain của người sở hữu mà không được sự cho phép của họ
- Thực tế, ai cũng có thể giả mạo địa chỉ tại trường "From" trong mail một cách dễ dàng, cơ chế này gọi là spoofing
- DMARC sẽ đảm bảo những mail giả mạo này sẽ bị chặn trước khi chúng đến mailbox của người nhận và chỉ có những người dùng mail hợp lệ mới được chấp nhận vào hệ thống

### SPF
- SPF viết tắt của Sender Policy Framwork
- Là cách thức để xác nhận một email server có được phép gửi email dưới tên của một domain nào không

### Cài đặt
#### DKIM
- Để cấu hình DKIM, truy cập vào tab **Configuration**, chọn **Domains**
- Chuột phải tên miền cần cấu hình, chọn **Edit**

![image](./image/Kerio%2092.png)

- Chọn **Sign outgoing messages from this domain with DKIM signature** và chọn **Show public key** để lấy thông tin của DKIM

![image](./image/Kerio%2093.png)

- Thông tin của DKIM

![image](./image/Kerio%2094.png)

- Tạo bản ghi TXT trên trang quản lý DNS với thông tin Kerio đưa ra

![image](./image/Kerio%2095.png)

#### DMARC
- Tạo bản ghi TXT trên trang quản lý DNS với nội dung

![image](./image/Kerio%2096.png)

> v=DMARC1; p=none; rua=mailto:mailauth-reports@mail.quyennx.xyz

#### SPF
- Tạo bản ghi TXT trên trang quản lý DNS với nội dung

![image](./image/Kerio%2097.png)

> v=spf1 +a +mx +ip4:103.159.51.14 ~all

### Kiểm tra DKIM, DMARC và SPF
- Kiểm tra bằng cách gửi 1 email từ Kerio Mailserver sang Gmail, chọn **Hiển thị thư gốc**

![image](./image/Kerio%2098.png)