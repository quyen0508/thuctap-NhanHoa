# Dịch vụ DNS
### Giới thiệu chung
DNS viết tắt của Domain Name  System là hệ thống phân giải tên miền được phát minh vào năm 1984 nhằm mục đích chính là phân giải tên miền thành địa chỉ IP
### Phân loại máy chủ
- Primary server DNS: là server DNS chính
- Secondary server DNS: là server DNS phụ, được cập nhật thông tin định kỳ qua server chính
- Cả hai đều có chức năng tương đương nhau

### Cấu trúc của một tên miền
- Gồm 4 phần:
    - Root Domain
    - Top-Level Domain
    - Second-Level Domain
    - Subdomain
- Ví dụ về tên miền ```ktht.nuce.edu.vn```:
    - Root Domain: là phần sau phần ```vn```, bao gồm một đấu chấm ".", thông thường khi sử dụng trình duyệt thì thành phần này thường được bỏ qua
    - Top-Level Domain: ```vn```
    - Second-Level Domain: ```edu```
    - Subdomain: ```nuce```
    - Host: ```ktht```

### Các bản ghi của DNS
##### Bản ghi SOA
Dùng để chỉ ra máy chủ Name Server là nơi cung cấp thông tin tin cậy từ dữ liệu có trong Zone
Cú pháp:
```[tiên-miền] IN SOA [tên-server-dns] [địa-chỉ-email] (serial number;refresh number;retry number;expire number;TTL number)```
##### Bản ghi NS
Chức năng: chỉ ra các máy chủ DNS quản lý tên miền của hệ thống
Cú pháp: ```[tên miền] IN NS [tên-server-dns]```
Ví dụ:
- ```ktht.nuce.edu.vn IN NS server1.ktht.nuce.edu.vn```
- ```ktht.nuce.edu.vn IN NS server2.ktht.nuce.edu.vn```

##### Bản ghi A
Chức năng: dùng để ánh xạ tên máy thành địa chỉ IP
Cú pháp: ```[tên-máy-tính] IN A [địa-chỉ-IP]```
Ví dụ:
- ```server1 IN A 10.0.0.1```
- ```server2 IN A 10.0.0.2```

##### Bản ghi CNAME
Chức năng: dùng để tạo tên gọi khác (bí danh) khác cho một máy chủ
Cú pháp: ```[tên-bí-danh] IN CNAME [địa-chỉ-IP]```
Ví dụ:
```www IN CNAME 10.0.0.1```

##### Bản ghi PTR
Chức năng: dùng để ánh xạ đại chỉ IP thành tên máy
Cú pháp: ```[địa-chỉ-IP] IN PTR [tên-máy-tính]```
Ví dụ:
```10.0.0.1 IN PTR server1.ktht.nuce.edu.vn```

##### Bản ghi MX
Chức năng: dùng trong việc chuyển mail
Cú pháp: ```[tên-miền] IN MX [thứ-tự-ưu-tiên] [tên-máy-chủ-mail]
Ví dụ:
- ```ktht.nuce.edu.vn IN MX 1 server1.ktht.nuce.edu.vn```
- ```ktht.nuce.edu.vn IN MX 2 server2.ktht.edu.vn```

### DNS Zone
##### Zone thuận
Chức năng: dùng để phân giải tên miền thành địa chỉ IP
Cú pháp:
```zone "[tên-miền]" IN {```
    ```type [tên-kiểu];```
    ```file "[tên-file-cấu-hình]";```
```}```
Ví dụ:
```zone "ktht.nuce.edu.vn" IN {```
    ```type master;```
    ```file "ktht.db";```
```}```
##### Zone nghịch
Chức năng: dùng để phân giải địa chỉ IP thành tên miền
Cú pháp:
```zone "[địa-chỉ-lớp-mạng.in-addr.arpa]" IN {```
    ```type [tên-kiểu];```
    ```file "[tên-file-cấu-hình]";```
```}```
Ví dụ:
```zone "0.0.10.in-addr.arpa" IN {```
    ```type master;```
    ```file "0.0.10.in-addr.arpa.db";```
```}```

### Bản tin DNS
![image](https://electronicspost.com/wp-content/uploads/2016/05/2.23.png)
- 12 bytes đầu tiên là header section, trong đó có một số trường như:
    - Identification chiếm 16-bit
    - 1-bit cờ query/reply để đưa ra chỉ dẫn liệu bản tin là query(0) hay reply(1)
    - 1-bit cơ authoritative, 1-bit cờ recursion-desired
    - 1-bit cờ recursion-desired
    - 1-bit trường recursion-available
    - Ngoài ra còn 4 trường, các trường naqfy chỉ dẫn số lần xuất hiện của 4 kiểu dữ liệu trong data section
- Question section bao gồm các thông tin về truy vấn đang được tạo
- Answer section bao gồm bản ghi nguồn cho phần tên miền đã yêu cầu
- Authority section bao gồm các bản ghi của các server authoritative khác
- Additional section bao gồm các bản ghi hữu dụng khác