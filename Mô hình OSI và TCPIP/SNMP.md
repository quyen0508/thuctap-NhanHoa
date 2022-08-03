# Giao thức SNMP
### Sơ lược về giao thức
SNMP viết tắt của Simple Network Management Protocol là một giao thức tầng ứng dụng sử dụng UDP port số 161/162 dùng để giám sát mạng, phát hiện lỗi mạng và thỉnh thoảng được dùng để cấu hình thiết bị từ xa

### Các thành phần của SNMP
##### SNMP Manager
Là hệ thống trung tâm được dùng để giám sát mạng. Được biết đến như là Network Management Station (NMS)
Các chức năng chính:
- Truy vấn agent
- Nhận phản hồi từ agent
- Đặt biến trong agent
- Nhận biết các sự kiện bất đồng bộ từ agent

##### SNMP agent
Là một mô-đun (module) phần mềm quản lý được cài vào thiết bị cần được quản lý như là máy tính, router, switch, server,...
Các chức năng chính:
- Thu thấp thông tin quản lý về môi trường nội bộ
- Lưu trữ thông tin quản lý được xác định trong MIB
- Báo một sự kiện cho bên quản lý
- Đóng vai trò như là một proxy cho một vài nút mạng non-SNMP

##### Management Information Base (MIB)
Bao gồm thông tin về các tài nguyên được quản lý. Thông tin này được tổ chức theo phân cấp bao gồm các chủ thể thường là các biến

### Các câu lệnh cơ bản của SNMP
##### Lệnh ```GET```
Được gửi từ bên quản lý tới thiết bị được quản lý để lấy một hoặc nhiều giá trị từ thiết bị được quản lý

##### Lệnh ```GET NEXT```
Tương tự với lệnh ```GET```, lệnh ```GET NEXT``` dùng để lấy giá trị của OID (Object of ID) tiếp theo trong cây MIB

##### Lệnh ```GET BULK```
Được dùng để lấy khối dữ liệu lớn từ bảng MIB lớn

##### Lệnh ```SET```
Được bởi bên quản lý để sửa đổi hoặc gán giá trị của thiết bị được quản lý

##### Lệnh ```TRAPS```
Được gửi từ các agent tới bên quản lý SNMP để báo sự xuất hiện của một sự kiện

##### Lệnh ```INFORM```
Tương tự với lệnh ```TRAPS``` nhưng có phản hồi xác nhận từ SNMP Manager

##### Lệnh ```RESPONSE```
Được sử dụng để nhận về giá trị hoặc thông báo các hành động từ SNMP Manager

### Các phiên bản của SNMP
##### SNMPv1
Là phiên bản đầu tiên, tuân thử theo chuẩn RFC 1155 và 1157

##### SNMPv2c
Là phiên bản nâng cấp của SNMPv1: cải tiến các loại gói tin giao thức, transport mappings, cấu trúc phần tử MIB nhưng sử dụng cấu trúc quản lý của SNMPv1
SNMPv2c tuân theo chuẩn RFC 1901, 1905, 1906 và 2578

##### SNMPv3
Là phiên bản có sử dụng mã hóa để bảo mật, cho phép cấu hình giám sát mạng từ xa
SNMPv3 tuân theo chuẩn RFC 1905, 1906, 3411, 3412, 3414 và 3415