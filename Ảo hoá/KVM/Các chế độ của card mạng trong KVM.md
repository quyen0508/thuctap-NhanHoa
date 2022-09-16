# Các chế độ card mạng trong KVM
VMware có 3 chế độ card mạng là Bridge. NAT và Host-only, tương tự như WMware, KVM có 3 chế độ là Public Bridge, NAT, Private Bridge

### NAT
- NAT là chế độ mặc định trong KVM, cung cấp cho mỗi VM một IP theo dải mạng của hệ thống, chế độ này cho phép chuyển tiếp gói tin giữa lớp mạng bên trong VM với lớp mạng bên ngoài để có thể kết nối ra Internet
- Cơ chế được hiểu đơn giản là một bridge cho card mạng ảo kết nối với card mạng thật để ra Internet
- Card mạng ảo của VM gắn vào 1 bridge (vibr0), vibr0 mặc định có gateway, các gói tin của máy ảo sẽ đi qua đường này để đến card máy ảo thật và ra ngoài Internet
- KVM cung cấo DHCP cho các máy ảo dùng chế độ NAT

### Public Bridge
- Chế độ sẽ cho phép các máy ảo có cùng dải mạng vật lý với card mạng thật
- Để làm được việc này, cần thiết lập một bridge và cho phép nó kết nối với cổng vật lý của thiết bị thật (eth0)

### Private Bridge
- Chế độ này sẽ sử dụng một bridge riêng biệt để các VM giao tiếp với nhau mà không ảnh hưởng tới địa chỉ của KVM host