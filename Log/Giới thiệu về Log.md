# Giới thiệu về Log
- File log dùng để ghi lại toàn bộ quá trình hoạt động của hệ thống

### Vai trò của Log
- TroubleShooting trong quá trình cài đặt các service
- Tra cứu nhanh chóng thông tin của hệ thống
- Truy vết các sự kiện đã và đang xảy ra

### Phân loại file log trên CentOS
##### Message log: /var/log/messages
- Message log chứa dữ liệu log của hầu hết các thông báo hệ thống nói chung, bao gồm các thông báo trong quá trình khởi động hệ thống
- Ví dụ, khi khởi động lại dịch vụ mạng, sẽ có các file log về mạng xuất hiện

```sh
Nov  9 21:32:51 elk systemd: Stopping LSB: Bring up/down networking...
Nov  9 21:32:52 elk network: Shutting down interface ens160:  [  OK  ]
Nov  9 21:32:52 elk network: Shutting down interface ens192:  [  OK  ]
Nov  9 21:32:52 elk network: Shutting down loopback interface:  [  OK  ]
Nov  9 21:32:52 elk systemd: Starting LSB: Bring up/down networking...
Nov  9 21:32:53 elk network: Bringing up loopback interface:  [  OK  ]
Nov  9 21:32:53 elk kernel: vmxnet3 0000:03:00.0 ens160: intr type 3, mode 0, 3 vectors allocated
Nov  9 21:32:53 elk kernel: vmxnet3 0000:03:00.0 ens160: NIC Link is Up 10000 Mbps
Nov  9 21:32:57 elk network: Bringing up interface ens160:  [  OK  ]
Nov  9 21:32:57 elk kernel: vmxnet3 0000:0b:00.0 ens192: intr type 3, mode 0, 3 vectors allocated
Nov  9 21:32:57 elk kernel: vmxnet3 0000:0b:00.0 ens192: NIC Link is Up 10000 Mbps
Nov  9 21:33:01 elk network: Bringing up interface ens192:  [  OK  ]
Nov  9 21:33:01 elk systemd: Started LSB: Bring up/down networking.
```

- Luồng xử lý cửa file log trong việc restart networking
    - Đóng dịch vj  mạng
    > Nov  9 21:32:51 elk systemd: Stopping LSB: Bring up/down networking...

    - Các interface ở trạng thái down

    > Nov  9 21:32:52 elk network: Shutting down interface ens160:  [  OK  ]
    Nov  9 21:32:52 elk network: Shutting down interface ens192:  [  OK  ]
    Nov  9 21:32:52 elk network: Shutting down loopback interface:  [  OK  ]
    Nov  9 21:32:52 elk systemd: Stopped LSB: Bring up/down networking.

    - Dịch vụ network ở trạng thái bật lên
    > Nov  9 21:32:53 elk network: Bringing up loopback interface:  [  OK  ]

    - Các interface được bật lên
    > Nov  9 21:32:53 elk network: Bringing up loopback interface:  [  OK  ]
    Nov  9 21:32:53 elk kernel: vmxnet3 0000:03:00.0 ens160: intr type 3, mode 0, 3 vectors allocated
    Nov  9 21:32:53 elk kernel: vmxnet3 0000:03:00.0 ens160: NIC Link is Up 10000 Mbps
    Nov  9 21:32:57 elk network: Bringing up interface ens160:  [  OK  ]
    Nov  9 21:32:57 elk kernel: vmxnet3 0000:0b:00.0 ens192: intr type 3, mode 0, 3 vectors allocated
    Nov  9 21:32:57 elk kernel: vmxnet3 0000:0b:00.0 ens192: NIC Link is Up 10000 Mbps
    Nov  9 21:33:01 elk network: Bringing up interface ens192:  [  OK  ]

    - Dịch vụ network xấc thực được bật
    > Nov  9 21:33:01 elk systemd: Started LSB: Bring up/down networking.

##### Crontab log: /var/log/cron
- File log cron chứa dữ liệu log của cron deamon, bao gồm việc khởi động hoặc dừng cron cũng như cronjob thất bại
- Cron deamon là tiến trình giúp thực hiện một hành động trên hệ thống một cách tự động theo mốc thời gian cố định
- Để cấu hình các tác vụ cron, sử dụng lệnh ```crontab -e```
```sh
0 */2 * * * /backup/backup_database.sh
```

