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
#### --local 
- Mặc định, nếu không có tùy chọn cấu hình nào thì git sẽ ghi hết vào cấu hình cục bộ. Cấu hình lưu tại file .git/config.

#### --global
- Cấu hình cấp toàn cục là cấu hình dành riêng cho người dùng, nghĩa là nó được áp dụng cho người dùng hệ điều hành. CCác giá trị cấu hình toàn cục được lưu trữ trong một tệp nằm trong thư mục chính của người dùng `C:\Users\<username>\.gitconfig` Windows.

#### --system
- Cấu hình cấp hệ thống được áp dụng trên toàn bộ máy tính. Điều này bao gồm tất cả người dùng trên hệ điều hành và tất cả các kho lưu trữ. Được lưu trữ ở `C:\ProgramData\Git\config`

### Thứ tự ưu tiên
--local => --global => --system. Có nghĩa là khi tìm kiếm 1 giá trị, nó sẽ bắt đầu từ level local tới level system.

### Các thiết lập phổ biến
- Danh tính người dùng
```
git config --global user.name "nhamvinhthuy6699"
git config --global user.email "thuyvinhnham69@gmail.com"
```

### Chọn trình soạn thảo văn bản
- Nếu lỡ quên nhập commit, nó sẽ bật 1 trình soạn thảo. Mặc định khi cài Git nó sẽ là vim, đổi sang phần mềm khác: 
```
git config --global core.editor "notepad"
```
Hoặc sử dụng vscode để thuận tiện cho Git
```
git config --global core.editor "code --wait"
```
### Merge tools
- Khi 2 người sửa 1 dòng code và gộp (merge) sẽ bị sai, báo lỗi xung đột
- Tác dụng của merge tool: cài đặt phần mềm cho bên thứ 3, chia 3 cột so sánh của bạn, đối phương và kết quả gộp. Để biết giữ cái nào dễ dàng hơn
```
git config --global merge.tool kdiff3
```
Hoặc sử dụng chính vscode
```
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd "code --wait --merge \$LOCAL \$REMOTE \$BASE \$MERGED"
```

### Colored outputs 
- Bật màu giúp thấy trạng thái Git nhanh hơn

### Aliases
- Lệnh Git thường dài và dễ sai. Alias giống phím tắt hoặc tên biệt danh để tạo cho các lệnh đó gõ nhanh hơn

### Formatting & whitespace
- Khi làm việc nhóm, việc một ai đó vô tình bấm thừa dấu cách (space) hoặc ấn phím Tab lung tung ở cuối dòng sẽ làm code bị bẩn và gây rối khi xem lịch sử thay đổi. Git có tính năng tự động phát hiện và tô màu cảnh báo các "lỗi khoảng trắng" này khi bạn xem git diff.  
#### Các lỗi được BẬT phát hiện mặc định:
- blank-at-eol: Có dấu cách vô dụng nằm ở cuối dòng code.
- space-before-tab: Dùng dấu cách đứng trước dấu Tab khi bạn thụt đầu dòng.
- blank-at-eof: Thừa các dòng trống trắng xóa ở tận cuối cùng của file.

#### Các tính năng sau đây bị vô hiệu hóa theo mặc định.
- indent-with-non-tab: Đánh dấu dòng được thụt lề bằng dấu cách thay vì dấu tab.

- tab-in-indent: báo lỗi khi thụt lề tab ban đầu.

- trailing-space: là viết tắt của cả blank-at-eol (khoảng trắng thừa ở cuối dòng) và blank-at-eof (dòng trống thừa ở cuối file)

- cr-at-eol highlights: xuống dòng ở cuối mỗi dòng. Trên Windows, khi bạn ấn Enter xuống dòng, nó sẽ tự sinh ra ký tự ẩn gọi là CR (Carriage Return). Nếu bạn bật tính năng này, Git sẽ coi ký tự CR đó là một lỗi và tô màu đánh dấu nó.

- tabwidth=<n>: Tham số này xác định số vị trí ký tự mà một tab chiếm giữ. Giá trị mặc định là 8. Các giá trị cho phép là từ 1 đến 63.

