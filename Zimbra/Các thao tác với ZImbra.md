# Các thao tác với Zimbra
### Tạo bản ghi DKIM để tránh bị đánh dấu là thư spam

```sh
su zimbra
/opt/zimbra/libexec/zmdkimkeyutil -a -d quyennx.xyz
```

![image](./image/Zimbra%205.png)

- Truy cập trang quản lý DNS để thêm bản ghi DKIM

![image](./image/Zimbra%206.png)

- Kiểm tra thử bằng cách gửi 1 mail từ Zimbra server tới gmail

![image](./image/Zimbra%207.png)

### Cài đặt SSL Let's Encrypt cho Zimbra server
- Tắt Zimbra server

```sh
su zimbra -c '/opt/zimbra/bin/zmcontrol stop'
```

- Cài đặt git

```sh
yum install -y git
```

- Tải xuống Certbot

```sh
git clone https://github.com/certbot/certbot
./certbot/letsencrypt-auto-source/letsencrypt-auto certonly --standalone
```

- Cấu hình tuỳ chọn

```sh
