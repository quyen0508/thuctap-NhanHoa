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

##### Cấu hình của Syslog
- File cấu hình của Syslog trên CentOS có đường dẫn /etc/rsyslog.conf
- Ví dụ về file cấu hình và khai báo trên CentOS
```sh
# rsyslog configuration file

# For more information see /usr/share/doc/rsyslog-*/rsyslog_conf.html
# If you experience problems, see http://www.rsyslog.com/doc/troubleshoot.html

#### MODULES ####

# The imjournal module bellow is now used as a message source instead of imuxsock.
$ModLoad imuxsock # provides support for local system logging (e.g. via logger command)
$ModLoad imjournal # provides access to the systemd journal
#$ModLoad imklog # reads kernel messages (the same are read from journald)
#$ModLoad immark  # provides --MARK-- message capability

# Provides UDP syslog reception
#$ModLoad imudp
#$UDPServerRun 514

# Provides TCP syslog reception
#$ModLoad imtcp
#$InputTCPServerRun 514


#### GLOBAL DIRECTIVES ####

# Where to place auxiliary files
$WorkDirectory /var/lib/rsyslog

# Use default timestamp format
$ActionFileDefaultTemplate RSYSLOG_TraditionalFileFormat

# File syncing capability is disabled by default. This feature is usually not required,
# not useful and an extreme performance hit
#$ActionFileEnableSync on

# Include all config files in /etc/rsyslog.d/
$IncludeConfig /etc/rsyslog.d/*.conf

# Turn off message reception via local log socket;
# local messages are retrieved through imjournal now.
$OmitLocalLogging on

# File to store the position in the journal
$IMJournalStateFile imjournal.state


#### RULES ####

# Log all kernel messages to the console.
# Logging much else clutters up the screen.
#kern.*                                                 /dev/console

# Log anything (except mail) of level info or higher.
# Don't log private authentication messages!
*.info;mail.none;authpriv.none;cron.none                /var/log/messages

# The authpriv file has restricted access.
authpriv.*                                              /var/log/secure

# Log all the mail messages in one place.
mail.*                                                  -/var/log/maillog


# Log cron stuff
cron.*                                                  /var/log/cron

# Everybody gets emergency messages
*.emerg                                                 :omusrmsg:*

# Save news errors of level crit and higher in a special file.
uucp,news.crit                                          /var/log/spooler

# Save boot messages also to boot.log
local7.*                                                /var/log/boot.log


# ### begin forwarding rule ###
# The statement between the begin ... end define a SINGLE forwarding
# rule. They belong together, do NOT split them. If you create multiple
# forwarding rules, duplicate the whole block!
# Remote Logging (we use TCP for reliable delivery)
#
# An on-disk queue is created for this action. If the remote host is
# down, messages are spooled to disk and sent when it is up again.
#$ActionQueueFileName fwdRule1 # unique name prefix for spool files
#$ActionQueueMaxDiskSpace 1g   # 1gb space limit (use as much as possible)
#$ActionQueueSaveOnShutdown on # save messages to disk on shutdown
#$ActionQueueType LinkedList   # run asynchronously
#$ActionResumeRetryCount -1    # infinite retries if host is down
# remote host is: name/ip:port, e.g. 192.168.0.1:514, port optional
#*.* @@remote-host:514
# ### end of the forwarding rule ###
```

- Trong đó, các service cơ bản của hệ thống được lưu trữ tại Syslog, ví dụ như
> cron.*                                                  /var/log/cron

- Cấu hình như trên được chia làm 2 trường
    - Trường 1: Trường Selector
        - Trường Selector chỉ ra nguồn tạo ra log và mức cảnh báo của log đó
        - Có 2 thành phần và được tách nhau bởi dấu "."
    - Trường 2: Trường Action
        - Chỉ ra nơi lưu log của tiến trình
        - Có 2 loại là lưu file tại localhost và gửi đến IP của máy chủ log tập trung

