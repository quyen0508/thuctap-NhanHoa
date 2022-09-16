# Phân biệt Thick Provisioning và Thin Provisioning
- Khi khởi tạo Virtual Machine sẽ có bước lựa chọn định dạng phân vùng lưu trữ cho VM như Thin Provisioned, Thick Provisioned Lazy Zeroed hay Thick Provisioned Eager Zeroed. Tuy vào cấu hình mà lựa chọn định dạng phù hợp để VM đạt được hiệu năng tốt nhất
- Điểm khác nhau rõ ràng nhất là sự chiếm dụng tài nguyên lưu trữ của server
- Ví dụ: Giả sử tạo 1 VM có dung lượng lưu trữ là 100GB, nếu chọn định dạng Thick thì VM sẽ lập tức chiếm đủ 100GB của server, trong khi đó Thin sẽ chỉ chiếm vừa đủ dung lượng mà nó đang lưu trữ
- Về hiệu suất, Thick Provisioned Eager Zeroed có hiệu suất tốt nhất, tiếp đến là Thick Provisioned Lazy Zeroed và cuối cùng là Thin Provisioned

### Thick Provisioning

![image](https://github.com/Tubui160999/thuctap_nhanhoa/raw/master/KVM/images/thin-thick.png)

- Dung lượng đĩa ảo hoàn chỉnh được phân bố trước trên bộ nhớ vật lý khi đĩa ảo được tạo. Đĩa ảo được cấp Thick Provisioning tiêu thụ tất cả không gian được phân bổ cho nó trong khi dữ liệu ngay từ đầu
- Có 2 kiểu Thick Provisioned virtual disk:
    - Lazy zeroed disk: Là một đĩa ảo dùng tất cả không gian của nó tại thời điểm tạo, nhưng không gian này có thể chứa một số dữ liệu cũ trên phương tiện vật lý. Dữ liệu cũ này không bị xoá hoặc ghi đè lên, do đó nó cần phải được "zeroed out" trước khi dữ liệu mới có thể được ghi vào các khối. Kiểu này có thể được tạo nhanh hơn nhưng hiệu suất của nó sẽ thấp hơn
    - Eager zeroed disk: Là một đĩa ảo dùng tất cả các không gian cần thiết còn lại tại thời điểm tạo ra nó và không bị xoá sạch mọi dữ liệu trước đó trên phương diện vật lý. Việc tạo đĩa trống mất nhiều thời gian hơn vì các số 0 được ghi vào toàn bộ ổ đĩa nhưng hiệu suất nhanh hơn trong lần viết đầu tiên
- Thick Provisioned Eager Zeroed cũng giống như Full Format, định dạng này thực hiện việc ghi giá trị 0 lên tẩ cả các sector, đồng nghĩa với việc sao chép dữ liệu vào sẽ ghi thêm giá trị 1 lần. Thick Provisioned Lazy Zeroed thì lại giống như Quick Format, sao chép dữ liệu đến đâu thì sẽ ghi đè dữ liệu tới đó

### Thin Provisioning

![image](https://github.com/Tubui160999/thuctap_nhanhoa/raw/master/KVM/images/thin.png)

- Đĩa ảo được tạo ra chỉ tiêu thụ không gian cần thiết khi ban đầu và tăng dần theo thời gian, theo nhu cầu, ví dụ, cấp 100GB cho máy ảo, máy ảo sư dụng đến đâu thì chiếm phần đó, giả sử chỉ cài OS chiếm 10GB thì tổng dung lượng của máy ảo chỉ là 10GB, 90GB còn lại vẫn được giải phóng để làm việc khác
- Lưu ý rằng khi xoá dữ liệu khỏi ổ đĩa ảo, kích thước đĩa sẽ không tự động giảm. Điều này là do hệ điều hành chỉ xoá các chỉ mục từ bảng tệp tham chiếu đến phần trên thân hệ thống tệp trong hệ thống tệp, nó đánh dấu các khối thuộc về các tệp "đã xoá" là trống và có hể truy cập được để ghi dữ liệu mới

### So sánh ưu nhược điểm
- Thick Provision: Tốc độ đọc ghi của VM có phần nhanh hơn, do được cập nhật cố định một khoảng trên ổ cứng, quản lý dễ dàng
- Thin Provision: Tốc độ đọc ghi VM có phần chậm hơn Thick Provision. Quản lý có phần phức tạp hơn. Nhưng lại linh động trong quản lý ổ đĩa, phần dung lượng giải phóng dễ dàng chia sẻ giữa các VM. Đặc biệt nếu phải backup/restore với trường hợp backup/restore sẽ nhanh hơn rất nhiều