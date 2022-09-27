# Linux Bridge
### Sơ lược
- Linux Bridge là một phần mềm được tích hợp sẵn vào trong nhân Linux để giải quyết các vấn đề ảo hoá phần network trong các máy vật lý. Về mặt logic, Linux Bridge sẽ tạo ra một switch ảo để cho các VM kết nối được vào và có thể nói chuyện được với nhau cũng như sử dụng để ra mạng ngoài
- Ngoài ra, khi tìm hiểu Linux Bridge có một số thuật ngữ:
    - Port: tương tự cổng của switch thật
    - Bridge: switch ảo
    - Tap: còn gọi là interface, là giao diện mạng để các VM kết nối với switch do Linux Bridge tạo ra (hoạt động ở tầng 2 của mô hình OSI)
    - Forward Data: có nhiệm vụ chuyển dữ liệu từ VM tới switch
- Switch ảo do Linux Bridge tạo ra có chức năng tương tự với một con switch vật lý

### Kiến trúc của Linux Bridge

![image](https://github.com/Tubui160999/thuctap_nhanhoa/blob/master/KVM/images/linuxbridge.png?raw=true)

### Chức năng của một switch ảo do Linux Bridge tạo ra
- STP: là giao thức chống loop gói tin trong switch
- VLAN: là tính năng quan trọng của switch
- FDB: là tính năng chuyển đổi gói tin theo database được xây dựng giúp tăng tốc độ của switch

### Công cụ và lệnh làm việc với Linux Bridge
- Linux Bridge được hỗ trợ version kernel từ 2.4 trở lên. Để sử dụng và quản lý các tính năng của Linux Bridge, cần cài đặt gói bridge-utilities
```sh
yum install bridge-ultils -y
```

##### Bridge management commandline
| ACTION | BRCTL | BRIDGE |
| - | - | - |
| Tạo một bridge | ```brctl addbr <bridge>``` | |
| Xoá đi một bridge | ```brctl delbr <bridge>``` | |
| Thêm một interface (port) vào bridge | ```brctl addif <bridge> <ifname>``` | |
| Xoá đi một interface (port) khỏi bridge | ```brctl delbr <bridge>``` | |

##### FDB management commandline
| ACTION | BRCTL | BRIDGE |
| - | - | - |
| Hiển thị danh sách địa chỉ MAC trong FDB | ```brctl showmacs <bridge>``` | ```bridge fdb show``` |
| Sets FDB entries ageing time | ```brctl setageingtime <bridge> <time>``` | |
| Sets FDB garbage collector interval | ```brctl setgcint <brname> <time>``` | |
| Adds FDB entry | | ```bridge fdb add dev <interface> [dst, vni, port, via]``` |
| Appends FDB entry | | ```bridge fdb append <interface> [dst, vni, port, via]``` |
| Deletes FDB entry | | ```bridge fdb delete <interface> [dst, vni, port, via]``` |

##### STP management commandline
| ACTION | BRCTL | BRIDGE |
| - | - | - |
| Turning STP on/off | ```brctl stp <bridge> <state>``` | |
| Setting bridge priority | ```brctl setbridgeprio <bridge> <priority>``` | |
| Setting bridge forward | ```brctl setfd <bridge> <time>``` | |
| Setting bridge 'hello' time | ```brctl sethello <bridge> <time>``` | |
| Setting bridge maximum message age | ```brctl setmaxage <bridge> <time>``` | |
| Setting cost of the port on bridge | ```brctl setpathcost <bridge> <port> <cost>``` | ```bridge link set dev <port> cost <cost>``` |
| Setting bridge port priority | ```brctl setportprio <bridge> <port> <priority>``` | ```bridge link set dev <port> priority <priority>``` |
| Should port process STP BDPUs | | ```bridge set dev <port> guard [on|off]``` |
| Should bridge might send traffic on the port it was received | | ```bridge link set dev <port> hairpin [on|off]``` |
| Enabling/disabling fastleave options on port | | ```bridge link set dev <port> fastleave [on|off]``` |
| Setting STP port state | | ```bridge link set dev <port> state <state>``` |

##### VLAN management commandline
| ACTION | BRCTL | BRIDGE |
| - | - | - |
| Creating new VLAN filter entry | | ```bridge vlan add dev <dev> [vid|pvid|untagged|self|master]``` |
| Delete VLAN filter entry | | ```bridge vlan delete dev <dev> [vid|pvid|untagged|self|master]``` |
| List VLAN configuration | | ```bridge vlan show``` |