##### Các nguồn tạo log (Facility Level)
| Numerical Code | Keyword | Facility Name |
| - | - | - |
| 0 | kern | Những log do kernel sinh ra |
| 1 | user | Log ghi lại cấp độ người dùng |
| 2 | mail | Log của hệ thống mail |
| 3 | deamon | Log của các tiến trình trên nền hệ thống |
| 4 | auth | Log từ quá trình đăng nhập hoặc xác thực hệ thống |
| 5 | syslog | Log từ chương trình syslogd |
| 6 | lpr | Log từ quá trình in |
| 7 | news | Thông tin tin tức từ hệ thống, liên quan đến giao thức Network News Protocol |
| 8 | uucp | Tập hợp các chương trình cấp thấp cho phép kết nối các máy tính Unix với nhau |
| 9 | cron | Tiện ích cho phép thực hiện các tác vụ theo định kỳ |
| 10 | authprix | Các thông báo liên quan đến truy cập và bảo mật |
| 11 | ftp | Log của FTP deamon |
| 12 | ntp | Hệ thống con NTP |
| 13 | security | Kiểm tra đăng nhập |
| 14 | console | Log cảnh báo hệ thống |
| 15 | solaris-cron | Log lịch trình |
| 16-23 | local0 to local7 | Log dự trữ cho sử dụng nội bộ |

##### Các mức độ cảnh báo của Syslog
- Mức độ cảnh báo được chia thành 8 mức từ 0 đến 7, với 0 là cấp độ cao nhất
- Bảng các mức độ nghiêm trọng của Syslog
| Value | Severity | Keyword |
| - | - | - |
| 0 | Emergency | ```emerg``` - Thông báo tình trạng khẩn cấp |
| 1 | Alert | ```alert``` - Hệ thống cần can thiệp ngay |
| 2 | Critical | ```crit``` - Tình trạng nguy kịch |
| 3 | Error | ```err``` - Thông báo lỗi đối với hệ thống |
| 4 | Warning | ```warning``` - Mức cảnh báo đối với hệ thống |
| 5 | Notice | ```notice``` - Chú ý đối với hệ thống |
| 6 | Information | ```info``` - Thông tin của hệ thống |
| 7 | Debug | ```debug``` - Quá trình kiểm tra hệ thống |

- Ví dụ với dịch vụ mail
    - Nếu chỉ muốn lưu các log với mức cảnh báo là ```info``` trở lên (từ mức 6 đến mức 0)
    > mail.info                     /var/log/mail

    - Nếu chỉ muốn lưu các log có mức là ```info```
    > mail.=info                    /var/log/mail

    - Nếu muốn lưu tất cả các mức của dịch vụ mail
    > mail.*                        /var/log/mail

    - Nếu muốn lưu lại tất cả các mức trừ mức ```info```
    > mail.!info                    /var/log/mail

### Tổng quan về Log tập trung

