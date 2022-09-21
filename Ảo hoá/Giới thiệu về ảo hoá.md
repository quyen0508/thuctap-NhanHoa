# Giới thiệu về ảo hoá
- Ảo hoá (virtualization) là tạo một phiên bản ảo của tài nguyên nào đó như server, hệ thống lưu trữ, hệ thống mạng hay hệ điều hành nơi framework chia tài nguyên thành một hoặc nhiều môi trường thực thi
- Các thiết bị, ứng dụng và người dùng có thể tương tác với tài nguyên ảo như thể nó là một tài nguyên logic thực sự duy nhất (single logical resource)
- Thuật ngữ ảo hoá đã trở thành một phần của các công nghệ máy tính, bao gồm:
    - Ảo hoá hệ thống mạng (Network virtualization) là phương pháp kết hợp tài nguyên sẵn có trong mạng bằng cách chia băng thông sẵn có thành các kênh, mỗi kênh độc lập với các kênh khác và mỗi kênh có thể được gán cho một máy chủ hoặc thiết bị cụ thể theo thời gian thực
    - Ảo hoá hệ thống lưu trữ (Storage virtualization) là tổng hợp các bộ nhớ vật lý từ nhiều thiết bị mạng vào chỉ một thiết bị lưu trữ được quản lý từ bảng điều khiển trung tâm. Ảo hoá hệ thống lưu trữ thường được sử dụng trong các mạng lưu trữ (SAN)
    - Ảo hoá máy chủ (Server virtualization) là ảo hoá tài nguyên máy chủ (bao gồm số và danh tính của máy chủ vật lý, bộ xử lý và hệ điều hành), cho phép chạy nhiều máy ảo trên một máy chủ vật lý

### Lợi ích của ảo hoá máy chủ (Server virtualization)
- Tiết kiệm năng lượng, thân thiện với môi trường: Phân chia tài nguyên các máy chủ vật lý thành các máy ảo và hợp nhất với số lượng ít các máy chủ hơn sẽ giúp giảm chi phí điện năng và làm mát hệ thống
- Máy chủ hoạt động nhanh hơn: Cho phép khả năng mở rộng hoặc thu hẹp quy mô trong quá trình triển khai hệ thống tại thời điểm có nhu cầu, nhanh chóng sao chép gold image, master template hay virtual machine hiện có để có thể khởi chạy ngày một server trong vòng vài phút
- Tăng uptime
    - Hầu hết các nền tảng ảo hoá máy chủ hiện cung cấp các tính năng nâng cao mà máy chủ vật lý không có, giúp cải thiện tính liên tục của doanh nghiệp và tăng uptime. Các tính năng thường có mà các nhà cung cấp đưa ra: live migration, storage migration, fault tolerance, high availability và distributed resource scheduling
    - Những công nghệ cung cấp khả năng phục hồi nhanh chóng từ các sự cố cúp điện không có kế hoạch, khả năng di chuyển một máy ảo từ máy chủ này sang máy chủ khác nhanh chóng và dễ dàng là một trong những lợi ích lớn nhất của ảo hoá, giúp ảo hoá được rộng rãi
- Cải thiện disaster recovery: Virtualization cung cấp cho tổ chức 3 thành phần quan trọng trong việc xây dựng giải pháp khăc phục thảm hoạ (disaster recovery solution)
    - Khả năng trìu tượng hoá phần cứng. Bằng cách loại bỏ sự phụ thuộc vào một nhà cung cấp phần cứng hoặc mô hình máy chủ cụ thể, một disaster recovery site không coaafn phải có phần cứng giống nhau để phù hợp với môi trường làm việc và có thể tiết kiệm tiền bằng cách mua phần cứng rẻ hơn
    - Bằng cách hợp nhất tổ chức các máy chủ thành ít các máy vật lý hơn trong sản phẩm, một tổ chức có thể dễ dàng tạo ra một trang web nhân bản có giá phải chăng
    - Hầu hết các nền tảng ảo hoá máy chủ doanh nghiệp đều có phần mềm có thể giúp chịu lỗi một cách tự động khi xảy ra thảm hoạ. Các phần mềm tương tự cũng cung cấp cách kiểm tra disaster recovery failover, cung cấp khả năng thử nghiệm kế hoạch chuyển đổi dự phòng hoạt động hiệu quả như thế nào trong thực tế, giúp chuẩn bị tốt hơn cho những thảm hoạ bất ngờ trong tương lai

### Các mô hình ảo hoá hệ thống máy chủ
##### Hypervisor Native
- Hypervisor Native hay còn gọi là bare-metal hypervisor, chạy trực tiếp trên phần cứng
- Hypervisor Native nằm giữa phần cứng và một hoặc nhiều hệ điều hành khách (guest operating system)
- Được khởi động trước cả hệ điều hành và tương tác với kernel, điều này mang lại hiệu suất cao nhất có thể vì không có hệ điều hành chính nào cạnh tranh tài nguyên máy tính cùng. Nhưng đồng thời, hệ thống chỉ có thể được sử dụng để chạy các máy ảo vì hypervisor luôn phải chạy ngầm bên dưới
- Các hệ thống Hypervisor Native có thể kể đến: Oracle VM, VMware ESX Server, IBM's POWER Hypervisor, Microsoft's Hyper-V, Citrix XenServer,...

##### Hypervisor Hosted
- Hypervisor dạng hosted được cài đặt trên một máy tính chủ (host computer) với hệ điều hành đã được cài đặt
- Hypervisor Hosted chạy như một ứng dụng cũng như các phần mềm khác trên máy tính
- Hầu hết các hypervisor dạng hosted có thể quản lý và chạy nhiều máy ảo cùng một lúc. Lợi thế của hypervisor dạng hosted là nó có thể bật lên hoặc tắt đi khi cần thiết, giải phóng lập tức tài nguyên máy chủ
- Vì chạy bên trên nền một hệ điều hành nên khó có thể đem lại hiệu suất tương tự như hypervisor native
- Các hệ thống Hypervisor Hosted có thể kể đến: VMware Server, VMware Workstation, Microsoft Virtual Server,...