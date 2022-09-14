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

- Cài đặt và chạy Certbot

```sh
yum install -y certbot
certbot certonly --standalone
```

- Cấu hình tuỳ chọn

```sh
Enter email address (used for urgent renewal and security notices)
 (Enter 'c' to cancel): quyen05082000@gmail.com

You must agree in order to register with the ACME server. Do you agree?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: y

Would you be willing, once your first certificate is successfully issued, to
share your email address with the Electronic Frontier Foundation, a founding
partner of the Let's Encrypt project and the non-profit organization that
develops Certbot? We'd like to send you email about our work encrypting the web,
EFF news, campaigns, and ways to support digital freedom.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: n

Please enter in your domain name(s) (comma and/or space separated)  (Enter 'c'
to cancel): mail.quyennx.xyz
```

- Chứng chỉ được cấp thành công

![image](./image/Zimbra%208.png)

- Tạo thư mục ```letsencrypt``` tại đường dẫn /opt/zimbra/ssl/
```sh
mkdir /opt/zimbra/ssl/letsencrypt
```

- Sao chép các file chứng chỉ vào thư mục vừa tạo
```sh
cp /etc/letsencrypt/live/mail.quyennx.xyz/* /opt/zimbra/ssl/letsencrypt/
```

- Thêm chứng chỉ IdenTrust root Certificate vào cuối file ```chain.pem``` để tạo chứng chỉ một chứng chỉ Intermediate CA plus Root CA với nội dung được lấy tại đường dẫn

https://letsencrypt.org/certs/isrgrootx1.pem.txt

```sh
-----BEGIN CERTIFICATE-----
MIIFazCCA1OgAwIBAgIRAIIQz7DSQONZRGPgu2OCiwAwDQYJKoZIhvcNAQELBQAw
TzELMAkGA1UEBhMCVVMxKTAnBgNVBAoTIEludGVybmV0IFNlY3VyaXR5IFJlc2Vh
cmNoIEdyb3VwMRUwEwYDVQQDEwxJU1JHIFJvb3QgWDEwHhcNMTUwNjA0MTEwNDM4
WhcNMzUwNjA0MTEwNDM4WjBPMQswCQYDVQQGEwJVUzEpMCcGA1UEChMgSW50ZXJu
ZXQgU2VjdXJpdHkgUmVzZWFyY2ggR3JvdXAxFTATBgNVBAMTDElTUkcgUm9vdCBY
MTCCAiIwDQYJKoZIhvcNAQEBBQADggIPADCCAgoCggIBAK3oJHP0FDfzm54rVygc
h77ct984kIxuPOZXoHj3dcKi/vVqbvYATyjb3miGbESTtrFj/RQSa78f0uoxmyF+
0TM8ukj13Xnfs7j/EvEhmkvBioZxaUpmZmyPfjxwv60pIgbz5MDmgK7iS4+3mX6U
A5/TR5d8mUgjU+g4rk8Kb4Mu0UlXjIB0ttov0DiNewNwIRt18jA8+o+u3dpjq+sW
T8KOEUt+zwvo/7V3LvSye0rgTBIlDHCNAymg4VMk7BPZ7hm/ELNKjD+Jo2FR3qyH
B5T0Y3HsLuJvW5iB4YlcNHlsdu87kGJ55tukmi8mxdAQ4Q7e2RCOFvu396j3x+UC
B5iPNgiV5+I3lg02dZ77DnKxHZu8A/lJBdiB3QW0KtZB6awBdpUKD9jf1b0SHzUv
KBds0pjBqAlkd25HN7rOrFleaJ1/ctaJxQZBKT5ZPt0m9STJEadao0xAH0ahmbWn
OlFuhjuefXKnEgV4We0+UXgVCwOPjdAvBbI+e0ocS3MFEvzG6uBQE3xDk3SzynTn
jh8BCNAw1FtxNrQHusEwMFxIt4I7mKZ9YIqioymCzLq9gwQbooMDQaHWBfEbwrbw
qHyGO0aoSCqI3Haadr8faqU9GY/rOPNk3sgrDQoo//fb4hVC1CLQJ13hef4Y53CI
rU7m2Ys6xt0nUW7/vGT1M0NPAgMBAAGjQjBAMA4GA1UdDwEB/wQEAwIBBjAPBgNV
HRMBAf8EBTADAQH/MB0GA1UdDgQWBBR5tFnme7bl5AFzgAiIyBpY9umbbjANBgkq
hkiG9w0BAQsFAAOCAgEAVR9YqbyyqFDQDLHYGmkgJykIrGF1XIpu+ILlaS/V9lZL
ubhzEFnTIZd+50xx+7LSYK05qAvqFyFWhfFQDlnrzuBZ6brJFe+GnY+EgPbk6ZGQ
3BebYhtF8GaV0nxvwuo77x/Py9auJ/GpsMiu/X1+mvoiBOv/2X/qkSsisRcOj/KK
NFtY2PwByVS5uCbMiogziUwthDyC3+6WVwW6LLv3xLfHTjuCvjHIInNzktHCgKQ5
ORAzI4JMPJ+GslWYHb4phowim57iaztXOoJwTdwJx4nLCgdNbOhdjsnvzqvHu7Ur
TkXWStAmzOVyyghqpZXjFaH3pO3JLF+l+/+sKAIuvtd7u+Nxe5AW0wdeRlN8NwdC
jNPElpzVmbUq4JUagEiuTDkHzsxHpFKVK7q4+63SM1N95R1NbdWhscdCb+ZAJzVc
oyi3B43njTOQ5yOf+1CceWxG1bQVs5ZufpsMljq4Ui0/1lvh+wjChP4kqKOJ2qxq
4RgqsahDYVvTH9w7jXbyLeiNdd8XM2w9U/t7y0Ff/9yi0GE44Za4rF2LN9d11TPA
mRGunUHBcnWEvgJBQl9nJEiU0Zsnvgc/ubhPgXRR4Xq37Z0j4r7g1SgEEzwxA57d
emyPxgcYxn/eR44/KJ4EBs+lVDR3veyJm+kXQ99b21/+jh5Xos1AnX5iItreGCc=
-----END CERTIFICATE-----
```

