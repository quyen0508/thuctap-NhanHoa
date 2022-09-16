# Giới thiệu về KVM
### Sơ lược về KVM
- KVM viết tắt của Kernel-based Virtual Machine sử dụng môi trường ảo không yêu cầu phần cứng bổ sung để thiết lập. Thay vào đó, nó sử dụng tài nguyên phần cứng hệ thống của máy tính hiện có. KVM tạo môi trường cho người dùng phục vụ nhiều mục đích sử dụng như kiểm thử phần mềm, nghiên cứu hành vi của virus,...

### Yêu cầu của KVM
- Đối với phần cứng, yêu cầu tối thiểu:
    - Bộ nhớ RAM: 16GB
    - Số nhân CPU: 4
    - Bộ nhớ lưu trữ: 40GB

- Đối với hệ điều hành, chỉ hỗ trợ RHEL 8.2 trở lên hoặc CentOS tương ứng

### Đặc điểm của KVM
- KVM giúp chia sẻ các nguồn tài nguyên ổ đĩa, mạng, CPU một cách công bằng
- KVM là một phần của Linux và được hưởng lợi từ các tính năng, do vậy, KVM sẽ được hưởng lợi từ mọi tính năng, khả năng sửa lỗi và các bản cập nhật mới của Linux mà không cần các thao tác bổ sung
- KVM không có tài nguyên dùng chung, do vậy sẽ tận dụng triệt để và không bị chia sẻ giúp hoạt động ổn định hơn

### Cách hoạt động
- Để có thể chạy ảo hoá, KVM cung cấp một số thành phần cấp hệ điều hành, chẳng hạn như trình quản lý bộ nhớ, bộ lập lịch xử lý, ngăn xếp đầu vào/ra (I/O), trình điều khiển thiết bị, quản lý bảo mật, ngăn xếp mạng,...
- Mọi ảo hoá sẽ được triển khai như một quy trình Linux thông thường, được lên lịch sẵn bởi bộ lập lịch Linux tiêu chuẩn, phần cứng ảo chuyên dụng như card mạng, adapter đồ hoạ, CPU, bộ nhớ và ổ đĩa

### Các tính năng
##### Tính năng bảo mật
Công nghệ KVM kết hợp với Linux giúp tăng khă năng bảo mật của SELinux (xây dựng ranh giới quanh máy ảo), sVirt(đẩy mạng khả năng bảo mật, kiểm soát truy cập MAC dùng cho máy ảo khách, chống lỗi ghi nhãn thủ công, cách ly VM)

##### Lưu trữ
KVM cho phép người dùng được sử dụng các bộ lưu trữ được Linux hỗ trợ như: NAS, đĩa cục bộ,...

##### Hỗ trợ phần cứng
KVM có thể được sử dụng trên nhiều nền tảng phần cứng được Linux hỗ trợ

##### Quản lý bộ nhớ
KVM sở hữu các chức năng quản lý bộ nhớ của Linux, hỗ trợ truy cập bộ nhớ không đồng nhất, hợp nhất kernel. Khi đó, bộ nhớ ảo hoá KVM có khả năng hoán đổi có hiệu suất tốt, được chia sẻ hoặc sao lưu bởi một tệp đĩa

##### Di chuyển công nghệ ảo hoá KVM trực tiếp
KVM cho phép di chuyển một chương trình ảo hoá đang chạy mà không gây ra sự gián đoạn giữa các máy chủ vật lý. Lúc này, KVM vẫn chạy, mọi kết mạng và ứng dụng vẫn hoạt động bình thường

##### Hiệu suất, khả năng mở rộng
Do KVM sở hữu các ưu điểm của Linux, đồng thời có khả năng mở rộng giúp phù hợp để đáp ứng nhu cầu khi máy khách yêu cầu truy cập tăng lên nhiều lần
Cong nghệ KVM cho phép khối lượng công việc ứng dụng yêu cầu khắt khe nhất được ảo hoá và là cơ sở cho nhiều thiết lập ảo hoá doanh nghiệp, điển hình như trung tâm dữ liệu, máy chủ ảo VPS và công nghệ đám mây riêng

##### Độ trễ thấp
Do Linux có các thành phần cho phép mở rộng thời gian thực tế để các ứng dụng dựa trên KVM chạy trong một chế độ trễ thấp hơn với mức độ ưu tiên tốt hơn. Đồng thời, chúng cũng tiến hành phân chia các quá trình yêu cầu một khoảng thời gian dài tính toán thành các khoảng nhỏ hơn, rồi sau đó lên lịch để xử lý tương ứng

##### Quản lý với KVM
KVM cho phép quản lý thủ công chương trình ảo hoá sau khi được kích hoạt từ máy trạm mà không cần thông qua công cụ quản lý
Chức năng này thường được các doanh nghiệp lớn sử dụng để quản trị nguồn tài nguyên, tăng khả năng phân tích dữ liệu, hợp lý các hoạt động

### Ưu điểm của KVM
- Khả năng linh hoạt: Mặc dù máy chủ gốc được cài đặt Linux nhưng KVM hỗ trợ tạo máy chủ ảo có thể chạy cả Linux, Windows. Khi được sử dụng kết hợp với QEMU, KVM có thể chạy Mac OS X. Ngoài ra, KVM cũng hỗ trợ cả 2 hệ thống kiến trúc tập lệnh x86 và x86_64
- Có tính độc quyền cao: Cấu hình từng gói VPS KVM sẽ chỉ có một người sở hữu và toàn quyền sử dụng tài nguyên (bao gồm CPU, RAM, Disk,...) mà khônhg bị chia sẻ hay ảnh hưởng bởi các VPS khác hoạt động trên cùng một hệ thống
- Độ bảo mật cao: Nhờ tích hợp các đặc điểm bảo mật của Linux như SELinux với các cơ chế bảo mật nhiều lớp, KVM bảo vệ các máy ảo tối đa và cách ly hoàn toàn, tránh bị xâm hại
- Tiết kiệm chi phí, khả năng mở rộng cao: Do được phát triển trên nền tảng mã nguồn mở hoàn toàn miễn phí và được hỗ trợ từ cộng đồng và nhà sản xuất thiết bị, KVM ngày càng lớn mạnh và trở thành một lựa chọn hàng đầu cho doanh nghiệp có chi phí thấp nhưng đem lại hiệu quả sử dụng cao

### Nhược điểm của KVM
- Yêu cầu cao cho máy chủ: Do là công nghệ ảo hoá hoàn toàn phần cứng, KVM yêu cầu cấu hình server vậy lý cao
- KVM chỉ có sẵn trên các hệ thống Linux
- Cần nhiều thời gian để nghiên cứu và học tập để có thể đưa vào sử dụng
- Do tập trung hoá phần cứng nên rủi ro tăng cao trong trường hợp hệ thống bị lỗi