# Giới thiệu về Open vSwitch
- Open vSwitch là một loại switch ảo mã nguồn mở theo giao thức OpenFlow
- Open vSwitch là một ứng dụng nhiều tầng được viết bằng ngôn ngữ C, cung cấp cho người dùng các chức năng quản lý network interface
- Phù hợp với chức năng như là một switch ảo trong môi trường ảo hoá
- Hỗ trợ nhiều nền tảng như Xen/XenServer, KVM và VirtualBox

### Các tính năng
- Hỗ trợ VLAN tagging và chuẩn 802.1q trunking
- Hỗ trợ STP (Spanning Tree Protocol 802.1D)
- Hỗ trợ LACP (Link Aggregation Control)
- Hỗ trợ port mirroring (SPAN/RSPAN)
- Hỗ trợ Flow export (Sử dụng giao thức sflowm netflow)
- Hỗ trợ các giao thức đường hầm (GRE, VXLAN, IPSEC tunneling)
- Hỗ trợ kiểm soát QoS

### Các thành phần và kiến trúc của Open vSwitch
- Các thành phần chính của Open vSwitch
    - ovs-vswitchd: daemon tạo ra switch, được đi kèm với Linux kernel module
    - ovsdb-server: Một máy chủ cơ sở dữ liệu nơi ovs-vswitchd truy vấn để lấy cấu hình
    - ovs-dpctl: Công cụ để cấu hình switch kernel module
    - ovs-vsctl: Dùng đe truy vấn và cập nhật cấu hình cho ovs-vswitchd
    - ovs-appctl: Dùng để gửi lệnh chạy Open vSwitch daemon

![image](https://github.com/Tubui160999/thuctap_nhanhoa/raw/master/KVM/images/openvs.png)

### Cơ chế hoạt động
- Open vSwitch được chia làm 2 phần: Open vSwitch kernel module và user space tools
- OVS kernel module sẽ dùng netlink socket để tương tác với vswitchd daemon nhằm tạo và quản lý số lượng OVS switches trên hệ thống local. SDN Controller sẽ tương tác với vswitchd sử dụng giao thức OpenFlow, ovsdb-server chứa bảng dữ liệu. Các client từ bên ngoài có thể tương tác với ovsdb-server sử dụng json rpc với dữ liệu dạng file JSON
- Open vSwitch có 2 chế độ
    - Normal Mode: Open vSwitch tự quản lý tất cả các công việc switching/forwarding, hoạt động như một switch layer 2
    - Flow Mode: Open vSwitch dùng flow table để quyết định xem port nào sẽ nhận packets, flow table sẽ được quản lý bởi SDN Controller nằm bên ngoài

![image](https://github.com/Tubui160999/thuctap_nhanhoa/blob/master/KVM/images/openvs1.png)

### Một vài câu lệnh với Open vSwitch
- ```ovs-vsctl```: Cài đặt và thay đổi một số cấu hình ovs, cung cấp interface cho phép người dùng tương tác với database để truy vấn và thay đổi dữ liệu
    - ```ovs-vsctl show:``` Hiển thị cấu hình hiện tại của switch
    - ```ovs-vsctl list-br```: Hiển thị tên của tất cả các bridge
    - ```ovs-vsctl list-port```: Hiển thị tên của tất cả các port trên bridge
    - ```ovs-vsctl list-interface```: Hiển thị tên của tất cả các interface trên bridge
    - ```ovs-vsctl add-br```: Tạo bridge mới trong database
    - ```ovs-vsctl add-port```: Gán interface (card ảo hoặc card vật lý) vào Open vSwitch bridge
- ```ovs-ofctl``` và ```ovs-dpctl```: Dùng để quản lý và kiểm soát các flow entries. OVS quản lý 2 loại flow:
    - OpenFlows: Flow quản lý control plane
    - Datapath: Kernel flow
    - ```ovs-ofctl``` giao tiếp với OpenFlow module, ovs-dpctl giao tiếp với Kernel module
- ```ovs-ofctl show```: Hiển thị thông tin ngắn gọn về switch bao gồm port number và port mapping
- ```ovs-ofctl dump-flows```: Dữ liệu trong OpenFlow tables
- ```ovs-dpctl show```: Thông tin cơ bản về logical datapath (các switch) trên switch
- ```ovs-dpctl dump-flows```: Hiển thị flow cached trong datapath
- ```ovs-appctl bridge/dumpflows```: Thông tin trong flow tables và offers kết nối trược tiếp cho VMs trên cùng host
- ```ovs-appctl fdb/show```: Hiển thị các cặp mac/vlan

### So sánh Open vSwitch và Linux Bridge
| Open vSwitch | Linux Bridge |
| - | - |
| Được thiết kế cho môi trường mạng ảo hoá | Mục đích ban đầu không phải dành cho môi trường ảo hoá |
| Có các chức năng của layer 2-4 | Chỉ có chức năng của layer 2 |
| Có khả năng mở rộng | Bị hạn chế về quy mô |
| ACLs, QoS, Bonding | Chỉ có chức năng forwarding |
| Có OpenFlow Controller | Không phù hợp với môi trường cloud |
| Hỗ trợ netflow và sflow | Không hỗ trợ tunneling |

##### Open vSwitch
- Ưu điểm: Các tính năng tích hợp nhiều và đa dạng, kế thừa từ Linux Bridge. Open vSwitch hỗ trợ ảo hoá lên tới layer 4. Được sự hỗ trợ mạnh mẽ từ cộng đồng. Hỗ trợ xây dựng overlay network
- Nhược điểm: Phức tạp, gây ra xung đột luồng dữ liệu

##### Linux Bridge
- Ưu điểm: Các tính năng chính của switch layer được tích hợp sẵn trong nhân. Có được sự ổng định và tin cậy, dễ dàng trong việc troubleshoot less moving parts: Được hiểu như DB hoạt động một cách đơn giản, các gói tin được forward nhanh chóng
- Nhược điểm: Để sử dụng ở mức user space phải cài đặt thêm các gói. VD: vlan, ifenslave. Không hỗ trợ openflow và các giao thức điều khiển khác, không có sự linh hoạt