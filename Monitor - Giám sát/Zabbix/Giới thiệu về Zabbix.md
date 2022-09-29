# Giới thiệu về Zabbix
- Zabbix là một công cụ dùng để giám sát hệ thống mạng, các thiết bị mạng, giám sát khả năng sẵn sàng và hiệu năng của mạng và thiết bị mạng. Nếu có xảy ra lỗi thì sẽ có cảnh báo gửi tới người quản trị mạng thông qua sms, email,...
- Zabbix là công cụ mã nguồn mở miễn phí
- Hỗ trợ bất kỳ kích thước của mô hình mạng nào, có thể là mô hình nhỏ hoặc mô hình lớn, thường xuyên cập nhật và phát hành phiên bản mới
- Được phát hành theo giấy phép GPIv2, không giới hạn về sức chứa và số lượng thiết bị được giám sát
- Zabbix được viết năm 1998, là dự án của Alexeo Vlandisher dùng để giám sát hệ thống CSDL

### Tính năng của Zabbix
- Zabbix cung cấp những tính năng quan trọng và cần thiết cho việc giám sát hệ thống và các thiết bị mạng
- Zabbix dựa trên các agent và agentless để giám sát hệ thống mạng và các thiết bị mạng. Các thiết bị phải hỗ trợ giao thức SNMP. Zabbix giám sát hiệu suất, hiệu năng của máy chủ vật lý cũng như máy ảo
- Trong trường hợp có lỗi xảy ra, Zabbix cảnh báo cho người quản trị. Tuy nhiên, Zabbix không có khả năng phát hiện hay dự đoán lỗi có thể xảy ra

##### Agent-based và Agentless
- Agent-based:
    - Được cài đặt trên máy chủ local và các thiết bị cần giám sát. Mục tiêu là thu thập thông tin gửi về Zabbix server và có thể cảnh báo tới người quản trị
    - Agent được cài đặt đơn giản nhẹ nhàng và tiêu thụ ít nguồn tài nguyên của server
    - Lợi ích của việc sử dụng agent là phân tích sâu hơn, ngoài ra có thể đoán được hiệu suất phần cứng, cung cấp khả năng cảnh báo và report

- Agentless:
    - Agentless là giải pháp không yêu cầu bất kỳ cài đặt agent riêng biệt nào. Phân tích mạng dựa trên việc giám sát package trực tiếp
    - Dựa trên giao thức SNMP haowjc WMI: một trạm quản lý trung tâm, giám sát tất cả các thiết bị mạng khác
    - Việc cài đặt không ảnh hưởng đến hiệu suất của server. Quá trình triển khai dễ dàng hơn, không phải cập nhật thường xuyên từ các agent. Tuy nhiên lại không đi sâu thu thập các số liệu, không cung cấp khả năng phân tích và báo cáo
    - Trong khi Zabbix agent cung cấp những tính năng tuyệt vời trên một số nền tảng, nhưng cũng có trường hợp có những nên tảng không thể cài đặt được. Đối với trường hợp này, sử dụng phương thức agentless để giám sát

##### Các tính năng của Agentless
- Network Service Check: Zabbix server có thể kiểm tra một service đang lăng nghe trên port nào hoặc chúng phản hồi có đúng không. Phương thức này hiẹn tại hỗ trợ một số service như FTP, IMAP, HTTP, HTTPS, LDAP, NNTP, POP3, SMTP, SSH, TCP và Telnet. Đối với các trường hợp không được xử lý bởi mục trước đó, Zabbix server có thể kiểm tra xem có gì đang lắng nghe trên các cổng TCP hay không, thông báo nếu một dịch vụ có sẵn hay không. Gồm có các chức năng: **TCP port availablity**, **TCP port response time** và **Service check**
- ICMP ping: Zabbix có thể kiểm tra xem máy chủ có đang phản hồi các gói ping ICMP hay không. Vì vậy, nó có thể kiểm soát sự sẵn sàng của một máy chủ cũng như thời gian phản hồi và mất gói tin. Kiểm tra có thể được tuỳ chỉnh bằng cách thiết lập kích thược và số lượng gói tin, thời gian chờ và độ trễ giữa các gói. Các chức năng bao gồm: **Server availability**, **ICMP response time** và **Package loss**
- Remote Check: Khi cấu hình Zabbix Agent không được hỗ trợ nhưng có thể truy cập thông qua SSH hoặc Telnet, máy chủ Zabbix có thể chạy bất kỳ lệnh tuỳ chỉnh nào và sử dụng lệnh trả về của nó như là một giá trị được thu thập. Từ các giá trị này được dùng để làm dữ liệu cho các đồ thị và cảnh báo. Chức năng này được gọi là **Executing commands via SSH or Telnet**

##### Auto discovery
- Hệ thống được cập nhật khi nó có sự thay đổi. Các thiết bị mới được thêm vào cần được tự động phát hiện. Tính năng theo dõi sự thay đổi môi trường liên tục được gọi là **Auto discovery**
- Cho phép thực hiện tìm kiếm các phần tử mạng, tự động thêm các thiết bị mới và loại bỏ các thiết bị không còn là một phần của hệ thống mạng, ngoài ra còn thực hiện việc khám phá các network interface, các port và các hệ thống file
- Auto discovery có thể được sử dụng để tìm ra trạng thái hiện tại trong mạng. Nếu mạng có Hệ thống phát hiện xâm phạm (Intrusion Detection System - IDS), tính năng phát hiện tự động có thể kích hoạt báo động xâm nhập
- Phát hiện tự động đóng một phần thiết yếu trong giám sát mạng, một số công cụ khác không cung cấp tính năng này, vì vậy cần chú ý auto discovery khi chọn công cụ giám sát mạng

