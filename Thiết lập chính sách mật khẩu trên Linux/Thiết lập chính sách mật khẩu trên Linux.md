# Thiết lập chính sách mật khẩu an toàn trên Linux
- Chính sách mật khẩu giúp bảo mật thông tin tốt hơn, tránh các trường hợp bị tấn công do đặt mật khẩu dễ đoán

- Các thiết lập về chính sách mật khẩu trên Linux được lưu tại file có đường dẫn ```/etc/login.defs```

### Thiết lập số ngày hết hạn của mật khẩu
- Thiết lập này giúp đặt ra thời gian giới hạn cho mật khẩu, khi mật khẩu hết hạn, người dùng phải thay đổi mật khẩu mới để tiếp tục sử dụng
```sh
PASS_MAX_DAYS   60              # (dòng 25)
```

> Thời gian hiệu lực tối đa của mật khẩu là 60 ngày

### Thiết lập thời gian tồn tại tối thiểu của mật khẩu
- Mật khẩu sẽ cần có thời gian chờ đợi trước khi có thể thay đổi lại mật khẩu
```sh
PASS_MIN_DAYS 2                 # (dòng 26)
```

> Thời gian hiệu lực tối thiểu của mật khẩu là 2 ngày

### Cảnh báo thời gian hết hạn tồn tại
- Thiết lập số ngày để thông báo sắp hết hạn mật khẩu

```sh
PASS_WARN_AGE 7                 # (dòng 28)
```

> Sẽ nhận được cảnh báo mật khẩu sắp hết thời gian tồn tại

### Giới hạn mật khẩu đã được đặt trước đó
- Người dùng sẽ không thể đặt được mật khâu đã đặt trước đó khi vượt quá số lần quy định
- Mở file cấu hình tại đường dẫn /etc/pam.d/system-auth và thêm ```remember=5``` tại dòng 17 để giới hạn 5 lần đặt mật khẩu đã thiết lập

![image](./image/Password%20policy%201.png)

### Thiết lập độ dài mật khẩu tối thiểu
- Thiết lập độ dài mật khẩu tối thiểu ngăn người dùng đặt mật khẩu ngắn hơn so với quy định làm tăng rủi ro bảo mật
- Thiết lập mật khẩu ít nhất 8 ký tự, sử dụng lệnh
```sh
authconfig --passminlen=8 --update
```

### Thiết lập độ phức tạp của mật khẩu theo lớp
- Gồm 4 lớp ký tự: uppercase letters (chữ in hoa), lowercase letter (in thường), numbers (chữ số) và special characters (ký tự đặc biệt)
- Độ phức tạp của mật khẩu sẽ dựa trên số các lớp tham gia trong mật khẩu
- Để thiết lập mật khẩu xuất hiện tối thiểu 3 trong 4 lớp trên, sử dụng lệnh
```sh
authconfig --passminclass=3 --update
```

### Thiết lập sô lần lặp ký tự liên tiếp
- Để thiết lập số lần lặp ký tự liên tiếp tối đa là 2, sử dụng lệnh
```sh
authconfig --passmaxrepeat=2 --update
```

### Thiết lập độ phức tạp mật khẩu với các lớp cụ thể
- Để thiết lập phải xuất hiện ký tự thường trong mật khẩu, sử dụng lệnh
```sh
authconfig --enablereqlower --update
```

- Để thiết lập phải xuất hiện ký tự in hoa trong mật khẩu, sử dụng lệnh
```sh
authconfig --enablerequpper --update
```

- Để thiết lập phải xuát hiện ký tự số trong mật khẩu, sử dụng lệnh
```sh
authconfig --enablereqdigit --update
```

- Để thiết lập phải xuất hiện các ký tự đặc biệt trong mật khẩu, sử dụng lệnh
```sh
authconfig --enablereqother --update
```

### Thiết lập độ dài monotonic
- Monotonic trong toán học là hàm số đơn điệu, là một chuỗi các số tăng hoặc giảm trong khoảng
- Ví dụ, khi thiết lập giới hạn là 5 thì chỉ có thể đặt mật khẩu bao gồm các chuỗi như ```12345``` hay ```abcde``` mà không thể đặt các chuỗi dài hơn được
- Để thiết lập, chỉnh sửa file cấu hình có đường dẫn ```/etc/security/pwquality.conf```, thêm vào cuối file cấu hình
```sh
maxsequence = 5
```