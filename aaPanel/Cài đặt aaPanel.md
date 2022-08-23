# Cài đặt aaPanel
- Update hệ thống trước khi cài đặt
```sh
yum update
```

- Để cài đặt sử dụng lệnh
```sh
yum install -y wget && wget -O install.sh http://www.aapanel.com/script/install_6.0_en.sh && bash install.sh
```

Trong đó:
> yum install -y wget

dùng để cài đặt ```wget``` nếu chưa có

> wget -O install.sh http://www.aapanel.com/script/install_6.0_en.sh

dùng để tải file install_6.0_en.sh về máy và đổi tên thành install.sh

> bash install.sh

dùng để chạy file cài đặt install.sh

- Xác nhận cài đặt aaPanel

![image](./image/aaPanel%201.png)

![image](./image/aaPanel%202.png)