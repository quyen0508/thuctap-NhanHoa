# Tổng quan về DirectAdmin
### Giới thiệu chung
- DirectAdmin là công cụ quản trị web server giúp đơn giản hóa việc thực hiện các công việc hàng ngày của webmaster, đặc biệt với những người có ít hoặc chưa có kinh nghiệm. DirectAdmin được quản lý thông qua giao diện trên trình duyệt web, có giao diện trực quan và dễ sử dụng
- DirectAdmin cung cấp cho người dùng nhiều tính năng như quản lý domain, subdomain, DNS, FTP và MySQL
- Ngoài ra, người dùng có thể tạo email theo tên miền, tạo SSH key, bảo mật SSL,... hay upload và quản lý file với File Manager một cách nhanh chóng và dễ dàng
- Tương tự cPanel, DirectAdmin có thể chạy rất tốt trên Linux với các bản phân phối như CloudLinux, RedHat Enterprise/CentOS, Debian/Ubuntu và FreeBSD. Hệ điều hành Windows không được hỗ trợ DirectAdmin


### Ưu và nhược điểm của DirectAdmin
##### Ưu điểm
- **Giao diện đồ họa thân thiện**: Thay vì quá nhiều phần và tùy chọn, tất cả các tính năng sẽ được xếp chồng lên nhau thành 3 nhánh chính: quản lý tài khoản, quản lý email và các tính năng bổ sung
- **Giá thành hợp lý**: giá thành là lý do chính giúp DirectAdmin có thể cạnh tranh với 2 đối thủ cùng lĩnh vực là cPanel và Plesk. DirectAdmin cung cấp một tài khoản dùng thử miễn phí cũng như nhiều tùy chọn trả phí khác chỉ từ $2/tháng
- **Hỗ trợ**: ngoài hỗ trợ của nhà cung cấp dịch vụ lưu trữ, người dùng còn có thể nhận được sự hỗ trợ trực tiếp từ các kỹ thuật viên của DirectAdmin. Người dùng gói trả phí Standard hay Lite trở lên đều có thể sử dụng hệ thống ticket
- **Phục hồi sự cố tự động**: nếu sự cố xảy ra bất ngờ, trước tiên DirectAdmin sẽ thử khởi động lại dịch vụ xem liệu điều này có khắc phục được sự cố hay không. Nếu không hiệu quả, hệ thống sẽ gửi thông báo lên quản trị viên web, giúp giải quyết vấn đề trong thời gian tối ưu nhất
- **Tốc độ**: DirectAdmin được thiết kế tương đối nhanh và nhẹ. Việc tải tài nguyên từ DirectAdmin cũng vô cùng thấp
- **Giao diện quản trị**: khác với cPanel vô cùng phức tạp với người mới sử dụng, DirectAdmin có một giao diện đơn giản, dễ dàng sử dụng và quản lý
- **Hỗ trợ nhiều phân cấp user**: hệ thống phân cấp người dùng (admin level, reseller level, user level) hỗ trợ tốt cho việc quản trị người dùng và đối tượng người dùng. Vì thế, DirectAdmin phù hợp với các đơn vị cung cấp hosting cho nhiều người dùng trực thuộc thông qua tài khoản reseller
- **Thiết lập thủ công**: mặc dù hầu hết các tính năng của DirectAdmin đều có thể thiết lập thông qua giao diện đồ họa (GUI) nhưng người dùng vẫn có thể thay đổi thiết lập thông qua giao diện dòng lệnh (CLI). Trên thực tế, người sử dụng thích sử dụng CLI hơn so với GUI

##### Nhược điểm
- **Tiện ích bổ sung**: các tiện ích bổ sung còn hạn chế. Tuy có thể thêm các chức năng nhưng khi đó sẽ tốn thêm chi phí
- **Cộng đồng nhỏ**: việc tìm kiếm các giải pháp cho các vấn đề gặp phải khó khăn hơn, đặc biệt với các vấn đề chuyên sâu
- **Giao diện thân thiện nhưng khó tìm**: DirectAdmin được chia thành nhiều phân cấp, điều đó khiến cho người dùng mới có thể sẽ gặp khó khăn khi cần xác định vị trí các tính năng cần tìm

### Các tính năng của DirectAdmin
##### Các tính năng chung
- **Integrated Ticket Support System**: hỗ trợ khách hàng với hệ thống ticket
- **Two-Factor Authentication**: yêu cầu xác thực 2 bước
- **Plugin System**: cho phép mở rộng chức năng trên DirectAdmin
- **Live Updates**: xem trạng thái giấy phép hiện tại, tự động thực hiện tải về và cài đặt các bản cập nhật hệ thống
- **Completely Customizable**: tùy biến giao diện tùy ý
- **Automatic Recovery From Crashes**: DirectAdmin TaskQueue đảm bảo rằng tất cả các dịch vụ luôn hoạt động. Nếu gặp sự cố xảy ra, DirectAdmin sẽ cố găng khắc phục bằng cách khởi động lại dịch vụ. Nếu không thành công, DirectAdmin sẽ thông báo cho quản trị viên ngay lập tức
- **We Support Your Customers Through Site-Helper**: Site-Helper được thiết kế giúp quản trị viên và khác hàng sử dụng DirectAdmin