- Cấp đúng quyền cho thư mục trên
```sh
chown -R zimbra:zimbra /opt/zimbra/ssl/letsencrypt/
```

- Kiểm chứng cho chứng chỉ
```sh
su - zimbra -c '/opt/zimbra/bin/zmcertmgr verifycrt comm /opt/zimbra/ssl/letsencrypt/privkey.pem /opt/zimbra/ssl/letsencrypt/cert.pem /opt/zimbra/ssl/letsencrypt/chain.pem'
```

- Nếu kiểm chứng chứng chỉ báo lỗi, xoá đoạn chứng chỉ thứ 2 của file ```chain.pem```

- Tạo backup cho thư mục SSL của Zimbra
```sh
cp -a /opt/zimbra/ssl/zimbra /opt/zimbra/ssl/zimbra.$(date "+%Y.%m.%d-%H.%M")
```

- Thay thế khoá riêng SSL của Zimbra và cấp quyền cho file
```sh
cp /opt/zimbra/ssl/letsencrypt/privkey.pem /opt/zimbra/ssl/zimbra/commercial/commercial.key
chown zimbra:zimbra /opt/zimbra/ssl/zimbra/commercial/commercial.key
```

- Deploy SSL
```sh
su - zimbra -c '/opt/zimbra/bin/zmcertmgr deploycrt comm /opt/zimbra/ssl/letsencrypt/cert.pem /opt/zimbra/ssl/letsencrypt/chain.pem'
```

- Khởi động lại Zimbra
```sh
su - zimbra -c '/opt/zimbra/bin/zmcontrol restart'
```

- Truy cập trang web của Zimbra để kiểm tra

![image](./image/Zimbra%209.png)

### Thay đổi logo của Zimbra server
- Phiên bản Zimbra Network Edition có thể thay đổi logo thông qua giao diện admin, nhưng đối với phiên bản Open Source thì chỉ có thể đổi logo tại server hosting

- Tạo thư mục chứa logo
```sh
mkdir /opt/zimbra/jetty/webapps/zimbra/logos/
```

- Đưa logo vào thư mục mới tạo và cấp quyền sở hữu zimbra
```sh
cp logo_nhanhoa.png /opt/zimbra/jetty/webapps/zimbra/logos/
chown zimbra:zimbra /opt/zimbra/jetty/webapps/zimbra/logos/logo_nhanhoa.png
```

- Cài đặt logo cho đường dẫn, logo trang đăng nhập và trang chính, sau đó khởi động lại dịch vụ zmmailboxdctl
```sh
su - zimbra -c 'zmprov md quyennx.xyz zimbraSkinLogoURL /logos/logo_nhanhoa.png'
su - zimbra -c 'zmprov md quyennx.xyz zimbraSkinLogoLoginBanner /logos/logo_nhanhoa.png'
su - zimbra -c 'zmprov md quyennx.xyz zimbraSkinLogoAppBanner /logos/logo_nhanhoa.png'
su - zimbra -c 'zmmailboxdctl restart'
```

- Kiểm tra trên trang web

