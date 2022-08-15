# Cài dặt SSL free bằng Certbot trên CentOS 7
### Cài đặt SSL với Apache
##### Cài đặt Certbot Let's Encrypt Client
- Sử dụng Certbot để cài đặt chứng chỉ với các bước đơn giản
- Cài đặt EPEL repository bằng lệnh

```sh
yum -y install epel=release
```

- Cài đặt certbot-nginx bằng lệnh

```sh
yum -y install certbot python2-certbot-apache mod_ssl

```

##### Cài đặt SSL Let's Encrypt
- Cài đặt SSL cho tên miền bằng lệnh
```sh
certbot --apache -d quyennx.xyz -d www.quyennx.xyz
```
Với ```-d [tên-miền]``` là mỗi tên miền được cấp chứng chỉ trong chứng chỉ này
- Nhập địa chỉ email khi được hỏi
- Xác nhận đăng ký với ACME server, chọn 'y')
- Xác nhận chia sẻ email với Electronic Frontier Foundation để cập nhật tin tức, chọn 'n'
- Cài đặt thành công, thông tin về chứng chỉ và khóa (fullchain.pem và privkey.pem) được lưu tại đường dẫn /etc/letsencrypt/live/quyennx.xyz/

##### Kiểm tra kết quả

##### Gia hạn tự động
- Do chứng chỉ Let's Encrypt có thời hạn 90 ngày nên cần phải gia hạn lại thường xuyên
- Để cấu hình gia hạn tự động sử dụng lệnh
```sh
00 6 * * * /usr/bin/certbot renew --quiet
```
Với lệnh này, vào mỗi 6:00AM sẽ chạy lệnh renew để kiểm tra liệu chứng chỉ đã hết hạn chưa, nếu hết thì sẽ gia hạn lại, việc này được diễn ra âm thầm

### Cài đặt SSL với nginx
Các bước đều tương tự như khi cài với Apache, chỉ khác lúc cài certbot sử dụng lệnh
```sh
yum -y install certbot-nginx
```