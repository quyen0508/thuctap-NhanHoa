# Các thao tác với Hyper-V
### Tạo và cấu hình máy ảo
- Truy cập trang quản lý của Hyper-V bằng cách chọn **Tools** -> **Hyper-V Manager**

![image](./image/Hyper-V%208.png)

- Chuột phải vào tên máy, chọn **New** -> **Virtual Machine**

![image](./image/Hyper-V%209.png)

- Đặt tên cho máy ảo

![image](./image/Hyper-V%2010.png)

- Chọn loại thế hệ máy ảo (nên chọn thế hệ thứ 2 có nhiều tính năng mới hơn, nhưng thế hệ 1 có khả năng tương thích rộng hơn)

![image](./image/Hyper-V%2011.png)

- Chọn dung lượng bộ nhớ RAM cho máy ảo

![image](./image/Hyper-V%2012.png)

- Chọn kết nối mạng

![image](./image/Hyper-V%2013.png)

- Thiết lập nơi lưu trữ máy ảo và dung lượng máy ảo

![image](./image/Hyper-V%2014.png)

- Chọn **Install an operating system later** để cài đặt hệ điều hành sau

![image](./image/Hyper-V%2015.png)

- Xem lại tổng quan thiết lập và chọn **Finish** khi thực hiện xong

![image](./image/Hyper-V%2016.png)

- Truy cập **Settings** bằng chuột phải vào tên máy ảo để truy cập thiết lập một vài thông số trước khi bật máy ảo

![image](./image/Hyper-V%2019.png)

- Để máy ảo nhận file cài, chọn **SCSI Controller**, chọn **DVD Drive** và chọn ***Add**

![image](./image/Hyper-V%2020.png)

- Chọn file cài đã tải về

![image](./image/Hyper-V%2021.png)

- Thay đổi vị trí boot của các ổ cứng

![image](./image/Hyper-V%2022.png)

- Tắt **Secure Boot** do các bộ cài thường không hỗ trợ, dẫn đến không thể cài được

![image](./image/Hyper-V%2023.png)

- Để khởi chạy, chọn chuột phải vào máy chủ cần chạy, chọn **Connect**

![image](./image/Hyper-V%2017.png)

- Chọn **Start** để khởi động máy ảo và bắt đầu sử dụng

![image](./image/Hyper-V%2018.png)

### Checkpoints
- Checkpoint là chức năng tương tự như Snapshot của VMware giúp lưu lại trạng thái của hệ thống tại một thời điểm xác định
- Để lưu một thời điểm của hệ thống, chọn chuột phải vào máy ảo và chọn **Checkpoint**

![image](./image/Hyper-V%2024.png)

- Để khôi phục lại một trạng thái của hệ thống, chuột phải vào thời điểm cần khôi phục, chọn **Apply**

![image](./image/Hyper-V%2025.png)