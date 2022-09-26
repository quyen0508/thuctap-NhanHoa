# Cài đặt Hyper-V trên Windows Server 2019
- Tại **Server Manager**, chọn **Add roles and features**

![image](./image/Hyper-V%201.png)

- Tại **Server Roles**, chọn **Hyper-V**

![image](./image/Hyper-V%202.png)

- Chọn **Add Features** để thêm các tính năng được yêu cầu khi sử dụng Hyper-V

![image](./image/Hyper-V%203.png)

- Tại mục cài đặt của Hyper-V, với **Virtual Switches**, chọn card mạng dùng để máy ảo kết nối tới các máy tính khác cũng như Internet

![image](./image/Hyper-V%204.png)

- **Migration** cho phép cấu hình gửi và nhận các bản migration của các máy ảo trên server này, mặc định có thể bỏ qua

![image](./image/Hyper-V%205.png)

- **Default Stores** cấu hình vị trí mặc định cho các file chạy máy ảo và file cấu hình máy ảo

![image](./image/Hyper-V%206.png)

- Tại **Confirmation**, chọn **Install** để xác nhận thay đổi và cài đặt

![image](./image/Hyper-V%207.png)

- Khởi động lại để cài đặt hoàn tất