##### Tính năng của Administrator Level
- **Create/Modify Admin and Reseller**: Admin có thể tạo Reseller hoặc Admin bổ sung một cách dễ dàng và nhanh chóng
- **Reseller Package**: Admin có thể tạo các gói tài khoản với các thông số được xác định trước. Khi tạo tài khoản, Admin chỉ cần chọn một gói đã được tạo trước đó thay vì phải thiết lập thủ công từng tính năng cho tài khoản
- **Show All Users**: cho phép Admin xem nhanh từng tài khoản trên hệ thống và sắp xếp danh sách này theo nhiều cách khác nhau
- **DNS Administrator**: cho phép Admin tạo, sửa đổi hoặc xóa bất kỳ bản ghi DNS nào trên server
- **IP Manager**: là nơi Admin đặt địa chỉ IP có sẵn cho server. Admin cũng có thể phân bổ địa chỉ IP cho Reseller
- **Mail Queue Administrator**: xem danh sách mail và message bao gồm các công cụ để thực hiện hành động đối với các message đó
- **System/Services Info**: Admin có thể xem, dừng, bắt đầu và khởi động lại các dịch vụ
- **Complete Usage Statics**: cung cấp cho Admin cái nhìn tổng quan đầy đủ về việc sử dụng hệ thống, đầu vào đầu ra chính xác từ Ethernet của server cũng được giám sát
- **DNS Clustering**: giao tiếp với các máy DirectAdmin khác để tự động chuyển dữ liệu DNS giữa chúng. Ngoài ra nó còn có khả năng tìm tên miền trên các máy chủ khác và tránh trùng lặp các bản ghi tên miền
- **Spam Fighting Tools**: nhiều công cụ chống Spam được cung cấp bởi DirectAdmin
- **Licensing/Updates**: Admin có thể xem trạng thái giấy phép hiện có và tải xuống các bản cập nhật phần mềm và bảo mật mới nhất

##### Tính năng của Reseller Level
- **Create/List/Modify Accounts**: tạo, liệt kê, sửa đổi và xóa các tài khoản
- **User Packages**: tạo các gói được xác định trước. Khi tạo tài khoản, Reseller chỉ cần chọn một gói đã được thiết lập từ trước thay vì thiết lập thử công cho từng tính năng cho tài khoản
- **Reseller Statics**: Reseller được cung cấp thông tin tổng quan đầy đủ về tổng mức sử dụng. Reseller cũng có thể sắp xếp dữ liệu theo User để nhanh chóng đánh giá tình hình tổng thể
- **Message All Users**: Reseller có thể nhanh chóng gửi tin nhắn đến tất cả khách hàng bằng cách sử dụng hệ thống hỗ trợ ticket được tích hợp sẵn
- **Import/Manage Skins**: Reseller có thể nhanh chóng nhập và áp dụng giao diện mới chỉ bằng một nút bấm
- **IP Assignment**: phân bổ địa chỉ IP cho khách hàng
- **System/Services Infomation**: truy cập vào trạng thái máy chủ và thông tin hệ thống
- **Name Servers**: tạo name server được cá nhân hóa cho khách hàng

##### Tính năng của User Level
- **E-mail Administrator**: User có thể tạo tài khoản POP/IMAP, địa chỉ email, forwarder, danh sách gửi thư, thư trả lời tự động và webmail, bộ lọc cho phép người dùng chạn mail theo tên miền, từ khóa và kích thước
- **FTP Management**: User có thể tạo tài khoản FTP và thiết lập quyền thư mục cho từng tài khoản. FTP ẩn danh cũng được hỗ trợ
- **DNS Menu**: User có thể thêm và xóa các bản ghi, thay đổi cài đặt MX và những phần khác với toàn quyền kiểm soát DNS
- **Statics Menu**: User có sẵn mọi thống kê về tài khoản của họ. Các tùy chọn nâng cao hơn và bao gồm cả Webalizer
- **Subdomains Menu**: User có thể liệt kê, tạo, xóa và lấy số liệu thống kê về các subdomain
- **File Manager**: là sự thay thế nhanh chóng và thân thiện với người dùng FTP, bao gồm mọi tính năng cần thiết để xây dựng và duy trì một trang web
- **MySQL Databases**: User có thể dễ dàng tại, sửa đổi và xóa cơ sở dữ liệu MySQL ngay từ menu này
- **Site Backup**: hỗ trợ sao lưu và khôi phục
- **Error Pages**: tạo các thông báo và kết quả đầu ra tùy chỉnh cho các mã lỗi 401, 403, 404 và 500
- **Directory Password Protection**: đặt mật khẩu bảo vệ bất kỳ thư mục nào bằng tên username và password
- **PHP Selector**: cho phép User chọn phiên bản PHP nào được liên kết với phần mở rộng .php
- **Advanced Tools**: nhiều tính năng nâng cao như chứng chỉ SSL, xem thông tin máy chủ và các module đã cài đặt, đặt cron job, mime types và trình xử lý apache, đồng thời cho phép chuyển hướng trang web và trỏ tên miền