## Git alias
- Git Alias giúp bạn biến các câu lệnh Git dài dòng trở thành những từ viết tắt siêu ngắn để gõ nhanh hơn, tiết kiệm thời gian và công sức.
### Cách tạo phím tắt cơ bản
```
git config --global alias.co checkout
```
- Thay vì gõ git checkout, giờ chỉ cần gõ git co
```
git config --global alias.br branch 
```
- Thay vì gõ git branch, giờ chỉ cần gõ git br
```
git config --global alias.ci commit
```
- Thay vì gõ git commit, giờ chỉ cần gõ git ci
```
git config --global alias.st status
```
- Thay vì gõ git status, giờ chỉ cần gõ git st

### Sử dụng git để tạo các lệnh git mới
- Có thể tạo ra một lệnh hoàn toàn mới tên là unstage bằng cách gõ:
Ví dụ: Khi bạn lỡ gõ git add nhầm một file vào khu vực hàng chờ (staging area), câu lệnh gốc để hủy bỏ hành động đó rất dài và khó nhớ: git reset HEAD -- tên_file.

Bạn có thể tạo ra một lệnh hoàn toàn mới tên là unstage bằng cách gõ:
```
git config --global alias.unstage 'reset HEAD --'
```
Từ giờ, mỗi khi muốn bỏ một file ra khỏi hàng chờ, bạn chỉ cần gõ cực kỳ ngắn gọn:
```
git unstage FileA
```

### Cách tạo git alias
#### Cách 1: tìm file và sửa trực tiếp lên đó
- Tìm và mở file có tên .gitconfig để sửa trực tiếp trên đó
#### Cách 2: Dùng lệnh git config để Git tự viết hộ
```
git config --global alias.co checkout
```

- Đã tạo thành công, giờ chỉ cần ghi git co, không cần ghi git config --global checkout 

## Saving changes in Git
- Khi làm việc với Git, khái niệm lưu trong git khác hoàn toàn so với các trình soạn thảo văn bản của windows chỉ cần ctrl + S hoặc các tệp chỉnh sửa tệp truyền thống khác. 

### Khái niệm lưu trong git
Trong các phần mềm truyền thống, "lưu" nghĩa là ghi đè lên file cũ. Nhưng trong Git, "lưu" (gọi là Commit) là chụp lại ảnh chụp toàn bộ dự án (snapshot) tại thời điểm đó và lưu vào lịch sử.

#### Quy trình ghi gọi là three trees:
1. Working directory: Trực tiếp sửa code, thêm file
1. staging area: gom file vào hàng chờ. Sử dụng git add để đưa file vào đây
1. commit history: lưu trữ và đẩy lên repo. Sử dụng lệnh git commit để done việc add file.

### Sự khác biệt giữa SVN và GIT 
- Với SVN (Centralized - Tập trung): Lệnh commit (hoặc check-in) sẽ đẩy thẳng code lên một máy chủ tập trung. Điều này có nghĩa là bạn bắt buộc phải có kết nối Internet thì mới có thể "lưu" được code.  
- Với Git (Distributed - Phân tán): Các commit được ghi lại và tích lũy ngay tại máy tính cục bộ của bạn (Locally). Sau đó, khi nào cần thiết và có mạng, bạn mới đẩy chúng lên máy chủ từ xa bằng lệnh:
```
git push -u origin main
```
#### ƯU điểm
Nếu máy chủ sập, bạn vẫn có toàn bộ lịch sử code trên máy mình làm việc

- Để thực hiện việc snapshop trạng thái dự án, Git kết hợp bộ ba lệnh: git add, git status, và git commit.

- Ngoài ra còn có `git stash`, `git ignore` phần sau sẽ học

## git add
- Đầu tiên, sửa đổi các file trong thư mục làm việc (Working Directory).

- Khi đã sẵn sàng lưu lại trạng thái hiện tại, đưa các file đó vào hàng chờ bằng lệnh git add.

Khi đã ưng ý với snapshot trong hàng chờ, chính thức lưu nó vào lịch sử dự án bằng lệnh git commit.

Lưu ý: Nếu muốn hủy bỏ một commit hoặc một file đã lỡ đưa vào hàng chờ,dùng lệnh git reset.

