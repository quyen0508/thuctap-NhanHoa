# Giới thiệu về OpenVZ
OpenVZ (Open Virtuizzo) là một công nghệ ảo hoá cấp hệ điều hành dành cho hệ điều hành Linux. Nó cho phép một máy chủ vật lý chạy nhiều phiên bản hệ điều hành riêng biệt, được gọi là containers, virtual private servers (VPSs) hay virtual enviroments (VEs). OpenVZ tương tự so với Solaris Containers và LXC

### So sánh với các công nghệ ảo hoá khác
- Trong khi các công nghệ ảo hoá khác như VMware, Xen và KVM cũng cấp khả năng ảo hoá đầy đủ và có khả năng chạy nhiều hệ điều hành và các phiên bản kernel khác nhau, OpenVZ sử dụng một kernel Linux đơn lẻ, vì vậy chỉ có thể chạy được Linux. Tất cả các containers đều chia sẻ chung kiến trúc và phiên bản kernel. Điều này gây ra nhược điểm khi các máy ảo yêu cầu các phiên bản kernel khác với máy host


### Kernel
OpenVZ sử dụng nhân (kernel) Linux được chỉnh sửa để hỗ trợ cho OpenVZ container. Kernal đã sử đổi cung cấp ảo hoá, cô lập và quản lý tài nguyên. Kể từ phiên bản vzctl 4.0, OpenVZ có thể chạy được các nhân Linux 3.x chưa được vá lỗi với tính năng bị hạn chế

#### Ảo hoá và cô lập
- Mỗi container là một thực thể riêng biệt, hoạt động phần lớn như một máy chủ vật lý
- Mỗi container bao gồm:
    - Files: Thư viện hệ thống, ứng dụng, ảo hoá /proc và /sys, các khoá ảo (virtualized locks),...
    - Users và groups: Mỗi container đều có tài khoản root cũng như là các tài khoản và nhóm khác
    - Cây tiến trình: Một container chỉ có thể thấy được các tiến trình của nó (bắt đầu bằng ```init```). Các PID đều được ảo hoá
    - Mạng: Thiết bị mạng ảo, cho phép container có địa chỉ IP, các bộ luật của tường lửa và các luật định tuyến một cách độc lập
    - Các thiết bị: Bất kể container nào cũng có thể có quyền truy cập vài các thiết buh thực như network interface, phân vùng ổ đĩa,...

### Quản lý tài nguyên
Quản lý tài nguyên trong OpenVZ gồm 4 thành phần: Phân chia đĩa theo 2 cấp, lập lịch cho CPU, lịch I/O và bộ đếm người dùng

### Hạn chế
- Theo mặc định, OpenVZ hạn chế quyền truy cập vùng chứa đối với các thiết bị vật lý thực, do đó làm cho vùng chứa không phụ thuộc vào phần cứng. Người quản trị OpenVZ có thể cho phép truy cập container vào các thiết bị thực khác nhau như ổ đĩa, usb,...
- /dev/loopN thường bị hạn chế trong triển khai
- OpenVZ bị giới hạn chỉ cung cấp một số công nghệ VPN dựa trên PPP (PPTP, L2TP) và TUN/TAP, ÍPec được hỗ trợ trong container kể từ kernal 2.6.32