- Mỗi khi chạy, cronjob sẽ tạo ra một đoạn log, để xem log với tác vụ cụ thể, sử dụng lệnh ```cat /var/log/cron  | grep /backup/backup_database.sh```
- Nội dung file log
> Jan 24 00:00:01 controller1 CROND[34033]: (root) CMD (/backup/backup_database.sh)
Jan 24 02:00:01 controller1 CROND[24735]: (root) CMD (/backup/backup_database.sh)
Jan 24 04:00:01 controller1 CROND[14661]: (root) CMD (/backup/backup_database.sh)
Jan 24 06:00:01 controller1 CROND[3334]: (root) CMD (/backup/backup_database.sh)
Jan 24 08:00:01 controller1 CROND[57850]: (root) CMD (/backup/backup_database.sh)
Jan 24 10:00:01 controller1 CROND[46964]: (root) CMD (/backup/backup_database.sh)
Jan 24 12:00:01 controller1 CROND[37449]: (root) CMD (/backup/backup_database.sh)
Jan 24 14:00:01 controller1 CROND[28280]: (root) CMD (/backup/backup_database.sh)
Jan 24 16:00:01 controller1 CROND[19629]: (root) CMD (/backup/backup_database.sh)
Jan 24 18:00:01 controller1 CROND[10219]: (root) CMD (/backup/backup_database.sh)
Jan 24 20:00:01 controller1 CROND[723]: (root) CMD (/backup/backup_database.sh)
Jan 24 22:00:01 controller1 CROND[57462]: (root) CMD (/backup/backup_database.sh)
Jan 25 00:00:01 controller1 CROND[48920]: (root) CMD (/backup/backup_database.sh)

##### Log login/logout: /var/log/wtmp
- File log này chứa tất cả thông tin lịch sử về các lần đăng nhập, đăng xuất
- Để truy xuất log, sử dụng lệnh
```sh
utmpdump /var/log/wtmp | less
```

- Nội dung của file log
> Utmp dump of /var/log/wtmp
[8] [20302] [    ] [        ] [pts/0       ] [                    ] [0.0.0.0        ] [Sat Nov 10 20:21:59 2018 +07]
[7] [20500] [ts/0] [root    ] [pts/0       ] [27.72.59.xxx        ] [27.72.59.xxx   ] [Sat Nov 10 20:22:14 2018 +07]
[8] [20441] [    ] [        ] [pts/1       ] [                    ] [0.0.0.0        ] [Sat Nov 10 20:22:20 2018 +07]

- Khi có người dùng logout khởi hệ thống
> [8] [20302] [    ] [        ] [pts/0       ] [                    ] [0.0.0.0        ] [Sat Nov 10 20:21:59 2018 +07]

- Mỗi khi có người login vào hệ thống
> [7] [20500] [ts/0] [root    ] [pts/0       ] [27.72.59.xxx        ] [27.72.59.xxx   ] [Sat Nov 10 20:22:14 2018 +07]

##### Log phần cứng: /var/log/dmesg
- File log này chứa thông tin bộ đệm kernel ring. Khi hệ thống khởi động, file log sẽ chứa thông tin về các thiết bị phần cứng mà kernel phát hiện được. Các message này có sẵn trong kernel ring butter và bất cứ khi nào có message mới xuất hiện, message sẽ bị ghi đè
- Để truy cập file log, sử dụng lệnh ```dmesg``` hoặc
```sh
tail -n 10 /var/log/dmesg
```

để lấy 10 dòng cuối cùng cua file log
> [    6.542930] systemd[1]: Inserted module 'ip_tables'
[    3.358422]  vda: vda1
[    7.014517] EXT4-fs (vda1): re-mounted. Opts: (null)
[    7.107034] systemd-journald[1355]: Received request to flush runtime journal from PID 1
[    2.449704] systemd[1]: Starting Journal Service...
[    2.455997] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    2.465960] systemd[1]: Starting Setup Virtual Console...
[    2.472855] systemd[1]: Starting Apply Kernel Variables...
[    7.583101] piix4_smbus 0000:00:01.3: SMBus Host Controller at 0x700, revision 0
[    7.773026] input: PC Speaker as /devices/platform/pcspkr/input/input5

##### Log SSH: /var/log/secure
- File log chứa các nội dung về SSH tới hệ thống
- Nội dung file log với mỗi trường hợp
    - Login SSH thành công
    > Jan 18 15:39:30 web sshd[14838]: Accepted password for duydm from 27.72.59.xxx port 49572 ssh2
    Jan 18 15:39:30 web sshd: Started Session 3057 of user duydm

    - Login SSH thất bại
    > Nov 10 20:54:32 elk sshd[26205]: Failed password for root from 218.92.1.148 port 21450 ssh2
    Nov 10 20:54:32 elk sshd[26205]: Received disconnect from 218.92.1.148 port 21450:11:  [preauth]
    Nov 10 20:54:32 elk sshd[26205]: Disconnected from 218.92.1.148 port 21450 [preauth]

    - Logout SSH
    > Nov 10 21:06:46 elk sshd[28506]: Received disconnect from 27.72.59.xxx port 56671:11: disconnected by user
    Nov 10 21:06:46 elk sshd[28506]: Disconnected from 27.72.59.xxx port 56671
    Nov 10 21:06:46 elk sshd[28506]: pam_unix(sshd:session): session closed for user root
    Nov 10 21:06:47 elk sshd[28511]: Connection closed by 27.72.59.xxx port 56673 [preauth]

### Giới thiệu về Syslog trong Linux
- Syslog là một giao thức dùng để xử lý các file log Linux. Các file log có thể được lưu tại chính máy chủ Linux đó hoặc có thể di chuyển hoặc lưu tại một máy khác
- Một vài đặc điểm của Syslog
    - Syslog có thể gửi qua UDP hoặc TCP
    - Các dữ liệu log được gửi dạng cleartext
    - Syslog mặc định dùng port 514