![image](https://camo.githubusercontent.com/91218fce169f3547691a0daf0781fd35aaacfc66/68747470733a2f2f696d6775722e636f6d2f44716366676e552e6a7067)

- Log tập trung được dùng khi
    - Có nhiều nguồn sinh log
        - Nằm trên nhiều máy chủ khác nhau
        - Nội dung log không đồng nhất
        - Định dạng log không đồng nhất
    - Đảm bảo tính toàn vẹn, bí mật và sẵn sàng của log
        - Nhiều các rootkit được thiết kế để xoá bỏ log
        - Do log mới được ghi đè lên log cũ, vì vậy, log cần phải được lưu trữ ở một nơi an toàn và phải có kênh truyền đủ để đảm bảo tính an toàn và sẵn sàng sử dụng để phân tích hệ thống

##### Ưu điểm
- Giúp quản trị viên có cái nhìn chi tiết và hệ thống, vì vậy cần có định hướng tốt hơn về hướng giải quyết
- Mọi hoạt động của hệ thống được ghi lại và lưu trữ ở một nơi an toàn (log server) để đảm bảo tính toàn vẹn, phục vụ cho quá trình phân tích điều tra các cuộc tấn công vào hệ thống
- Log tập trung kết hợp với các ứng dụng thu thập và phân tích log khác giúp cho việc phân tích log trở nên thuận tiện hơn, dô đó có thể giảm thiểu được nguồn nhân lực

##### Nhược điểm
- Có nguy cơ bị quá tải máy chủ Syslog: nếu máy chủ bị tấn công, có thể hàng ngàn log messages được gửi đến dẫn tới quá tải máy chủ log
- Khi có sự cố với máy chủ Syslog, máy khách sẽ không thể gửi các bản log tới server, vì vậy máy khách sẽ phải lưu trữ cục bộ tới khi máy chủ khả dụng trở lại, điều này để lâu có thể dẫn tới dung lượng đĩa của máy khách nhanh đầy

### Cấu hình Log tập trung trên CentOS
##### Cấu hình Rsyslog trên Server
- Chỉnh sửa file cấu hình Syslog có đường dẫn ```/etc/rsyslog.conf``` để cho phép nhận các bản ghi log từ các client gửi về
```sh
# Provides UDP syslog reception (dòng 14)
#$ModLoad imudp
#$UDPServerRun 514

# Provides TCP syslog reception (dòng 18)
$ModLoad imtcp
$InputTCPServerRun 514
```

- Ở đây có thể lựa chọn sử dụng UDP hoặc TCP để cho phép server nhận các bản tin log. Mặc định syslog sử dụng port 514 để gửi và nhận thông tin log

- Thiết lập cấu hình thư mục cho các bản log của cùng client, có 2 cách đặt tên
    - Thư mục log client trả về là ip-client
    ```sh
    $template RemoteServer, "/var/log/%fromhost-ip%/%SYSLOGFACILITY-TEXT%.log"
    *.* ?RemoteServer
    ```

    - Thư mục log client trả về là tên máy (hostname) của client
    ```sh
    $template RemoteServer, "/var/log/%HOSTNAME%/%SYSLOGFACILITY-TEXT%.log"
    *.* ?RemoteServer
    ```

- Mở port 514 nếu đang dùng tường lửa
```sh
firewall-cmd --permanent --add-port=514/udp
firewall-cmd --permanent --add-port=514/tcp
firewall-cmd --reload
```

- Khởi động lại Rsyslog server và kiểm tra xem có đang lắng nghe trên port 514 hay không
```sh
systemctl restart rsyslog
netstat -tna | grep 514
```

##### Cấu hình Rsyslog trên Client
- Client phải truyền đúng giao thức đã cấu hình ở Rsyslog Server
    - Đối với giao thức UDP: ```*.* @IPserver:514```
    - Đối với giao thức TCP: ```*.* @@IPserver:514```

- Thiết lập cấu hình tại file cấu hình của Rsyslog có đường dẫn ```/etc/rsyslog.conf```, cấu hình với giao thức tương ứng ở mục RULES (dòng 46)

- Khởi động lại Rsyslog để thiết lập có hiệu lực
```sh
systemctl restart rsyslog
```

##### Kiểm tra việc thiết lập cấu hình Rsyslog trên Server
- Sử dụng ```tcpdump``` để bắt các gói tin gửi về Server từ Client
```sh
tcpdump -nni ens33 port 514
```

![image](./image/Rsyslog%201.png)

- Kiểm tra trong thư mục ```/var/log/``` xuất hiện thư mục có tên là địa chỉ IP của client (192.168.14.137)

![image](./image/Rsyslog%203.png)

- Kiểm tra trong thư mục của client xuất hiện các file log (cron, deamon, user,...)

![image](./image/Rsyslog%202.png)

### Cấu hình Log Apache gửi về Rsyslog Server
- Dịch vụ ```httpd``` (Apache) có các file log nằm trong thư mục ```/var/log/httpd/``` bao gồm ```access_log``` và ```error_log```

- Đầu tiên, tạo file cấu hình ```apache.conf``` tại thư mục ```/etc/rsyslog.d/``` trên máy client
```sh
nano /etc/rsyslog.d/apache.conf
```

- Nội dung file cấu hình
```sh
$ModLoad imfile                                 # Dòng này chỉ thêm một lần

# Apache error file:
$InputFileName /var/log/httpd/error_log         # Đường dẫn file log muốn đẩy
$InputFileTag errorlog                          # Tên file
$InputFileSeverity info                         # Các log từ mức info trở lên được ghi lại
$InputFileFacility local3                       # Facility log
$InputRunFileMonitor

# Apache access file:
$InputFileName /var/log/httpd/access_log
$InputFileTag accesslog
$InputFileSeverity info
$InputFileFacility local4
$InputRunFileMonitor

$InputFilePollInterval 10                       # Cứ sau 10 giây lại gửi tin nhắn
```

- Khởi động lại ```rsyslog``` trên client
```sh
systemctl restart rsyslog
```

- Kiểm tra trên server bằng tcpdump thấy có bản ghi log ```local3.info``` và ```local4.info``` được gửi từ client

![image](./image/Rsyslog%205.png)

- Kiểm tra tại thư mục của client trên server, thấy xuất hiện 2 file ```local3.log``` và ```local4.log```

![image](./image/Rsyslog%204.png)

- ```local3.log``` tương ứng với ```error_log``` và ```local4.log``` tương ứng với ```access_log```