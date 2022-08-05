# Thực hành Packet Tracer
## 2.7.6 Packet Tracer - Implement Basic Connectivity
### Cấu hình cơ bản cho S1 và S2
#### Thay đổi hostname
```sh
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#hostname S1
S1(config)#
S1#
```
#### Đặt mật khẩu và mã hóa mật khẩu cho chế độ thực thi
```sh
S1(config)#line console 0
S1(config-line)#password cisco
S1(config-line)#login
S1(config-line)#exit
S1(config)#enable password class
S1(config)#enable secret class
The enable secret you have chosen is the same as your enable password.
This is not recommended.  Re-enter the enable secret.
S1(config)#
```

#### Tạo banner cảnh báo truy cập không được xác thực
```sh
S1(config)#banner motd "Authorized access only. Violators will be prosecuted to the full extent of the law."
```

#### Lưu cấu hình vào NVRAM
```sh
S1#copy running-config startup-config
Destination filename [startup-config]? 
Building configuration...
[OK]
S1#
```

#### Cấu hình tương tự cho S2
```sh
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#hostname S2
S2(config)#line console 0
S2(config-line)#password cisco
S2(config-line)#login
S2(config-line)#exit
S2(config)#enable password class
S2(config)#enable secret class
The enable secret you have chosen is the same as your enable password.
This is not recommended.  Re-enter the enable secret.
S2(config)#banner motd "Authorized access only. Violators will be prosecuted to the full extent law."
S2(config)#exit
S2#
%SYS-5-CONFIG_I: Configured from console by console

S2#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
S2#
```

### Cấu hình cho PC
#### Cài đặt địa chỉ IP cho PC1 và PC 2
![image](./image/2.7.6%20PC1.png)
![image](./image/2.7.6%20PC2.png)

### Cấu hình giao diện quản lý Switch
#### Cấu hình địa chỉ IP cho S1
```sh
S1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S1(config)#int vlan 1
S1(config-if)#ip address 192.168.1.253 255.255.255.0
S1(config-if)#no shutdown

S1(config-if)#
%LINK-5-CHANGED: Interface Vlan1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up

S1(config-if)#exit
S1(config)#exit
S1#
%SYS-5-CONFIG_I: Configured from console by console

S1#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
S1#
```

#### Cấu hình địa chỉ IP cho S2
```sh
S2#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
S2(config)#int vlan 1
S2(config-if)#ip address 192.168.1.254 255.255.255.0
S2(config-if)#no shutdown

S2(config-if)#
%LINK-5-CHANGED: Interface Vlan1, changed state to up

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up

S2(config-if)#exit
S2(config)#exit
S2#
%SYS-5-CONFIG_I: Configured from console by console

S2#copy
S2#copy running-config startup-config 
Destination filename [startup-config]? 
Building configuration...
[OK]
S2#
```

### Kiểm tra kết nối mạng
#### Kết nối giữa PC1 và S1
![image](./image/2.7.6%20ping%20PC1%20to%20S1.png)

#### Kết nối giữa PC1 và S2
![image](./image/2.7.6%20ping%20PC1%20to%20S2.png)

#### Kết nối giữa PC1 và PC2
![image](./image/2.7.6%20ping%20PC1%20to%20PC2.png)

#### Nhận xét
Khi ping tới các Switch, lần ping đầu tiên sẽ bị lỗi do lệnh yêu cầu ping phải chờ bản tin ARP để nhận biết các thiết bị khác. Việc chờ đợi này khá lâu nên lần ping đầu tiên sẽ bị lỗi, các lần sau do đã có trong ARP cache nên ping sẽ thành công

## 4.6.5 Packet Tracer - Connect a Wired and Wireless LAN
### Kết nối tới Cloud
#### Kết nối Cloud tới Router0
Sử dụng cáp đồng trục (Copper Straight-Through) kết nối Router0 F0/0 tới CLoud Eth6
![image](./image/4.6.5%20Cloud%20to%20Router0.png)

#### Kết nối Cloud tới Cable Modem
Kết nối Cloud Coax7 tới Modem Port0 bằng dây Coaxial
![image](./image/4.6.5%20Cloud%20to%20Cable%20Modem.png)

### Kết nối Router0
#### Kết nối Router0 tới Router1
Kết nối Router0 Ser0/0/0 tới Router1 Ser0/0 bằng dây Serial DTE
![image](./image/4.6.5%20Router0%20to%20Router1.png)

#### Kết nối Router0 tới netacad.pka
Kết nối Router0 F0/1 tới netcad.pka F0 bằng cáp xoắn đôi (Copper Cross-Over)
![image](./image/4.6.5%20Router0%20to%20netacad.pka.png)

#### Kết nối Router0 tới Configuration Terminal
Kết nối Router0 Console tới Configuration Terminal RS232 bằng cáp Console
![image](./image/4.6.5%20Router0%20to%20Configuration%20Terminal.png)

### Kết nối các thiết bị còn lại
#### Kết nối Router1 tới Switch
Kết nối Router1 F1/0 tới Switch F0/1 bằng cáp Fiber (cáp quang)
![image](./image/4.6.5%20Router1%20to%20Switch.png)

#### Kết nối Cable Modem tới Wireless Router
Kết nối Cable Modem Port1 tới Wireless Router Internet bằng cáp đồng trục (Copper Straight-Through)
![image](./image/4.6.5%20Cable%20Modem%20to%20Wireless%20Router.png)

#### Kết nối Wireless Router tới Family PC
Kết nối Wireless Router Ethernet1 tới Family PC bằng cáp đồng trục (Copper Straight-Through)
![image](./image/4.6.5%20Wireless%20Router%20to%20Family%20PC.png)

### Kiểm tra kết nối
#### Kết nối từ Family PC tới netacad.pka
Truy cập trang http://netacad.pka trên Web Browser của Family PC
![image](./image/4.6.5%20Family%20PC%20to%20netacad.pka.png)

#### Ping Switch từ Home PC
![image](./image/4.6.5%20Home%20PC%20to%20Switch.png)

#### Mở Router0 từ Configuration Terminal
Kết nối bằng Terminal trên Configuration Terminal và nhập lệnh ```show ip interface brief```
![image](./image/4.6.5%20Configuration%20Terminal%20to%20Router0.png)

## 10.1.4 Packet Tracer - Configure Initial Router Settings
### Kiểm tra cài đặt Default Router Configuration
#### Kết nối PCA tới R1
Kết nối PCA RS 232 tới R1 Console bằng cáp Console

#### Kiểm tra cài đặt hiện tại
![image](./image/10.1.4%20verify%20R1.png)

### Cấu hình và kiểm tra Initial Router Configuration
#### Cấu hình cài đặt ban đầu trên R1
![image](./image/10.1.4%20initial%20settings%20R1.png)
Bổ sung thêm lệnh ```service password-encryption``` trong ```R1(config)#```

#### Kiểm tra cài đặt trên R1
![image](./image/10.1.4%20verify%20initial%20settings%20R1.png)

### Lưu file cấu hình
#### Lưu file cấu hình vào NVRAM
![image](./image/10.1.4%20save%20to%20NVRAM.png)