git push được sử dụng để gửi các thay đổi đã được cam kết đến các kho lưu trữ từ xa để cộng tác. Điều này cho phép các thành viên khác trong nhóm truy cập vào tập hợp các thay đổi đã được lưu.

#### Điểm khác biệt lớn nhất giữa svn add và git add:
- `svn add` chỉ cần gọi 1 lần duy nhất khi tạo file để báo cho hệ thống theo dõi file đó  
- `git add` hoạt động ở cấp độ "sự thay đổi" (changes). Vì vậy, mỗi lần bạn sửa file, bạn đều phải gọi lại lệnh git add thì Git mới ghi nhận phần sửa đổi đó vào commit tiếp theo. Quy trình này giúp việc tổ chức dự án ngăn nắp hơn rất nhiều.
##### Git cho phép bạn chia nhỏ các phần chỉnh sửa trong cùng một file thành nhiều lần lưu khác nhau, giúp lịch sử sửa code của bạn cực kỳ sạch sẽ, rõ ràng và ngăn nắp. Còn SVN thì không làm được như vậy, hễ commit là nó hốt sạch sành sanh toàn bộ file đi luôn.

### Staging area
- là vùng đệm trung gian dùng để chuẩn bị, nhóm các thay đổi hoặc dữ liệu trước khi đưa vào hệ thống chính, đảm bảo tính an toàn và tổ chức. 
- Giúp lịch sử commit trở nên gọn gàng và dễ theo dõi hơn.
- Xem lại các thay đổi
- Cho phép lưu nhanh các thay đổi, sau đó quay lại để chỉnh sửa nếu chưa đạt yêu cầu

### Các tùy chọn git add phổ biến
- `git add <file>` : đưa toàn bộ thay đổi của 1 file vào hàng chờ
- `git add <direction>` : đưa toàn bộ thay đổi của thư mục vào hàng chờ
- git add -p: Bật chế độ tương tác(Interactive). Git sẽ chia nhỏ các đoạn code đã sửa và hỏi bạn từng đoạn một: ấn y để duyệt đưa vào hàng chờ, ấn n để bỏ qua, ấn s để chia nhỏ hơn, ấn e để tự sửa bằng tay, hoặc ấn q để thoát.

### Ví dụ thực tế
Khi bắt đầu 1 dự án mới, `git add` hoạt động giống `svn import`. Để tạo commit đầu tiên cho toàn bộ thư mục hiện tại:
```
git add .
git commit
```
Khi dự án đã chạy, bạn thêm file mới hoặc lưu file cũ bằng cách truyền đường dẫn:
```
git add hello.py
git commit
```

## git commit
- git commit trong hệ thống quản lý phiên bản Git đóng vai trò như một bản lưu (snapshot) hoặc chốt điểm lưu. Nó ghi lại toàn bộ trạng thái mã nguồn tại 1 thời điểm cụu thể vào local respository. Kèm theo 1 thông điệp (message) mô tả chi tiết các thay đổi được thực hiện

### So sánh commit git và commit SVN 
- Trong SVN, thay đổi sẽ đẩy thẳng lên máy chủ trung tâm. Nếu có ai đó sửa cùng 1 file đó, xảy ra xung đột và ngăn commit lên
- Trong Git, commit là thao tác hoàn toàn cục bộ (local). Nó lưu trên máy bạn, không cần internet. Có thể chia nhỏ commit thành nhiều commit nhỏ, khi đã sẵn sàng thì mới git push lên github.

### How it works
Ở mức độ tổng quan, bạn hãy tưởng tượng toàn bộ lịch sử dự án của bạn là một con đường thời gian dài phẳng tắp:

Mỗi một Commit đóng vai trò là một mốc thời gian (milestone) hoặc một snapshot nằm trên dòng thời gian đó.  

Khi gõ lệnh `git commit`. tiếp tục ghi lại dự án ở thời điểm đó hoặc cột mốc đánh dấu trạng thái của dự án tại 1 thời điểm.

Lưu trữ cục bộ: các snapshot này luôn được lưu vào kho lưu trữ nội bộ

