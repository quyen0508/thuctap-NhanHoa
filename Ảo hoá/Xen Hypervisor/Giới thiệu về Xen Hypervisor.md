# Giới thiệu về Xen Hypervisor
- Xen Hypervisor là một trình giám sát máy ảo Virtual Machine Monitor (VMM) hypervisor native và là một sản phẩm mã nguồn mở
- Được sử dụng làm cơ sở cho một số ứng dụng thương mại mã nguồn mở khác nhau như server virtualization, infrastracture as a Service (IaaS), desktop virtualization, security application, embedded and hardware devices,...

### Một số tính năng chính
- Size và Interface nhỏ (kích thước khoảng 1MB). vì sử dụng thiết kế microkernel, với dung lượng bộ nhớ và giao diện (interface) hạn chế cho máy khách, nên nó mạnh mẽ và an toàn hơn so với các trình ảo hoá khác
- Hệ điều hành không rõ ràng: Hầu hết các cài đặt với Linux là do stack điều khiển chính (gọi là "doamin 0"). Nhưng một số hệ điều hành có thể thay thể, bao gồm NetBSD và OpenSolaris
- Trình điều khiển được cách ly: Xen Project hypervisor có khả năng cho phép trình điều khiển thiết bị chính của hệ thống chạy bên trong một máy ảo. Nếu trình điều khiển gặp sự cố hoặc bị xâm phạm, VM có chứa trình điều khiển có thể được khởi động lại mà không hề ảnh hưởng tới phần còn lại của hệ thống
- Paravirtualization: Fully paravirtualized guests được tối ưu như một máy ảo, cho phép guest chạy nhanh hơn nhiều so với các tiện ích mở rộng phần cứng không hỗ trợ tiện ích mở rộng phần cứng (Hardware Virtual Machine - HVM). Ngoài ra, trình ảo hoá có thể chạy trên phần cứng không hỗ trợ các tiện ích mở rộng ảo hoá

### Kiến trúc của Xen
- Trình ảo hoá Xen Hypervisor chạy trực tiếp và chịu trách nhiệm xử lý CPU, bộ nhớ, bộ hẹn giờ và ngắt. Đây là chương trình đầu tiên chạy sau khi thoát khỏi bộ nạp hệ thống. Một phiên bản đang chạy của máy ảo sẽ được gọi là domain hoặc guest
- Một domain đặc biệt được gọi là domain0 chứa trình điều khiển cho tẩt cả các thiết bị trong hệ thống, Domain0 cũng chứa control stack và các service systems khác  để quản lý hệ thống trên Xen
- Thông qua Dom0 Disaggregation: có thể chạy một số trình điều khiển dịch vụ và thiết bị này trong một máy ảo chuyển dụng, tuy nhiên, đây không phải là thiết lập hệ thống thông thường

![image](https://github.com/minhhoang699x/thuctap_lmh/raw/main/C%C3%B4ng%20ngh%E1%BB%87%20%E1%BA%A3o%20h%C3%B3a/Xen%20VPS/image/1.PNG)

- Guest Domain/Virtual Machines là môi trường ảo hoá, mỗi môi trường chạy hệ điều hành và ứng dụng riêng của chúng. Trình ảo hoá hỗ trợ một số chế độ ảo hoá khác nhau. Guest VM hoàn toàn tách biệt với phần cứng, nói cách khác, chúng không có quyền truy cập vào phần cứng hoặc functions I/O. Do đó chúng được gọi nlaf domain không có đặc quyền (hoặc DomU)
- Domain điều khiển (Dom0) là một máy ảo chuyên dụng và có đặc quyền đặc biệt như khả năng truy cập trực tiếp vào phần cứng, xử lý tất cả các quyền vào functions I/O của hệ thống và tương tác với VM khác. Không thể sử dụng trình ảo hoá Xẻn mà không có Domain0, đây là VM đầu tiên được khởi động. Trong một thiết lập tiêu chuẩn, Dom0 chứa các chứ năng
    - System Services: chẳn hạn như XenStore/XenBus(XS) để quản lý cài đặt. Toolstack (TS) hiển thị giao diện người dùng Xen sử dụng thiết bị mô phỏng (DE) dựa trên QEMU (Quick EMUlator) trong các hệ thống được sử dụng bởi Xen
    - Native Device Drivers: Dom0 là nguồn của trình điều khiển thiết bị vật lý và do đó hỗ trợ phần cứng riêng cho hệ thống Xen
    - Virtual Device Drivers: Dom0 chứa trình điều khiển thiết bị ảo (gọi là back-ends)
    - Toolstack: Cho phép người quản lý việc tạo, huỷ và cấu hình máy ảo. Bộ công cụ hiển thị giao diện được điều khiển bởi bẳng điều khiển dòng lệnhm giao diện đồ hoạ hoặc bỏi cloud orchestration stack như OpenStack hoặc CloudStack

### Công cụ ảo hoá cho Web Server
#### Công nghệ của Xen Citrix
- Là giải pháp ảo hoá miễn phí phù hợp với các doanh nghiệp vừa và nhỏ, Xen Server cung cấp những tính năng cao cấp không trả phí bao gồm:
    - Hỗ trợ số lượng máy chủ không giới hạn, máy ảo và bộ nhớ vật lý
    - Cho phép chuyển đổi từ một máy chủ ảo thành một máy chủ vật lý và ngược lại nếu cần (có tính phí)
    - Chia sẻ hệ thống lưu trữ SAN và NAS giữa các máy chủ
    - Quản lý dễ dàng các máy chủ ảo từ một nơi duy nhất
    - Khi máy chủ vật lý bị lỗi, những máy ảo bị ảnh hưởng sẽ tự động được khởi động trên một máy chủ vật lý khác
    - Một thư viện máy ảo mẫu được cấu hình sẵn
    - Quản lý tập trung việc cập nhật các bản vá lỗi cho máy chủ ảo
    - Nhân bản dễ dàng các máy chủ ảo từ máy chủ vậy lý này sang máy chủ vật lý khác
    - Xen Server là mã nguồn mở nên có ưu thế là nhiều người cùng đóng góp và xây dựng
    - Xen Server tương thích hầu hết với phần cứng hiện tại

#### Xen Desktop
- Là giải pháp ảo hoá Desktop của Citrix, Xen Desktop phân phối giao diện người dùng đến bất cứ đâu
- Các tính năng bao gồm
    - Người dùng có thể truy cập vào giao diện người dùng của họ ở bất kỳ đâu và trên nhiều thiết bị hỗ trợ khác nhau
    - ĐƯợc tối ưu hoá hiệu suất và bảo mật cho người dùng
    - Tương thích với hầu hết thiết bị người dùng đầu cuối

#### Xen App
- Là giải pháp ảo hoá ứng dụng của Citrix cho phép người dùng kết nối trực tiếp đến ứng dụng Windows thông qua một máy Desktop hay một trình duyệt web
- Những tính năng bao gồm
    - Truy cập ứng dụng Windows trên các thiết bị sử dụng hệ điều hành không thuộc Windows có hơn 30 hệ điều hành được hỗ trợ
    - Giải pháp này chỉ yêu cầu một bản sao ảo của ứng dụng được cài đặt như là Office, trong khi đó nó cho phép số lượng người dùng không giới hạn truy cập và sử dụng
    - Sử dụng có thể được truyền đi trực tiếp từ máy chủ đến người dùng đang làm việc trong mạng cục bộ hay ở xa, cho phép người dùng tải và truy cập ứng dụng trong khi đang Offline. Tương thích với hầu hết thiết bị người dùng đầu cuối