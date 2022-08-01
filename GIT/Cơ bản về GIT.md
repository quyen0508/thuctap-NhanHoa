# Cơ bản về GIT
### Giới thiệu chung
GIT là một hệ thống quản lý các phiên bản dưới dạng phân tán. GIT lưu trữ lịch sử thay đổi của hệ thống, thuận tiện cho lập trình viên theo dõi.
### Các thuật ngữ cơ bản
##### Branch
Các nhánh (branch) đại diện cho các phiên bản cụ thể của một kho lưu trữ được tách ra từ dự án chính.
Branch cho phép theo dõi các thử nghiệm và có thể hoàn nguyên về các phiên bản cũ hơn.
##### Commit
Commit đánh dấu một thời điểm trong lịch sử của dự án. Sử dụng kèm với lệnh ```git add``` để cho git biết những thay đổi muốn lưu vào local repository (kho lưu trữ nội bộ).
##### Fork
Một Fork là một bản sao của một kho lưu trữ. Thường được tận dụng để thử nghiệm các thay đổi mà khồng ảnh hưởng tới dự án chính.
##### Head
Các commit ở đầu mỗi nhánh được gọi là head, nó đại diện cho commit mới nhất của repository đang làm việc.
##### Master
Master là nhánh chính của tất cả repository, bao gồm những thay đổi và commit gần nhất.
##### Remote
Một Remote là một bản sao của một nhánh.
##### Repository
Kho lưu trữ GIT chứa tất cả các tệp dự án bao gồm các branch, tags và commit.
##### Tags
Cung cấp cách để theo dõi các commit quan trọng. Các tags nhẹ đóng vai trò là con trỏ trong khi các tags chú thích được lưu trữ dưới dạng đối tượng.
### Các lệnh cơ bản của GIT
##### Lệnh git config
Lệnh config dùng để thiết lập tên người dùng và email trong main configuration file. Để cập nhật lại tên và email, sử dụng lệnh:
```sh
git config --global user.name "user"
git config --global user.email "email"
```
##### Lệnh git init
Dùng để tạo một git repo trong một dự án mới hoặc đã có sẵn. Lệnh này được sử dụng trong thư mục gốc của dự án.
##### Lệnh git clone
Sử dụng để copy một git repo từ kho lưu trữ từ xa. Cú pháp lệnh:
```sh
git clone <clone-git-url>
```
##### Lệnh git status
Sử dụng để kiểm tra trạng thái các tệp tin trong thư mục trong quá trình làm việc, ví dụ như kiểm tra sự thay đổi gần đây của các tệp tin từ lần commit gần nhất
##### Lệnh git add
Sử dụng lệnh ```git add``` để thêm thay đổi đến stage/index trong thư mục làm việc hoặc ```git add <:tên-file:>``` và ```git add all``` để đưa một file hoặc tất cả các file trong thư mục vào Staging Area.
##### Lệnh git checkout
Sử dụng lệnh ```git checkout``` để chuyển giữa các branch. Để chuyển sang branch khác, sử dụng lệnh ```git checkout <tên-nhánh>```. Để chuyển về nhánh chính, sử dụng lệnh ```git checkout master```.
##### Lệnh git fetch
Lệnh ```git fetch``` dùng để tìm nạp các bản sao và tảu xuống các tệp của branch vảo máy tính. Sử dụng để lưu các thay đổi mới nhất vào kho lưu trữ,
##### Lệnh git commit
Cú pháp lệnh:
```sh
git commit -m"<nội-dung-commit>"
```
##### Lệnh git push/git pull
Dùng để push hoặc pull các thay đổi đến remote. Cú pháp:
```sh
git pull <:remote:> <:branch:>
git push <:remote:> <:branch:>
```
##### Lệnh git branch
Liệt kê tất cả các nhanh.
Cú pháp:
```sh
git branch
```
hoặc
```sh
git branch -a
```
##### Lệnh git stash
Dùng để lưu thay đổi mà không muốn commit ngay lập tức.
Cú pháp:
```sh
git stash
```
##### Lệnh git reset
Dùng để đưa tập tin ra khỏi Staging Area để không bị commit.
Cú pháp:
```sh
git reset HEAD <:tên-file:>
```
##### Lệnh git merge
Đùng để merge hai nhánh với nhau. Để sử dụng, chuyển tới nhánh muốn merge và sử dụng lệnh ```git merge <:branch-muốn-merge:>```