### Sự khác biệt cốt lõi giữa Git và SVN
- Với SVN (Cũ): Khi bạn commit, mã nguồn từ máy bạn sẽ được đẩy trực tiếp lên máy chủ trung tâm (Central Repository). Bạn bị bắt buộc phải kết nối mạng và tương tác với máy chủ ngay lập tức.
- Với Git: nó giúp dễ dàng chia nhỏ một tính năng thành các cam kết riêng lẻ, giữ các cam kết liên quan được nhóm lại với nhau và dọn dẹp lịch sử cục bộ trước khi xuất bản lên kho lưu trữ trung tâm. 
- Giúp các nhà phát triển được làm việc trrong môi trường biệt lập, trì hoãn sự tích hợp trước khi hợp nhất lại dự án với mọi người.

- Mặc dù vậy, tốt nhất các nhóm phải gộp code trên máy thường xuyên và chia thành nhiều phần nhỏ. Nếu giữ code quá lâu sẽ khiến cho việc gộp lại (merge) sau này sẽ cực kì đau đầu.

### Snapshots, not differences

Mô hình SVN: mỗi khi bạn commit, chỉ lưu những phần khác biệt so với phiên bản trước đó

Mô hình Git:Git coi những commit là snapshot tại thời điểm đó. Toàn bộ nội dung của file đều có sẵn trong dữ liệu nội bộ của Git.

#### Ưu điểm hơn của Git so với SVN
- Cơ chế tối ưu dung lượng: để ổ cứng không bị đầy, nếu file A không được sửa gì nhưng đã commit trước đó thì khi commit lại, nó không copy file A 1 lần nào nữa. Nó tự trỏ ngược về file commit trước đó. 
- Ưu điểm về mặt tốc độ : Muốn về phiên bản nào cũng được, không như mô hình SVN không tách nhau ra và không bị mất thời gian tính toán như SVN

### common options
```
git commit
```
- Xác nhận snapshot đang ở trong stage, sau đó mở trình soạn thảo để viết lời nhắn rồi mới lưu
```
git commit -a
```
- Lưu lại bản sao lưu toàn bộ thay đổi trong thư mục làm việc. Thao tác này chỉ bao gồm các sửa đổi đối với các tệp được theo dõi ( tức là những tệp đã được đưa vào git add)
```
git commit -m "commit message"
```
- Commit nhanh với lời nhắn viết trực tiếp.
```
git commit -am "commit message"
```
- Lệnh này là sự kết hợp giữa 2 lệnh trên nhằm gộp tất cả các file đang trong stage và viết lời nhắn nhanh
```
git commit --amend
```
- Dùng để sửa đổi commit gần nhất
- bổ sung file hay code bị thiếu  
Ví dụ: 
push lên quên mất chưa đưa tài liệu hướng dẫn, add lại lên stage với tên là file.txt và gộp: 
```
git commit --amend --no-edit
```
- Cờ --no-edit giúp bạn gộp code vào commit cũ mà giữ nguyên thông điệp cũ, không phải viết lại

## git diff
- Là lệnh dùng để so sánh của mã nguồn. Lệnh này chính xác là so sánh xem lệnh nào đã được thêm, sửa, xóa trong mã nguồn trước khi commit và merge lại với nhau