![image](./image/Zimbra%2010.png)

![image](./image/Zimbra%2011.png)

### Thay đổi tiêu đề của Zimbra
- Thay đổi tiêu đề của Zimbra giúp tuỳ chỉnh phù hợp với những đơn vị, tổ chức riêng

- Để thay đổi tiêu đề của trang đăng nhập và trang chính của webapp, chỉnh sửa file ```ZmMsg.properties``` tại đường dẫn /opt/zimbra/jetty/webapps/zimbra/WEB-INF/classes/messages/

```sh
nano /opt/zimbra/jetty/webapps/zimbra/WEB-INF/classes/messages/ZmMsg.properties
```
- Để sửa tiêu đề trang đăng nhập, sửa giá trị của trường ```zimbraLoginTitle```
- Để sửa tiêu đề của mailbox, sửa giá trị của trường ```zimbraTitle```
- Để sửa tiêu đề của trang quản trị, truy cập file ZabMsg.properties tại đường dẫn /opt/zimbra/jetty_base/webapps/zimbraAdmin/WEB-INF/classes/messages/ và sửa giá trị của trường ```zimbraAdminTitle```

- Sau khi thay đổi thông tin xong, cần phải khởi động lại ZImbra server
```sh
su - zimbra -c 'zmcontrol restart'
```

- Kết quả

![image](./image/Zimbra%2012.png)

![image](./image/Zimbra%2013.png)

![image](./image/Zimbra%2014.png)

### Quản lý domain
##### Tạo domain
- Sử dụng lệnh
```sh
su - zimbra -c 'zmprov createDomain newquyennx.xyz'
```

##### Sửa domain
- Sử dụng lệnh
```sh
su - zimbra -c 'zmprov -l renameDomain newquyennx.xyz renamequyennx.xyz'
```

##### Xoá domain
- Sử dụng lệnh
```sh
su - zimbra -c 'zmprov dd renamequyennx.xyz'
```

- Lưu ý: cần phải xoá hết các tài khoản thuộc domain trước khi xoá domain đó

### Đổi mật khẩu tài khoản admin
- Liệt kê những tài khoản có quyền admin
```sh
su - zimbra -c 'zmprov gaaa'
```

- Thay đổi mật khẩu tài khoản tương ứng
```sh
su - zimbra -c 'zmprov sp admin@quyennx.xyz mật-khẩu'
```

### Thiết lập chính sách cho mật khẩu đối vối các tài khoản trong Zimbra
- Khi mới cài đặt, chính sách mật khẩu còn khá lỏng lẻo, vì vậy, cần phải thiết lập lại chính sách để tăng tính bảo mật

- Tại giao diện chính của trang quản trị, chọn tab **Configure**

- Tại **Class of Service**, chọn **default** -> **Advanced**

- Chỉnh sửa thiết lập tại mục **Password**
    - **Prevent user from chaging password**: Ngăn người dùng thay đổi mật khẩu
    - **Minimum password length**: Độ dài mật khẩu tối thiểu
    - **Maximum password length**: Độ dài mật khẩu tối đa
    - **Minimum upper case characters**: Số ký tự viết hoa tối thiểu
    - **Minimum lower case characters**: Số ký tứ viết thường tối thiểu
    - **Minimum punctuation symbols**: Số ký tự chấm câu tối thiểu
    - **Minimum numeric characters**: Số ký tự số tối thiểu
    - **Minimum numeric characters or punctuation symbols**: Số ký tự số hoặc ký tự dấu chấm câu tối thiểu
    - **Minimum password age (days)**: Thời hạn tối thiểu của mật khẩu (tính theo ngày)
    - **Maximum password age (days)**: Thời hạn tối đa của mật khẩu (tính theo ngày)
    - **Minimum number of unique passwords history**: Số lượng tối thiểu của lịch sử mật khẩu duy nhất

![image](./image/Zimbra%2015.png)

### Quản lý tài khoản
- Để truy cập trang quản lý tài khoản, tại trang chính của tài khoản quản trị, chọn **Manage**, sau đó chọn **Accounts** (mặc định đang ở tab này)

##### Thêm tài khoản
- Chọn nút cài đặt (ở góc trên bên phải, có hình bánh răng, ngay cạnh nút **Help**), chọn **New**

![image](./image/Zimbra%2016.png)

- Thiết lập thông tin tài khoản cho user mới, tối thiểu là tên tài khoản và mật khẩu

![image](./image/Zimbra%2017.png)

![image](./image/Zimbra%2018.png)

##### Chỉnh sửa tài khoản
- Tại trang quản lý tài khoản, chọn chuột phải với tài khoản cần chỉnh sửa và chọn **Edit**

