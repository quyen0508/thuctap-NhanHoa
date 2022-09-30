# Giới thiệu giao diện của Zabbix
- Zabbix có các tab chính: Monitoring, Inventory, Reports, Configuration và Administration

### Monitoring
##### Dashboard
- Dashboard là giao diện hiển thị trực quan để người quản trị dễ dàng thấy được các thông tin của dashboard
- Người quản trị có thể tạo ra nhiều dashboard khác nhau nhưng tại một thời điểm chỉ có thể xem được một dashboard bất kỳ
- Từ Dashboard có thể nhanh chóng liên kết đến các thành phần như Graphs, Screens, Maps bằng cách thêm các thành phần mong muốn vào mục Favourite Graphs, Favourite Screen cà Favourite Maps

![image](./image/Zabbix%2012.png)

##### Problems
- Hiển thị các vấn đề đối với từng thiết bị mà zabbix server thu thập dữ liệu về
- Hỗ trợ cơ chế lọc theo ý muốn của người quản trị

![image](./image/Zabbix%2013.png)

##### Overview
- Overview là sự tổng hợp thông tin về data zabbix server thu thập được, có thể lọc theo group, host, kiểu data

![image](./image/Zabbix%2014.png)

##### Lastest data
- Lastest data là nơi dữ liệu mới nhất mà zabbix server thu thập được

![image](./image/Zabbix%2015.png)

##### Screens
- Screens là sự tập hợp các thông tin như Graphs, Maps, Data, Overview,... vào chung một màn hình giám sát. Giúp người quản trị có thể lựa chọn các thông tin cần thiết để hiển thị, giúp có cái nhìn tổng quát những thông tin mong muốn

![image](./image/Zabbix%2016.png)

![image](./image/Zabbix%2017.png)

##### Maps
- Maps là thành phần cung cấp khả năng giám sát hệ thống dưới hình thức mô hình mạng, giúp người quản trị có cái nhìn tổng quan về hệ thống mạng dưới dạng sơ đồ, trong trường hợp có sự cố sẽ giúp người quản trị đánh giá tầm ảnh hưởng của thiết bị gặp sự cố và đưa ra giải pháp phù hợp

![image](./image/Zabbix%2018.png)

##### Discovery
- Discovery cho phép Zabbix server tự động tìm kiếm các thiết bị được cài đặt Zabbix agent đã cấu hình kết nối về Zabbix server trong cùng một mạng với Zabix server

### Configuration
##### Host groups
- Host groups tập hợp lại các host có chung một mục đích sử dụng hoặc người quản trị tập hợp lại để phục vụ một mục đích quản lý chung

![image](./image/Zabbix%2019.png)

##### Templates
- Templates là tập hợp các thực thể có thể áp dụng cho các host, 1 template sẽ chứa trong nó các lệnh để truy vấn lấy dữ liệu, hiển thị thông tin dữ liệu lấy được, thông tin tình trạng thiết bị, hiển thị và thông báo lỗi,...
- Trong mỗi template, các tập lệnh được chia thành các danh mục: Items, Triggers, Graphs, Applications, Screens (có từ phiên bản Zabbix 2.0 trở lên), Low-level discovery rules (Zabbix 2.0+), Web scenarios (Zabbix 2.2+). Tuỳ theo giám sát thiết bị, dịch vụ, ứng dụng nào thì các thành phần này sẽ được thiết lập khác nhau

![image](./image/Zabbix%2020.png)

##### Hosts
- Hosts là một máy tính, server, vps chạy các hệ điều hành khác nhau hay một thực thể trong hệ thống mạng như máy in, máy chấm công, máy photo và camera có hỗ trợ các giao thức mà monitor zabbix cung cấp

![image](./image/Zabbix%2021.png)

##### Maintenance
- Maintenance có thể xác định thời gian bảo trì cho máy chủ và group trong Zabbix
- Có 2 loại Maintenance: thu thập dữ liệu và không thu thập dữ liệu
- Ví dụ, khi off server trong một khoảng thời gian để nâng cấp sửa chữa thì maintenance sẽ được lựa chọn cấu hình để không thu thập dữ liệu trong khoảng thời gian đó

![image](./image/Zabbix%2022.png)

##### Actions
- Actions là nơi cấu hình, lựa chọn các kiểu thông báo khi có sự kiện xảy ra bởi cấu hình trigger. Người dùng phải tự định nghĩa các action theo mục đích

![image](./image/Zabbix%2023.png)

##### Event correlation
- Cho phép cấu hình tương quan giữa các sự kiện với độ chính xác và tuỳ biến linh hoạt

