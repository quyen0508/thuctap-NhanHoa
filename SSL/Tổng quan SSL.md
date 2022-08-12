# SSL
### Sơ lược về SSL
SSL viết tắt của Secure Socket Layer là tiêu chuẩn của công nghệ bảo mật giúp truyền thông mã hóa giữa máy chủ Web server và trình duyệt
Tiêu chuẩn này đảm bảo các dữ liệu truyền tải giữa máy chủ và trình duyệt của người dùng đều riêng tư và toàn vẹn
SSL hiện đang là tiêu chuẩn bảo mật cung cấp cho hàng triệu website trên thế giới giúp xác minh tính xác thực của website, đảm bảo dữ liệu, thông tin trao đổi giữa website và người dùng được mã hóa, tránh nguy cơ bị can thiệp

![image](https://nhanhoa.com/templates/images/ssl/1.png)

### Cách thức hoạt động
![image](https://nhanhoa.com/templates/images/ssl/2.jpg)

### Một số thuật ngữ
##### Domain Validation (DV SSL)
Chứng chỉ số SSL chứng thực cho Domain Name
Khi một website sử dụng DV SSL thì sẽ được xác thực tên domain, website đã được mã hóa và an toàn khi trao đổi dữ liệu

##### Organization Validation (OV SSL)
Chứng chỉ số SSL chứng thực cho website và xác thực doanh nghiệp đang sở hữu website đó

##### Extended Validation (EV SSL)
Website sử dụng chứng chỉ này có độ bảo mật cao nhất và được rà soát pháp lý kỹ càng

##### Subject Alternative Names (SANs SSL)
Nhiều tên miền được hợp nhất trong một chứng chỉ số:
- Với mỗi chứng chỉ số SSL tiêu chuẩn thì chỉ bảo mật duy nhất một tên miền đã được kiểm định. SANs mang lại sự linh hoạt cho người sử dụng, dễ dàng hơn trong việc cài đặt, sử dụng và quản lý chứng chỉ số SSL. Ngoài ra, SANs có tính bảo mật cao hơn Wildcard SSL, đáp ứng chính xác yêu cầu an toàn đối với máy chủ và làm giảm tổng chi phí triển khai SSL tới tất cả các tên miền và máy chủ cần thiểt
- SANs SSL có thể tích hợp tất cả các loại chứng chỉ số SSL của GlobalSign bao gồm: Chứng thực tên miền (DV SSL), chứng thực tổ chức doanh nghiệp (OV SSL) và chứng thực mở rộng (EV SSL)

##### Wildcard SSL
Wildcard SSL lý tưởng cho các trang thương mai điện tử. Mỗi e-store là một sub-domain và được chia sẻ trên một hoặc nhiều địa chỉ IP. Khi đó, để triển khai giải pháp bảo mật giao dịch trực tuyển (đặt hàng, thanh toán, đăng ký và đăng nhập tài khoản...) bằng SSL thì chỉ cần dùng duy nhất một chứng chỉ số Wildcard cho tên miền chính của website và tất cả các sub-domain

### Các đặc điểm của SSL
- _An toàn dữ liệu_: dữ liệu không bị thay đổi bởi hacker
- _Bảo mật dữ liệu_: dữ liệu được mã hóa và chỉ người nhận đích thực mới có thể giải mã
- _Chống chối bỏ_: đối tượng thực hiện gửi dữ liệu không thể phủ nhận dữ liệu của mình

### Các lợi ích của việc sử dụng SSL
- Xác thực website, giao dịch
- Nâng cao hình ảnh, thương hiệu và uy tín của doanh nghiệp
- Bảo mật các giao dịch giữa khách hàng và doanh nghiệp, các dịch vụ truy nhập hệ thống
- Bảo mật webmail và các ứng dụng mail như Outlook Web Access, Exchange và Office Communication Server
- Bảo mật các ứng dụng ảo hóa như Citrix Delivery Platform hoặc các ứng dụng điện toán đám mây
- Bảo mật dịch vụ FTP
- Bảo mật truy nhập control panel
- Bảo mật các dịch vụ truyền dữ liệu trong mạng nội bộ, file sharing và extranet
- Bảo mật VPN Access Server, Citrix Access Gateway,...
- Website không được xác thực và bảo mật sẽ luôn ẩn chứa nguy cơ bị xâm nhập dữ liệu, dẫn đến khách hàng không tin tưởng sử dụng dịch vụ