![image](./image/Zimbra%2019.png)

- Chỉnh sửa các thiết lập và chọn **Save** để lưu sửa đổi

![image](./image/Zimbra%2020.png)

##### Xoá tài khoản
- Tại trang quản lý tài khoản, chuột phải tài khoản cần xoá và chọn **Delete**

![image](./image/Zimbra%2021.png)

- Xác nhận xoá

![image](./image/Zimbra%2022.png)

### Blacklsit và Whitelist
- Blacklist và Whitelist giúp chặn họặc cho phép thư từ địa chỉ email hoặc tên miền đã được thiết lập trước đó

- Để thiết lập, truy cập trang quản lý tài khoản của người dùng, chọn tab **Preferences**, chọn mục **Mail** và tìm tới mục **Spam Mail Options**

![image](./image/Zimbra%2023.png)

- Nhập các tên miền muốn chặn hoặc cho phép gửi thư tới server này, chọn **Add** để thêm vào danh sách

### Tim ID mailbox account trong Zimbra
- Với mỗi account có một ID định danh được sinh ra ngẫu nhiên, việc biết ID của tài khoản sẽ thuận lợi hơn trong backup/restore

- Lấy ID của user
```sh
su - zimbra -c 'zmprov getMailboxInfo admin@quyennx.xyz'
```

![image](./image/Zimbra%2024.png)

- Truy cập vào mailbox theo đường dẫn /opt/zimbra/store/0/, tại đây chứa nội dung thư tổ chức theo thư mục với tên là theo ID người dùng

![image](./image/Zimbra%2025.png)

### Chặn email trong Zimbra
##### Chặn thư từ một địa chỉ IP/tên miền gửi tới Zimbra
- Tạo danh sách IP block
```sh
nano /opt/zimbra/conf/postfix_reject_sender
```

- Thêm vào IP/tên miền cần block
```sh
quyen123@quyennx.xyz REJECT     # Đối với chặn một địa chỉ email cụ thể
quyennx.xyz REJECT              # Đối với chặn một tên miền cụ thể
```

- Chậy lệnh để cập nhật danh sách chặn và khởi động lại mta
```sh
su - zimbra -c 'zmprov ms mail.quyennx.xyz +zimbraMtaSmtpdSenderRestrictions "check_sender_access lmdb:/opt/zimbra/conf/postfix_reject_sender"'
su - zimbra -c '/opt/zimbra/common/sbin/postmap /opt/zimbra/conf/postfix_reject_sender'
su - zimbra -c 'zmmtactl restart'
```

- Kiểm tra bằng cách sử dụng email bị chặn để gửi mail sẽ nhận được thông báo không gửi được mail

![image](./image/Zimbra%2026.png)

### Thiết lập forward mail trong Zimbra
- Truy cập vào trang quản lý tài khoản cần thiết lập, chọn **Preference** -> **Mail** -> **Receiving Messages**, sau đó nhập địa chỉ email muốn được forward thư đến tại mục **Forward a copy to:**

![image](./image/Zimbra%2027.png)

### Thiết lập giới hạn (quota) cho tài khoản trong Zimbra
- Mặc định Zimbra đã tự động phân chia quota cho mỗi tài khoản theo mặc định, thực tế thì mỗi tài khoản sẽ có như cầu dùng khác nhau, vì vậy việc thiết lập giới hạn thích hợp cho từng tài khoản là cần thiết

- Truy cập trang quản trị, chọn **Manage** -> **Accounts**, chuột phải vào tài khoản cần thiết lập và chọn **Edit**

![image](./image/Zimbra%2028.png)

- Truy cập tab **Advanced**, chỉnh sửa thông số tại mục **Quotas**
    - **Limit user-specified forwarding addresses field to (chars)**: Giới hạn địa chỉ chuyển tiếp theo người dùng trong phạm vi (ký tự)
    - **Maximum number of user-specified forwarding addresses**: Số lượng tối đa các địa chỉ chuyển tiếp theo người dùng
    - **Account quota (MB)**: Hạn mức tài khoản tính theo MB (không giới hạn nếu được đặt là 0)
    - **Maximum number of contacts allowed in folder**: Số lượng liên hệ tối đa cho phép trong thư mục
    - **Percentage threshold for quota warning messages (%)**: Ngưỡng theo phần trăm cho các thư cảnh báo hạn mức
    - **Minimum duration of time between quota warnings**: Khoảng thời gian tối thiểu giữa các lần cảnh báo hạn mức
    - **Quota warning message template**: Mẫu thư cảnh báo hạn mức

![image](./image/Zimbra%2029.png)