# TÀI LIỆU GIT CƠ BẢN
## git cheat sheet

### git basics
```
git init <directory>
```
- Khởi tạo 1 kho lưu trữ (repository) Git trống tại thư mục được chỉ định. 

```
git clone <repo>
```
- Sao chép 1 kho lưu trữ từ xa (remote repo) về máy cục bộ.

```
git config user.name <name>
```
- Cấu hình tên tác giả cho các commit cho repo này.
```
git add <directory>
```
- đưa thư mục vào hàng chờ cho lần commit tiếp theo
```
git commit -m "<messages>"
```
- tin nhắn ngắn gọn cho các commit về stage đã được thay đổi vd: khi stage mới đẩy lên thì phải thêm commit như "update tính năng này"
```
git status
```
- Kiểm tra trạng thái các file (file nào đã stage, chưa stage, hoặc chưa được Git theo dõi - untracked).
```
git log
```
- Hiển thị toàn bộ lịch sử các commit đã thực hiện theo định dạng mặc định.
```
git diff
```
- Xem các thay đổi chưa đưa vào stage giữa các thư mục làm việc và vùng index
### Undoing changes
```
git revert <commit>
```
- Git tạo một commit mới lưu trạng thái ngược lại của commit được chỉ định.
``` 
git reset <file>
```
- Loại bỏ file khỏi vùng chờ (unstage) nhưng giữ nguyên nội dung thay đổi trong thư mục làm việc (không ghi đè dữ liệu).
```
git clean -n
```
- Dùng để xem trước các tệp sẽ bị xóa
- Lệnh này chỉ liệt kê chứ không xóa bất kỳ thứ gì, giúp bạn kiểm tra để tránh xóa nhầm trước khi dùng lệnh xóa thật `git clean -f`.
### Rewriting git history
```
git commit --amend
```
- Thay thế commit gần nhất bằng các thay đổi đang được stage hiện tại. Nếu không có gì được stage, lệnh này sẽ thay đổi tin nhắn commit gần nhất.
```
git rebase <base>
```
- Di chuyển hoặc gộp các commit của nhánh hiện tại sang một base mới
```
git reflog
```
- Hiển thị lại nhật ký hoạt động. thêm --relative-date để xem mốc thời gian hoặc --all để xem toàn bộ tham chiếu
### GIT BRANCHES
```
git branch
```
- Dùng để quản lý các nhánh trong dự án của bạn.
- `git branch <tên-nhánh>`: Tạo ra một nhánh mới từ vị trí hiện tại.
- `git branch -d <tên-nhánh>`: Xóa một nhánh đã gộp (merged).
```
git checkout -b <branch>
```
- Tạo một nhánh mới và chuyển ngay sang nhánh đó. Bỏ flag -b nếu chỉ muốn chuyển sang một nhánh đã tồn tại.
```
git merge <branch>
```
- Gộp các thay đổi từ nhánh chỉ định vào nhánh hiện tại đang đứng.
### REMOTE REPOSITORIES
```
git remote add <name> <url>
```
- Thiết lập kết nối tới một repo từ xa mới. Sau khi thêm, có thể dùng name làm lối tắt cho url trong các lệnh khác.
```
git fetch <remote> <branch>
```
- dùng để tải các commit mới nhất từ một nhánh trên mạng về máy tính của bạn.Lệnh này chỉ tải dữ liệu về để bạn xem trước chứ không tự động gộp (merge) vào code bạn đang viết, giúp bạn kiểm tra các thay đổi của người khác một cách an toàn mà không sợ bị hỏng code hiện tại.
```
git pull <remote>
```
- Dùng để tải code mới nhất về và tự động đồng bộ (bằng cách merge) vào nhánh đang làm việc.
```
git push <remote> <branch>
```
- dùng để đẩy các commit từ máy cá nhân lên remote repo. Sẽ tự tạo nhánh branch nếu remote không có.
## Tài liệu về Git Bash
### Git Bash là gì?
Git ban đầu được dùng rất thuận tiện trên Linux và macOS vì hai hệ điều hành này có sẵn môi trường dòng lệnh kiểu UNIX. 
Trong khi đó, Windows chủ yếu dùng Command Prompt nên không phải môi trường UNIX đầy đủ để thao tác Git theo kiểu quen thuộc. 
Git Bash là ứng dụng đi kèm Git for Windows, cung cấp Bash shell và một số tiện ích dòng lệnh giúp chạy Git dễ hơn trên Windows. 
### Giải thích tên gọi Bash
Bash là viết tắt của **Bourne Again Shell**, là một chương trình shell dùng để giao tiếp với hệ điều hành thông qua câu lệnh.
Git Bash được cài cùng với Git for Windows nên chỉ cần cài Git là thường đã có Git Bash.
## Các lệnh điều hướng cơ bản
### 1. `pwd`

Dùng để hiển thị thư mục hiện tại đang đứng. 

Ví dụ:

```
pwd
```

### 2. `ls`

Dùng để hiển thị các file và thư mục bên trong thư mục hiện tại. 
Ví dụ:

```
ls
```

### 3. `cd`

Dùng để chuyển sang thư mục khác. 

Ví dụ:

```
cd Documents
cd /d/Brup
cd /c/Users/Admin/Desktop
```

## Git Archive
Lệnh git `archive` dùng để đóng gói nhiều file trong repository thành một file duy nhất, khá giống cách WinRAR tạo file nén.
### Lệnh cơ bản nhất
```
git archive --format=tar HEAD
```
- Ở đây thì nó chỉ xuất hiện trên màn hình của Git bash các kí tự lạ của file (mã máy, mã nhị phân). Nên chỉ thấy các kí tự nhị phân khó đọc.

