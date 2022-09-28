# Cài đặt Check MK
### Cài đặt Check MK Server
- Cập nhật hệ thống

```sh
yum -y update
```

- Cài đặt repo EPEL và wget

```sh
yum install -y epel-release wget
```

- Tải về file cài OMD - Check MK

```sh
wget https://download.checkmk.com/checkmk/2.0.0p26/check-mk-raw-2.0.0p26-el7-38.x86_64.rpm
```

- Cài đặt file vừa tải về

```sh
yum install -y check-mk-raw-2.0.0p26-el7-38.x86_64.rpm
```

- Tạo site trên OMD

```sh
omd create quyennx
```

- Check MK tạo thông tin đăng nhập

![image](./image/OMD%201.png)

- Khởi động site trên OMD

```sh
omd start quyennx
```

- Truy cập trang địa chỉ được cung cấp lúc tạo site có dạng http://[tên-miền]/quyennx

![image](./image/OMD%202.png)

### Cài đặt Check MK Agent
- Mô hình triển khai giám sát
    - Host: Máy client dùng để đẩy metrics về checkmk
    - Server: Máy chủ đã được cài đặt checkmk

- Lấy đường dẫn file cài đặt Agent bằng cách chọn **Setup** -> **Agents** -> **Linux**/**Windows**

- Các package dành cho các distro chính
    - *.deb: dành cho các host sử dụng Debian
    - *.rpm: dành cho cac host sử dụng REHL
    - *.msi dành cho các host sử dụng Windows

- Cài đặt ```xinetd```

```sh
yum install -y xinetd
```

- Khởi động dịch vụ và chạy cùng hệ thống

```sh
systemctl start xinetd
systemctl enable xinetd
```

- Chạy lệnh cài đặt Agent

```sh
rpm -ivh check-mk-agent-2.0.0p26-1.noarch.rpm
```

- Sửa port tại file cấu hình của xinetd tại đường dẫn /etc/xinetd.d/check_mk
    - ```port = 6556```: cổng để server truy cập vào hôst
    - ```only_from```: địa chỉ IP server check mk
    - ```disable = no```: bật tắt dịch vụ

- Lưu và khởi động lại

```sh
systemctl restart xinetd
```

- Mở port 6556 nếu cần

- Thêm host trên Web GUI tại Check MK Server: Chọn **Setup** -> **Hosts**

![image](./image/OMD%203.png)

- Chọn **Add host** hoặc **Add host to the monitoring**

![image](./image/OMD%204.png)

- Nhập thông tin của host gồm **Hostname**, **IPv4 address** và **Checkmk agent / API integrations**, sau đó chọn **Save & go to service configuration** để kiểm tra cấu hình

![image](./image/OMD%205.png)

- Sau khi cấu hình xong, cần áp dụng thay đổi bằng cách chọn thông báo lưu ý thay đổi ở góc trên bên phải

![image](./image/OMD%206.png)

- Chọn **Activate on selected sites** để áp dụng thay đổi

![image](./image/OMD%207.png)

- Quay trở về màn hình chính để giám sát host vừa được thêm

![image](./image/OMD%208.png)