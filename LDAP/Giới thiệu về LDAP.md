# Giới thiệu về LDAP
- LDAP viết tắt của Lightweight Directory Access Protocol: là một giao thức phát triển trên chuẩn X500
- Là một giao thức dạng client-server sử dụng để truy cập một dịch vụ thư mục
- Cho phép người dùng xác định cấu trúc và đặc điểm của thông tin trong thư mục
- Các ứng dụng để triển khai LDAP: OpenLDAP, OPENDS, Active Directory,...

### Phương thức hoạt động của LDAP
- LDAP hoạt động theo mô hình client-server, client gửi yêu cầu đến LDAP server, server này sẽ nhận yêu cầu và thực hiện tìm kiếm và trả lại kết quả cho client

- Trình tự của một phiên kết nối LDAP
    - Client mở một kết nối TCP đến LDAP server và thực hiện một thao tác bind. Thao tác này gồm tên của directory entry và thông tin xác thực sẽ được sử dụng trong quá trình xác thực, thông tin xác thực thông thường sẽ là Password, tuy nhiên cũng có thể là ID của người dùng
    - LDAP server nhận được thao tác bind của client để xử lý và trả lại kết quả của thao tác bind
    - Nếu thao tác bind thành công, client gửi một yêu cầu tìm kiếm đến LDAP server
    - Server thực hiện xử lý và trả về kết quả cho client
    - Client gửi yêu cầu unbind
    - Server đóng kết nối

![image](https://soshace.com/wp-content/uploads/2021/01/ldap-protocol-sequence-example-1024.jpg)

### LDAP là giao thức hướng thông điệp
- Do client và server giao tiếp với nhau thông qua các thông điệp. Client tạo một thông điệp chứa yêu cầu và gửi nó đến cho server. Server nhận được thông điệp và xử lý yêu cầu của client sau đó gửi trả cho client cũng bằng một thông điệp LDAP
- Nếu client tìm kiếm thư mục và nhiều kết quả được tìm thấy thì kết quả này được gửi đến client bằng nhiều thông điệp

![image](https://blog.cloud365.vn/images/img-ldap-datpt/ldap-2-2.png)

- Do LDAP là giao thức hướng thông điệp nên client dược phép phát ra nhiều thông điệp yêu cầu cùng lúc. Trong LDAP message ID dùng để phân biệt các yêu cầu của client và trả về kết quả trả về từ server

![image](https://blog.cloud365.vn/images/img-ldap-datpt/ldap-3-3.png)

### Cấu trúc file LDIF
- LDIF (LDAP Interchange Format) được định nghĩa trong RFC 2849, là một chuẩn định dạng file text lưu trữ thông tin cấu hình LDAP và nội dung thư mục
- File LDIF thường được sử dụng để import dữ liệu mới vào trong directory. Mọi thành phần được thêm vào hoặc thay đổi dữ liệu đã có. Dữ liệu có trong file LDIF cần phải tuân theo luật schema của LDAP directory
- Schema là một loại dữ liệu đã được định nghĩa từ trước trong directory. Mọi thành phần được thêm vào hoặc thay đổi trong directory đều được kiểm tra lại trong schema để đảm bảo sự chính xác. Lỗi vi phạm schema sẽ xuất hiện nếu dữ liệu không đúng với quy luật đã có. Đây là giải pháp nhập dữ liệu lớn vào LDAP
- Thông thường một file LDIF sẽ có khuôn dạng
    - Một tập entry khác nhau được phân cách bởi một dòng trắng
    - Tên thuộc tính: giá trị
    - Một tập các chỉ dẫn cú pháp để xử lý thông tin
- Ví dụ:

![image](https://blog.cloud365.vn/images/img-ldap-datpt/ldap-4.png)

- Những quy định khi báo nội dung file LDIF
    - Dấu comment trong file LDIF là "#"
    - Thuộc tính được đặt bên trái dâu ":" và giá trị của thuộc tính nằm phía bên phải
    - Thuộc tính ```dn``` định nghĩa duy nhất một DN xác định trong DN đó
    - Những thuộc tính có dấu "::" ngăn cách với giá trị thì giá trị của nó được mã hoá theo chuẩn BASE64
- Một entry là tập hợp của các thuộc tính, từng thuộc tính sẽ mô tả một nét đặc trưng tiêu biểu của đối tượng. Một entry bao gồm nhiều thuộc tính, ví dụ về một entry

![image](https://blog.cloud365.vn/images/img-ldap-datpt/ldap-5.png)

- Trong đó
    - dn - Distinguished Name: tên của entry thư mục, tất cả được viết trên một dòng
    - givenName: tên của người sở hữu account
    - sn - Surname: họ
    - cn - Common Name: tên thường gọi
    - uid: id người dùng
    - userPassword: mật khẩu người dùng
    - Và các thuộc tính khác

### Mô hình đặt tên LDAP (LDAP Naming model)
- Mô hình LDAP Naming định nghĩa ra cách để chúng ta có thể sắp xếp và tham chiếu đến dữ liệu của mình, hay có thể nói, mô hình này mô tả cách sắp xếp các entry vào một cấu trúc logic và mô hình LDAP Naming chỉ ra cách để chúng ta có thể tham chiếu đến bất kỳ một entry thư mục nằm trong cấu trúc đó
- Mô hình LDAP Naming cho phép đặt dữ liệu vào thư mục theo cách dễ dàng quản lý nhất
- Giống như đường dẫn của hệ thống tập tin, tên của một entry LDAP đườc hình thành bằng cách nối tất cả các  tên của từng entry cấp trên  cho đến cấp cáo nhất là ```root```

![image](https://blog.cloud365.vn/images/img-ldap-datpt/ldap-6-6.png)

### Mô hình chức năng LDAP (LDAP Function model)
- Mô hình LDAP function chứa một tập các thao tác chia thành 3 nhóm
    - Thao tác thẩm tra: cho phép search trên thư mục và nhận dữ liệu từ thư mục
    - Thao tác cập nhật: thêm, sửa, xoá, đổi tên và thay đổi các entry thư mục
    - Thao tác xác thực và điều khiển: cho phép client xác định mièn mình đến chỗ thư mục và điều khiển các hoạt động của phiên kết nối