```
git archive --output=./example.tar --format=tar HEAD
```
- Lệnh này tạo file `example.tar` trong thư mục hiện tại
```
git archive --output=./example.tar.gz --format=tar HEAD ./BUILD
```
- Lệnh này chỉ lấy nội dung trong thư mục BUILD để đóng gói

### Dùng `prefix`
```
git archive --prefix=phien_ban_1/ --output=./code.zip HEAD
```
- prefix như 1 thư mục cha nơi chứa toàn bộ thư mục con bên trong, khi giải nén sẽ không bị bừa ra mà chỉ nằm hết trong 1 thư mục phien_ban_1

### Đóng gói từ remote
```
git archive --remote=https://duanlon.git --output=./codemain.zip main 
```
- Lệnh này yêu cầu phía remote tự đóng gói nhánh `main` thành file archive thay vì bạn phải clone toàn bộ repository về máy trước.
- Lệnh này giúp tải nhanh toàn bộ source code (tại thời điểm mới nhất của nhánh main) từ dự án https://duanlon.git về máy dưới dạng tệp codemain.zip 1 cách gọn gàng

## Git Init
Lệnh `git init` tạo một kho lưu trữ Git mới và biến một thư mục bình thường thành thư mục được Git quản lý.

### Phân biệt `git init` và `git clone`
- `git init` dùng khi muốn bắt đầu một repository mới từ đầu trên máy cá nhân. 
- `git clone` dùng khi muốn sao chép một repository đã tồn tại từ GitHub hoặc GitLab về máy.
- Về bản chất, `git clone` sẽ tạo repository local rồi mới sao chép dữ liệu từ remote về.

### Git Init --bare
```
git init --bare
```
Repository tạo bằng `--bare` là kho lưu trữ không có thư mục làm việc, thường dùng để làm máy chủ Git trung tâm cho việc lưu trữ và đồng bộ code giữa nhiều người. 
### Khi nào cần dùng --bare: 
khi muốn dựng máy chủ Git của riêng mình, chỉ được tạo để làm nhiệm vụ lưu trữ, đồng bộ và trao đổi code giữa tất cả mọi người

### Ví dụ hình dung cho dễ hiểu: 
Ở máy server:
```
git init --bare project-thuy.git
```
Ở máy cá nhân:
```
git clone ssh://user@server/path/project-thuy.git
```
Sau đó làm việc rồi:
```
git add .
git commit -m "update"
git push
```

## git clone
### git clone là gì?
- Hiểu đơn giản thì git clone dùng để sao chép các respository về máy,lấy nguồn từ GitHub hoặc trên các server nội bộ. Sau khi clone, có thể làm việc với bản copy đó.

### git clone dùng khi nào?
- git clone dùng khi đã có sẵn dự án và muốn lấy về máy để làm việc.

#### Ví dụ:
```
git clone ssh://john@example.com/path/to/my-project.git 
cd my-project 
```
- Sau đó làm việc trên my-project, lệnh trên đã tải respository 'my-project.git'

### git clone hoạt động như thế nào?
- Tạo 1 respository lên chính máy tính của bạn
- Sao chép toàn bộ lịch sử commit từ respository gốc về máy
- tự động tạo kết nối từ xa mang tên `origin` trỏ ngược lại kho lưu trữ gốc ban đầu
- Cho phép bạn `pull`, `push` về respository gốc 

### Clone vào thư mục khác
Cú pháp:

```
git clone <repo> <directory>
```

Ví dụ:

```
git clone https://github.com/nhamvinhthuy6699/THUCTAPNGHENGHIEP.git nhatkythuctap
```

Lệnh này sẽ clone repository vào thư mục `nhatkythuctap`.

### Shallow clone 
- shallow clone chỉ lấy 1 phần lịch sử của commit, nó cực kì hữu dụng khi repo quá lớn và bị giới hạn ổ đĩa và dung lượng, thời gian chờ khi sao chép. Shallow clone có thể giảm bớt những vấn đề mở rộng này.
```
git clone -depth=1 <repo>
```
- Chỉ lấy 1 commit gần nhất 

### Clone một nhánh cụ thể
```
git clone --branch <tag> <repo>
```
### git clone --mirror vs git clone --bare

#### git clone --bare
- Chỉ dược sử dụng để Làm kho lưu trữ trung tâm hoặc để backup, không dùng như chỉnh sửa file trực tiếp hay môi trường làm việc
```
git clone --bare https://github.com/user/project.git
```

### git clone --mirror
- Kế thừa hoàn toàn git clone --bare, nhưng nếu trên repo gốc thay đổi ra sao thì repo mirror sẽ thay đổi và cập nhập y hệt
- với repo --bare, sẽ bị lỗi thời vì không được cập nhập
- với repo --mirror, nó sẽ được cập nhập với lệnh:
```
git remote update
```
- ngay lập tức sẽ tự động ghi đè và cập nhập toàn bộ các nhánh cục bộ, chính xác 100% theo repo gốc hiện tại.

### git url phổ biến
### SSH
```
ssh://[user@]host.xz[:port]/path/to/repo.git/  
```

### HTTPS
```
git://host.xz[:port]/path/to/repo.git/  
```

### Git 
```
http[s]://host.xz[:port]/path/to/repo.git/  
```

## git config
- git config dùng để cấu hình toàn cục hay cục bộ của dự án. Là lệnh dùng để thiết lập, tùy chỉnh các thông số và hành vi hoạt động của hệ thống Git trên máy tính của bạn.  
### Cách sử dụng
- Trường hợp cơ bản nhất:
```
git config user.email
```
- Các commit sẽ được tự động liên kết với tài khoản của chính mình

### Các level của git config
