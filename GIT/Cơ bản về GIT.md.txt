# Cơ bản về GIT
### Giới thiệu chung
GIT là một hệ thống quản lý các phiên bản dưới dạng phân tán. GIT lưu trữ lịch sử thay đổi của hệ thống, thuận tiện cho lập trình viên theo dõi.
### Các thuật ngữ cơ bản
##### Branch
Các nhánh (branch) đại diện cho các phiên bản cụ thể của một kho lưu trữ được tách ra từ dự án chính.
Branch cho phép theo dõi các thử nghiệm và có thể hoàn nguyên về các phiên bản cũ hơn.
##### Commit
Commit đánh dấu một thời điểm trong lịch sử của dự án. Sử dụng kèm với lệnh ```git add``` để cho git biết những thay đổi muốn lưu vào local repository (kho lưu trữ nội bộ).
##### Checkout
Sử dụng lệnh ```git checkout``` để chuyển giữa các branch. Để chuyển sang branch khác, sử dụng lệnh ```git checkout <tên-nhánh>```. Để chuyển về nhánh chính, sử dụng lệnh ```git checkout master```.
##### Fetch
Lệnh ```git fetch``` dùng để tìm nạp các bản sao và tảu xuống các tệp của branch vảo máy tính. Sử dụng để lưu các thay đổi mới nhất vào kho lưu trữ,
##### Fork
Một Fork là một bản sao của một kho lưu trữ. Thường được tận dụng để thử nghiệm các thay đổi mà khồng ảnh hưởng tới dự án chính.
##### Head
Các commit ở đầu mỗi nhánh được gọi là head, nó đại diện cho commit mới nhất của repository đang làm việc.
##### Master
Master là nhánh chính của tất cả repository, bao gồm những thay đổi và commit gần nhất.
##### Remote
Một Remote là một bản sao của một nhánh.
### Các lệnh cơ bản của GIT
##### Lệnh git config
Lệnh config dùng để thiết lập tên người dùng và email trong main configuration file. Để cập nhật lại tên và email, sử dụng lệnh:
```sh
$ git config --global user.name "user"
$ git config --global user.email "email"
```
##### Lệnh git init
Dùng để tạo một git repo trong một dự án mới hoặc đã có sẵn. Lệnh này được sử dụng trong thư mục gốc của dự án.
##### Lệnh git clone
Sử dụng để copy một git repo từ kho lưu trữ từ xa. Cú pháp lệnh:
```sh
git clone <clone-git-url>
```
##### Lệnh git status
Sử dụng để kiểm tra trạng thái các tệp tin trong thư mục trong quá trình làm việc, ví dụ như kiểm tra sự thay đổi gần đây của các tệp tin từ lần commit gần nhất.