### Đọc kết quả của diff
ví dụ sau cho dễ hiểu 
```
$:> mkdir diff_test_repo
$:> cd diff_test_repo
$:> touch diff_test.txt
$:> echo "this is a git diff test example" > diff_test.txt
$:> git init .
Initialized empty Git repository in /Users/kev/code/test/.git/
$:> git add diff_test.txt
$:> git commit -am"add diff test file"
[main (root-commit) 6f77fc3] add diff test file
1 file changed, 1 insertion(+)
create mode 100644 diff_test.txt
```
- Lúc này không có gì bất thường, nhập lệnh git diff ở đây sẽ không có kết quả nào hiển thị. Bây giờ thay đổi nội dung của tệp.
```
$:> echo "this is a diff example" > diff_test.txt
```
- Bây giờ mới tới bước so sánh
```
diff --git a/diff_test.txt b/diff_test.txt
```
- Sẽ tạo ra kết quả như sau 
```
index 6b0c6cf..b37e70a 100644
--- a/diff_test.txt
+++ b/diff_test.txt
@@ -1 +1 @@
-this is a git diff test example
+this is a diff example
```
#### Giải mã từng dòng
- `diff --git a/diff_test.txt b/diff_test.txt` **Đầu vào so sánh**: Cho biết Git đang so sánh giữa phiên bản cũ (kí hiệu a/) và phiên bản mới (kí hiệu b/) của file diff_test.txt
- `index 6b0c6cf..b37e70a 100644` **Meta data**: Mã băm nội bộ của Git, không cần quan tâm tới dòng này quá nhiều
- **Các dấu hiệu của sự thay đổi**:`--- a/ và +++ b/` những gì thay đổi của file cũ a sẽ đánh dấu là dấu trừ (---), còn file mới b sẽ đánh dấu là dấu cộng (+++)
- `@@ -1,+1 @@` **Đoạn header của block chứa thay đổi**: Kí hiệu nằm giữa 2 dấu @@ cho biết vị trí thay đổi. Ở đây -1 +1 nghĩa là: tại dòng số 1 của file đã có sự thay đổi, và nội dung mới đang nằm ở số 1 của file mới

**VÍ DỤ NHỮNG TÌNH HUỐNG KHÁC**  
`@@ -34,6 +34,8 @@`
- Ở đây thì có 6 dòng ở dòng 34 bị tác động, và cũng ở dòng 34 ở file mới thì có 8 dòng khác đã sửa đổi

### Highlighting changes
1. git diff --color-words  
`git diff --color-words`
**Cách hoạt động:**
- Từ bị xóa sẽ được bôi đỏ
- Từ được thêm sẽ giữ nguyên màu xanh
- Các từ khác sẽ để màu mặc định
- kí từ (+) và (-) bị loại bỏ 
1. git diff-highlight
** Công cụ nâng cao đi kèm**  
- Đây là một đoạn script nhỏ nằm trong thư mục cài đặt nâng cao (contrib) của Git. Nó sẽ kết hợp cả hai cách hiển thị: vừa giữ lại dấu -/+ thô, vừa tô đậm đúng cái từ/ký tự cụ thể bị sửa đổi bên trong dòng đó để bạn nhìn thấy ngay lập tức.

### Diffing binary files
- Mặc định, nếu bạn dùng git diff cho file nhị phân (ví dụ file PDF), Git chỉ báo một câu vô dụng: Binary files a/script.pdf and b/script.pdf differ (Hai file có sự khác biệt).  
- Giải pháp: Bạn có thể cấu hình thông qua file .gitconfig (hoặc .git/config) để bắt Git chạy một phần mềm chuyển đổi (converter) biến file nhị phân thành dạng chữ thô trước khi so sánh.

- Với file PDF: Dùng công cụ pdftohtml để dịch PDF thành dạng chữ HTML rồi mới diff.

- Với file ZIP/JAR: Dùng lệnh unzip -l để so sánh danh sách các file bên trong xem có file nào mới bị thêm hoặc xóa không.

- Với file Ảnh: Dùng exiv2 để so sánh sự thay đổi về siêu dữ liệu (metadata) như kích thước ảnh, ngày chụp.

### Các câu lệnh thực tế từ cơ bản tới nâng cao
**So sánh các file chưa lưu tạm (Unstaged changes)**
```
git diff
Hoặc chỉ đích danh 1 file: git diff ./path/to/file
```
- So sánh những gì bạn vừa gõ thêm với các file bạn đã cho vào khu vực staging area. Nó giúp bạn biết mình đã sửa những gì kể từ lần gõ git add gần nhất.

### So sánh các file ĐÃ lưu tạm (Staged / Cached changes)
```
git diff --cached ./path/to/file
```
- So sánh các thay đổi đã gõ git add thành công với cú commit gần nhất (HEAD). Dùng lệnh này để soát lại xem đã chuẩn chưa trước khi gõ lệnh git commit.

