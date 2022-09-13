# Cài đặt Zimbra
- Cập nhật và cài đặt repo EPEL

```sh
yum update -y
yum install -y epel-release
```

- Cài đặt và cấu hình đồng bộ thời gian

```sh
yum install -y chronyd
systemctl enable chronyd
system start chronyd
ln -f -s /usr/share/zoneinfo/Asia/Ho_Chi_Minh /etc/localtime
```

- Tắt firewall và các dịch vụ mail khác nếu đang bật

```sh
systemctl stop sendmail
systemctl disable sendmail
systemctl stop httpd
systemctl disable httpd
systemctl stop firewalld
systemctl disable firewalld
systemctl stop iptables
systemctl disable iptables
systemctl stop ip6tables
systemctl disable ip6tables
```

- Đổi tên hostname và thêm hostname vào file hosts

```sh
hostnamectl set-hostname mail.quyennx.xyz
nano /etc/hosts
```

và thêm ```103.159.51.14 mail.quyennx.xyz``` vào cuối file host

- Cài đặt các package cần thiết

```sh
yum -y install unzip net-tools sysstat openssh-clients perl-core libaio nmap-ncat libstdc++.so.6 nano wget
```

- Tải file cài đặt Zimbra
```sh
wget -c https://files.zimbra.com/downloads/8.8.15_GA/zcs-8.8.15_GA_3869.RHEL7_64.20190918004220.tgz
```

- Giải nén và tiến hành cài đặt
```sh
tar -xzvf zcs-8.8.15_GA_3869.RHEL7_64.20190918004220.tgz
cd zcs-8.8.15_GA_3869.RHEL7_64.20190918004220
./install.sh
```

- Cài đặt các tuỳ chọn
```sh
Do you agree with the terms of the software license agreement? [N] Y

Use Zimbra's package repository [Y] Y

Select the packages to install

Install zimbra-ldap [Y] Y

Install zimbra-logger [Y] Y

Install zimbra-mta [Y] Y

Install zimbra-dnscache [Y] N

Install zimbra-snmp [Y] Y

Install zimbra-store [Y] Y

Install zimbra-apache [Y] Y

Install zimbra-spell [Y] Y

Install zimbra-memcached [Y] Y

Install zimbra-proxy [Y] Y

Install zimbra-drive [Y] Y

Install zimbra-imapd (BETA - for evaluation only) [N] N

Install zimbra-chat [Y] Y

The system will be modified.  Continue? [N] Y

Change domain name? [Yes] yes

Create domain: [mail.quyennx.xyz] quyennx.xyz
```

- Thiết lập mật khẩu cho tài khoản admin
    - Tại menu chính, chọn **6**

    ![image](./image/Zimbra%201.png)

    - Chọn **4** để đặt mật khẩu

    ![image](./image/Zimbra%202.png)

    - Sau khi đặt mật khẩu xong, nhấn **r** rồi **a** để quay lại menu chính và áp dụng cài đặt

- Tiếp tục thiết lập các tuỳ chọn
```sh
Save configuration data to a file? [Yes] yes

Save config in file: [/opt/zimbra/config.25752]

The system will be modified - continue? [No] yes
```

- Sau khi cài đặt xong, truy cập vào tài khoản ```zimbra``` để cấu hình memcached chỉ lắng nghe địa chỉ 127.0.0.1 để tránh khai thác Memcached Exploit, sau đó khởi động lại memcached

```sh
su zimbra
/opt/zimbra/bin/zmprov ms `zmhostname` zimbraMemcachedBindAddress 127.0.0.1
/opt/zimbra/bin/zmprov ms `zmhostname` zimbraMemcachedClientServerList 127.0.0.1
zmmemcachedctl restart
```

- Truy cập địa chỉ https://mail.quyennx.xyz:7071 hoặc https://103.159.51.14:7071 để đăng nhập trang quản trị

![image](./image/Zimbra%203.png)

![image](./image/Zimbra%204.png)