##### Low-level discovery
- Low-level discovery (LLD) được sử dụng để giám sát các hệ thống file và interface mà không cần tạo thêm thủ công từng phần tử: LLD là một tính năng tự động thêm và xoá các phần tử. Nó cũng tự động tạo ra các trigger, graph cho file system, network interface và SNMP table

##### Trend Prediction
- Một số công cụ theo dõi mạng có tính năng dự đoán. Nó được sử dụng để phát hiện lỗi trước khi nó có thể xảy ra. Điều này được thực hiện bằng cách thu thập dữ liệu về băng thông mạng và trạng thái của các thiết bị theo mức độ hoạt động. Tất cả các thông tin được lưu trữ trong CSDL SQL. Các kết quả giám sát tiếp theo được so sánh với thông tin được lưu trữ trong cơ sở dữ liệu. Nếu một số thay đổi đối với dữ liệu đã được tìm thấy, giám sát mạng sẽ tạo ra một cảnh báo
- Trend Prediction cho phép phát hiện trước vấn đề quản trị viên mạng có thể giải quyết nó trước khi người dùng cuối nhận thấy nó. Mặc dù tính năng này hay nhưng hầu hết các sản phẩm lại không hỗ trợ tính năng này

##### Logical grouping
- Trong các mạng lớn bao gồm nhiều thiết bị thì khó có thể theo dõi và khắc phục tất cả các thiết bị trong quá trình giám sát mạng. Logical grouping cho phép kết hợp cùng một loạt các thiết bị cùng loại với nhau. Kết quả là logical grouping giúp việc giúp việc giám sát các mạng cấp doanh nghiệp dễ dàng hơn đáng kể
- Logical grouping cho phép kết hợp một loạt các thiết bị cùng loại thành các nhóm. Đối với mỗi nhóm có thể được xác định những gì cần được theo dõi và những hành động nên được thực hiện trong trường hợp xảy ra lỗi. Ngoài ra, với việc logical grouping có thể định cấu hình cài đặt hợp nhất cho tất cả phần tử của nhóm. Nếu một hoặc nhiều phần tử của nhóm ngừng hoạt động thì một cảnh báo sẽ xuất hiện
- Có thể tạo các nhóm lồng nhau cho các mạng lớn. Điều này có nghĩa là các nhóm có thể được tạo bên trong một nhóm khác. Kết quả là, việc quản lý các thiết bị mạng bên trong một mạng lớn trở nên dễ dàng hơn

##### Cấu trúc của Zabbix

![image](https://github.com/shaidoka/thuctap-NhanHoa/raw/main/CheckMK_Zabbix/CheckMK/images/checkmk_15.png)

- Zabbix bao gồm các thành phần: Zabbix Server, Zabbix Proxy, Zabbix Agent và Web Interface
    - Zabbix Server: là thành phần trung tâm của Zabbix. Zabbix Server có thể kiểm tra các dịch vụ mạng từ xa thông qua các báo cáo của Agent gửi về cho Zabbix Server và tự đó nó sẽ lưu trữ tất cả các cấu hình cũng như số liệu thống kê
    - Zabbix Proxy: là phần tuỳ chọn của Zabbix, có nhiệm vụ thu nhận dữ liệu trong bộ nhớ đêhn và chuyển đến Zabbix Server
    - Zabbix Agent: giám sát chủ động các thiết bị cụ bộ và các ứng dụng (ổ cứng, bộ nhớ,...) trên hệ thống mạng. Zabbix Agent sẽ được cài lên trên Server và từ đó Agent sẽ thu thập thông tin hoạt động từ Server mà nó đang chạy và báo cáo dữ liệu này đến Zabbix Server để xử lý
    - Web Interface: truy cập dữ liệu theo dõi và sau đó cấu hình từ giao diện web cung cấp

![image](https://github.com/shaidoka/thuctap-NhanHoa/raw/main/CheckMK_Zabbix/CheckMK/images/checkmk_16.png)

### Ưu điểm của Zabbix
- Zabbix đáp ứng các yêu cầu của công cụ giám sát mạng đáng tin cậy tới 90%. Nó thực hiện cả giám sát agentless, hỗ trợ low-level discovery, auto discovery, logical grouping
- Tất cả các tính năng nêu trên làm cho Zabbix trở thành một công cụ giám sát mạng hoàn hảo, đáp ứng đầy đủ các yêu cầu của bất kỳ mạng kích thước nào. Tuy nhiên, Zabbix không hỗ trợ dự đoán trường hợp xấu xảy ra
- Zabbix là một công cụ giám sát mạng đáng tin cậy, ngoài ra, lợi thế chính của Zabbix là khả năng mở rộng của nó, vì vậy nó có thể áp dụng cho môi trường có kích thước bất kỳ

### Nhược điểm
- Web Interface: thao tác sử dụng hiện tại của giao diện người dùng quá phức tạp. Người dùng Zabbix mới có thể sẽ gặp khó khăn với giao diện web. Một số thao tác cơ bản có thể tốn thời gian ngay cả đối với người dùng đã có kinh nghiệm, phải thao tác quá nhiều cho một hoạt động cơ bản
- API có thể có hiện tượng rất chậm, đặc biệt khi nói đến các hoạt động template linking. Ví dụ, có 10000 host muốn được liên kết chúng thành 1 template đơn giản. Nó sẽ mất khoảng 10 - 20p tuỳ thuộc vào phần cứng. Ngoài ra, nó sẽ tạo ra quá nhiều truy vấn SQL. Số lượng thậm chí có thể đạt tới hàng triệu