### So sánh các tệp giữa 2 lần commit khác nhau 
```
git log --pretty=oneline
957fbc92b123030c389bf8b4b874522bdf2db72c add feature
ce489262a1ee34340440e55a0b99ea6918e19e7a rename some classes
6b539f280d8b0ec4874671bae9c6bed80b788006 refactor some code for feature
646e7863348a427e1ed9163a9a96fa759112f102 add some copy to body

$:> git diff 957fbc92b123030c389bf8b4b874522bdf2db72c ce489262a1ee34340440e55a0b99ea6918e19e7a
```
- Lấy mã băm (Commit ID) từ lệnh git log, sau đó truyền vào để xem giữa hai thời điểm lịch sử đó, dự án đã thay đổi những gì.

### Comparing branches
#### Với 2 dấu .
```
git diff branch1..other-feature-branch
```
- Đầu hiện tại của branch1 với đầu hiện tại của other-feature-branch
Ví dụ có lịch sử như này:
```
A---B---C  branch1
     \
      D---E  other-feature-branch
```
branch1 đang đứng ở commit C
other-feature-branch đang đứng ở commit E   
Khi chạy 
Git sẽ so sánh nội dung tại commit C với nội dung tại commit E.

#### Với 3 dấu . 
```
git diff branch1...other-feature-branch
```
Dùng khi bạn muốn xem branch phụ đã thay đổi gì kể từ lúc tách khỏi branch chính.

Có thể hiểu là:

Xem những thay đổi mà new_branch đã làm kể từ khi nó tách từ main.

Cái này rất hay dùng trước khi merge hoặc pull request.

** Ví dụ **
```
A---B---C  branch1
     \
      D---E  other-feature-branch
```
Git sẽ so sánh giữa B và E

Nghĩa là `“Từ lúc other-feature-branch tách ra khỏi branch1, branch other-feature-branch đã thay đổi những gì?”`

### Comparing files from two branches
```
git diff main new_branch ./diff_test.txt
```
- Cách hoạt động: Thay vì so sánh toàn bộ hàng trăm file trong dự án, bạn chỉ muốn soi đúng file diff_test.txt.

## git stash

- 1 Công cụ cực kỳ hữu ích, nó cho phép tạo ra bản tạm thời lưu trữ những thay đổi bạn đang thực hiện để bạn có thể làm việc khác. Ví dụ:  
Bạn đang code dở 1 dự án ở nhánh branch, chưa xong gì hết nhưng leader báo lỗi ở nhánh main, lúc này nếu bạn nhảy qua luôn thì sẽ mất luôn code đang code dở, nếu bạn commit lên sẽ thành 1 đống commit rác. Stash giúp giải quyết tình huống này.

### Các câu lệnh git stash hay dùng nhất hàng ngày
#### cho dự án vào Stash

```
git stash
# Hoặc lệnh đầy đủ có kèm lời nhắn để dễ nhớ:
git stash save "đang làm dở tính năng đăng nhập"
```
**Tác dụng**: Gom toàn bộ các file đã sửa (nhưng chưa commit) cất đi. Thư mục làm việc của bạn lập tức trở lại trạng thái "sạch sẽ".

### Xem trong stash có gì
```
$ git stash list
stash@{0}: WIP on main: 5002d47 our new homepage
stash@{1}: WIP on main: 5002d47 our new homepage
stash@{2}: WIP on main: 5002d47 our new homepage
```
**Tác dụng**: Hiển thị danh sách các lượt stash bạn đã cất.

### Lấy dự án ra để tiếp tục
```
git stash apply
# Hoặc chỉ định rõ lượt cụ thể: git stash apply stash@{1}
```
**Tác dụng**: Đưa code ra lại và tiếp tục thực hiện, nhưng đối với lệnh này vẫn có bản sao trong ngăn kéo

### Lấy dự án ra và xóa trong stash
```
git stash pop
```
**Tác dụng**: Lệnh này kết hợp giữa apply (lấy code ra) và drop (xóa cái stash đó đi). Ngăn kéo của bạn sẽ sạch sẽ, không bị đầy.
### Xóa bỏ stash không cần nữa
```
git stash drop stash@{0}
# Hoặc xóa sạch sành sanh toàn bộ ngăn kéo:
git stash clear
```
**Tác dụng**:Xóa hết trong stash, điều này làm rỗng trong stash và không có cách khôi phục để tiếp tục
### Các tùy chọn nâng cao (Advanced Options)
Mặc định, lệnh git stash chỉ cất những file cũ đã được Git theo dõi từ trước (tracked files). Nếu bạn vừa tạo ra một file mới tinh (untracked file) và gõ git stash, Git sẽ bỏ quên file đó. 
Để bắt Git cất luôn cả file mới, bạn có các tùy chọn sau:

- git stash -u (hoặc --include-untracked): Cất cả những file mới tinh chưa từng được git add.

- git stash -a (hoặc --all): Cất tất cả mọi thứ, kể cả các file bị bỏ qua trong 
- .gitignore (Rất hiếm khi dùng).

### Git ignore

- Là những file mà bạn chỉ đích danh bắt Git phải ngó lơ, không được đụng vào

#### Các file thường được cho vào danh sách bỏ qua này
- Thư mục chứa thư viện tải về: /node_modules, /packages.

- File sinh ra sau khi biên dịch code: .o, .pyc, .class.

- Thư mục chứa kết quả build/xuất bản: /bin, /out, /target.

- File tạm sinh ra khi chạy ứng dụng: .log, .lock, .tmp.

- File ẩn của hệ điều hành: .DS_Store (Mac), Thumbs.db (Windows).

- File cấu hình cá nhân của phần mềm code: .idea/workspace.xml.

**Lưu ý**:  Không có câu lệnh git ignore. Để bỏ qua file, tự tạo 1 văn bản tên .gitignore ở thư mục gốc dự án, viết các quy tắt vào

File .gitignore sử dụng các ký tự đặc biệt (gọi là globbing patterns) để lọc tên file. Dưới đây là bảng tra cứu đầy đủ:

| Cú pháp (Pattern) | Ví dụ viết trong file | Ý nghĩa và Cách hoạt động |
| :--- | :--- | :--- |
| **Dấu sao (`*`)** | `*.log` | **Ký tự đại diện**: Bỏ qua tất cả các file có đuôi là `.log` (Ví dụ: `debug.log`, `error.log`). |
| **Dấu hỏi (`?`)** | `debug?.log` | **Khớp đúng 1 ký tự**: Sẽ bỏ qua `debug0.log`, `debugg.log` nhưng **không** bỏ qua `debug10.log`. |
| **Cặp ngoặc vuông (`[ ]`)** | `debug[0-9].log`<br><br>`debug[01].log` | **Khớp 1 ký tự trong khoảng/tập hợp**:<br>- Lọc từ 0 đến 9 (`debug0.log` đến `debug9.log`).<br>- Chỉ lọc đúng số 0 hoặc số 1. |
| **Dấu chấm than vuông (`[! ]`)** | `debug[!01].log` | **Phủ định tập hợp**: Bỏ qua các file như `debug2.log`, nhưng **không** bỏ qua `debug0.log` hay `debug1.log`. |
| **Dấu gạch chéo đầu (`/`)** | `/debug.log` | **Chỉ áp dụng ở thư mục gốc**: Chỉ bỏ qua file `debug.log` nằm ngay bên ngoài, nếu file này nằm trong thư mục con (ví dụ: `logs/debug.log`) thì **không** bị bỏ qua. |
| **Dấu gạch chéo cuối (`/`)** | `logs/` | **Chỉ định đây là thư mục**: Bỏ qua toàn bộ thư mục tên là `logs` và tất cả những gì nằm bên trong nó. |
| **Không có gạch chéo cuối** | `logs` | **Khớp cả file lẫn thư mục**: Bỏ qua cả file tên là `logs` và thư mục tên là `logs`. |
| **Hai dấu sao đầu (`**/`)** | `**/logs` | **Áp dụng ở bất kỳ đâu**: Bỏ qua thư mục `logs` dù nó nằm ở thư mục gốc hay nằm sâu trong các thư mục con khác (`build/logs`). |
| **Hai dấu sao giữa (`/**/`)** | `logs/**/debug.log` | **Tìm xuyên qua các thư mục con**: Bỏ qua file `debug.log` nằm trong `logs/`, nằm trong `logs/monday/`, hay `logs/monday/pm/`... |
| **Dấu chấm than (`!`)** | `*.log`<br><br>`!important.log` | **Ngoại lệ (Đảo ngược quy tắc)**: Bỏ qua tất cả file `.log`, nhưng **giữ lại (không bỏ qua)** file `important.log`. |