##### Discovery
- Thiết lập range IP, nếu trong range có thiết bị đã cài đặt các giao thức mà Zabbix server hỗ trợ thì sẽ tự động thu thập data về

![image](./image/Zabbix%2024.png)

### Administration
- Các chức năng trong Administration dùng để cấu hình chung cho Zabbix đối với user có quyền admin

##### General
- General là nơi cho phép quản trị viên tuỳ chỉnh giao diện cho Zabbix Web Interface
- GUI: cung cấp một số tuỳ chỉnh mặc định liên quan đến giao diện người dùng
    - Default theme: chủ đề mặc định của giao diện (thường là màu xanh da trời)
    - Dropdown first entry: được chọn là mục tiêu đầu trong Dropdown
    - Search/Filter elements limit: số lượng tối đa hiển thị các hàng trong tìm kiếm và lọc
    - Max count of element to show inside table cell: giới hạn hiển thị bằng thông
    - Enable event acknowledges: cho phép các event Zabbix kích hoạt
    - Show events not older than (in days): cho phép hiển thị trạng thái trigger trong bao nhiêu ngày
    - Max count of events per trigger to show: số event được kích hoạt tối đa trong màn hình trạng thái
    - Show warning if Zabbix server is down: cho phép hiển thị thông điệp cảnh báo khi không kết nối được Zabbix Server

- HouseKeeping: quy định các thời gian định kỳ được thực hiện bởi Zabbix. Quá trình xoá thông tin hết hạn và thông tin được xoá bởi người dùng. Có thể tuỳ chỉnh các dữ liệu được lưu tối đa trong bao lâu trên Zabbix. Gồm các phần có thể cấu hình như Event and alerts, Services, Audit, User sessions, History và Trends
    - Enable internal housekeeping: lựa chọn bật hoặc tính thời gian để xoá bỏ thông tin
    - Trigger data storage period: khoảng thời gian dọn dẹp các thông tin về việc lưu trữ data trigger
    - Internal data storage period: khoảng thời gian dọn dẹp Internal data storage
    - Network discovery data storage period: khoảng thời gian dọn dẹp discovery data storage

- Images: chứa tất cả các hình ảnh, icon, background được hiển thị trong Zabbix

- Icon mapping: cho phép tạo biểu tượng bản đồ của 1 host với các biểu tượng nhất định. Các thông tin trong các tuỳ chọn đều phục vụ cho việc tạo bản đồ
    - Name: tên icon map (là duy nhất)
    - Mappings: danh sách các ánh xạ mà icon map tham chiếu đến
    - Inventory field: danh sách các thiết bị tồn tại
    - Expression: mô tả biểu thức chính quy
    - Icon: icon được dùng nếu biểu thức chính quy lỗi
    - Default: icon mặc định được dùng

- Regular expression: tạo và quy ước các biểu thức chính quy

- Macros: tạo các đoạn macro tương ứng với giá trị

- Value mapping: tạo các giá trị tương ứng với các mức

- Working time: tham số toàn hệ thống xác định thời gian làm việc

- Trigger severities: cấu hình màu hiển thị đối với các mức của trigger

- Trigger display options: màu sắc, hiệu ứng hiển thị khi có event

- Other configuration parameters

##### Proxies
- Cho phép cấu hình các Proxy trên giao diện Zabbix
- Name: tên của proxy
- Mode: chế độ của proxy (active hoặc passive)
- Encryption: mã hoá kết nối từ Zabbix Server đến Proxy
- Last seen (age): thời gian tại thời điểm kết nối cuối cùng với Proxy
- Host count: Số lượng item mà Proxy sử dụng
- Required performance (vps): Hiệu suất Proxy
- Host: Danh sách các host mà proxy quản lý

![image](./image/Zabbix%2025.png)

##### Authentication
- Authentication chứa thiết lập các phương pháp xác thực người dùng Zabbix: thẩm định nội bộ, LDAP và HTTP

![image](./image/Zabbix%2026.png)

![image](./image/Zabbix%2027.png)

![image](./image/Zabbix%2028.png)

##### User groups
- User groups giúp quản lý các nhóm trong Zabbix

![image](./image/Zabbix%2029.png)

##### Users
- Tuỳ chỉnh các tài khoản user cho Zabbix, có thể tạo các user khác với việc phân quyền tương ứng

![image](./image/Zabbix%2030.png)

##### Media types
- Các kênh alert

![image](./image/Zabbix%2031.png)

##### Script
- Các đoạn mã được thiết lập sẵn

![image](./image/Zabbix%2032.png)

##### Queue
- Thông tin về hàng đợi trong quá trình cập nhật dữ liệu về từ các nguồn agent

![image](./image/Zabbix%2033.png)