#### Ký tự đặc biệt khác:
**Dấu thăng** (#): Dùng để viết chú thích (Comment), Git sẽ bỏ qua dòng này.

**Dấu gạch chéo ngược** (\):  Dùng để vô hiệu hóa ký tự đặc biệt. Ví dụ file của bạn tên chứa ngoặc vuông là foo[01].txt, bạn phải viết là: foo\[01\].txt.

### Ba cấp độ quản lý File Ignore trong Git
Bạn có thể cấu hình danh sách bỏ qua ở 3 nơi khác nhau tùy vào mục đích:

1. Shared .gitignore (Mức dự án - Khuyên dùng): Tạo file .gitignore ở thư mục gốc. File này được commit và đẩy lên GitHub để tất cả mọi người trong nhóm cùng dùng chung quy tắc.

1. Personal Ignore (.git/info/exclude - Mức cá nhân): File này nằm ẩn trong thư mục cấu hình .git của riêng máy bạn. Nó không được đẩy lên GitHub. Rất thích hợp để bạn viết các file rác phát sinh từ công cụ code riêng của cá nhân bạn mà không làm ảnh hưởng đến nhóm.

1. Global Ignore (Mức toàn cục): Áp dụng cho tất cả mọi dự án Git trên máy tính của bạn. Bạn cài đặt bằng cách:
```
touch ~/.gitignore
git config --global core.excludesFile ~/.gitignore
```

### Các kỹ thuật xử lý tình huống thực tế (Advanced Workflows)

**Tình huống 1**: Muốn ignore một file ĐÃ LỠ COMMIT trong quá khứ
```
# Thêm tên file vào .gitignore trước
echo "debug.log" >> .gitignore

# Xóa file khỏi bộ nhớ theo dõi của Git (nhưng giữ lại file gốc trên máy)
git rm --cached debug.log

# Commit lại để chốt hạ
git commit -m "Bắt đầu ignore file debug.log"
```

**Tình huống 2**: Ép Git phải commit một file đang bị cấm  
Nếu bạn có quy tắc chung là cấm *.log, nhưng bạn lại rất muốn commit một file log đặc biệt tên là debug.log.

Cách ép buộc bằng bạo lực: Dùng tham số -f (Force):
```
git add -f debug.log
```
**Cách chuyên nghiệp (Khuyên dùng)**: Mở file .gitignore ra và viết thêm một dòng ngoại lệ bằng dấu !:
```
*.log
!debug.log
```
Cách này giúp đồng đội của bạn khi đọc file .gitignore sẽ hiểu ngay lý do tại sao file đó được phép commit.

**Tình huống 3**: Gom cả file đang bị cấm vào git stash  
Mặc định, lệnh git stash (ngăn kéo tạm thời) chỉ cất các file đang được theo dõi (Tracked). Nếu bạn muốn hốt sạch sành sanh cả file mới tinh (Untracked) và các file đang bị cấm (Ignored) cất đi cho sạch máy, hãy dùng tham số --all:
```
git stash --all
```

#### Mẹo gỡ lỗi (Debug) khi .gitignore quá phức tạp

Khi dự án của bạn quá lớn, có nhiều file .gitignore lồng nhau và bạn không hiểu tại sao cái file debug.log của mình cứ bị Git cứng đầu bỏ qua (không add được).

Bạn hãy dùng lệnh kiểm tra ngầm sau:
```
git check-ignore -v debug.log
```
Màn hình sẽ trả về kết quả chính xác theo định dạng:
.gitignore : 3 : *.log debug.log

Ý nghĩa: File debug.log đang bị chặn bởi file .gitignore ở thư mục gốc, tại dòng số 3, do quy tắc *.log quy định. Biết được dòng nào rồi, bạn chỉ cần mở file ra sửa hoặc xóa dòng đó đi là xong!