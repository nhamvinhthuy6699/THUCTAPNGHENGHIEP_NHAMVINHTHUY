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
- Cấu hình cấp toàn cục là cấu hình dành riêng cho người dùng, nghĩa là nó được áp dụng cho người dùng hệ điều hành. Các giá trị cấu hình toàn cục được lưu trữ trong một tệp nằm trong thư mục chính của người dùng `C:\Users\<username>\.gitconfig` Windows.

#### --system
- Cấu hình cấp hệ thống được áp dụng trên toàn bộ máy tính. Điều này bao gồm tất cả người dùng trên hệ điều hành và tất cả các kho lưu trữ. Được lưu trữ ở `C:\ProgramData\Git\config`

### Thứ tự ưu tiên
--local => --global => --system. Có nghĩa là khi tìm kiếm 1 giá trị, nó sẽ bắt đầu từ level local tới level system.

#### Hiểu đơn giản:

--local là dành riêng cho dự án của mình, thư mục thường được lưu cùng với dự án (vd: D:\THUCTAPNGHENGHIEP_NHAMVINHTHUY\.git\config)  
--global riêng cho mình trên máy này, không phải dự án nhiều người ( ví dụ: trên máy đang sử dụng user của windows là thuyv thì khi đăng nhập vào user này thì sẽ sử dụng tài khoản của global này trên toàn bộ dự án nếu không có tài khoản local) (thường được lưu trong cùng thư mục user của windows vd: C:\Users\thuyv\.gitconfig)  
-- system chung cho cả máy (thường được lưu trong cùng dự án: C:\Program Files\Git\etc\gitconfig)  

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


## INSPECTING A REPOSITORY
### Kiểm tra mức độ Dự án (Project Level)
#### A. git log - Nhật ký dòng thời gian

Lệnh này hiển thị danh sách các commit ngược dòng thời gian (từ mới nhất đến cũ nhất). Nó cho bạn biết ai đã làm gì vào lúc nào trên toàn bộ dự án.

Bản chất: Git lội qua các con trỏ commit nối đuôi nhau bằng mã băm SHA-1 để dựng lại lịch sử.

Các lệnh chi tiết cần thuộc lòng:

#### Các lệnh git log phổ biến

| Lệnh | Mục đích sử dụng | Kết quả hiển thị |
|------|------------------|------------------|
| `git log` | Xem nhật ký mặc định. | Hiện đầy đủ Mã băm, Tác giả, Ngày giờ, Lời nhắn. |
| `git log --oneline` | Xem lịch sử rút gọn. | Mỗi commit hiển thị trên 1 dòng gồm 7 ký tự đầu mã băm và tiêu đề lời nhắn. Rất dễ nhìn. |
| `git log -n <số>` | Giới hạn số lượng commit. | Chỉ hiển thị đúng `<số>` commit gần nhất (Ví dụ: `git log -n 5`). |
| `git log --p <tên_file>` | Xem lịch sử của file. | Hiển thị các commit có tác động đến file này, kèm chi tiết code bị sửa bên trong. |
| `git log --graph --oneline --all` | Vẽ sơ đồ nhánh. | Hiển thị dòng thời gian dạng đồ thị nhánh (nhìn rõ các nhánh rẽ và gộp vào nhau). |


### Kiểm tra mức độ Thư mục & Hàng chờ (Index Level)

#### A. git status - Gương soi trạng thái
Lệnh này kiểm tra sự sai lệch dữ liệu giữa Thư mục làm việc (màn hình code), Hàng chờ Staging Area và Commit gần nhất (HEAD).

Các trạng thái file Git trả về:

Changes to be committed: File đã nằm trong Staging Area (màu xanh), sẵn sàng để commit.

Changes not staged for commit: File cũ có sửa đổi nhưng chưa gõ git add (màu đỏ).

Untracked files: File mới tinh chưa từng khai báo với Git (màu đỏ).

#### B. git diff - Kính hiển vi soi ký tự
Dùng để so sánh chi tiết nội dung văn bản giữa các trạng thái dữ liệu.

Quy trình đọc hiểu thông số diff thô:

--- a/file.txt: Trạng thái cũ (Gắn dấu trừ -, chữ màu đỏ là code bị xóa).

+++ b/file.txt: Trạng thái mới (Gắn dấu cộng +, chữ màu xanh là code được thêm).

@@ -34,6 +34,8 @@: Đoạn code thay đổi bắt đầu từ dòng 34 của file cũ (kéo dài 6 dòng) và biến thành dòng 34 của file mới (kéo dài 8 dòng).

#### Các lệnh nâng cao của git diff:

git diff: Xem những gì vừa gõ thêm trên màn hình nhưng chưa git add.

git diff --staged (hoặc --cached): Xem những gì đã git add thành công để chuẩn bị commit.

git diff branch1..branch2: So sánh ngọn mới nhất của 2 nhánh.

git diff branch1...branch2: Tìm điểm chung lúc mới tách nhánh để xem từ đó đến nay branch2 đã viết thêm những gì.

## Git tag
Trong Git, lịch sử dự án là một chuỗi các commit nối tiếp nhau trên một dòng thời gian. Lệnh git tag được dùng để đánh dấu (dán nhãn) một commit cụ thể nào đó được coi là một cột mốc quan trọng trong lịch sử của dự án.

Thông thường, lập trình viên sử dụng tag để đánh dấu các điểm phát hành phiên bản phần mềm (ví dụ: v1.0.0, v2.0.0).

### Điểm khác biệt cốt lõi: Git Tag vs Git Branch (Nhánh)
Rất nhiều người nhầm lẫn giữa Tag và Nhánh vì cả hai đều trỏ đến một commit cụ thể. Tuy nhiên, bản chất của chúng hoàn toàn khác nhau:

**Nhánh (Branch) là ĐỘNG**: Khi bạn đang ở nhánh main và bạn tạo một commit mới, ngọn của nhánh main sẽ tự động nhảy tiến lên để ôm lấy commit mới đó.

**Tag là TĨNH (Bất biến)**: Một khi bạn đã dán nhãn (tag) vào một commit, nó sẽ đứng yên tại commit đó mãi mãi. Cho dù dự án có phát triển thêm hàng nghìn commit phía sau, cái tag đó vẫn nằm im tại vị trí lịch sử cũ. Nó hoạt động như một lịch sử tham chiếu cố định.

### 2 loại tag trong Git
Git phân chia tag làm hai loại dựa trên lượng dữ liệu và thông tin đi kèm mà bạn muốn lưu trữ:

**A. Annotated Tags (Tag có chú thích - Khuyên dùng)**
Loại tag này được lưu trữ dưới dạng một đối tượng đầy đủ (full object) trong cơ sở dữ liệu của Git. Nó lưu lại rất nhiều siêu dữ liệu (metadata) bảo mật bao gồm:

Tên của người gắn tag.

Email người gắn tag.

Ngày giờ chính xác khi tạo tag.

Một lời nhắn giải thích (tương tự như commit message).

Có thể được ký xác thực bằng GPG (GNU Privacy Guard) để đảm bảo tính chính danh.

**Khi nào dùng?** Luôn luôn sử dụng Annotated Tag cho các cột mốc phát hành chính thức (Public Releases) của dự án để đảm bảo tính minh bạch.

**B. Lightweight Tags (Tag rút gọn / Tag nhẹ)**
Loại tag này thực chất chỉ là một con trỏ (pointer) trỏ thẳng đến mã băm SHA-1 của một commit cụ thể, ngoài ra không lưu thêm bất kỳ thông tin nào khác. Nó giống như một cái nhãn dán tạm thời (bookmark) tự chế.

**Khi nào dùng?** Sử dụng cho các mục đích thử nghiệm nội bộ, đánh dấu nhanh một vị trí code trên máy cá nhân để lát nữa quay lại tìm cho dễ.

### Toàn bộ câu lệnh Git tag thực tế
#### Xem danh sách các tag đang có
```
git tag
```
Nếu dự án có quá nhiều tag, bạn có thể lọc tìm kiếm bằng ký tự đại diện (*). Ví dụ, muốn tìm tất cả các tag thuộc phiên bản đầu v1.x:
```
git tag -l "v1.0*"
```
### Tạo một Tag mới (Dán nhãn cho hiện tại)
Mặc định khi bạn gõ lệnh tạo tag, Git sẽ dán nhãn lên cú commit hiện tại nơi bạn đang đứng (HEAD).

Tạo Annotated Tag (Đầy đủ): Dùng tham số -a và -m:
```
git tag -a v1.0.0 -m "Phát hành phiên bản 1.0.0 chính thức"
```
Tạo Lightweight Tag (Rút gọn): Chỉ viết tên tag:
```
git tag v1.0.0-beta
```
### Xem thông tin chi tiết của một Tag
```
git show v1.0.0
```
Nếu là Annotated Tag: Git sẽ in ra thông tin người tạo, ngày tháng, lời nhắn tag, rồi mới đến thông tin chi tiết của cú commit bên dưới.

Nếu là Lightweight Tag: Git chỉ hiển thị thông tin của cú commit được trỏ tới.

### Tagging old commits

- Nếu dự án đã chạy qua thêm vài commit rồi bạn mới chợt nhớ ra phải dán nhãn cho một cú commit từ hôm qua, hãy dùng git log --oneline lấy mã băm rút gọn (Commit ID) của commit đó rồi truyền vào cuối lệnh:
```
$ git log --pretty=oneline
    15027957951b64cf874c3557a0f3547bd83b3ff6 Merge branch 'feature'
    a6b4c97498bd301d84096da251c98a07c7723e65 add update method for thing
    0d52aaab4479697da7686c15f77a3d64d9165190 one more thing
    6d52a271eda8725415634dd79daabbc4d9b6008e Merge branch 'experiment'
```
Lúc này viết Tag vào:
```
git tag -a v1.2 15027957951b64cf874c3557a0f3547bd83b3ff6
```
### ReTagging/Replacing old tags
- Nếu bạn đã có tên tag đó rồi nhhungw lại muốn viêt lên dự án mới, nó sẽ báo lỗi 
```
fatal: tag 'v0.4' already exists
```
- Lúc này, bắt buộc phải thêm tham số bắt buộc phải thêm tham số -f (hoặc --force):
```
git tag -a -f v1.4 15027957951b64cf874c3557a0f3547bd83b3ff6
```
- Lệnh này sẽ ép buộc Git đem nhãn v1.4 (loại Annotated) đi dán thẳng vào cú commit có mã băm dài ngoằng kia, xóa sạch mọi liên kết cũ của nhãn v1.4 trước đó.

### Sharing: Pushing tags to remote
- Việc chia sẻ Tag với cả nhóm có cơ chế gần giống như việc bạn đẩy một cái nhánh (branch) lên mạng.
- **Quy tắc vàng:** Theo mặc định, lệnh git push thông thường KHÔNG tự động đẩy các Tag lên mạng. Bạn bắt buộc phải chỉ định rõ ràng:  

#### Đẩy một cái Tag duy nhất:
```
git push origin v1.4
```
- Màn hình sẽ hiển thị thông báo thành công
```
$ git push origin v1.4
    Counting objects: 14, done.
    Delta compression using up to 8 threads.
    Compressing objects: 100% (12/12), done.
    Writing objects: 100% (14/14), 2.05 KiB | 0 bytes/s, done.
    Total 14 (delta 3), reused 0 (delta 0)
    To git@bitbucket.com:atlasbro/gittagdocs.git
     * [new tag]         v1.4 -> v1.4
```
- Màn hình sẽ hiển thị thông báo thành công: * [new tag] v1.4 -> v1.4.
#### Đẩy hàng loạt Tag cùng lúc:
```
git push origin --tags
```
- Khi đồng nghiệp của bạn thực hiện lệnh git clone hoặc git pull để tải code về, máy của họ sẽ tự động nhận được toàn bộ các Tag mới này từ server.

### Checking out tags
- Nếu bạn muốn xem lại trạng thái của toàn bộ dự án tại thời điểm phiên bản v1.4 trông như thế nào, bạn dùng lệnh:
```
git checkout v1.4
```
- Khi chạy lệnh trên, bạn sẽ bị dưa vào tình trạng Detached HEAD
- **Cơ chế:** Con trỏ HEAD (vị trí mắt bạn đang nhìn) bị rút ra khỏi các nhánh động và chỉ cắm thẳng vào đúng cú commit của Tag v1.4 mà thôi.
- **Hệ quả:** Bất kỳ thay đổi hoặc commit nào bạn tạo ra tại đây **sẽ không cập nhật vào Tag**. Chúng sẽ sinh ra một commit "mồ côi" biệt lập. Commit mồ côi này không thuộc về bất kỳ một nhánh nào cả, và bạn chỉ có thể tìm lại nó nếu nhớ chính xác mã băm SHA của nó. Khi bạn checkout sang nhánh khác, commit mồ côi này sẽ bị Git xóa bỏ vĩnh viễn.
```
git checkout -b new_branch v1.4
```
### Deleting tags
- Thao tác xóa tag rất đơn giản và gọn gàng. Bạn chỉ cần truyền tham số -d (Delete) cùng với tên của Tag muốn gỡ bỏ:
```
# Bước 1: Xem danh sách tag hiện tại (Ví dụ có: v1, v2, v3)
$ git tag

# Bước 2: Tiến hành xóa tag v1
$ git tag -d v1

# Bước 3: Kiểm tra lại xem mất chưa (Chỉ còn v2, v3)
$ git tag
```
## Git blame
- Git blame là 1 tiện ích để khắc phục sự cốlinh hoạt và nhiều tùy chọn mở rộng
- Git blame dùng để hiển thị siêu dữ liệu của tác giả đã được gắn kèm vào dòng code hay commit cụ thể. Chủ yếu để kiểm tra xem ai đã thay đổi những gì trong dòng code đó tại thời điểm nào.Điều này giúp khám phá lịch sử của một đoạn code cụ thể và trả lời các câu hỏi về cái gì, như thế nào, và tại sao đoạn code đó lại được thêm vào kho chứa. 

- git blame thường được sử dụng kết hợp với một giao diện hiển thị đồ họa (GUI). Các trang lưu trữ Git trực tuyến như Bitbucket cung cấp các chế độ xem blame (blame views) – thực chất là các lớp giao diện bọc ngoài lệnh git blame. Các chế độ xem này thường được trỏ tới trong các cuộc thảo luận nhóm xoay quanh các Pull Request và các Commit. Ngoài ra, hầu hết các môi trường phát triển tích hợp (IDE) có tích hợp Git đều sở hữu các chế độ xem blame động này.

### How it works
- Để minh họa, Cần có 1 kho chứa đã có lịch sử. Nên clone 1 dự án nào dó về:
```
git clone https://kevzettler@bitbucket.org/kevzettler/git-blame-example.git && cd git-blame-example
```
- Có thể kiểm tra trước kho chứa này bằng lệnh git log. Lịch sử commit sẽ như thế này:
```
$ git log
    commit 548dabed82e4e5f3734c219d5a742b1c259926b23
    Author: Juni Mukherjee <jmukherjee@atlassian.com>
    Date:   Thu Mar 1 19:55:15 2018 +0000

        Another commit to help git blame track the who, the what, and the when

    commit eb06faedb1fdd159d62e4438fc8dbe9c9fe0728b
    Author: Juni Mukherjee <jmukherjee@atlassian.com>
    Date:   Thu Mar 1 19:53:23 2018 +0000

        Creating the third commit, along with Kev and Albert, so that Kev can get git blame docs.

    commit 990c2b6a84464fee153253dbf02e845a4db372bb
    Merge: 82496ea 89feb84
    Author: Albert So <aso@atlassian.com>
    Date:   Thu Mar 1 05:33:01 2018 +0000

        Merged in albert-so/git-blame-example/albert-so/readmemd-edited-online-with-bitbucket-1519865641474 (pull request #2)

        README.md edited online with Bitbucket

    commit 89feb84d885fe33d1182f2112885c2a64a4206ec
    Author: Albert So <aso@atlassian.com>
    Date:   Thu Mar 1 00:54:03 2018 +0000

        README.md edited online with Bitbucket
```
- **Lưu ý:** git blame chỉ hoạt động trên 1 file đơn lẻ, bắt buộc phải truyền 1 đường dẫn file (file-path) thì lệnh mới trả về kết quả hữu ích. Ví dụ, chúng ta sẽ thao tác trên readme.md
```
git blame README.md
```
-Thực thi lệnh trên sẽ trả về mẫu kết quả đầu ra đầu tiên của lệnh blame.
```
$ git blame README.md
    82496ea3 (kevzettler     2018-02-28 13:37:02 -0800  1) # Git Blame example
    82496ea3 (kevzettler     2018-02-28 13:37:02 -0800  2)
    89feb84d (Albert So      2018-03-01 00:54:03 +0000  3) This repository is an example of a project with multiple contributors making commits.
    82496ea3 (kevzettler     2018-02-28 13:37:02 -0800  4)
    82496ea3 (kevzettler     2018-02-28 13:37:02 -0800  5) The repo use used elsewhere to demonstrate `git blame`
    82496ea3 (kevzettler     2018-02-28 13:37:02 -0800  6)
    89feb84d (Albert So      2018-03-01 00:54:03 +0000  7) Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod TEMPOR incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum
    89feb84d (Albert So      2018-03-01 00:54:03 +0000  8)
    eb06faed (Juni Mukherjee 2018-03-01 19:53:23 +0000  9) Annotates each line in the given file with information from the revision which last modified the line. Optionally, start annotating from the given revision.
    eb06faed (Juni Mukherjee 2018-03-01 19:53:23 +0000 10)
    548dabed (Juni Mukherjee 2018-03-01 19:55:15 +0000 11) Creating a line to support documentation needs for git blame.
    548dabed (Juni Mukherjee 2018-03-01 19:55:15 +0000 12)
    548dabed (Juni Mukherjee 2018-03-01 19:55:15 +0000 13) Also, it is important to have a few of these commits to clearly reflect the who, the what and the when. This will help Kev get good screenshots when he runs the git blame on this README.
```
-Đây là mẫu hiển thị của 13 dòng đầu tiên trong file README.md. Để hiểu rõ hơn về kết quả này, hãy cùng bẻ tách phân tích chi tiết cấu trúc dữ liệu của Dòng số 3 thông qua bảng sau:
### Thông tin Commit

1. **ID (Mã commit):** `89feb84d`  
1. **Author (Tác giả):** Albert So  
1. **Timestamp (Thời gian):** 2018-03-01 00:54:03 +0000  
1. **Line Number (Số dòng):** 3  
1. **Line Content (Nội dung dòng code):**  


- Khi nhìn vào danh sách kết quả blame này, chúng ta có thể đưa ra một vài quan sát. Có ba tác giả được liệt kê: bên cạnh người quản trị dự án là Kev Zettler, còn có sự xuất hiện của Albert So và Juni Mukherjee. Cột Tác giả (Author) thường là phần thông tin có giá trị nhất trong kết quả của git blame. Cột Thời gian (Timestamp) đóng vai trò bổ trợ và những gì đã bị thay đổi sẽ được chỉ rõ ở cột Nội dung dòng code.

### Common options
#### Giới hạn khoảng dòng hiển thị
```
git blame -L 1,5 README.md
```
- Yêu cầu phạm vi dòng được yêu cầu. Ở đây chỉ hiển thị từ dòng 1 tới dòng 5.
#### Hiển thị địa chỉ Email
```
git blame -e README.md
```
- Tùy chọn -e sẽ hiển thị địa chỉ email của tác giả thay vì hiển thị tên người dùng (username).
#### Bỏ qua khoảng trắng (Whitespace)
```
git blame -w README.md
```
- Tùy chọn -w sẽ bỏ qua các thay đổi liên quan đến khoảng trắng. Nếu một tác giả trước đó chỉ sửa đổi định dạng thụt lề của file bằng cách chuyển từ tab sang dấu cách hoặc thêm các dòng trống mới, việc này vô tình làm sai lệch kết quả của git blame. Tham số -w sẽ giúp lọc bỏ các thay đổi hình thức này.
#### Phát hiện các dòng bị di chuyển trong cùng một file
```
git blame -M README.md
```
- Tùy chọn -M giúp phát hiện các dòng code bị di chuyển vị trí hoặc sao chép trong cùng một file. Nó sẽ truy vết và báo cáo lại tên của tác giả gốc đầu tiên viết đoạn code đó, thay vì báo cáo tên của người cuối cùng chỉ làm thao tác di chuyển vị trí đoạn code.
#### Phát hiện các dòng bị sao chép từ file khác sang
```
git blame -C README.md
```
- Tùy chọn -C giúp phát hiện các dòng code được di chuyển hoặc sao chép từ các file khác sang file hiện tại. Lệnh này cũng sẽ báo cáo chính xác tác giả gốc ban đầu của đoạn code thay vì người thực hiện hành động sao chép.

### Git blame vs git log
- Mặc dù git blame hiển thị tác giả cuối cùng sửa đoạn code đó, nhưng nhiều lúc bạn sẽ muốn biết dòng code đó được thêm vào lần đầu tiên từ bao giờ.Việc tìm kiếm điều này bằng lệnh git blame đơn thuần sẽ khá cồng kềnh vì đòi hỏi bạn phải kết hợp đồng thời các tham số -w, -C, và -M. Trong tình huống này, sử dụng lệnh git log sẽ tiện lợi hơn rất nhiều.

- Để liệt kê tất cả các commit gốc mà tại đó một đoạn code cụ thể được thêm vào hoặc sửa đổi, hãy thực thi git log với tùy chọn -S. Hãy đính kèm đoạn code bạn muốn tìm kiếm ngay sau tham số -S. Ví dụ, chúng ta sẽ lấy một đoạn văn bản "CSS3D and WebGL renderers." nằm ở dòng số 12 của file README để làm mẫu tìm kiếm:
```
$ git log -S"CSS3D and WebGL renderers." --pretty=format:'%h %an %ad %s'
    e339d3c85 Mario Schuettel Tue Oct 13 16:51:06 2015 +0200 reverted README.md to original content
    509c2cc35 Daniel Tue Sep 8 13:56:14 2015 +0200 Updated README
    cb20237cc Mr.doob Mon Dec 31 00:22:36 2012 +0100 Removed DOMRenderer. Now with the CSS3DRenderer it has become irrelevant.
```
- Kết quả đầu ra này cho chúng ta thấy nội dung tìm kiếm trong file README đã được thêm hoặc sửa đổi 3 lần bởi 3 tác giả khác nhau. Đoạn code này thực chất được thêm vào đầu tiên trong commit cb20237cc bởi tác giả Mr.doob. Trong ví dụ này, lệnh git log cũng đã được bổ sung thêm tùy chọn --pretty=format để chuyển đổi định dạng hiển thị mặc định của nhật ký log sang định dạng tùy chỉnh gọn gàng hơn.

## Undoing Commits & Changes
- Về bản chất, Git là 1 công cụ quản lý thời gian. Các commit chính là đơn vị khối xây dựng cốt lõi của dòng thời gian trong một dự án Git. Commit có thể được coi là những snapshots hoặc các milestones dọc theo dòng thời gian của dự án. Các commit được tạo ra bằng lệnh git commit nhằm đóng băng và ghi trạng thái của dự án tại thời điểm đó.
- Tài liệu này chia quy trình hủy bỏ thay đổi thành 2 nhóm giải pháp chính:
1. Khám phá các commit cũ để xem lại lịch sử. 
1. Phân biệt rõ ràng giữa việc Revert (Hoàn tác các commit đã đẩy lên mạng công khai) và Reset (Xóa bỏ các thay đổi chưa xuất bản dưới máy cục bộ).

### Finding what is lost: Reviewing old commits
- Ý tưởng cốt lõi của bất kỳ hệ thống quản lý phiên bản nào là lưu trữ các bản sao "an toàn" của dự án để bạn không bao giờ phải lo lắng về việc code của mình bị hỏng đến mức không thể cứu vãn. Một khi bạn đã xây dựng được một chuỗi lịch sử, bạn có thể xem lại bất kỳ commit nào trong quá khứ thông qua lệnh git log.
```
git log --oneline
e2f9a78fe Replaced FlyControls with OrbitControls
d35ce0178 Editor: Shortcuts panel Safari support.
9dbe8d0cf Editor: Sidebar.Controls to Sidebar.Settings.Shortcuts. lean up.
05c5288fc Merge pull request #12612 from TyLindberg/editor-controls-panel
0d8b6e74b Merge pull request #12805 from harto/patch-1
23b20c22e Merge pull request #12801 from gam0022/improve-raymarching-example-v2
fe78029f1 Fix typo in documentation
7ce43c448 Merge pull request #12794 from WestLangley/dev-x
17452bb93 Merge pull request #12778 from OndrejSpanel/unitTestFixes
b5c1b5c70 Merge pull request #12799 from dhritzkiv/patch-21
1b48ff4d2 Updated builds.
88adbcdf6 WebVRManager: Clean up.
2720fbb08 Merge pull request #12803 from dmarcos/parentPoseObject
9ed629301 Check parent of poseObject instead of camera
219f3eb13 Update GLTFLoader.js
15f13bb3c Update GLTFLoader.js
6d9c22a3b Update uniforms only when onWindowResize
881b25b58 Update ProjectionMatrix on change aspect
```
- Bạn có thể sử dụng git checkout để quay về xem cú commit 
- **Lưu ý:** Mặc định, git log chỉ hiển thị các commit của nhánh bạn đang đứng. Nếu commit bạn tìm nằm ở nhánh khác, hãy gõ git log --branches=* để xem tất cả các nhánh. Lệnh git branch -a sẽ liệt kê toàn bộ các nhánh đang có trong hệ thống.

### Viewing an old revision
- Giả sử đang tiến hành một thử nghiệm viết code rất điên rồ, nhưng gõ được một lúc thì phân vân không biết có nên giữ lại đoạn code này không. Bạn muốn quay về xem trạng thái dự án trước khi cuộc thử nghiệm bắt đầu.

Lịch sử git log --oneline của bạn đang như thế này:
```
b7119f2 Continue doing crazy things (Đang thử nghiệm điên rồ)
872fa7e Try something crazy
a1e8fb5 Make some important changes to hello.txt (Mốc an toàn)
435b61d Create hello.txt
9773e52 Initial import
```
Để quay về mốc an toàn a1e8fb5, bạn gõ:
```
git checkout a1e8fb5
```
- Lệnh này sẽ làm cho thư mục làm việc của bạn biến đổi để khớp chính xác 100% với trạng thái của commit a1e8fb5. Bạn có thể thoải mái xem file, biên dịch dự án, chạy thử nghiệm, thậm chí sửa file mà không phải lo lắng về việc làm hỏng trạng thái hiện tại của dự án. Không có bất kỳ điều gì bạn làm trong trạng thái này được lưu lại vào kho chứa của bạn.
- Để tiếp tục phát triển code ở hiện tại, bạn cần phải quay trở lại trạng thái "mới nhất" của dự án:
```
git checkout main
```
### Undoing a committed snapshot
Chúng ta sẽ tiếp tục sử dụng đoạn lịch sử log ở ví dụ trên và tập trung vào việc hủy bỏ cú commit 872fa7e Try something crazy

#### Cách 1: Hủy commit bằng git checkout (Rẽ nhánh mới)
- Từ trạng thái đang ở commit cũ a1e8fb5 (sau khi chạy lệnh git checkout a1e8fb5), hệ thống của bạn sẽ rơi vào chế độ Detached HEAD (Không thuộc nhánh nào). Từ đây, bạn có thể thực thi lệnh:
```
git checkout -b new_branch_without_crazy_commit
```
- Lệnh này sẽ tạo ra một nhánh mới mang tên new_branch_without_crazy_commit và lập tức chuyển sang nhánh đó. Kho chứa của bạn bây giờ đã nằm trên một dòng thời gian lịch sử mới – nơi mà cú commit lỗi 872fa7e hoàn toàn không tồn tại. Bạn có thể tiếp tục công việc trên nhánh mới này và coi như commit lỗi đã được "hủy bỏ".

- Tuy nhiên, nếu bạn bắt buộc phải làm việc trên nhánh cũ (ví dụ đó là nhánh chính main của bạn), thì chiến lược hủy bỏ này hoàn toàn không phù hợp.

#### Cách 2: Hủy commit công khai bằng git revert
- Quay trở lại với lịch sử gốc ban đầu (có chứa commit lỗi 872fa7e). Lần này chúng ta sẽ thử dùng giải pháp đảo ngược. Nếu bạn thực thi lệnh:
```
git revert HEAD
```
- Git sẽ tự động tính toán dữ liệu và tạo ra một commit mới tinh có nội dung hoàn toàn nghịch đảo (trái ngược) so với commit gần nhất của bạn. Lịch sử trên nhánh hiện tại của bạn sẽ được nối dài và trông giống như thế này:
```
e2f9a78 Revert "Try something crazy"
872fa7e Try something crazy
a1e8fb5 Make some important changes to hello.txt
435b61d Create hello.txt
9773e52 Initial import
```
- Tại thời điểm này, về mặt kỹ thuật bạn đã "hủy bỏ" thành công commit 872fa7e. Mặc dù mốc 872fa7e vẫn tồn tại trong lịch sử, nhưng commit mới e2f9a78 đã triệt tiêu toàn bộ các thay đổi của nó. Khác với chiến lược dùng lệnh checkout ở trên, bạn có thể tiếp tục sử dụng trên chính cái nhánh cũ này.

 - * Lời khuyên phối hợp nhóm: Đây là phương pháp "undo" lý tưởng nhất khi làm việc với các kho chứa công khai, được chia sẻ chung với nhiều người (Public/Shared Repositories). Tuy nhiên, nếu bạn có yêu cầu khắt khe về việc phải giữ cho lịch sử Git luôn ngắn gọn và được sàng lọc tối giản, chiến lược này có thể sẽ không làm bạn hài lòng. 

 #### Cách 3: Hủy commit bằng git reset (Xóa sổ lịch sử)
 - Đối với chiến lược hủy bỏ này, chúng ta tiếp tục với ví dụ đang làm dở. Lệnh git reset là một lệnh mở rộng có rất nhiều công dụng và chức năng. Nếu bạn thực thi câu lệnh:
 ```
 git reset --hard a1e8fb5
 ```
 - Dòng thời gian lịch sử commit của bạn sẽ lập tức bị kéo giật lùi về đúng cái commit được chỉ định đó. Kiểm tra lại lịch sử bằng git log, kết quả sẽ chỉ còn lại thế này:
 ```
 a1e8fb5 Make some important changes to hello.txt
435b61d Create hello.txt
9773e52 Initial import
 ```
 - Kết quả hiển thị cho thấy hai commit e2f9a78 và 872fa7e không còn tồn tại trong lịch sử commit nữa. Tại thời điểm này, bạn có thể tiếp tục làm việc và tạo ra các commit mới như thể cú commit "điên rồ" kia chưa từng xảy ra trên đời.
 - - Phương pháp hủy bỏ thay đổi này mang lại hiệu quả sạch sẽ nhất cho lịch sử dự án. Việc thực hiện một cú reset là điều tuyệt vời đối với các thay đổi nội bộ cá nhân (Local), tuy nhiên nó sẽ gây ra những biến chứng phức tạp khi bạn làm việc với một kho chứa chung trên mạng (Shared Remote Repository). Nếu kho chứa chung trên mạng đã lỡ nhận cú commit 872fa7e do bạn đẩy lên trước đó, và bây giờ bạn cố gắng chạy lệnh git push một cái nhánh mà bạn đã xóa lịch sử bằng lệnh reset, Git sẽ phát hiện ra điều này và chặn lại kèm theo thông báo lỗi. Git sẽ cho rằng nhánh bạn đang cố đẩy lên mạng đang bị lỗi thời vì nó bị thiếu hụt các commit so với máy chủ. Trong những kịch bản làm việc nhóm như thế này, git revert bắt buộc phải là phương pháp undo được ưu tiên sử dụng.

 ## Git clean
 - Lệnh git clean ở một góc độ nào đó có thể được coi là một lệnh "hủy bỏ" (undo). Nó đóng vai trò bổ trợ cho các lệnh khác như git reset và git checkout. Trong khi các lệnh vừa nêu hoạt động trên các file đã được đưa vào hàng chờ theo dõi (Git tracking index) từ trước, thì lệnh git clean lại chuyên trị các file chưa được theo dõi (untracked files). File chưa theo dõi là những file đã được tạo ra bên trong thư mục làm việc (working directory) của kho chứa nhưng chưa từng được khai báo bằng lệnh git add.

Để hình dung rõ hơn sự khác biệt giữa file được theo dõi (tracked) và chưa được theo dõi (untracked), hãy cùng xem ví dụ dòng lệnh dưới đây:
```
$ mkdir git_clean_test
$ cd git_clean_test/
$ git init .
Initialized empty Git repository in /Users/kev/code/git_clean_test/.git/
$ echo "tracked" > ./tracked_file
$ git add ./tracked_file
$ echo "untracked" > ./untracked_file
$ mkdir ./untracked_dir && touch ./untracked_dir/file
$ git status
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   tracked_file

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	untracked_dir/
	untracked_file
```
- Ví dụ trên khởi tạo một kho chứa Git mới tinh trong thư mục git_clean_test. Sau đó, nó tiến hành tạo file tracked_file và đưa vào hàng chờ Git Index bằng lệnh git add. Tiếp theo, một file untracked_file và một thư mục untracked_dir được tạo ra nhưng không gõ git add. Khi chạy git status, Git hiển thị rõ ràng trạng thái ngầm bên trong của hai nhóm file này.

- Bây giờ, nếu chúng ta cố tình chạy lệnh git clean ở trạng thái này, một lỗi nghiêm trọng (fatal error) sẽ xảy ra:
```
$ git clean
fatal: clean.requireForce defaults to true and neither -i, -n, nor -f given; refusing to clean
```
#### Cơ chế bảo vệ của Git
- Mặc định, Git được cấu hình toàn cục để bắt buộc người dùng phải truyền vào một tham số "ép buộc" (force) thì lệnh git clean mới chịu chạy. Đây là một cơ chế an toàn cực kỳ quan trọng. Khi đã thực thi hoàn tất, hành động của git clean là KHÔNG THỂ CỨU VÃN. Nó sẽ thực hiện một cú xóa cứng trực tiếp trên ổ cứng hệ thống (filesystem deletion), tương tự như khi bạn gõ lệnh rm trong Linux hay Terminal. Hãy chắc chắn rằng bạn thực sự muốn xóa bỏ các file rác đó trước khi kích hoạt lệnh.

### Common options and usage
- Dưới đây là các kịch bản sử dụng thực tế của git clean đi kèm với các tham số dòng lệnh tương ứng:

#### -n (Chạy thử nghiệm - Dry Run)

- Tham số -n sẽ thực hiện một cú "chạy thử" ngầm. Git sẽ liệt kê ra những file nào sẽ bị xóa sạch nếu lệnh thực thi thật, nhưng hoàn toàn chưa xóa gì cả.
- Luôn luôn chạy thử nghiệm với -n trước khi gõ lệnh xóa thật để kiểm tra.
```
git clean -n
Would remove untracked_file
```
- Kết quả báo rằng file untracked_file sẽ bị xóa. Hãy lưu ý rằng thư mục untracked_dir không hề xuất hiện trong danh sách này. Theo mặc định, git clean sẽ không tự động quét sâu vào các thư mục con (không chạy đệ quy). Đây lại là một cơ chế an toàn khác nhằm ngăn chặn việc lỡ tay xóa mất cả một thư mục dữ liệu lớn.

#### -f hoặc --force (Ép buộc xóa file)
- Tham số này chính thức ra lệnh cho Git quét sạch các file chưa được theo dõi khỏi thư mục hiện tại. Force là bắt buộc, trừ khi bạn cấu hình lại thuộc tính hệ thống clean.requireForce thành false. Lệnh này mặc định không xóa các thư mục chưa được theo dõi, cũng như không đụng vào các file được quy định trong .gitignore.
```
$ git clean -f
Removing untracked_file
```
- Git thông báo file untracked_file đã bị xóa bỏ. Nếu bạn gõ git status hoặc ls tại thời điểm này, file đó đã bốc hơi hoàn toàn không để lại dấu vết.

- - Ngoài ra, bạn có thể truyền thêm đường dẫn vào -f để chỉ đích danh file muốn xóa chứ không xóa toàn bộ
```
git clean -f <path>
```

#### -d (Quét sạch cả thư mục con)
- Mặc định Git sẽ lờ các thư mục đi. Tham số -d ra lệnh cho git clean xử lý luôn cả các thư mục chưa được theo dõi. Bạn có thể kết hợp chung với các tham số khác:
```
# Chạy thử nghiệm kết hợp -dn
$ git clean -dn
Would remove untracked_dir/

# Thực thi xóa thật bằng -df
$ git clean -df
Removing untracked_dir/
```
#### -x (Xóa luôn cả các file nằm trong .gitignore)
- Trong quy trình phát triển phần mềm, chúng ta thường có các thư mục chứa file biên dịch, file build (như /bin, /out hoặc /target) tự sinh ra từ mã nguồn. Các thư mục này thường được đưa vào file .gitignore để không bị push lên mạng.

- Tuy nhiên, khi bạn muốn dọn sạch dự án về trạng thái nguyên bản lúc mới tải về, bạn sẽ muốn xóa luôn cả đống file build ẩn này. Tham số -x sẽ ép Git xóa sạch mọi file chưa theo dõi, bao gồm cả các file đang bị cấm bởi .gitignore.
```
git clean -xf
```

**Cảnh báo:** Tham số -x sẽ tác động lên tất cả các file bị ignore, bao gồm cả những file cấu hình cá nhân của phần mềm code (như thư mục .idea/ của IDE) mà có thể bạn không hề muốn làm mất. Hãy luôn chạy thử với git clean -xn trước.

### Interactive mode or git clean interactive
- Nếu bạn không muốn gõ lệnh một cách mù quáng, Git cung cấp một giao diện tương tác từng bước cực kỳ trực quan thông qua tham số -i (Interactive). Quay trở lại trạng thái kho chứa ban đầu, chúng ta kích hoạt chế độ này (có kèm thêm -d để quét cả thư mục):
```
$ git clean -di
Would remove the following items:
  untracked_dir/  untracked_file
*** Commands ***
    1: clean                2: filter by pattern    3: select by numbers    4: ask each             5: quit                 6: help
What now>
```
Hệ thống hiển thị danh sách các file sắp bị tác động và đưa ra một con trỏ lệnh What now>. Dưới đây là ý nghĩa chi tiết của từng lựa chọn:

-  quit: Thoát ngay lập tức khỏi chế độ tương tác mà không thay đổi hay xóa bất kỳ thứ gì.

- 6: help: Hiển thị menu hướng dẫn giải thích chi tiết tính năng của các phím bấm khác.

- 1: clean: Tiến hành xóa sạch toàn bộ danh sách các mục đang được hiển thị. (Nếu bấm 1, cả untracked_dir/ và untracked_file sẽ bay màu ngay).

- 4: ask each: Git sẽ lội qua từng file một và hiển thị một câu hỏi Xác nhận Có/Không (Y/N) trước khi quyết định xóa file đó (y hệt như lệnh rm -i của Linux).
```
What now> 4
Remove untracked_dir/ [y/N]? N
Remove untracked_file [y/N]? N
```
- 2: filter by pattern: Hiển thị thêm một con trỏ lệnh cho phép bạn gõ ký tự đại diện (wildcard) nhằm lọc bớt, giữ lại một số file không muốn xóa ra khỏi danh sách tử thần.
```
What now> 2
Input ignore patterns>> *_file
  untracked_dir/
```
(Trong ví dụ này, việc gõ *_file giúp loại trừ file có đuôi _file ra, danh sách xóa lúc này chỉ còn trơ trọi lại untracked_dir/).

- 3: select by numbers: Thay vì gõ chữ để lọc, bạn có thể gõ số thứ tự tương ứng với file được Git liệt kê để chọn đích danh xem muốn xử tử file nào.
```
Select items to delete>> 2
    1: untracked_dir/  * 2: untracked_file
Select items to delete>> [Bấm Enter để chốt]
Would remove the following item:
  untracked_file
  ```
(Dấu sao * xuất hiện bên cạnh số 2 báo hiệu file đó đã được chọn để xóa).

## Git revert
- Lệnh git revert có thể được coi là một lệnh thuộc kiểu "hủy bỏ" (undo), tuy nhiên, nó không phải là một thao tác hoàn tác truyền thống. Thay vì xóa bỏ cú commit khỏi lịch sử của dự án, lệnh này sẽ tính toán cách để nghịch đảo (trái ngược) các thay đổi được đưa vào bởi commit đó, rồi tạo thêm một commit mới tinh chứa nội dung đảo ngược này. Cơ chế này giúp Git không bị mất lịch sử dữ liệu, một điều tối quan trọng đối với tính toàn vẹn của lịch sử phiên bản và quy trình làm việc nhóm đáng tin cậy.

- Bạn nên sử dụng hành động revert khi muốn áp dụng những thay đổi trái ngược của một commit cụ thể trong lịch sử dự án. Lệnh này cực kỳ hữu ích trong trường hợp bạn đang truy vết một lỗi (bug) và phát hiện ra rằng nó được sinh ra từ đúng một commit duy nhất. Thay vì phải vào sửa code bằng tay một cách thủ công rồi commit một ảnh chụp mới, bạn có thể dùng git revert để hệ thống tự động làm toàn bộ các bước này cho bạn.
### How it works
- Lệnh git revert được sử dụng để hủy bỏ các thay đổi đối với lịch sử commit của một kho chứa. Các lệnh "undo" khác như git checkout và git reset hoạt động bằng cách di chuyển con trỏ HEAD và con trỏ nhánh (branch ref) về một commit được chỉ định. git revert cũng tiếp nhận một commit được chỉ định, tuy nhiên, git revert KHÔNG di chuyển các con trỏ tham chiếu về commit đó.

- Một thao tác revert sẽ lấy commit được chỉ định, đảo ngược các thay đổi của commit đó, và tạo ra một "commit đảo ngược" (revert commit) mới tinh. Sau đó, các con trỏ tham chiếu nhánh sẽ được cập nhật để trỏ vào chính cái commit đảo ngược mới này, biến nó thành ngọn mới nhất (tip) của nhánh.

Để minh họa, hãy cùng tạo một kho chứa ví dụ thông qua các dòng lệnh dưới đây:
```
$ mkdir git_revert_test
$ cd git_revert_test/
$ git init .
Initialized empty Git repository in /git_revert_test/.git/
$ touch demo_file
$ git add demo_file
$ git commit -am"initial commit"
[main (root-commit) 299b15f] initial commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 demo_file
$ echo "initial content" >> demo_file
$ git commit -am"add new content to demo file"
[main 3602d88] add new content to demo file
 1 file changed, 1 insertion(+)
$ echo "prepended line content" >> demo_file
$ git commit -am"prepend content to demo file"
[main 86bb32e] prepend content to demo file
 1 file changed, 1 insertion(+)
$ git log --oneline
86bb32e prepend content to demo file
3602d88 add new content to demo file
299b15f initial commit
```
- Tại đây, chúng ta đã khởi tạo một kho chứa trong một thư mục mới tạo tên là git_revert_test. Chúng ta tiến hành thực hiện 3 commit, trong đó chúng ta thêm file demo_file và sửa đổi nội dung của nó 2 lần. Cuối quy trình, chúng ta gọi lệnh git log để hiển thị lịch sử commit, kết quả trả về tổng cộng 3 commit. Với kho chứa ở trạng thái này, chúng ta đã sẵn sàng để kích hoạt một cú git revert:
```
$ git revert HEAD
[main b9cd081] Revert "prepend content to demo file"
 1 file changed, 1 deletion(-)
```
Lệnh git revert luôn bắt buộc bạn phải truyền vào một tham chiếu commit (commit ref) và sẽ từ chối chạy nếu thiếu thông tin này. Ở ví dụ trên, chúng ta truyền vào tham chiếu HEAD. Lệnh này sẽ tiến hành đảo ngược cú commit mới nhất hiện tại. Hành động này đem lại kết quả hoàn toàn tương tự như việc bạn chỉ đích danh mã băm commit 3602d88.

Gần giống như một thao tác gộp nhánh (merge), lệnh revert sẽ tạo ra một commit mới, do đó Git sẽ tự động mở trình soạn thảo văn bản mặc định của hệ thống để yêu cầu bạn nhập lời nhắn cho commit mới này (commit message). Một khi lời nhắn được nhập và lưu lại, Git sẽ hoàn tất quy trình. Bây giờ chúng ta kiểm tra lại trạng thái kho chứa bằng git log:
```
$ git log --oneline
1061e79 Revert "prepend content to demo file"
86bb32e prepend content to demo file
3602d88 add new content to demo file
299b15f initial commit
```
Hãy đặc biệt lưu ý rằng cú commit thứ 3 (86bb32e) vẫn nằm nguyên trong lịch sử dự án sau khi thực hiện lệnh revert. Thay vì xóa sổ nó, git revert đã ghi thêm một commit mới (1061e79) để triệt tiêu các thay đổi của nó. Hệ quả là, trạng thái code của commit thứ 2 (3602d88) và commit thứ 4 (1061e79) đại diện cho cùng một nền tảng code chính xác như nhau, trong khi commit thứ 3 vẫn được giữ lại trong lịch sử phòng trường hợp bạn muốn quay lại dùng nó ở chặng đường phía trước.

### Common options
1. **-e hoặc --edit**  
Đây là tùy chọn mặc định của hệ thống nên bạn không cần phải gõ chỉ định. Tùy chọn này sẽ tự động mở trình soạn thảo văn bản để bạn chỉnh sửa lời nhắn commit trước khi chính thức chốt cú commit revert.

1. **-- no-edit**  
Đây là tùy chọn đảo ngược của -e. Lệnh revert sẽ tự động thực thi và chốt commit mà không thèm mở trình soạn thảo văn bản lên nữa.

1. **-n hoặc --no-commit**  
Việc truyền thêm tham số này sẽ ngăn chặn git revert tự động tạo ra một cú commit mới. Thay vì tạo commit chốt hạ, tùy chọn này sẽ chỉ tính toán các thay đổi đảo ngược rồi đẩy toàn bộ chúng vào Khu vực hàng chờ (Staging Index) và Thư mục làm việc (Working Directory) của bạn (để hiển thị thành các file đỏ/xanh cho bạn tự tay kiểm tra hoặc sửa đổi tiếp trước khi tự commit bằng tay).
### Resetting vs. Reverting
Một điều cực kỳ quan trọng cần phải thấu hiểu là: git revert chỉ hủy bỏ duy nhất một commit đơn lẻ được chỉ định – nó hoàn toàn không "khôi phục" dự án quay về trạng thái cũ bằng cách xóa bỏ tất cả các commit thế hệ sau. Trong Git, hành động xóa bỏ hàng loạt commit phía sau để lùi về quá khứ được gọi là Reset, chứ không phải Revert. 

Lệnh Revert sở hữu hai ưu điểm vượt trội hoàn toàn so với lệnh Reset:
- Thứ nhất (An toàn cho làm việc nhóm): Nó hoàn toàn không làm thay đổi hay bóp méo lịch sử vốn có của dự án. Điều này biến nó trở thành một thao tác "an toàn tuyệt đối" đối với các commit đã được xuất bản (push) lên một kho chứa chung với đội nhóm.
- Thứ hai (Nhắm mục tiêu linh hoạt): Lệnh git revert có khả năng nhắm thẳng vào một commit đơn lẻ nằm ở bất kỳ vị trí tùy ý nào trong lịch sử, trong khi git reset chỉ có thể hoạt động bằng cách đi giật lùi từ commit hiện tại về sau. Ví dụ, nếu bạn muốn hủy một commit rất cũ bằng lệnh git reset, bạn sẽ buộc phải xóa sạch sành sanh toàn bộ các commit mới hơn được tạo ra sau commit đó, xóa commit lỗi, rồi sau đó mới tiến hành commit lại đống file mới kia. Đây rõ ràng là một giải pháp hoàn tác vô cùng vụng về và thiếu tinh tế.

## Git reset
Lệnh git reset là một công cụ phức tạp và đa năng để hủy bỏ các thay đổi. Nó có ba dạng kích hoạt chính, tương ứng với các tham số dòng lệnh: --soft, --mixed, và --hard. Ba tham số này lần lượt tác động trực tiếp đến ba cơ chế quản lý trạng thái nội bộ của Git, thường được gọi là Ba Cây (Three Trees) của Git: Cây Commit (HEAD), Hàng chờ Staging Index, và Thư mục làm việc (Working Directory).

### Git reset & three trees of git

Để hiểu đúng cách sử dụng git reset, trước tiên chúng ta phải hiểu hệ thống quản lý trạng thái nội bộ của Git. Đôi khi các cơ chế này được gọi là "ba cây" của Git. Gọi là "cây" thì có vẻ hơi sai thuật ngữ, vì chúng không hoàn toàn là cấu trúc dữ liệu cây (tree) truyền thống. Tuy nhiên, chúng là các cấu trúc dữ liệu dựa trên nút (node) và con trỏ (pointer) mà Git sử dụng để theo dõi dòng thời gian chỉnh sửa. Cách tốt nhất để chứng minh các cơ chế này là tạo ra một tập hợp thay đổi (changeset) trong kho chứa và theo dõi nó đi qua ba cây.

Để bắt đầu, chúng ta sẽ tạo một kho chứa mới bằng các câu lệnh dưới đây:

```
$ mkdir git_reset_test
$ cd git_reset_test/
$ git init .
Initialized empty Git repository in /git_reset_test/.git/
$ touch reset_lifecycle_file
$ git add reset_lifecycle_file
$ git commit -m"initial commit"
[main (root-commit) d386d86] initial commit
1 file changed, 0 insertions(+), 0 deletions(-)
create mode 100644 reset_lifecycle_file
```
Đoạn mã ví dụ trên tạo ra một kho chứa Git mới với một file trống duy nhất: reset_lifecycle_file. Tại thời điểm này, kho chứa ví dụ có một commit duy nhất (d386d86) từ việc thêm file này.

### 1. **The Working Directory**
Cây thư mục đầu tiên chúng ta sẽ xem xét là "Thư mục làm việc". Cây thư mục này đồng bộ với hệ thống tệp cục bộ và thể hiện những thay đổi tức thời được thực hiện đối với nội dung trong các tệp và thư mục.
```
$ echo 'hello git reset' > reset_lifecycle_file
$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   reset_lifecycle_file
```
- Trong kho chứa thử nghiệm, chúng ta sửa đổi và thêm một số nội dung vào reset_lifecycle_file. Việc gọi lệnh git status cho thấy Git đã nhận biết được các thay đổi đối với file. Những thay đổi này hiện đang là một phần của cây đầu tiên, "The Working Directory". Lệnh git status được dùng để hiển thị các thay đổi trong Working Directory. Chúng sẽ được hiển thị bằng màu đỏ với tiền tố 'modified'.

### 2. **Staging index**
Tiếp theo là cây "Staging Index". Cây này theo dõi các thay đổi từ Working Directory đã được thăng cấp bằng lệnh git add để chuẩn bị lưu vào commit tiếp theo. Cây này là một cơ chế bộ nhớ đệm (caching) nội bộ phức tạp. Git thường cố gắng ẩn các chi tiết triển khai của Staging Index khỏi người dùng.

Để xem chính xác trạng thái của Staging Index, chúng ta phải sử dụng một lệnh ít được biết đến là git ls-files. Lệnh git ls-files về cơ bản là một công cụ kiểm thử (debug) để kiểm tra trạng thái ngầm của cây Staging Index.
```
$ git ls-files -s
100644 e69de29bb2d1d6434b8b29ae775ad8c2e48c5391 0   reset_lifecycle_file
```
Ở đây chúng ta đã thực thi git ls-files với tùy chọn -s hoặc --stage. Nếu không có tùy chọn -s, kết quả đầu ra đơn giản chỉ là một danh sách tên file và đường dẫn hiện có trong index. Tùy chọn -s hiển thị thêm siêu dữ liệu (metadata) cho các file trong Staging Index. Siêu dữ liệu này là các bit chế độ của nội dung được stage, tên đối tượng (mã SHA-1), và số stage.

Ở đây chúng ta quan tâm đến tên đối tượng, giá trị thứ hai (e69de29...). Đây là mã băm SHA-1 chuẩn của Git cho nội dung của file. Lịch sử commit lưu trữ các mã SHA đối tượng của riêng nó để xác định các con trỏ tới các commit và tham chiếu, còn Staging Index có các mã SHA đối tượng của riêng nó để theo dõi các phiên bản của file trong index.

Tiếp theo, chúng ta sẽ đưa file reset_lifecycle_file đã sửa đổi vào Staging Index.

```
$ git add reset_lifecycle_file
$ git status
On branch main
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   reset_lifecycle_file
```
Tại đây chúng ta gọi lệnh git add reset_lifecycle_file để đưa file vào Staging Index. Gọi lệnh git status lúc này sẽ hiển thị file bằng màu xanh lá cây dưới mục "Changes to be committed". Một lưu ý quan trọng là git status không phải là đại diện thực sự của Staging Index. Đầu ra của lệnh git status chỉ hiển thị các thay đổi giữa Lịch sử Commit và Staging Index. Hãy cùng kiểm tra nội dung Staging Index tại thời điểm này:
```
$ git ls-files -s
100644 d7d77c1b04b5edd5acfc85de0b592449e5303770 0 reset_lifecycle_file
```
Chúng ta có thể thấy mã SHA đối tượng của reset_lifecycle_file đã được cập nhật từ e69de29... thành d7d77c1b04b5edd5acfc85de0b592449e5303770.

### 3. **Commit history**  
Cây cuối cùng là Commit History. Lệnh git commit thêm các thay đổi vào một ảnh chụp (snapshot) vĩnh viễn tồn tại trong Commit History. Ảnh chụp này cũng bao gồm trạng thái của Staging Index tại thời điểm commit.
```
$ git commit -am"update content of reset_lifecycle_file"
[main dc67808] update content of reset_lifecycle_file
 1 file changed, 1 insertion(+)
$ git status
On branch main
nothing to commit, working tree clean
```
Tại đây chúng ta đã tạo một commit mới với lời nhắn "update content of reset_lifecycle_file". Tập hợp thay đổi đã được ghi vào Commit History. Gọi git status lúc này cho thấy không còn thay đổi nào chờ xử lý ở bất kỳ cây nào nữa. Chạy lệnh git log sẽ hiển thị Lịch sử Commit. Bây giờ, sau khi đã theo dõi tập hợp thay đổi đi qua cả ba cây, chúng ta có thể bắt đầu sử dụng git reset.

### How it works
Ở bề mặt giao diện, git reset có hành vi khá giống với git checkout. Trong khi git checkout chỉ hoạt động duy nhất trên con trỏ tham chiếu HEAD, thì git reset sẽ di chuyển cả con trỏ HEAD lẫn con trỏ tham chiếu của nhánh hiện tại (current branch ref pointer). Để hình dung rõ hơn, hãy xem ví dụ sau:
Ví dụ này mô tả một chuỗi các commit trên nhánh main. Con trỏ HEAD và tham chiếu nhánh main hiện đang cùng trỏ vào commit d. Bây giờ chúng ta hãy thực thi và so sánh giữa git checkout b và git reset b:

- git checkout b: Tham chiếu nhánh main vẫn tiếp tục trỏ vào commit d. Chỉ có con trỏ HEAD bị di chuyển và bây giờ trỏ vào commit b. Kho chứa rơi vào trạng thái Detached HEAD.

- git reset b: Di chuyển cả hai con trỏ HEAD và tham chiếu nhánh main về commit được chỉ định (b).

Bên cạnh việc cập nhật các con trỏ tham chiếu commit, git reset còn sửa đổi trạng thái của ba cây nội bộ. Việc sửa đổi con trỏ tham chiếu luôn xảy ra (đây chính là cập nhật cây thứ 3 - Cây Commit). Các tham số dòng lệnh --soft, --mixed, và --hard sẽ điều hướng cách thức sửa đổi hai cây còn lại là Staging Index và Working Directory.  

### Main options
Mặc định, lệnh git reset nếu không viết gì thêm sẽ tự hiểu các tham số ẩn là --mixed và HEAD. Nghĩa là gõ git reset tương đương với gõ git reset --mixed HEAD. Thay vì HEAD, bất kỳ mã băm SHA-1 của commit nào cũng có thể được sử dụng làm mục tiêu. 

#### --hard
Đây là tùy chọn trực tiếp nhất, NGUY HIỂM nhất và được sử dụng thường xuyên nhất. Khi được truyền vào, --hard các con trỏ tham chiếu Lịch sử Commit sẽ được cập nhật thành commit được chỉ định. Sau đó, Chỉ mục Staging và Thư mục Làm việc sẽ được đặt lại để khớp với commit được chỉ định. Bất kỳ thay đổi nào đang chờ xử lý trước đó đối với Chỉ mục Staging và Thư mục Làm việc sẽ được đặt lại để khớp với trạng thái của Cây Commit. Điều này có nghĩa là bất kỳ công việc nào đang chờ xử lý trong Chỉ mục Staging và Thư mục Làm việc sẽ bị mất.  
Hãy tiếp tục với kho chứa ví dụ ở trên. Đầu tiên, chúng ta tạo ra vài thay đổi mới:
```
$ echo 'new file content' > new_file
$ git add new_file
$ echo 'changed content' >> reset_lifecycle_file
```
Lệnh này tạo file mới new_file và đưa vào hàng chờ, đồng thời sửa đổi nội dung reset_lifecycle_file nhưng chưa add. Hãy xem git status:
```
$ git status
On branch main
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   new_file

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   reset_lifecycle_file
```
Kiểm tra trạng thái Staging Index bằng lệnh debug:
```
$ git ls-files -s
100644 8e66654a5477b1bf4765946147c49509a431f963 0 new_file
100644 d7d77c1b04b5edd5acfc85de0b592449e5303770 0 reset_lifecycle_file  
```
Chúng ta thấy new_file đã nằm trong Index. File reset_lifecycle_file có thay đổi dưới Working Directory nhưng mã SHA trong Index vẫn giữ nguyên vì chưa gõ lệnh git add.

Bây giờ, chúng ta kích hoạt một cú Hard Reset về commit gần nhất: 
```
$ git reset --hard
HEAD is now at dc67808 update content of reset_lifecycle_file
$ git status
On branch main
nothing to commit, working tree clean
$ git ls-files -s
100644 d7d77c1b04b5edd5acfc85de0b592449e5303770 0 reset_lifecycle_file
```
Git thông báo HEAD hiện đang trỏ về commit dc67808. Kiểm tra git status, hệ thống báo trạng thái sạch tinh tươm. Xem lại Staging Index, file new_file đã hoàn toàn biến mất, mã SHA của reset_lifecycle_file quay về nguyên bản. Toàn bộ công sức viết file mới và sửa file cũ của bạn đã bị hủy diệt vĩnh viễn và không thể lấy lại.

#### --mixed
Đây là chế độ hoạt động mặc định của lệnh reset. Các con trỏ tham chiếu được cập nhật. Staging Index bị reset về trạng thái của commit chỉ định, nhưng Thư mục làm việc (Working Directory) được giữ nguyên. Bất kỳ thay đổi nào bị loại bỏ khỏi Staging Index sẽ bị đẩy ngược về thành file đỏ ở Working Directory.

Hãy lặp lại thí nghiệm tạo file rác như trên và gõ git add cho cả hai:
```
$ echo 'new file content' > new_file
$ git add new_file
$ echo 'append content' >> reset_lifecycle_file
$ git add reset_lifecycle_file
$ git status
On branch main
Changes to be committed:
	new file:   new_file
	modified:   reset_lifecycle_file
```
Bây giờ, chúng ta thực hiện lệnh Mixed Reset (hoặc chỉ gõ git reset trống):
```
$ git reset --mixed
$ git status
On branch main
Changes not staged for commit:
	modified:   reset_lifecycle_file

Untracked files:
	new_file
```
Kiểm tra lại cây Index:
```
$ git ls-files -s
100644 d7d77c1b04b5edd5acfc85de0b592449e5303770 0 reset_lifecycle_file
```
Kết quả rõ ràng: Staging Index đã bị dọn sạch (file new_file biến mất khỏi Index), nhưng toàn bộ nội dung code bạn vừa gõ không bị mất đi. Chúng chỉ bị đẩy ngược về làm file đỏ (Untracked và Chứa sửa đổi) nằm ở Working Directory để bạn sửa đổi tiếp. Điều này an toàn hơn nhiều so với --hard.

#### --soft
Khi tham số --soft được truyền vào, các con trỏ tham chiếu commit được cập nhật và lệnh dừng lại ở đó. Cả Staging Index lẫn Working Directory đều hoàn toàn không bị đụng tới.

Hành vi này rất khó để nhìn thấy nếu bạn chỉ reset về HEAD (vì mặc định hệ thống đang đứng ở HEAD rồi nên lùi về HEAD sẽ không thấy gì thay đổi). Để thấy rõ sức mạnh của --soft, chúng ta phải chọn một mục tiêu commit cũ hơn trong quá khứ.

Hãy tạo một commit mới để đẩy lịch sử lên 3 commit:
```
$ git commit -am"prepend content to reset_lifecycle_file"
```
Xem lịch sử bằng git log để lấy mã ID của commit đầu tiên ("initial commit"):
```
$ git log
commit 62e793f6941c7e0d4ad9a1345a175fe8f45cb9df (HEAD -> main)
prepend content to reset_lifecycle_file

commit dc67808a6da9f0dec51ed16d3d8823f28e1a72a8
update content of reset_lifecycle_file

commit 780411da3b47117270c0e3a8d5dcfd11d28d04a4
initial commit
```
Mã ID commit gốc của chúng ta ở đây là 780411da3b47117270c0e3a8d5dcfd11d28d04a4. Trước khi thực hiện cú nhảy vọt thời gian, hãy check trạng thái: dự án đang sạch sẽ.

Bây giờ, hãy kích hoạt cú Soft Reset giật lùi lịch sử về tận commit đầu tiên:
```
$ git reset --soft 780411da3b47117270c0e3a8d5dcfd11d28d04a4
$ git status
On branch main
Changes to be committed:
	modified:   reset_lifecycle_file
```
Hãy xem điều kỳ diệu xảy ra: Khi gõ git log, bạn thấy lịch sử chỉ còn lại duy nhất một commit đầu tiên (initial commit), hai commit sau đã bị xóa sổ khỏi trục thời gian. Tuy nhiên, khi gõ git status, toàn bộ code của hai commit bị xóa kia không hề mất đi, chúng đang nằm nguyên vẹn, gọn gàng dưới dạng các file màu xanh lá cây trong mục "Changes to be committed".  
**Bản chất ngầm:** Vì --soft không chạm vào Staging Index, nên toàn bộ dữ liệu tích lũy trong Index đã đi theo bạn lùi về quá khứ. Lệnh này cực kỳ hữu ích khi bạn muốn gom 3-4 commit nhỏ, vụn vặt trước đó lại thành một cú commit lớn duy nhất cho sạch lịch sử dự án.

### Resetting vs Reverting
Nếu coi git revert là một cách hủy bỏ thay đổi "an toàn", thì bạn có thể coi git reset là một phương pháp đầy nguy hiểm. Nguy cơ mất dữ liệu với git reset là rất cao.

Lệnh reset không bao giờ xóa hẳn một commit, tuy nhiên, các commit bị đẩy lùi sẽ rơi vào trạng thái "mồ côi" (orphaned) – nghĩa là không có một đường dẫn trực tiếp nào từ các nhánh trỏ tới chúng được nữa. Bạn thường có thể tìm và cứu lại các commit mồ côi này bằng lệnh git reflog. Tuy nhiên, nếu để quá lâu, cơ chế dọn rác tự động ngầm (Garbage Collector) của Git sẽ quét qua và tiêu hủy vĩnh viễn chúng (mặc định chu kỳ dọn rác là 30 ngày).

| Tiêu chí so sánh | `git revert` | `git reset` |
| :--- | :--- | :--- |
| **Mục đích thiết kế** | Hủy bỏ các commit **công khai trên mạng** (Public/Shared Repo). | Hủy bỏ các thay đổi **nội bộ dưới máy local** (Private/Local). |
| **Tác động lịch sử** | **Giữ nguyên lịch sử cũ**, viết thêm 1 commit đảo ngược mới vào tương lai. | **Cắt cụt lịch sử**, kéo giật lùi các con trỏ về quá khứ. |
| **Mức độ an toàn** | **An toàn tuyệt đối**, không gây mất code và không làm gián đoạn tiến độ của nhóm. | **Nguy hiểm**, dễ gây mất trắng code chưa commit hoặc gây xung đột nếu lỡ push lên mạng. |

### Tuyệt đối không Reset lịch sử công khai (Public History)

Bạn không bao giờ được phép sử dụng git reset <commit> khi mà các commit phía sau mốc đó đã được gõ lệnh git push đẩy lên kho chứa chung của toàn đội.

Khi bạn xóa một commit mà các thành viên khác trong đội đã tải về và đang dựa vào đó để viết tiếp code, một thảm họa cộng tác sẽ xảy ra. Khi họ tiến hành đồng bộ (pull) với kho chứa của bạn, lịch sử dự án của họ sẽ đột ngột bị đứt gãy và biến mất một đoạn. Ngay khi bạn tạo các commit mới sau cú reset, Git sẽ hiểu rằng nhánh cục bộ của bạn đã bị rẽ hướng lệch pha (diverged) hoàn toàn so với nhánh origin/main trên server từ xa. Việc ép buộc gộp nhánh lúc này sẽ sinh ra hàng tá commit xung đột (conflict), gây bối rối và ức chế cho toàn bộ đội ngũ của bạn.

Quy tắc cốt lõi: Chỉ dùng git reset cho các cuộc thử nghiệm viết code thất bại ở dưới máy cá nhân của riêng bạn. Một khi code đã lên mạng, hãy luôn luôn trung thành với git revert.

### Examples
- git reset <tên_file>: Rút một file cụ thể ra khỏi hàng chờ Staging Area, nhưng giữ nguyên nội dung file đó ở Working Directory. Giúp hủy lệnh git add cho từng file mà không làm mất code.
- git reset: Hủy bỏ hàng chờ Staging Area của tất cả mọi file để bạn xây dựng lại ảnh chụp commit từ đầu, thư mục làm việc không bị ảnh hưởng.
- git reset --hard: Xóa sạch cả hàng chờ lẫn thư mục làm việc về trạng thái của commit gần nhất. Xóa sổ mọi code đang gõ dở chưa commit.

- git reset <mã_commit>: Di chuyển con trỏ nhánh hiện tại giật lùi về commit cũ, đưa Staging Index về mốc đó, nhưng giữ nguyên code ở Working Directory dưới dạng file đỏ.

- git reset --hard <mã_commit>: Kéo giật lùi dòng thời gian về commit cũ, đồng thời san phẳng, xóa sạch mọi dữ liệu ở cả hàng chờ lẫn thư mục làm việc để khớp 100% với commit cũ đó.

### Unstaging a file
Bạn đang chuẩn bị commit code, lỡ tay gõ git add . gom cả hai file hello.py và main.py vào hàng chờ. Bạn chợt nhận ra hai file này thuộc hai tính năng khác nhau, nên được lưu ở hai commit riêng biệt để lịch sử được rõ ràng.
```
# 1. Bạn lỡ tay đưa tất cả vào hàng chờ
git add .

# 2. Bạn dùng reset để rút riêng file main.py ra ngoài
git reset main.py

# 3. Lúc này trong hàng chờ chỉ còn hello.py, bạn commit nó trước
git commit -m "Make some changes to hello.py"

# 4. Bây giờ bạn add file main.py vào lại để tạo commit thứ hai
git add main.py
git commit -m "Edit main.py"
```
Nhờ git reset, bạn có thể kiểm soát cực kỳ tinh tế các file nào được phép lọt vào cú commit tiếp theo.

### Removing local commits
Ví dụ tiếp theo minh họa một trường hợp sử dụng nâng cao hơn. Nó cho thấy điều gì xảy ra khi bạn đã làm việc trên một thử nghiệm mới được một thời gian, nhưng quyết định loại bỏ hoàn toàn nó sau khi đã lưu một vài ảnh chụp nhanh.
```
# Sử dụng ký hiệu HEAD~2 để ra lệnh cho Git lùi lại chính xác 2 commit trong lịch sử
git reset --hard HEAD~2
```
Lệnh này di chuyển nhánh hiện tại lùi lại 2 bước, xóa sạch 2 commit thử nghiệm vừa tạo khỏi lịch sử, đồng thời xóa luôn file foo.py trên ổ cứng, trả lại cho bạn một thư mục làm việc sạch sẽ giống hệt như trước khi bạn làm thí nghiệm. (Nhắc lại: Chỉ làm việc này khi 2 commit kia chưa được push lên GitHub).

## Git rm
Một câu hỏi vô cùng phổ biến khi mới bắt đầu học Git là: "Làm thế nào để tôi bảo Git ngừng theo dõi một hoặc nhiều file nào đó?". Lệnh git rm chính là câu trả lời, nó được sử dụng để xóa các file ra khỏi một kho chứa Git. Bạn có thể coi lệnh này là hành động nghịch đảo (trái ngược) của lệnh git add.

### Git rm overview

Lệnh git rm có thể được dùng để xóa một file đơn lẻ hoặc một tập hợp nhiều file. Chức năng chính của git rm là loại bỏ các file đang được theo dõi (tracked files) ra khỏi hàng chờ Git Index.

Bên cạnh đó, khi thực thi, git rm sẽ xóa file ở cả hai nơi: Hàng chờ Staging Area và Thư mục làm việc (Working Directory). Git không cung cấp tùy chọn nào để chỉ xóa file duy nhất ở thư mục làm việc mà giữ lại trong hàng chờ.

### Cơ chế chặn để bảo vệ dữ liệu gõ dở
Các file được chọn để xóa phải có nội dung hoàn toàn trùng khớp với phiên bản nằm ở cú commit gần nhất (HEAD). Nếu có bất kỳ sự sai lệch nào giữa phiên bản file ở HEAD so với phiên bản đang nằm trong hàng chờ hoặc thư mục làm việc (tức là bạn đang sửa dở file đó mà chưa commit), Git sẽ lập tức chặn hành động xóa lại. Cơ chế chặn này là một chốt chặn an toàn để ngăn bạn vô tình xóa mất các thay đổi quan trọng đang làm dở.
**Lưu ý:** Lệnh git rm không dùng để xóa nhánh (branch).

### Usage
```
<file>...
```
Chỉ định các file mục tiêu muốn xóa. Bạn có thể truyền vào một file đơn lẻ, một danh sách các file cách nhau bằng khoảng trắng (file1 file2 file3), hoặc sử dụng ký tự đại diện wildcard (./directory/*).

```
-f or --force
```
Tham số "ép buộc". Dùng để ghi đè lên cơ chế chặn an toàn của Git, ép hệ thống phải xóa file ngay cả khi nội dung file ở thư mục làm việc hoặc hàng chờ đang khác so với HEAD (đang sửa dở).
```
-n or --dry-run
```
Chạy thử nghiệm an toàn. Git sẽ mô phỏng lệnh xóa và hiển thị ra màn hình danh sách những file nào sẽ bị xóa, nhưng hoàn toàn chưa phá hủy bất kỳ dữ liệu thật nào.
```
-r
```
Viết tắt của "recursive" (đệ quy). Khi muốn xóa nguyên một thư mục, bạn bắt buộc phải thêm tham số -r này để Git quét sạch thư mục đó cùng toàn bộ các file/thư mục con bên trong.
```
--
```
Dấu ngăn cách. Dùng để phân tách rõ ràng giữa danh sách tên file và các tham số lệnh phía trước. Việc này cực kỳ hữu ích nếu bạn đặt tên file có chứa các ký tự đặc biệt dễ bị Git hiểu nhầm thành một tham số cấu hình.
```
--cached
```
Tham số này ra lệnh cho Git chỉ xóa file trong hàng chờ Staging Index nhưng GIỮ NGUYÊN file đó trên ổ cứng thư mục làm việc. File của bạn sẽ không bị mất, nó chỉ bị biến từ file màu xanh (Tracked) thành file màu đỏ (Untracked) để bạn cho vào .gitignore.
```
--ignore-unmatch
```
Ép lệnh trả về mã trạng thái thành công bằng 0 (Unix status code) ngay cả khi không tìm thấy file nào khớp với mô tả để xóa. Tham số này rất hữu ích khi bạn viết git rm trong các đoạn mã script tự động chạy ngầm và muốn nó tự bỏ qua lỗi nếu file không tồn tại.
```
-q or --quiet
```
Chế độ im lặng, ẩn toàn bộ thông báo kết quả ra màn hình. Bình thường, cứ mỗi file bị xóa, Git sẽ in ra một dòng thông báo.

### How to undo git rm
Việc chạy lệnh git rm chưa phải là một thay đổi vĩnh viễn. Lệnh này mới chỉ cập nhật trên Thư mục làm việc và Hàng chờ mà thôi. Thay đổi này sẽ không bị đóng băng cho đến khi bạn tạo một cú commit mới. Điều này đồng nghĩa với việc bạn hoàn toàn có thể "quay xe" cứu file bằng các lệnh quen thuộc:
- Cách 1: Rút lệnh xóa khỏi hàng chờ
```
git reset HEAD .
```
Lệnh này đưa hàng chờ Staging Area của file quay trở lại trạng thái của commit HEAD, hủy bỏ hiệu lực của git rm.

- Cách 2: Tải lại file từ quá khứ về thư mục
```
git checkout .
```
Lệnh này sẽ lấy phiên bản file mới nhất đang được lưu an toàn trong commit HEAD và đắp ngược trở lại vào thư mục làm việc của bạn.

**Trường hợp đã lỡ tay Commit lệnh xóa:** Nếu bạn đã gõ git rm và cũng đã gõ luôn git commit, file đã biến mất khỏi lịch sử hiện tại. Bạn hãy sử dụng lệnh git reflog để tìm lại mã băm commit tại thời điểm trước khi lệnh xóa diễn ra và tiến hành khôi phục lại.

### Discussion 
Các đối số <file> truyền vào có thể là đường dẫn chính xác, mẫu ký tự đại diện wildcard, hoặc tên thư mục. Lệnh chỉ có tác dụng với các đường dẫn hiện đang được commit và theo dõi bởi Git.  
### Hãy cẩn thận khi dùng ký tự đại diện
Việc dùng dấu sao * để xóa hàng loạt có thể quét qua nhiều thư mục con và rất dễ gây tai nạn. Hãy so sánh hai ví dụ: directory/* và directory*:

directory/*: Sẽ xóa toàn bộ các file con nằm bên trong thư mục directory/.

directory*: Sẽ xóa sạch tất cả các thư mục đồng cấp có tên bắt đầu bằng chữ directory, ví dụ: directory1, directory2, directory_whatever... Đây thường là một kết quả tai hại ngoài ý muốn.

### Phạm vi ảnh hưởng của git rm
Lệnh git rm chỉ có tác dụng trên nhánh hiện tại bạn đang đứng. Sự kiện xóa file chỉ mới diễn ra trên hai cây dữ liệu là Working Directory và Staging Index, hoàn toàn chưa ghi vào lịch sử Commit History cho đến khi có commit mới.

### Tại sao nên dùng git rm thay vì lệnh rm của hệ điều hành?

Nếu bạn dùng lệnh rm mặc định của Linux/Mac (hoặc bấm chuột phải chọn Delete file trên Windows):

File sẽ bị xóa khỏi Thư mục làm việc (Working Directory).

Khi gõ git status, Git sẽ nhận ra file bị thiếu và hiện file màu đỏ.

Tuy nhiên, Hàng chờ Staging Index vẫn chưa biết gì. Bạn bắt buộc phải gõ thêm lệnh git add <đường_dẫn_file> thì Git mới đưa trạng thái xóa đó vào hàng chờ.

Lệnh git rm hoạt động như một phím tắt thông minh. Nó thực hiện đồng thời cả 2 bước: Xóa file trên ổ cứng + Cập nhật luôn trạng thái xóa vào hàng chờ Staging Area. Bạn bớt được một công đoạn gõ lệnh.

### Examples
#### Ví dụ 1: Xóa file theo định dạng bằng Wildcard
```
git rm Documentation/\*.txt
```
**Ý nghĩa:** Xóa toàn bộ các file có đuôi .txt nằm trong thư mục Documentation/ và tất cả các thư mục con của nó.
Dấu gạch chéo ngược \ đứng trước dấu sao \* là để bảo vệ, ngăn không cho trình Terminal của máy tính tự ý phân tách dấu sao trước khi lệnh được truyền vào cho Git xử lý.

#### Ví dụ 2: Ép buộc xóa file đang sửa dở
```
git rm -f git-*.sh
```
**Ý nghĩa:** Sử dụng tham số -f để xóa áp đặt toàn bộ các file script có tên dạng git-*.sh ra khỏi cả thư mục làm việc lẫn hàng chờ, bất chấp việc file đó có đang bị sửa dở hay không.

### Cách dọn dẹp hệ thống khi lỡ xóa file bằng lệnh rm thường
Như đã giải thích ở trên, nếu bạn lỡ dùng lệnh rm của hệ điều hành để xóa hàng loạt hàng chục file, kho chứa của bạn sẽ rơi vào trạng thái khá hỗn độn (file mất trên ổ cứng nhưng Git vẫn báo đang theo dõi ngầm).

- Giải pháp 1 (Nhanh nhất): Nếu bạn muốn chốt commit luôn toàn bộ các file vừa xóa đó, hãy gõ tham số -a khi commit:
```
git commit -a -m "Xác nhận xóa các file"
```
Tham số -a sẽ tự động quét và đưa tất cả các sự kiện xóa file ngoài ổ cứng cập nhật vào hàng chờ Staging Area để commit luôn.

- Giải pháp 2 (Đồng bộ hàng chờ): Nếu bạn muốn cập nhật trạng thái xóa của các file đó vào hàng chờ trước rồi mới commit sau, hãy dùng chuỗi lệnh kết hợp (đường ống Pipe của Unix) sau:
```
git diff --name-only --diff-filter=D -z | xargs -0 git rm --cached
```
Lệnh này sẽ tự lọc ra danh sách tất cả các file đã bị xóa (--diff-filter=D) ngoài ổ cứng, rồi truyền danh sách đó vào lệnh git rm --cached để dọn sạch hàng chờ Staging Area giúp bạn.

## Rewriting history
### Changing the Last Commit:git commit --amend
Lệnh git commit --amend là một cách tiện lợi để sửa đổi cú commit gần đây nhất. Nó cho phép bạn kết hợp các thay đổi đang nằm trong hàng chờ (staged changes) với commit ngay trước đó thay vì phải tạo ra một commit mới tinh. Nó cũng có thể được dùng để đơn thuần là chỉnh sửa lại lời nhắn commit (commit message) trước đó mà không làm thay đổi ảnh chụp code của nó.

Tuy nhiên, bạn cần hiểu rằng hành động amend không chỉ đơn giản là sửa đổi commit gần nhất, nó thay thế hoàn toàn commit đó. Điều này có nghĩa là commit sau khi amend sẽ là một thực thể mới hoàn toàn với mã băm tham chiếu (ref) riêng của nó. Đối với Git, nó sẽ nhìn nhận đây như một commit mới tinh (được minh họa bằng dấu sao * trong các sơ đồ cấu trúc). Có một vài kịch bản phổ biến để sử dụng git commit --amend dưới đây:

1. Thay đổi lời nhắn (commit message) của commit gần nhất
```
git commit --amend
```
- Giả sử bạn vừa commit xong và phát hiện ra mình viết sai chính tả hoặc sai quy chuẩn trong lời nhắn commit. Việc chạy lệnh này khi không có file nào nằm trong hàng chờ (staging area trống) sẽ cho phép bạn mở trình soạn thảo để sửa lại lời nhắn của commit trước đó mà không làm thay đổi nội dung code bên trong ảnh chụp.

- Những cú commit vội vã (premature commits) xảy ra thường xuyên trong quá trình phát triển hàng ngày. Bạn rất dễ quên chưa add một file hoặc viết sai định dạng lời nhắn. Tham số --amend là một cách tiện lợi để sửa các lỗi nhỏ này.

```
git commit --amend -m "an updated commit message"
```
- Việc thêm tùy chọn -m cho phép bạn truyền trực tiếp lời nhắn mới từ dòng lệnh mà không cần hệ thống phải mở trình soạn thảo văn bản lên nữa.

2. Thay đổi các file đã commit (Sửa đổi nội dung)
- Ví dụ sau đây minh họa một kịch bản rất kinh điển. Giả sử bạn vừa sửa xong hai file hello.py và main.py và muốn lưu chúng chung trong một ảnh chụp commit duy nhất. Tuy nhiên, ở lượt gõ lệnh đầu tiên, bạn lại lỡ quên mất không add file main.py:
```
# Sửa cả hello.py và main.py
git add hello.py
git commit 
# Chợt nhận ra bạn đã quên chưa đưa thay đổi của main.py vào commit!
git add main.py 
git commit --amend --no-edit
```
Tham số --no-edit sẽ cho phép bạn thực hiện việc bổ sung file vào commit cũ mà không làm thay đổi lời nhắn commit sẵn có. Commit mới sau đó sẽ thay thế hoàn toàn cho commit thiếu sót trước đó, và trên lịch sử trông sẽ như thể bạn đã commit cả hello.py và main.py cùng một lúc ngay từ đầu.

#### ĐIỀU CẤM KỴ: Không amend các commit công khai (Public Commits)

Như đã phân tích, các commit sau khi amend thực chất là các commit mới tinh và commit cũ trước đó sẽ biến mất khỏi nhánh hiện tại của bạn. Việc này mang lại hậu quả tai hại tương tự như việc bạn dùng git reset trên một ảnh chụp công khai. Tuyệt đối tránh amend một commit mà các lập trình viên khác trong đội đang dựa vào đó để phát triển tiếp. Đây là một tình huống cực kỳ dễ gây hỗn loạn cho cả đội và rất phức tạp để khôi phục lại dữ liệu đồng bộ.

#### Changing older or multiple commits (Sửa các commit cũ hoặc nhiều commit)

Để sửa đổi các commit cũ hơn hoặc sửa đổi nhiều commit cùng một lúc, bạn có thể sử dụng git rebase để kết hợp một chuỗi các commit thành một commit nền tảng mới (new base commit). Ở chế độ tiêu chuẩn, git rebase cho phép bạn viết lại lịch sử một cách cơ học – tự động áp dụng các commit ở nhánh làm việc hiện tại lên ngọn của nhánh được truyền vào. Vì các commit mới của bạn sẽ thay thế các commit cũ, điều tối quan trọng là không được sử dụng git rebase trên các commit đã được push lên mạng công khai, nếu không lịch sử dự án của bạn trên server sẽ hiển thị như thể bị biến mất một đoạn.

Trong các tình huống cần phải giữ cho lịch sử dự án luôn sạch sẽ và thẳng hàng, việc thêm tùy chọn -i (Interactive) vào lệnh git rebase sẽ cho phép bạn chạy rebase tương tác. Tính năng này cung cấp cho bạn cơ hội được can thiệp, chỉnh sửa từng commit riêng lẻ trong suốt quá trình chạy, thay vì phải di chuyển mù quáng toàn bộ các commit.

1. Thay đổi các file đã commit trong quá khứ

Trong quá trình rebase tương tác, việc bạn chọn lệnh edit (hoặc viết tắt là e) sẽ làm quy trình rebase tạm dừng lại ngay tại cú commit đó và cho phép bạn thực hiện các chỉnh sửa bổ sung bằng lệnh git commit --amend. Git sẽ ngắt quy trình và hiển thị thông báo hướng dẫn:

```
Stopped at 5d025d1... formatting
You can amend the commit now, with

 git commit --amend

Once you are satisfied with your changes, run

 git rebase --continue
```
Sau khi bạn sửa code xong, gõ git commit --amend để chốt dữ liệu, bạn chỉ cần gõ git rebase --continue để Git tiếp tục chạy các commit tiếp theo.

#### Gộp các commit bằng lệnh Squash để làm sạch lịch sử
- Lệnh squash (hoặc viết tắt là s) chính là nơi thể hiện giá trị cốt lõi cao nhất của rebase. Squash cho phép bạn chỉ định những commit nào muốn gộp (shove/merge) vào commit ngay phía trước nó. Đây chính là công cụ giúp tạo ra một "lịch sử sạch đẹp" (clean history).
- Trong quá trình rebase chạy lại, Git sẽ thực thi lệnh được chỉ định cho từng commit. Đối với các commit được đánh dấu là squash, Git sẽ tự động mở trình soạn thảo văn bản lên và yêu cầu bạn kết hợp các lời nhắn commit lại với nhau thành một lời nhắn chung duy nhất.
- Lưu ý về định danh: Các commit được chỉnh sửa hoặc tạo ra thông qua lệnh rebase sẽ sở hữu một Mã ID (Commit Hash) hoàn toàn mới khác biệt với các commit gốc ban đầu. Ngay cả các commit được đánh dấu là pick (giữ nguyên không sửa) cũng sẽ bị đổi mã ID nếu như các commit đứng trước nó trong chuỗi rebase đã bị viết lại lịch sử.

### The safety net: git reflog
- Nhật ký tham chiếu, hay "reflogs", là một cơ chế ngầm mà Git sử dụng để ghi lại mọi sự cập nhật, di chuyển của các con trỏ đầu nhánh (tips of branches) và các tham chiếu commit khác. Reflog cho phép bạn quay trở lại các commit cũ ngay cả khi chúng không còn được tham chiếu bởi bất kỳ nhánh hoặc tag nào (các commit bị mồ côi sau khi reset hoặc rebase).

- Sau khi bạn viết lại lịch sử, reflog sẽ chứa đầy đủ thông tin về trạng thái cũ của các nhánh và cho phép bạn lội ngược dòng quay về trạng thái đó nếu cần thiết. Mỗi khi đầu nhánh của bạn bị cập nhật vì bất kỳ lý do gì (chuyển nhánh, kéo code mới pull, viết lại lịch sử, hoặc đơn giản là tạo commit mới), một dòng nhật ký mới sẽ lập tức được ghi nhận vào reflog.

### Các câu lệnh cơ bản:
- git reflog: Hiển thị danh sách nhật ký tham chiếu của kho chứa cục bộ dưới máy bạn.

- git reflog --relative-date: Hiển thị nhật ký kèm theo thông tin thời gian tương đối (ví dụ: 2 weeks ago - 2 tuần trước) giúp bạn dễ định vị thời điểm xảy ra hành động.
#### Ví dụ thực tế về việc cứu dữ liệu bằng Reflog:
Hãy cùng xem một đoạn kết quả đầu ra của lệnh git reflog:
```
0a2e358 HEAD@{0}: reset: moving to HEAD~2
0254ea7 HEAD@{1}: checkout: moving from 2.2 to main
c10f740 HEAD@{2}: checkout: moving from main to 2.2
```
Đoạn reflog trên ghi nhận hành động di chuyển: Đầu tiên là checkout từ nhánh main sang nhánh 2.2 và ngược lại. Hành động mới nhất nằm ở trên cùng labeled HEAD@{0}: Người dùng vừa thực hiện một cú git reset --hard giật lùi về quá khứ mất 2 commit.

Nếu cú reset đó là một tai nạn tai hại khiến bạn bị mất code, bạn nhìn xuống dòng dưới HEAD@{1}, bạn thấy mã commit của nhánh main ngay trước khi bị reset là 0254ea7. Bạn hoàn toàn có thể cứu lại 2 commit tưởng như đã mất bằng lệnh:

```
git reset --hard 0254ea7
```
Bằng cách này, bạn đưa nhánh main quay trở lại đúng vị trí an toàn trước khi vụ tai nạn xảy ra. Reflog chính là tấm lưới bảo hiểm tối cao cứu mạng bạn trong các tình huống viết lại lịch sử bị lỗi.

**Các điều kiện ràng buộc của Reflog:**

Reflog chỉ cung cấp lưới bảo hiểm nếu như các file của bạn đã được gõ lệnh commit thành công dưới máy local từ trước. Code đang gõ dở chưa commit sẽ không được reflog cứu.

Reflog chỉ hoạt động và lưu trữ cục bộ trên máy của riêng bạn, nó không được push lên server từ xa.

Các dòng nhật ký reflog có hạn sử dụng. Mặc định, Git cấu hình tự động xóa bỏ các dòng reflog cũ sau 90 ngày.

## Git rebase
Rebase là một trong hai công cụ của Git chuyên về việc tích hợp các thay đổi từ nhánh này sang nhánh khác. Công cụ tích hợp thay đổi còn lại chính là git merge. Lệnh Merge luôn luôn là một bản ghi lịch sử tiến về phía trước. Ngược lại, rebase sở hữu những tính năng viết lại lịch sử vô cùng mạnh mẽ. Bản thân Rebase có 2 chế độ hoạt động chính: Chế độ "Tiêu chuẩn" (Manual/Standard) và Chế độ "Tương tác" (Interactive).
### What is git rebase?
Tái cấu trúc nền tảng (Rebasing) là quá trình di chuyển hoặc kết hợp một chuỗi các commit sang một commit nền tảng mới (base commit). Rebase hữu ích nhất và dễ hình dung nhất trong bối cảnh của quy trình làm việc phân nhánh tính năng (feature branching workflow).

Xét về mặt nội dung, rebase là hành động thay đổi gốc nền tảng của nhánh của bạn từ commit này sang commit khác, làm cho nó trông như thể bạn đã tạo nhánh đó từ một commit hoàn toàn khác ngay từ đầu.

Về mặt nội bộ, Git đạt được điều này bằng cách tạo ra các commit mới tinh và áp chúng vào gốc nền tảng được chỉ định. Việc thấu hiểu điều này là vô cùng quan trọng: Mặc dù về mặt trực quan cái nhánh đó trông có vẻ giống hệt nhau, nhưng nó lại được cấu thành từ những commit có mã định danh hoàn toàn mới.

### Usage
Lý do hàng đầu cho việc sử dụng rebase là nhằm duy trì một lịch sử dự án tuyến tính (thẳng hàng). Hãy tưởng tượng tình huống khi nhánh main đã tiến thêm vài commit kể từ ngày bạn tách nhánh tính năng (feature_branch) ra làm riêng. Bạn muốn đem những cập nhật mới nhất của main vào nhánh của mình, nhưng đồng thời muốn giữ cho lịch sử của nhánh thật sạch sẽ, như thể bạn chỉ vừa mới tách nhánh từ cú commit mới nhất của main. Điều này mang lại lợi ích rất lớn cho việc gộp nhánh (merge) sạch đẹp về sau.

### Tại sao chúng ta lại muốn duy trì một "Lịch sử sạch"?
Lợi ích của một lịch sử thẳng hàng sẽ trở nên cực kỳ rõ rệt khi bạn thực hiện các thao tác Git để điều tra nguồn gốc của một lỗi logic mới phát sinh (regression). Hãy xem một kịch bản thực tế:

1. Một lỗi (bug) được phát hiện trên nhánh main. Một tính năng vốn đang chạy ngon lành bỗng dưng bị hỏng.

1. Lập trình viên kiểm tra lịch sử của main bằng lệnh git log. Nhờ có một "lịch sử sạch", lập trình viên có thể nhanh chóng đọc hiểu và nắm bắt mạch tư duy của dự án.

1. Nếu lập trình viên vẫn chưa thể tìm ra chính xác lỗi xuất hiện từ khi nào bằng mắt thường, họ sẽ kích hoạt lệnh git bisect.

1. Vì lịch sử Git thẳng hàng và không có các commit gộp nhánh chằng chịt, git bisect có được một tập hợp các commit cực kỳ chuẩn xác để so sánh nhị phân. Lập trình viên nhanh chóng định vị được commit gây lỗi và đưa ra phương án xử lý.

Bạn có hai lựa chọn để tích hợp nhánh tính năng vào nhánh chính: Gộp trực tiếp (merge) hoặc Rebase trước rồi mới gộp.

- Cách gộp trực tiếp sẽ tạo ra một cú gộp 3 đường (3-way merge) và tự sinh một commit gộp (merge commit) làm rối dòng lịch sử.
- Cách rebase trước sẽ giúp bạn tạo ra một cú gộp tiến thẳng (fast-forward merge) và một lịch sử tuyến tính hoàn hảo.

#### Rebase là cách phổ biến để tích hợp các thay đổi từ thượng nguồn (upstream) về kho chứa cục bộ. Việc kéo code bằng git merge sẽ tự đẻ ra một commit gộp thừa thãi mỗi khi bạn muốn cập nhật tiến độ dự án. Ngược lại, rebase giống như việc bạn tuyên bố: "Tôi muốn đặt nền móng các thay đổi của tôi lên trên những gì mà mọi người đã hoàn thành trước đó."

### ĐIỀU CẤM KỴ: Không rebase lịch sử công khai
- Như đã nhấn mạnh ở các chương trước, bạn không bao giờ được phép rebase các commit một khi chúng đã được push lên server công khai. Hành động rebase sẽ thay thế các commit cũ bằng các commit mới, và đối với những người dùng khác trong đội, một đoạn lịch sử dự án của họ sẽ bỗng dưng bị bốc hơi mất tích.

### Git rebase standard vs git rebase interactive

Lệnh Rebase tương tác xuất hiện khi chúng ta truyền thêm tham số -i (viết tắt của Interactive). Nếu không viết gì, lệnh sẽ chạy ở chế độ tiêu chuẩn. Trong cả hai trường hợp, hãy giả định chúng ta vừa tạo một nhánh tính năng từ main:

```
# Tạo nhánh tính năng từ main và chuyển sang làm việc
git checkout -b feature_branch main
# Chỉnh sửa code và commit
git commit -a -m "Adds new feature"
```

1. Chế độ tiêu chuẩn (Standard Mode)
```
git rebase <base>
```
Lệnh này sẽ tự động bốc toàn bộ các commit ở nhánh làm việc hiện tại của bạn và đem xếp chồng lên trên ngọn của nhánh <base> được truyền vào (Tham số <base> có thể là tên một nhánh khác, mã commit ID, một cái tag hoặc một tham chiếu tương đối tới HEAD).

1. Chế độ tương tác (Interactive Mode)
```
git rebase --interactive <base>
```

Thay vì mù quáng di chuyển toàn bộ các commit sang nền tảng mới, rebase tương tác trao cho bạn cơ hội được chỉnh sửa từng commit một trong suốt quá trình chạy. Nó cho phép bạn dọn dẹp lịch sử bằng cách xóa bỏ, chia tách hoặc nhào nặn lại một chuỗi commit cũ. Lệnh này hoạt động giống như một phiên bản git commit --amend nhưng được tiếp thêm "bột tăng lực".

Khi gõ lệnh này, một trình soạn thảo văn bản sẽ mở ra và liệt kê danh sách các commit kèm theo các từ khóa hành động (lệnh điều hướng) đứng ở đầu. Bạn có thể thay đổi các từ khóa này hoặc đảo thứ tự các dòng để sắp xếp lại lịch sử:

```
pick 231360some old commit
pick ee2adc2 Adds new feature

# Rebase 2cf755d..ee2adc2 onto 2cf755d (9 commands)
#
# Commands:
# p, pick = giữ nguyên và sử dụng commit này
# r, reword = sử dụng commit nhưng dừng lại để sửa lời nhắn (commit message)
# e, edit = sử dụng commit nhưng dừng lại để sửa nội dung code bên trong
# s, squash = gộp nội dung commit này vào commit ngay phía trước nó
# f, fixup = giống như "squash", nhưng xóa bỏ luôn lời nhắn của commit này
# x, exec = chạy một câu lệnh shell script test hệ thống ngầm trên commit này
# d, drop = xóa bỏ, vứt xó hoàn toàn commit này
```

### Configuration options
Bạn có thể thiết lập một số thuộc tính của rebase thông qua câu lệnh git config để thay đổi cách hiển thị và hành vi của hệ thống:  
- rebase.stat: Định dạng kiểu Boolean (mặc định là false). Tùy chọn này dùng để bật/tắt việc hiển thị sơ đồ phân tích diffstat trực quan, cho thấy những gì đã thay đổi kể từ lần rebase cuối cùng.

- rebase.autoSquash: Giá trị Boolean dùng để bật/tắt tự động tính năng gộp commit (--autosquash).

- rebase.missingCommitsCheck: Thay đổi hành vi của rebase khi phát hiện có commit bị thiếu trong quá trình chạy tương tác. Có thể nhận các giá trị:

- warn: In ra cảnh báo trong chế độ tương tác nếu phát hiện có commit bị xóa bỏ.

- error: Chặn đứng quy trình rebase và in ra thông báo lỗi cảnh báo dữ liệu.

- ignore: (Mặc định) Bỏ qua và lờ đi mọi cảnh báo về việc thiếu commit.

- rebase.instructionFormat: Chuỗi định dạng định nghĩa cách hiển thị danh sách các commit trong bảng lệnh của rebase tương tác.
### Advanced rebase application
Tham số --onto cho phép bạn kích hoạt một dạng rebase cực kỳ mạnh mẽ, giúp bạn chủ động "cắt đuôi" và di dời ngọn của một nhánh sang một vị trí tham chiếu hoàn toàn mới. Cú pháp đầy đủ như sau:
```
git rebase --onto <newbase> <oldbase>
```
Hãy cùng xem một kịch bản dự án đang phân nhánh chằng chịt như sau:
```
o---o---o---o---o  main
     \
       o---o---o---o---o  featureA
            \
             o---o---o  featureB
```
Nhánh featureB đang được tách ra và bám vào nền tảng của nhánh featureA. Tuy nhiên, bạn chợt nhận ra các tính năng trong featureB hoàn toàn độc lập, không cần dùng bất kỳ đoạn code nào của featureA cả. Bạn muốn đưa featureB về bám trực tiếp vào nhánh chính main cho sạch sẽ.

Bạn thực thi câu lệnh:

```
git rebase --onto main featureA featureB
```
Trong đó, featureA đóng vai trò là gốc nền tảng cũ (<oldbase>), main trở thành gốc nền tảng mới tinh (<newbase>), và featureB chỉ định con trỏ HEAD sẽ di chuyển theo. Kết quả lịch sử sẽ biến đổi thành:
```
o---o---o  featureB
                     /
    o---o---o---o---o  main
     \
      o---o---o---o---o  featureA
```

### Understanding the dangers of rebase
Một điểm trừ cần lưu ý khi làm việc với quy trình Rebase là xung đột code (merge conflicts) có thể xảy ra với tần suất dày đặc hơn. Điều này thường xuất hiện nếu bạn sở hữu một nhánh tính năng có tuổi thọ quá lâu (long-lived branch) và đã đi quá xa so với nhánh chính main. Đến khi bạn rebase, main đã có thêm hàng trăm commit mới, dẫn đến việc code của bạn bị xung đột chan chát qua từng commit một.

**0Giải pháp khắc phục:** Hãy tạo thói quen rebase nhánh tính năng của bạn với main một cách thường xuyên (hàng ngày) và chia nhỏ các commit ra. Khi đối mặt với xung đột trong lúc rebase, bạn có thể dùng tham số --continue (để tiếp tục chạy sau khi đã fix xong xung đột) hoặc --abort (để hủy bỏ hoàn toàn lệnh rebase, đưa dự án an toàn về trạng thái trước khi gõ lệnh).

Một mối nguy hiểm lớn khác là việc vô tình làm mất commit trong quá trình chạy tương tác lịch sử (khi chọn lệnh squash hoặc drop). Commit của bạn sẽ biến mất khỏi lịch sử hiển thị của nhánh. Tuy nhiên, bạn hoàn toàn có thể dùng công cụ cứu hộ git reflog để tìm lại mã băm commit mồ côi này và hoàn tác toàn bộ quy trình rebase sai lầm đó.

Mối hiểm họa thực sự chỉ xảy ra khi bạn viết lại lịch sử bằng rebase tương tác, sau đó gõ lệnh ép buộc git push --force đẩy lên một nhánh chung đang được chia sẻ với nhiều người khác trên mạng. Đây là hành vi tuyệt đối phải tránh, vì nó có khả năng ghi đè và phá hủy hoàn toàn toàn bộ công sức gõ code của các đồng nghiệp khác khi họ tiến hành kéo code về.

### Recovering from upstream rebase
Nếu một người khác trong nhóm lỡ tay rebase và push --force lên một cái nhánh chung mà bạn cũng đang commit code vào đó, lệnh git pull thông thường của bạn sẽ ghi đè và phá hủy các commit của bạn bằng ngọn commit mới của họ.

Để cứu vãn tình thế, bạn hãy gõ lệnh git reflog để truy vết lại lịch sử dịch chuyển con trỏ của nhánh từ xa (remote branch). Hãy tìm dòng trạng thái của nhánh đó ở thời điểm ngay trước khi vụ tai nạn rebase diễn ra để lấy mã commit ID an toàn. Sau đó, bạn sử dụng lệnh rebase nâng cao với tham số --onto (như đã học ở mục phía trên) để đem nhánh của mình gắn trở lại vào cái mốc an toàn đó là xong!

## Git Reflog

Lệnh git reflog là một công cụ cứu hộ trong Git. Git theo dõi các cập nhật đối với đầu ngọn của các nhánh bằng một cơ chế gọi là nhật ký tham chiếu, hay "reflogs". Rất nhiều câu lệnh Git chấp nhận một tham số để chỉ định một tham chiếu hoặc "ref" – thực chất là một con trỏ trỏ tới một commit. Các ví dụ phổ biến bao gồm:

git checkout

git reset

git merge <ref>

Reflogs ghi lại nhật ký chính xác thời điểm các Git refs được cập nhật trong kho chứa cục bộ (local repository). Ngoài việc theo dõi đầu ngọn của các nhánh, một reflog đặc biệt cũng được duy trì riêng cho bộ nhớ tạm git stash.

Về mặt lưu trữ, Reflogs được lưu trong các thư mục ẩn nằm dưới thư mục .git của kho chứa cục bộ. Bạn có thể tìm thấy các thư mục dữ liệu ngầm này tại:

- .git/logs/refs/heads/[tên_nhánh] (Nhật ký của từng nhánh).

- .git/logs/HEAD (Nhật ký di chuyển của con trỏ HEAD).

- .git/logs/refs/stash (Nhật ký của bộ nhớ tạm stash nếu đã từng sử dụng).

### Basic usage
Cách sử dụng Reflog cơ bản nhất là kích hoạt câu lệnh:
```
git reflog
```
Về bản chất, đây là một lối viết tắt và nó hoàn toàn tương đương với câu lệnh:
```
git reflog show HEAD
```
Lệnh này sẽ in ra toàn bộ nhật ký dịch chuyển của con trỏ HEAD. Bạn sẽ nhìn thấy kết quả hiển thị trên màn hình tương tự như sau:
```
eff544f HEAD@{0}: commit: migrate existing content
bf871fd HEAD@{1}: commit: Add Git Reflog outline
9a4491f HEAD@{2}: checkout: moving from main to git_reflog
9a4491f HEAD@{3}: checkout: moving from Git_Config to main
39b159a HEAD@{4}: commit: expand on git context 
9b3aa71 HEAD@{5}: commit: more color clarification
f34388b HEAD@{6}: commit: expand on color support 
9962aed HEAD@{7}: commit: a git editor -> the Git editor
```
### Reflog references
- Mặc định, git reflog sẽ xuất ra nhật ký của tham chiếu HEAD (con trỏ tượng trưng cho nhánh đang hoạt động hiện tại). Tuy nhiên, reflog cũng có sẵn cho các tham chiếu dữ liệu khác. Cú pháp chuẩn để truy cập vào một Git ref log là: name@{qualifier} (tên_tham_chiếu@{bộ_định_dịnh}). Ngoài HEAD, bạn có thể kiểm tra nhật ký của các nhánh khác, các tag, các remote server, và cả git stash.

1. Xem nhật ký của tất cả các tham chiếu cùng lúc
```
git reflog show --all
```
1. Xem nhật ký của một nhánh cụ thể
Bạn chỉ cần truyền tên nhánh đó vào sau lệnh git reflog show:
```
git reflog show otherbranch
```
Kết quả trả về sẽ hiển thị riêng lịch sử của nhánh đó:
```
9a4491f otherbranch@{0}: commit: seperate articles into branch PRs
435aee4a otherbranch@{1}: commit (initial): initial commit add git-init and setting-up-a-repo docs
```
1. Xem nhật ký của bộ nhớ tạm Git Stash
Giả sử trước đó bạn đã cất giấu một số đoạn code đang gõ dở bằng lệnh git stash, bạn có thể tra cứu lại bằng lệnh:
```
git reflog stash
```
Kết quả hiển thị:  
```
30d44de3 stash@{0}: WIP on git_reflog: c492574 flesh out intro
```
Các con trỏ tham chiếu reflog này (stash@{0}, otherbranch@{0}) hoàn toàn có thể được truyền vào làm đối số cho các câu lệnh Git khác. Ví dụ, bạn có thể so sánh sự sai lệch giữa đoạn code đang cất trong stash với ngọn của nhánh otherbranch bằng lệnh:

```
git diff stash@{0} otherbranch@{0}
```
### Timed reflogs
Mỗi dòng nhật ký trong reflog đều được đính kèm ngầm một mốc thời gian (timestamp). Những mốc thời gian này có thể được tận dụng làm bộ định danh (qualifier) trong cú pháp con trỏ Git, giúp bạn lọc nhật ký theo thời gian. Dưới đây là các từ khóa thời gian được Git hỗ trợ:
```
1.minute.ago (1 phút trước)

1.hour.ago (1 giờ trước)

1.day.ago (1 ngày trước)

yesterday (ngày hôm qua)

1.week.ago (1 tuần trước)

1.month.ago (1 tháng trước)

1.year.ago (1 năm trước)

2011-05-17.09:00:00 (Mốc ngày giờ chính xác)
```
Các từ khóa thời gian có thể được kết hợp linh hoạt (ví dụ: 1.day.2.hours.ago) và chấp nhận cả danh từ số nhiều (ví dụ: 5.minutes.ago). Bạn có thể truyền các con trỏ thời gian này vào các câu lệnh khác như git diff để kiểm tra biến động của dự án:
```
git diff main@{0} main@{1.day.ago}
```
**Ứng dụng:** Lệnh này giúp bạn so sánh file code của nhánh main ở thời điểm hiện tại (main@{0}) với chính nó của 1 ngày trước (main@{1.day.ago}). Cực kỳ hữu ích để rà soát xem trong vòng 24 giờ qua dự án đã thay đổi những gì.

### Subcommands & configuration options
Lệnh git reflog tiếp nhận một số đối số bổ sung đóng vai trò là các lệnh phụ (subcommands):
**1. Show - git reflog show**  
Đây là lệnh phụ mặc định được hệ thống tự hiểu ngầm. Định dạng git reflog show <refid> thực chất là một tên gọi khác (alias) của chuỗi lệnh phức tạp: git log -g --abbrev-commit --pretty=oneline.

**2. Expire - git reflog expire**  
Lệnh phụ này dùng để dọn dẹp, xóa bỏ các dòng nhật ký reflog đã quá cũ hoặc không thể liên kết tới đâu nữa nhằm tiết kiệm dung lượng ổ cứng. Lệnh này tiềm ẩn nguy cơ mất dữ liệu và thường chỉ được Git tự chạy ngầm bên trong hệ thống chứ lập trình viên ít khi phải gõ thủ công.
- Mặc định, hạn sử dụng của một dòng reflog là 90 ngày. Bạn có thể ép thời gian hết hạn bằng tham số --expire=time hoặc cấu hình thuộc tính hệ thống gc.reflogExpire. Bạn có thể gõ git reflog expire --dry-run để chạy thử xem Git dự định xóa những dòng nhật ký nào.

**3. Delete - git reflog delete**
Lệnh này dùng để xóa đích danh một dòng nhật ký reflog cụ thể nào đó. Tương tự như expire, lệnh này ít khi được người dùng cuối kích hoạt trừ các trường hợp đặc biệt.

### Recovering lost commits
Về bản chất, Git không bao giờ thực sự làm mất bất kỳ thứ gì, ngay cả khi bạn thực hiện các thao tác viết lại lịch sử mang tính chất phá hủy như git rebase hay git commit --amend. Hãy cùng đi qua một kịch bản thực tế để xem cách Reflog cứu lại các commit bị biến mất sau khi gộp nhánh:

Lịch sử ban đầu của file git log --pretty=oneline đang rất sạch đẹp:
```
338fbcb41de10f7f2e54095f5649426cb4bf2458 extended content
1e63ceab309da94256db8fb1f35b1678fb74abd4 bunch of content
c49257493a95185997c87e0bc3a9481715270086 flesh out intro
eff544f986d270d7f97c77618314a06f024c7916 migrate existing content
bf871fd762d8ef2e146d7f0226e81a92f91975ad Add Git Reflog outline
35aee4a4404c42128bee8468a9517418ed0eb3dc initial commit
```
Sau đó, bạn gõ thêm một commit chứa các đoạn code đang làm dở:
```
git commit -am "some WIP changes"
```
Lúc này lịch sử log được nối dài thêm dòng: 37656e1... some WIP changes đứng ở trên cùng.
Ngay sau đó, bạn thực hiện một cú Rebase tương tác với nhánh chính để nén gọn lịch sử trước khi nộp bài:
```
git rebase -i origin/main
```
Trong quá trình rebase, bạn sử dụng lệnh squash (s) để gộp hàng loạt các commit nhỏ phía dưới vào chung với commit some WIP changes gần nhất. Sau khi rebase hoàn tất, bạn gõ git log kiểm tra lại:
```
40dhsoi37656e19d4e4f1a9b419f57850ch87dah987698hs some WIP changes
35aee4a4404c42128bee8468a9517418ed0eb3dc initial commit
```
Nhìn vào log, toàn bộ các commit nhỏ trung gian đã bị nén biến mất khỏi màn hình, chỉ còn lại duy nhất commit gộp chung. Chuyện gì xảy ra nếu lúc này bạn hối hận và muốn lấy lại một cú commit nhỏ đã bị squash trước đó để bóc tách lại code? git log đã bất lực. Đây chính là lúc bạn gọi đến cứu viện git reflog:
```
$ git reflog
37656e1 HEAD@{0}: rebase -i (finish): returning to refs/heads/git_reflog
37656e1 HEAD@{1}: rebase -i (start): checkout origin/main
37656e1 HEAD@{2}: commit: some WIP changes
``` 

Nhìn vào bảng reflog, bạn thấy rõ lịch sử chuyển động: dòng HEAD@{0} và HEAD@{1} ghi lại thời điểm bắt đầu và kết thúc vụ tai nạn rebase. Quan trọng nhất, dòng HEAD@{2} chính là trạng thái nguyên bản an toàn của bạn ngay trước khi lệnh rebase diễn ra.

Bạn tiến hành khôi phục lại toàn bộ các commit đã mất bằng lệnh giật lùi reset:

```
git reset --hard HEAD@{2}
```
Ngay sau lệnh này, con trỏ HEAD lập tức được kéo về mốc HEAD@{2}, cứu sống toàn bộ các commit đã bị nén oan uổng, trả lại đầy đủ lịch sử ban đầu cho bạn.

## Git remote
Hệ thống quản lý phiên bản Subversion (SVN) sử dụng một kho chứa trung tâm duy nhất đóng vai trò là trung tâm kết nối cho các lập trình viên. Việc cộng tác diễn ra bằng cách truyền các tập hợp thay đổi (changesets) qua lại giữa bản sao làm việc của lập trình viên và kho chứa trung tâm đó. Mô hình này khác biệt hoàn toàn với mô hình cộng tác phân tán (distributed collaboration model) của Git.

Trong Git, mỗi lập trình viên có một bản sao độc lập hoàn chỉnh của kho chứa, đi kèm với lịch sử commit cục bộ và cấu trúc nhánh riêng. Người dùng thường có nhu cầu chia sẻ một chuỗi các commit thay vì một changeset đơn lẻ. Thay vì commit một changeset từ bản sao làm việc lên máy chủ trung tâm, Git cho phép bạn chia sẻ toàn bộ các nhánh giữa các kho chứa với nhau.

Lệnh git remote là một mảnh ghép nằm trong một hệ thống lớn chịu trách nhiệm đồng bộ hóa các thay đổi. Các bản ghi được đăng ký thông qua lệnh git remote sẽ được sử dụng kết hợp với các lệnh git fetch, git push, và git pull.

### Git remote là gì?
Lệnh git remote cho phép bạn tạo, xem và xóa các kết nối tới các kho chứa khác. Các kết nối từ xa (remote connections) này hoạt động giống như các "dấu trang" (bookmarks) hơn là các liên kết trực tiếp vào kho chứa khác. Thay vì cung cấp quyền truy cập thời gian thực vào một kho chứa, chúng phục vụ như những cái tên gợi nhớ tiện lợi để thay thế cho một đường dẫn URL dài dòng, khó nhớ.

### Git remote usage overview (Tổng quan cách sử dụng)
Lệnh git remote về mặt bản chất là một giao diện quản lý danh sách các cấu hình từ xa được lưu trữ ngầm bên trong file văn bản ./.git/config của dự án. Các câu lệnh dưới đây được sử dụng để kiểm tra trạng thái hiện tại của danh sách remote này:

#### Viewing git remote configurations
- git remote: Liệt kê tên các kết nối từ xa mà bạn đang có với các kho chứa khác.

- git remote -v: Tương tự như lệnh trên, nhưng hiển thị kèm theo cả đường dẫn URL chi tiết của từng kết nối.

#### Creating and modifying git remote configurations
Lệnh git remote đóng vai trò là một phương thức "trợ giúp" tiện lợi để sửa đổi file ./.git/config. Các kết quả của những lệnh dưới đây hoàn toàn có thể đạt được bằng cách dùng trình soạn thảo văn bản mở trực tiếp file ./.git/config ra để sửa:

- git remote add <name> <url>: Khởi tạo một kết nối mới tới một kho chứa từ xa. Sau khi add thành công, bạn có thể dùng tên <name> làm phím tắt cho <url> trong các lệnh khác.
- git remote rm <name>: Xóa bỏ hoàn toàn kết nối tới kho chứa từ xa có tên là <name>.
- git remote rename <old-name> <new-name>: Đổi tên một kết nối từ xa từ tên cũ <old-name> thành tên mới <new-name>.

#### Git remote discussion
Git được thiết kế để cung cấp cho mỗi lập trình viên một môi trường phát triển biệt lập hoàn toàn. Điều này đồng nghĩa với việc thông tin dữ liệu không tự động truyền qua lại giữa các kho chứa. Thay vào đó, các lập trình viên cần phải tự tay kéo các commit thượng nguồn về máy (pull) hoặc tự tay đẩy các commit cục bộ của mình lên mạng (push). Lệnh git remote đơn giản chỉ là một cách dễ dàng hơn để bạn truyền các đường dẫn URL vào các lệnh chia sẻ dữ liệu này.

#### Remote mặc định: origin
Khi bạn tải một dự án về bằng lệnh git clone, Git sẽ tự động tạo ngầm một kết nối từ xa đặt tên là origin trỏ ngược về kho chứa gốc mà bạn vừa clone. Điều này cực kỳ tiện lợi cho các lập trình viên khi cần cập nhật code mới hoặc xuất bản sản phẩm lên server. Đây cũng là lý do vì sao hầu hết các dự án Git trên thế giới đều quy ước gọi kho chứa trung tâm của họ là origin.

#### Đường dẫn URL của kho chứa (Repository URLs)
Git hỗ trợ nhiều giao thức để tham chiếu tới một kho chứa từ xa. Hai giao thức phổ biến nhất là HTTP và SSH:
- HTTP (hoặc HTTPS): Phù hợp cho việc cấp quyền truy cập ẩn danh, chỉ đọc (read-only). Ví dụ: http://host/path/to/repo.git. Thông thường bạn không thể push code qua địa chỉ HTTP ẩn danh này (chẳng ai muốn cho người lạ đẩy code lung tung vào dự án của mình cả).
- SSH: Phù hợp cho quyền đọc-ghi (read-write) có xác thực bảo mật: ssh://user@host/path/to/repo.git. Bạn sẽ cần một tài khoản SSH hợp lệ trên máy chủ. Các nền tảng hiện đại như GitHub hay Bitbucket luôn cung cấp sẵn cả 2 đường dẫn này trên giao diện để bạn copy.

### Git remote subcommands
**1. ADD <NAME> <URL>**  
Ghi một dòng cấu hình vào ./.git/config.
- Có thể thêm tham số -f: Git sẽ tự động chạy lệnh git fetch <name> ngay lập tức sau khi kết nối được tạo để tải dữ liệu về.

- Có thể thêm tham số --tags: Tự động fetch và tải toàn bộ các nhãn tag từ kho chứa từ xa về máy local.

**2. RENAME <OLD> <NEW>**  
Cập nhật file cấu hình để đổi tên remote. Tất cả các nhánh theo dõi từ xa (remote-tracking branches) và các cài đặt cấu hình cho remote đó đều sẽ được cập nhật đồng bộ theo tên mới.

**3. REMOVE hoặc RM <NAME>**  
Xóa bỏ bản ghi remote khỏi file config. Toàn bộ các nhánh theo dõi từ xa thuộc về remote này cũng sẽ bị xóa sạch khỏi máy local.

**4. GET-URL <NAME>**  
In ra màn hình đường dẫn URL của remote.

- Thêm --push: Hiển thị URL phục vụ cho việc đẩy code (push URL) thay vì URL tải code (fetch URL).

- Thêm --all: Hiển thị toàn bộ các URL đang gắn với remote đó.
**5. SHOW <NAME>**
Xuất ra màn hình một bảng báo cáo thông tin cấp cao chi tiết về remote <NAME>.
**6. PRUNE <NAME> (Dọn dẹp nhánh rác)**
Xóa bỏ toàn bộ các nhánh local đại diện cho remote <NAME> mà thực tế trên server từ xa các nhánh đó đã bị người khác xóa mất rồi.

- Thêm --dry-run: Chạy thử xem những nhánh nào nằm trong diện bị dọn dẹp chứ chưa xóa thật.

### Git remote examples
Bên cạnh origin, đôi khi sẽ rất tiện lợi nếu bạn tạo thêm kết nối tới kho chứa của các đồng nghiệp khác để lấy code trực tiếp từ máy của họ. Ví dụ, nếu người bạn làm chung tên là John có một kho chứa công khai tại địa chỉ dev.example.com/john.git, bạn có thể add kết nối như sau:
```
git remote add john http://dev.example.com/john.git
```
Việc kết nối trực tiếp này giúp hai người có thể trao đổi, duyệt code cho nhau mà không cần phải đi đường vòng thông qua máy chủ trung tâm. Cực kỳ hữu ích cho các nhóm nhỏ đang cùng xử lý một tính năng phức tạp.

**1. Kiểm tra danh sách Remote hiện có**
Lệnh mặc định chỉ hiện tên viết tắt:
```
$ git remote
origin
upstream
other_users_repo
```
Nếu muốn xem chi tiết cả URL (Verbose mode), hãy thêm -v:
```
$ git remote -v
origin  git@bitbucket.com:origin_user/reponame.git (fetch)
origin  git@bitbucket.com:origin_user/reponame.git (push)
upstream    https://bitbucket.com/upstream_user/reponame.git (fetch)
upstream    https://bitbucket.com/upstream_user/reponame.git (push)
other_users_repo    https://bitbucket.com/other_users_repo/reponame (fetch)
other_users_repo    https://bitbucket.com/other_users_repo/reponame (push)
```
(Cột cuối cùng chỉ rõ đường link nào được dùng để nạp code về fetch, đường link nào dùng để xuất code lên push).

**2. Thao tác Add Remote ngầm kiểm tra file config**
Khi bạn gõ lệnh thêm một remote tên là fake_test:
```
$ git remote add fake_test https://bitbucket.com/upstream_user/reponame.git
```
Mở file ẩn ./.git/config ra, bạn sẽ thấy Git tự động viết thêm đoạn text sau vào cuối file:
```
[remote "fake_test"]
   url = https://bitbucket.com/upstream_user/reponame.git
   fetch = +refs/heads/*:refs/remotes/fake_test/*
```
**3. Soi chi tiết một Remote bằng lệnh Show**
Lệnh này giúp bạn xem tình trạng đồng bộ các nhánh giữa máy mình và server:
```
$ git remote show upstream
* remote upstream
   Fetch URL: https://bitbucket.com/upstream_user/reponame.git
   Push URL: https://bitbucket.com/upstream_user/reponame.git
   HEAD branch: main
   Remote branches:
      main tracked
      simd-deprecated tracked
      tutorial tracked
   Local ref configured for 'git push':
      main pushes to main (fast-forwardable)
```
**4. Đẩy code và Xóa bỏ Remote**
- Để tải dữ liệu từ một remote về, bạn truyền tên remote đó vào lệnh git fetch <remote-name> hoặc git pull.

- Để đẩy tính năng lên mạng, bạn dùng lệnh git push:
```
git push origin feature_branch
```
Lệnh này tải trạng thái cục bộ của nhánh feature_branch lên kho chứa từ xa origin.
- Để gỡ bỏ một kết nối remote đã add nhầm (ví dụ xóa remote fake_test vừa tạo ở trên):
```
git remote rm fake_test
```
Sau khi chạy xong, bản ghi của fake_test trong file ./.git/config lập tức bị xóa sạch không còn dấu vết.

## Git fetch
Lệnh git fetch thực hiện tải về các commit, file và các tham chiếu (refs) từ một kho chứa từ xa (remote repository) vào kho chứa cục bộ (local repo) của bạn. Fetching là hành động bạn thực hiện khi muốn kiểm tra xem mọi người xung quanh đang làm việc tới đâu. Lệnh này tương tự như svn update ở chỗ nó cho phép bạn thấy lịch sử trung tâm đã tiến triển như thế nào, nhưng nó không ép buộc bạn phải thực sự gộp (merge) những thay đổi đó vào kho chứa của mình.

Git cô lập hoàn toàn nội dung vừa fetch về khỏi nội dung cục bộ hiện tại; nó tuyệt đối không gây ra bất kỳ ảnh hưởng nào tới công việc phát triển cục bộ của bạn. Nội dung được fetch về bắt buộc phải được chuyển đổi một cách tường minh bằng lệnh git checkout. Điều này biến fetch trở thành một phương thức an toàn bậc nhất để xem xét, duyệt các commit trước khi tích hợp chúng vào kho chứa cục bộ.

Khi muốn tải nội dung từ một remote repo, bạn có hai công cụ là git pull và git fetch. Bạn có thể coi git fetch là phiên bản "an toàn" của hai lệnh này. Nó sẽ tải nội dung từ xa về nhưng không cập nhật trạng thái làm việc cục bộ của bạn, giữ nguyên vẹn công việc hiện tại.

Khi muốn tải nội dung từ một remote repo, bạn có hai công cụ là git pull và git fetch. Bạn có thể coi git fetch là phiên bản "an toàn" của hai lệnh này. Nó sẽ tải nội dung từ xa về nhưng không cập nhật trạng thái làm việc cục bộ của bạn, giữ nguyên vẹn công việc hiện tại.

Ngược lại, git pull là một giải pháp thay thế quyết liệt hơn; nó sẽ tải nội dung từ xa về cho nhánh cục bộ đang hoạt động và ngay lập tức thực thi git merge để tạo ra một commit gộp cho nội dung từ xa mới đó. Nếu bạn đang có những thay đổi dở dang chưa hoàn thành, hành động này sẽ gây ra xung đột (conflicts) và kích hoạt quy trình giải quyết xung đột gộp nhánh đầy phiền toái.

### How git fetch works with remote branches
Để hiểu rõ hơn cách hoạt động của git fetch, hãy cùng thảo luận về cách Git tổ chức và lưu trữ các commit. Phía sau hậu trường, trong thư mục ./.git/objects của kho chứa, Git lưu trữ toàn bộ các commit, bao gồm cả cục bộ và từ xa. Git giữ cho các commit của nhánh cục bộ và nhánh từ xa tách biệt rõ ràng với nhau thông qua việc sử dụng các tham chiếu nhánh (branch refs).

Các tham chiếu cho nhánh cục bộ được lưu trữ tại ./.git/refs/heads/. Thực thi lệnh git branch thông thường sẽ in ra danh sách các tham chiếu nhánh cục bộ này. Dưới đây là một ví dụ về đầu ra của lệnh git branch với vài tên nhánh thử nghiệm:
```
git branch
  main
  feature1
  debug2
```
Kiểm tra nội dung của thư mục ./.git/refs/heads/ cũng sẽ tiết lộ kết quả tương tự:
```
ls ./.git/refs/heads/
  main
  feature1
  debug2
```
Các nhánh từ xa (remote branches) hoàn toàn giống như các nhánh cục bộ, ngoại trừ việc chúng ánh xạ tới các commit từ kho chứa của một người khác. Các nhánh từ xa luôn được gắn tiền tố (prefix) bởi tên của chính remote sở hữu chúng để bạn không bị nhầm lẫn với nhánh cục bộ. Giống như nhánh local, Git cũng có các tham chiếu riêng cho nhánh remote. Các tham chiếu nhánh từ xa nằm trong thư mục ./.git/refs/remotes/.

Đoạn mã ví dụ tiếp theo hiển thị các nhánh bạn có thể nhìn thấy sau khi fetch một remote repo được đặt tên là remote-repo:
```
$ git branch -r
# origin/main
# origin/feature1
# origin/debug2
# remote-repo/main
# remote-repo/other-feature
```
Kết quả này hiển thị lại các nhánh cục bộ chúng ta đã xem xét trước đó nhưng giờ đây được gắn thêm tiền tố origin/. Thêm vào đó, chúng ta thấy các nhánh từ xa mới xuất hiện với tiền tố remote-repo/. Bạn có thể checkout một nhánh từ xa y hệt như nhánh cục bộ, nhưng hành động này sẽ đưa bạn vào trạng thái Detached HEAD (giống như khi checkout về một commit cũ). Bạn có thể tạm coi chúng là các nhánh chỉ đọc (read-only branches). Để xem các nhánh từ xa, bạn chỉ cần truyền thêm tham số -r vào lệnh git branch.

Bạn có thể thanh tra các nhánh từ xa bằng các lệnh quen thuộc như git checkout và git log. Nếu bạn chấp thuận những thay đổi mà nhánh từ xa đó nắm giữ, bạn có thể gộp nó vào một nhánh cục bộ bằng một lệnh git merge thông thường. Vì vậy, khác với SVN, việc đồng bộ hóa kho chứa cục bộ của bạn với một kho chứa từ xa thực chất là một quy trình gồm hai bước tách biệt: fetch trước, rồi merge sau. Lệnh git pull đơn thuần chỉ là một phím tắt tiện lợi kết hợp quy trình này lại làm một.

### Git fetch commands and options
- git fetch <remote>: Tải về toàn bộ các nhánh từ một kho chứa chỉ định. Thao tác này cũng đồng thời tải xuống tất cả các commit và file cần thiết từ kho chứa đó.

- git fetch <remote> <branch>: Tương tự như lệnh trên, nhưng thu hẹp phạm vi, chỉ tải về duy nhất một nhánh được chỉ định cụ thể.

- git fetch --all: Một bước đi giúp tải về toàn bộ các nhánh dữ liệu từ tất cả các remote mà bạn đã đăng ký kết nối trong cấu hình.

- git fetch --dry-run: Thực hiện một cú chạy mô phỏng . Git sẽ in ra màn hình các hành động và các nhánh mà nó sẽ tác động trong quá trình fetch chứ chưa thực sự tải dữ liệu thật về máy.

### Git fetch examples
**Kịch bản 1: Fetch một nhánh từ xa của đồng nghiệp**
Ví dụ này sẽ minh họa cách fetch một nhánh từ xa và cập nhật trạng thái làm việc cục bộ của bạn theo nội dung từ xa đó. Giả định rằng chúng ta có một repo trung tâm tên là origin (nơi kho chứa cục bộ được clone về). Hãy giả định thêm một kho chứa từ xa thứ hai tên là coworkers_repo chứa nhánh tính năng feature_branch mà chúng ta cần cấu hình và fetch về máy.

Đầu tiên, chúng ta cần cấu hình kết nối remote bằng lệnh git remote:
```
git remote add coworkers_repo git@bitbucket.org:coworker/coworkers_repo.git
```
Bây giờ, chúng ta truyền tên remote đó vào lệnh git fetch để tải nội dung về:
```
$ git fetch coworkers_repo coworkers/feature_branch
fetching coworkers_repo/feature_branch
```
Hiện tại chúng ta đã có nội dung của nhánh từ xa lưu trữ một cách biệt lập ở máy local, chúng ta cần tích hợp nội dung này vào bản sao làm việc của mình. Hãy bắt đầu bằng cách dùng git checkout để nhảy tới xem nhánh từ xa vừa tải về:
```
$ git checkout coworkers_repo/feature_branch
Note: checking out coworkers_repo/feature_branch'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.
```
Đầu ra của lệnh checkout báo hiệu bạn đang ở trạng thái Detached HEAD. Điều này hoàn toàn bình thường, có nghĩa là con trỏ HEAD đang trỏ vào một tham chiếu nằm ngoài chuỗi lịch sử cục bộ của bạn. Để có thể thoải mái viết code tiếp trên nền tảng nhánh này một cách an toàn mà không sợ bị dọn rác mất dữ liệu, chúng ta tạo một nhánh cục bộ mới từ mốc này:
```
git checkout -b local_feature_branch
```
Lệnh này tạo ra nhánh cục bộ local_feature_branch, cập nhật con trỏ HEAD bám vào nó và bạn có thể tự do phát triển tiếp từ thời điểm này.
**Kịch bản 2: Đồng bộ hóa nhánh Main với máy chủ trung tâm**
Ví dụ này đi qua một quy trình làm việc kinh điển hàng ngày để đồng bộ hóa kho chứa local của bạn với nhánh chính main của repo trung tâm.
```
git fetch origin
```
Màn hình hiển thị danh sách các nhánh được tải về:
```
a1e8fb5..45e66a4 main -> origin/main
a1e8fb5..9e8ab1c develop -> origin/develop
* [new branch] some-feature -> origin/some-feature
```
Để xem những commit nào đã được mọi người thêm vào nhánh main ở trên mạng (upstream main), bạn có thể chạy lệnh git log và sử dụng con trỏ từ xa origin/main làm bộ lọc:
```
git log --oneline main..origin/main
```
(Lệnh này chỉ lọc và hiển thị ra những commit nào có ở trên server origin/main nhưng chưa xuất hiện dưới máy main của bạn).  
Sau khi xem xét, nếu bạn phê duyệt các thay đổi này và muốn gộp chúng vào nhánh main cục bộ của mình, hãy thực thi chuỗi lệnh sau:
```
# 1. Chuyển về nhánh main của mình
git checkout main

# 2. Tiến hành gộp nhánh từ xa vào nhánh mình
git merge origin/main
```
Kết quả là hai nhánh origin/main (ở trên mạng) và nhánh main (dưới máy bạn) giờ đây cùng trỏ vào một commit chung duy nhất, và hệ thống của bạn đã được đồng bộ hóa hoàn toàn với tiến độ phát triển của thượng nguồn.

## Git push
Lệnh git push được sử dụng để tải nội dung từ kho chứa cục bộ (local repository) lên một kho chứa từ xa (remote repository). Đẩy dữ liệu (Pushing) chính là cách bạn chuyển các commit từ kho chứa local sang một remote repo. Nó là bản sao đối nghịch của lệnh git fetch; nhưng trong khi fetch nhập (imports) các commit vào các nhánh cục bộ, thì push lại xuất (exports) các commit ra các nhánh từ xa. Các nhánh từ xa được cấu hình bằng lệnh git remote. Hành động push có khả năng ghi đè lên các thay đổi, vì vậy bạn cần phải hết sức cẩn trọng khi thực hiện.

### Git push usage
- git push <remote> <branch>: Đẩy nhánh được chỉ định lên <remote>, cùng với tất cả các commit và các đối tượng nội bộ cần thiết. Hành động này sẽ tạo ra một nhánh cục bộ tương ứng trong kho chứa đích. Để ngăn bạn ghi đè lên các commit của người khác, Git sẽ không cho phép bạn push nếu nó dẫn đến một cú gộp nhánh không-phải-tiến-thẳng (non-fast-forward merge) tại kho chứa đích.

- git push <remote> --force: Tương tự như lệnh trên, nhưng ép buộc (force) đẩy dữ liệu lên bất kể nó có gây ra một cú gộp non-fast-forward hay không. Tuyệt đối không sử dụng tham số --force trừ khi bạn hoàn toàn chắc chắn mình đang làm gì.

- git push <remote> --all: Đẩy toàn bộ các nhánh cục bộ của bạn lên remote được chỉ định

-git push <remote> --tags: Các nhãn (tags) sẽ không tự động được đẩy lên khi bạn push một nhánh thông thường hoặc khi dùng tùy chọn --all. Tham số --tags sẽ gửi tất cả các nhãn tag cục bộ của bạn lên kho chứa từ xa.

### Git push discussion
Lệnh git push thường được sử dụng phổ biến nhất để xuất bản và tải các thay đổi cục bộ lên một kho chứa trung tâm. Sau khi kho chứa local được sửa đổi, một lệnh push sẽ được thực thi để chia sẻ các sửa đổi đó với các thành viên khác trong đội nhóm.

Sơ đồ trên hiển thị những gì xảy ra khi nhánh main cục bộ của bạn đã tiến xa hơn nhánh main của kho chứa trung tâm, và bạn xuất bản các thay đổi bằng cách chạy lệnh git push origin main. Hãy lưu ý rằng về mặt bản chất, lệnh git push hoạt động hoàn toàn tương tự như việc chạy lệnh git merge main từ bên trong kho chứa từ xa.

### Syncing
git push là một thành phần trong số nhiều công cụ được sử dụng cho toàn bộ quy trình "đồng bộ hóa" (syncing) của Git. Các lệnh đồng bộ hoạt động trên các nhánh từ xa vốn được cấu hình bằng lệnh git remote. Bạn có thể coi git push là lệnh "tải lên" (upload), trong khi git fetch và git pull có thể được hiểu là các lệnh "tải về" (download). Một khi các tập hợp thay đổi (changesets) đã được di chuyển thông qua hành động tải về hoặc tải lên, một lệnh git merge có thể được thực hiện tại điểm đích để tích hợp các thay đổi đó vào code chung.

### Pushing to bare repositories
Một thói quen sử dụng Git hiện đại và thường xuyên được áp dụng là cấu hình một kho chứa từ xa được khởi tạo với tham số --bare để làm kho chứa trung tâm (origin). Kho chứa origin này thường được lưu trữ trực tuyến thông qua một bên thứ ba đáng tin cậy như Bitbucket hay GitHub. Vì hành động push sẽ can thiệp trực tiếp vào cấu trúc nhánh của hệ thống từ xa, nên việc push vào các kho chứa được tạo với cờ --bare là an toàn nhất và phổ biến nhất.

Các kho chứa Bare repos không có thư mục làm việc (working directory), do đó một cú push từ máy bạn lên sẽ không làm xáo trộn hay ảnh hưởng đến bất kỳ nội dung nào đang được gõ dở ở thư mục làm việc trên server.

### Force pushing
- Git ngăn chặn bạn ghi đè lên lịch sử của kho chứa trung tâm bằng cách từ chối các yêu cầu push khi chúng dẫn đến một cú gộp nhánh non-fast-forward. Do đó, nếu lịch sử trên remote đã bị rẽ hướng (diverged) so với lịch sử dưới máy bạn, bạn bắt buộc phải kéo nhánh từ xa đó về (pull), gộp nó vào nhánh cục bộ của mình, rồi sau đó mới thử push lại. Quy trình này tương tự như cách SVN bắt bạn phải đồng bộ với kho chứa trung tâm qua lệnh svn update trước khi được phép commit một changeset.

- Tham số --force sẽ ghi đè và phá vỡ cơ chế bảo vệ này, nó ép buộc nhánh của kho chứa từ xa phải thay đổi để khớp chính xác với nhánh cục bộ dưới máy bạn, đồng thời XÓA BỎ hoàn toàn bất kỳ thay đổi thượng nguồn (upstream changes) nào đã được người khác push lên kể từ lần cuối cùng bạn pull code.

- Trường hợp duy nhất nên dùng Force Push: Đó là khi bạn nhận ra các commit mình vừa push lên mạng bị sai sót nhẹ và bạn đã tự sửa lại chúng dưới máy local bằng lệnh git commit --amend hoặc chạy một cú git rebase tương tác. Tuy nhiên, trước khi gõ --force, bạn phải hoàn toàn chắc chắn rằng chưa có bất kỳ đồng nghiệp nào trong đội kịp kéo (pull) những commit lỗi trước đó của bạn về máy của họ.

### Examples
1. Default git push

Ví dụ dưới đây mô tả một trong những phương pháp chuẩn mực nhất để xuất bản các đóng góp cục bộ lên kho chứa trung tâm.

Đầu tiên, nó đảm bảo nhánh main cục bộ của bạn đã được cập nhật mới nhất bằng cách fetch bản sao của kho chứa trung tâm về, sau đó rebase các thay đổi của bạn lên trên ngọn của chúng. Việc rebase tương tác cũng là một cơ hội tuyệt vời để dọn dẹp, trau chuốt lại các commit trước khi chia sẻ. Cuối cùng, lệnh git push sẽ gửi toàn bộ các commit an toàn từ máy bạn lên server.

```
# 1. Chuyển về nhánh main của bạn
git checkout main

# 2. Tải toàn bộ dữ liệu mới nhất trên server về
git fetch origin main

# 3. Chạy rebase tương tác để nén gọn, dọn sạch lịch sử code local của bạn
git rebase -i origin/main
# (Tại đây bạn có thể Squash commit, sửa lại commit message cho chuẩn chỉ...)

# 4. Chính thức push lên mạng
git push origin main
```

Vì chúng ta đã chủ động bảo đảm nhánh main local được cập nhật đồng bộ hoàn toàn với server từ trước, hành động gộp nhánh lúc này sẽ là một cú gộp tiến thẳng (fast-forward merge), và git push sẽ chạy mượt mà mà không hề đưa ra bất kỳ lời phàn nàn hay cảnh báo chặn lỗi nào.

2. Amended force push
Lệnh git commit chấp nhận tùy chọn --amend để cập nhật lại cú commit ngay trước đó (sửa chính tả lời nhắn hoặc thêm file thiếu). Một khi commit đã bị amend, mã SHA của nó bị đổi và một cú git push thông thường sẽ bị thất bại ngay lập tức vì Git nhận diện nội dung giữa máy bạn và remote đã bị lệch pha rẽ hướng. Bạn bắt buộc phải dùng tham số --force để đẩy commit đã amend này lên:
```
# Sửa đổi file trong repo và add vào hàng chờ
git add .

# Sửa đổi nội dung hoặc lời nhắn của chính cú commit vừa tạo
git commit --amend

# Ép buộc push lên server để ghi đè commit cũ bằng commit mới tinh này
git push --force origin main
```

3. Xóa một nhánh hoặc một Tag trên Server từ xa  

Đôi khi các nhánh cần phải được dọn dẹp sạch sẽ để phục vụ cho mục đích quản lý tổ chức ngăn nắp. Để xóa hoàn toàn một nhánh, bạn phải xóa nó ở cả dưới máy local lẫn trên remote server.

- Xóa nhánh dưới máy local:
```
git branch -D tên_nhánh
```
- Xóa nhánh trên Remote Server từ xa:
```
git push origin :tên_nhánh
```
Cơ chế ngầm: Việc truyền một tên nhánh có gắn dấu hai chấm : ở ngay phía trước vào lệnh git push chính là cách bạn ra lệnh cho Git phải xóa bỏ cái nhánh đó trên remote server origin.

## Git pull
- Lệnh git pull được sử dụng để truy xuất, tải về nội dung từ một kho chứa từ xa (remote repository) và ngay lập tức cập nhật kho chứa cục bộ (local repository) để khớp với nội dung đó. Việc gộp các thay đổi từ thượng nguồn (remote upstream changes) vào kho chứa local của bạn là một công việc cực kỳ quen thuộc trong quy trình làm việc nhóm phối hợp của Git.

Về bản chất, lệnh git pull là sự kết hợp của hai câu lệnh khác: git fetch chạy trước, theo sau đó là git merge.
1. Trong giai đoạn hoạt động đầu tiên, git pull sẽ thực thi một lệnh git fetch có phạm vi thu hẹp trong chính nhánh cục bộ mà con trỏ HEAD đang trỏ vào.

1. Một khi nội dung đã được tải xuống hoàn tất, git pull sẽ lập tức bước vào quy trình gộp nhánh (merge workflow). Một commit gộp (merge commit) mới sẽ được khởi tạo và con trỏ HEAD được cập nhật để trỏ vào commit mới đó.

### How it works

### Cách hoạt động của `git pull`

Lệnh `git pull` dùng để lấy các thay đổi mới nhất từ **remote repository** về máy **local** và gộp vào nhánh hiện tại.

Về bản chất:

```bash
git pull = git fetch + git merge
```

---

#### 1. Bước 1: Git chạy `git fetch`

Đầu tiên, Git sẽ tải các commit mới từ remote repository về máy local.

Ví dụ remote `origin/main` có thêm các commit mới:

```text
A - B - C
```

Lúc này, Git chỉ tải dữ liệu về, chưa gộp ngay vào nhánh local.

---

#### 2. Bước 2: Git chạy `git merge`

Sau khi tải commit mới về, Git sẽ gộp các commit đó vào nhánh local hiện tại.

Giả sử nhánh local cũng có các commit riêng:

```text
E - F - G
```

Khi đó, Git sẽ merge các commit từ remote `A - B - C` với các commit local `E - F - G`.

---

#### 3. Bước 3: Tạo merge commit

Nếu nhánh local và remote đã phát triển theo hai hướng khác nhau, Git sẽ tạo thêm một commit mới để gộp hai nhánh lại.

Commit mới này gọi là **merge commit**.

Ví dụ merge commit được ký hiệu là:

```text
H
```

Commit `H` chứa nội dung đã được gộp từ cả remote và local.

---

#### 4. Kết quả của `git pull`

Khi chạy:

```bash
git pull origin main
```

Git sẽ thực hiện:

```bash
git fetch origin main
git merge origin/main
```

Kết quả là các commit mới từ remote được đưa vào local, đồng thời Git có thể tạo thêm merge commit nếu cần.

---

#### 5. Dùng `git pull --rebase`

Ngoài cách merge mặc định, có thể dùng:

```bash
git pull --rebase origin main
```

Lệnh này vẫn tải commit mới từ remote về, nhưng không tạo merge commit `H`.

Thay vào đó, Git sẽ đưa các commit remote lên trước, sau đó đặt các commit local lên sau.

Ví dụ:

```text
A - B - C - E' - F' - G'
```

Trong đó:

* `A - B - C`: các commit từ remote
* `E' - F' - G'`: phiên bản mới của các commit local

---

#### 6. Kết luận

```text
git pull
= lấy commit từ remote về rồi merge vào local.
```

```text
git pull --rebase
= lấy commit từ remote về rồi đặt commit local lên sau commit remote.
```

Tóm lại:

* `git pull` mặc định có thể tạo **merge commit**.
* `git pull --rebase` giúp lịch sử commit gọn và thẳng hơn.

### Common Options
- git pull <remote>: Tải về bản sao của nhánh hiện tại từ remote chỉ định và ngay lập tức gộp nó vào bản sao cục bộ dưới máy. Lệnh này hoàn toàn tương đương với việc gõ git fetch <remote> rồi gõ tiếp git merge origin/<current-branch>.

- git pull --no-commit <remote>: Tương tự như lệnh mặc định, nó vẫn tải nội dung từ xa về nhưng không tự động tạo ra một commit gộp mới.

- git pull --rebase <remote>: Tương tự như cú pull trước đó nhưng thay vì sử dụng git merge để tích hợp nhánh từ xa với nhánh local, hệ thống sẽ sử dụng git rebase.

- git pull --verbose: Chế độ hiển thị chi tiết (verbose). Git sẽ in ra toàn bộ thông tin về các file đang được tải xuống cũng như các chi tiết ngầm của quy trình gộp nhánh lên màn hình terminal.

### Git pull discussion
Bạn có thể coi git pull chính là phiên bản Git của lệnh svn update. Nó là một cách dễ dàng để đồng bộ hóa kho chứa cục bộ của bạn với các thay đổi ở thượng nguồn.

Ban đầu bạn có thể nghĩ rằng kho chứa của mình đã được đồng bộ hóa hoàn toàn, nhưng sau đó lệnh git fetch tiết lộ rằng phiên bản main trên origin đã tiến xa hơn kể từ lần cuối cùng bạn kiểm tra nó. Ngay sau đó, lệnh git merge lập tức tích hợp nhánh main từ xa vào nhánh main cục bộ của bạn.

### Git pull and syncing
git pull là một thành phần trong số nhiều công cụ chịu trách nhiệm cho toàn bộ quy trình "đồng bộ hóa" (syncing) nội dung từ xa. Lệnh git remote được sử dụng để chỉ định các điểm cuối remote (remote endpoints) nào mà các lệnh đồng bộ sẽ tác động lên. Lệnh git push được sử dụng để tải nội dung lên một kho chứa từ xa.

Lệnh git fetch có thể bị nhầm lẫn với git pull. Cả hai đều được sử dụng để tải nội dung từ xa về máy. Tuy nhiên, giữa chúng có một ranh giới khác biệt cực kỳ quan trọng về mức độ an toàn:

- git fetch là tùy chọn "AN TOÀN": Lệnh này sẽ tải nội dung từ xa về và không làm thay đổi trạng thái của kho chứa cục bộ, giữ nguyên vẹn công việc hiện tại của bạn.

- git pull là tùy chọn "KHÔNG AN TOÀN": Lệnh này vừa tải nội dung về là lập tức cố gắng thay đổi trạng thái cục bộ để khớp với nội dung từ xa đó. Điều này có thể vô tình đẩy kho chứa cục bộ của bạn rơi vào trạng thái xung đột (conflict).

### Pulling via Rebase
Tùy chọn --rebase có thể được sử dụng để đảm bảo một lịch sử tuyến tính bằng cách ngăn chặn các commit gộp không cần thiết. Rất nhiều nhà phát triển thích rebase hơn merge, vì nó giống như việc bạn tuyên bố: "Tôi muốn đặt các thay đổi của tôi lên trên những gì mà tất cả mọi người đã hoàn thành." Xét theo nghĩa này, sử dụng git pull với cờ --rebase thậm chí còn giống với lệnh svn update hơn là một cú git pull thông thường.

Quy trình pull rebase phổ biến đến mức Git cung cấp sẵn một cấu hình chuyên biệt toàn cục cho nó:
```
git config --global branch.autosetuprebase always
```

### Git Pull Examples
1. Hành vi mặc định (Default Behavior)  
```
git pull
```
Việc thực thi lệnh git pull mặc định hoàn toàn tương đương với chuỗi lệnh: git fetch origin HEAD và git merge HEAD (trong đó HEAD chính là tham chiếu trỏ vào nhánh hiện tại của bạn).

2. Git pull trên các Remote chỉ định  
```
git checkout new_feature
git pull <remote repo>
```
Ví dụ này đầu tiên thực hiện lệnh git checkout để chuyển sang nhánh <new_feature>. Ngay sau đó, lệnh git pull được thực thi và truyền vào tên của <remote_repo>. Hành động này sẽ hiểu ngầm là tải xuống nhánh new_feature từ <remote_repo>. Một khi quá trình tải về hoàn tất, nó sẽ tự động kích hoạt một quy trình git merge.

3. Đồng bộ bằng Rebase thay vì Merge  
Ví dụ dưới đây minh họa cách đồng bộ hóa với nhánh chính của kho chứa trung tâm bằng chiến lược rebase:
```
git checkout main
git pull --rebase origin
```
Thao tác này đơn giản chỉ là chuyển các thay đổi cục bộ của bạn lên trên những đóng góp mà mọi người khác đã thực hiện.

## Making a Pull Request
Pull request (Yêu cầu kéo) là một tính năng giúp các lập trình viên cộng tác với nhau dễ dàng hơn khi sử dụng Bitbucket. Chúng cung cấp một giao diện web thân thiện với người dùng để thảo luận về các thay đổi được đề xuất trước khi chính thức tích hợp chúng vào dự án chính thức.

Ở dạng đơn giản nhất, pull request là một cơ chế để một lập trình viên thông báo cho các thành viên trong đội rằng họ đã hoàn thành một tính năng. Khi nhánh tính năng (feature branch) đã sẵn sàng, lập trình viên sẽ gửi một pull request thông qua tài khoản Bitbucket của họ. Việc này giúp mọi người liên quan biết rằng họ cần rà soát (review) lại code và gộp (merge) nó vào nhánh chính main.

Tuy nhiên, pull request không chỉ đơn thuần là một thông báo — nó là một diễn đàn chuyên dụng để thảo luận về tính năng được đề xuất. Nếu có bất kỳ vấn đề gì với các thay đổi, đồng nghiệp có thể gửi phản hồi ngay trong pull request và thậm chí tinh chỉnh tính năng bằng cách đẩy lên (push) các commit bổ sung. Toàn bộ hoạt động này được theo dõi trực tiếp ngay bên trong pull request.

So với các mô hình cộng tác khác, giải pháp chính thức này cho việc chia sẻ các commit giúp quy trình làm việc trở nên hợp lý và tinh gọn hơn nhiều. SVN và Git đều có thể tự động gửi email thông báo bằng một đoạn script đơn giản; tuy nhiên, khi cần thảo luận về các thay đổi, các lập trình viên thường phải dựa vào các luồng email. Việc này có thể trở nên lộn xộn, đặc biệt là khi có các commit bổ sung tiếp theo. Pull request gom tất cả các chức năng này vào một giao diện web thân thiện ngay cạnh các kho chứa Bitbucket của bạn.

### Anatomy of a Pull Request
Khi bạn gửi một pull request, tất cả những gì bạn đang làm là yêu cầu một lập trình viên khác (ví dụ: người quản trị dự án) kéo (pull) một nhánh từ kho chứa của bạn vào kho chứa của họ. Điều này có nghĩa là bạn cần cung cấp 4 thông tin sau để tạo một pull request:

1. Source repository (Kho chứa nguồn).

1. Source branch (Nhánh nguồn).

1. estination repository (Kho chứa đích).

1. Destination branch (Nhánh đích).

Nhiều giá trị trong số này sẽ được Bitbucket tự động thiết lập sẵn ở mức hợp lý. Tuy nhiên, tùy thuộc vào quy trình làm việc cộng tác của bạn, đội nhóm của bạn có thể cần phải chỉ định các giá trị khác nhau. Sơ đồ cấu trúc thường hiển thị một pull request yêu cầu gộp một nhánh tính năng vào nhánh main chính thức, nhưng cũng có rất nhiều cách khác để sử dụng pull request.

### How it works

Pull request có thể được sử dụng kết hợp với Quy trình nhánh tính năng (Feature Branch Workflow), Quy trình Gitflow (Gitflow Workflow), hoặc Quy trình phân nhánh bản sao (Forking Workflow). Tuy nhiên, một pull request bắt buộc phải yêu cầu có hai nhánh riêng biệt hoặc hai kho chứa riêng biệt, do đó chúng sẽ không hoạt động với Quy trình trung tâm (Centralized Workflow). Việc sử dụng pull request với mỗi quy trình này sẽ hơi khác nhau một chút, nhưng quy trình tổng quát diễn ra như sau:

Lập trình viên tạo tính năng trên một nhánh chuyên dụng trong repo cục bộ của họ.

Lập trình viên đẩy (push) nhánh đó lên một kho chứa Bitbucket công khai.

Lập trình viên tạo và gửi một pull request thông qua Bitbucket.

Toàn bộ đội nhóm tiến hành rà soát code, thảo luận và thay đổi nó.

Người quản trị dự án gộp (merge) tính năng vào kho chứa chính thức và đóng pull request lại.

Phần còn lại của tài liệu này mô tả cách pull request được tận dụng trong các quy trình cộng tác khác nhau.

### Feature Branch Workflow With Pull Requests
Quy trình Feature Branch sử dụng một kho chứa Bitbucket dùng chung để quản lý việc cộng tác, và các lập trình viên tạo các tính năng trên các nhánh cô lập. Tuy nhiên, thay vì gộp ngay chúng vào nhánh main, các lập trình viên nên mở một pull request để khởi xướng một cuộc thảo luận xoay quanh tính năng đó trước khi nó được tích hợp vào nền tảng code chính.

Vì chỉ có duy nhất một kho chứa công khai trong Quy trình Feature Branch, nên kho chứa đích (destination repository) và kho chứa nguồn (source repository) của pull request sẽ luôn luôn giống nhau. Thông thường, lập trình viên sẽ chỉ định nhánh tính năng của họ làm nhánh nguồn và nhánh main làm nhánh đích.

Sau khi nhận được pull request, người quản trị dự án phải quyết định xem sẽ xử lý thế nào. Nếu tính năng đã sẵn sàng, họ chỉ cần gộp nó vào main và đóng pull request. Nhưng nếu có vấn đề với các thay đổi được đề xuất, họ có thể đăng phản hồi vào pull request. Các commit bổ sung sau đó sẽ hiển thị ngay bên cạnh các bình luận liên quan.

Bạn cũng hoàn toàn có thể gửi một pull request cho một tính năng chưa hoàn thiện. Ví dụ, nếu một lập trình viên gặp khó khăn trong việc triển khai một yêu cầu cụ thể, họ có thể gửi một pull request chứa phần công việc đang làm dở (work-in-progress). Các lập trình viên khác sau đó có thể đưa ra gợi ý ngay bên trong pull request, hoặc thậm chí tự sửa vấn đề bằng các commit bổ sung.

### Gitflow Workflow With Pull Requests
Trong Quy trình Forking, một lập trình viên sẽ đẩy một tính năng đã hoàn thành lên kho chứa công khai của riêng họ thay vì một kho chứa dùng chung. Sau đó, họ gửi một pull request để thông báo cho người quản trị dự án biết rằng nó đã sẵn sàng để rà soát.

Khía cạnh thông báo của pull request đặc biệt hữu ích trong quy trình này vì người quản trị dự án không có cách nào biết được khi nào một lập trình viên khác đã thêm các commit vào kho chứa Bitbucket cá nhân của họ.

Vì mỗi lập trình viên có một kho chứa công khai của riêng mình, nên kho chứa nguồn của pull request sẽ khác với kho chứa đích của nó. Kho chứa nguồn là kho chứa công khai của lập trình viên và nhánh nguồn là nhánh chứa các thay đổi được đề xuất. Nếu lập trình viên đang cố gắng gộp tính năng vào nền tảng code chính thức, thì kho chứa đích là dự án chính thức và nhánh đích là main.

Pull request cũng có thể được sử dụng để cộng tác với các lập trình viên khác bên ngoài dự án chính thức. Ví dụ, nếu một lập trình viên đang cùng thực hiện một tính năng với một người bạn trong đội, họ có thể gửi một pull request với điểm đích là kho chứa Bitbucket của người bạn đó thay vì dự án chính thức. Lúc này họ sẽ dùng chung một nhánh tính năng cho cả nhánh nguồn và nhánh đích.

Hai lập trình viên có thể thảo luận và phát triển tính năng ngay bên trong pull request đó. Khi họ hoàn thành, một trong hai người sẽ gửi một pull request khác yêu cầu gộp tính năng vào nhánh main chính thức của dự án. Sự linh hoạt này biến pull request trở thành một công cụ cộng tác cực kỳ mạnh mẽ trong quy trình Forking.

### Example
Ví dụ dưới đây minh họa cách pull request được sử dụng trong Quy trình Forking. Nó áp dụng tương tự cho các lập trình viên làm việc trong các đội nhóm nhỏ và cho một lập trình viên bên thứ ba đang đóng góp vào một dự án mã nguồn mở.

Trong ví dụ này, Mary là một lập trình viên, và John là người quản trị dự án. Cả hai đều có kho chứa Bitbucket công khai của riêng mình, và kho chứa của John nắm giữ dự án chính thức.

1. Mary fork dự án chính thức  
Để bắt đầu làm việc trong dự án, Mary đầu tiên cần phải sao chép (fork) kho chứa Bitbucket của John. Cô ấy có thể làm điều này bằng cách đăng nhập vào Bitbucket, điều hướng đến kho chứa của John và nhấp vào nút Fork.

Sau khi điền tên và mô tả cho kho chứa được fork, cô ấy sẽ có một bản sao của dự án nằm trên máy chủ từ xa của riêng mình.

2. Mary clone kho chứa Bitbucket của cô ấy  
Tiếp theo, Mary cần clone kho chứa Bitbucket mà cô ấy vừa fork về máy. Việc này sẽ cho cô ấy một bản sao làm việc của dự án trên máy tính cục bộ của mình. Cô ấy chạy câu lệnh:
```
git clone https://user@bitbucket.org/user/repo.git
```
Hãy nhớ rằng lệnh git clone sẽ tự động tạo ra một remote tên là origin trỏ ngược về kho chứa đã fork của Mary.

3. Mary phát triển một tính năng mới  
Trước khi bắt đầu viết bất kỳ đoạn code nào, Mary cần tạo một nhánh mới cho tính năng này. Nhánh này chính là nhánh sẽ được dùng làm nhánh nguồn cho pull request.

```
git checkout -b some-feature
# Tiến hành chỉnh sửa code
git commit -a -m "Add first draft of some feature"
```
Mary có thể sử dụng bao nhiêu commit tùy ý để tạo ra tính năng. Và nếu lịch sử của tính năng đó bừa bộn hơn mức cô ấy muốn, cô ấy có thể sử dụng lệnh git rebase tương tác để xóa bỏ hoặc nén gọn (squash) các commit không cần thiết. Đối với các dự án lớn, việc dọn sạch lịch sử của một tính năng giúp người quản trị dự án dễ dàng theo dõi những gì đang diễn ra trong pull request hơn rất nhiều.

4. Mary push tính năng lên kho chứa Bitbucket của cô ấy  
Sau khi tính năng hoàn tất, Mary đẩy nhánh tính năng lên kho chứa Bitbucket của riêng mình (không phải kho chứa chính thức) bằng một lệnh git push đơn giản:
```
git push origin some-feature
```
Điều này giúp các thay đổi của cô ấy sẵn có để người quản trị dự án (hoặc bất kỳ cộng tác viên nào cần quyền truy cập) có thể xem được.

5. Mary tạo pull request  

Sau khi Bitbucket đã nhận được nhánh tính năng của cô ấy, Mary có thể tạo pull request thông qua tài khoản Bitbucket của mình bằng cách điều hướng đến kho chứa được fork và nhấp vào nút Pull request ở góc trên cùng bên phải. Biểu mẫu xuất hiện sau đó sẽ tự động đặt kho chứa của Mary làm kho chứa nguồn, và yêu cầu cô ấy chỉ định nhánh nguồn, kho chứa đích và nhánh đích.

Mary muốn gộp tính năng của mình vào nền tảng code chính, vì vậy nhánh nguồn là nhánh tính năng của cô ấy, kho chứa đích là kho chứa công khai của John, và nhánh đích là main. Cô ấy cũng cần cung cấp tiêu đề và mô tả cho pull request. Nếu có những người khác ngoài John cần phê duyệt code, cô ấy có thể điền tên họ vào trường Reviewers.

Sau khi cô ấy tạo pull request, một thông báo sẽ được gửi đến John qua bảng tin Bitbucket của anh ấy và (tùy chọn) qua email.

6. John rà soát (review) pull request

John có thể truy cập tất cả các pull request mà mọi người đã gửi bằng cách nhấp vào tab Pull request trong kho chứa Bitbucket của chính mình. Nhấp vào pull request của Mary sẽ hiển thị cho anh ấy phần mô tả của pull request, lịch sử commit của tính năng, và một bảng so sánh thay đổi (diff) của toàn bộ nội dung bên trong.

Nếu anh ấy nghĩ rằng tính năng đã sẵn sàng để gộp vào dự án, tất cả những gì anh ấy cần làm là nhấn vào nút Merge để phê duyệt pull request và gộp tính năng của Mary vào nhánh main của mình.

Tuy nhiên, đối với ví dụ này, hãy giả sử John tìm thấy một lỗi nhỏ (bug) trong code của Mary và yêu cầu cô ấy sửa nó trước khi gộp vào. Anh ấy có thể đăng một bình luận tổng quát cho toàn bộ pull request, hoặc có thể chọn một commit cụ thể trong lịch sử tính năng để bình luận trực tiếp vào đó.

7. Mary thêm một commit bổ sung (follow-up commit)  

Nếu Mary có bất kỳ câu hỏi nào về phản hồi của John, cô ấy có thể phản hồi ngay bên trong pull request, biến nó thành một diễn đàn thảo luận cho tính năng của mình.

Để sửa lỗi, Mary thêm một commit khác vào nhánh tính năng của mình và push nó lên kho chứa Bitbucket cá nhân, giống hệt như cô ấy đã làm ở lần đầu tiên. Commit này sẽ tự động được cập nhật thêm vào pull request ban đầu, và John có thể rà soát lại các thay đổi mới này ngay bên cạnh bình luận gốc của mình.

8. John chấp nhận pull request

Cuối cùng, John chấp nhận các thay đổi, gộp nhánh tính năng vào main, và đóng pull request lại. Tính năng hiện đã được tích hợp vào dự án chính thức, và bất kỳ lập trình viên nào khác đang làm việc trong dự án đều có thể kéo nó về kho chứa cục bộ của họ bằng lệnh git pull tiêu chuẩn.

## Overview using Git branch
Tài liệu này là một bài đánh giá chuyên sâu về lệnh git branch và thảo luận về mô hình phân nhánh tổng thể của Git. Phân nhánh (Branching) là một tính năng có sẵn trong hầu hết các hệ thống quản lý phiên bản hiện đại. Việc phân nhánh trong các hệ thống VCS khác có thể là một thao tác rất tốn kém cả về thời gian lẫn dung lượng ổ cứng. Trong Git, các nhánh là một phần không thể thiếu trong quy trình phát triển hàng ngày của bạn.

Các nhánh Git về mặt bản chất là một con trỏ trỏ tới một ảnh chụp (snapshot) các thay đổi của bạn. Khi bạn muốn thêm một tính năng mới hoặc sửa một lỗi (bug) — bất kể lớn hay nhỏ — bạn đều sinh ra một nhánh mới để bao bọc các thay đổi đó. Điều này giúp ngăn chặn các đoạn code kém ổn định bị gộp vào nền tảng code chính, đồng thời mang lại cho bạn cơ hội để dọn dẹp lịch sử trước khi gộp nó vào nhánh chính.

Sơ đồ trên trực quan hóa một kho chứa với hai dòng phát triển biệt lập, một dòng dành cho một tính năng nhỏ và một dòng dành cho một tính năng chạy dài hạn. Bằng cách phát triển chúng trên các nhánh, bạn không chỉ có thể làm việc song song trên cả hai tính năng mà còn giữ cho nhánh chính luôn sạch sẽ, không bị ảnh hưởng bởi các đoạn code chưa kiểm định.

Cách thức triển khai phía sau các nhánh Git gọn nhẹ hơn rất nhiều so với mô hình của các hệ thống quản lý phiên bản khác. Thay vì sao chép các file từ thư mục này sang thư mục khác, Git lưu trữ một nhánh như một tham chiếu (reference) đến một commit. Theo nghĩa này, một nhánh đại diện cho ngọn của một chuỗi các commit — nó không phải là một thùng chứa (container) chứa các commit. Lịch sử của một nhánh được suy diễn ra thông qua các mối quan hệ liên kết giữa các commit.

Hãy nhớ rằng các nhánh Git không giống như các nhánh SVN. Trong khi các nhánh SVN chỉ được sử dụng để ghi nhận các nỗ lực phát triển quy mô lớn thỉnh thoảng mới có, thì các nhánh Git là một phần không thể tách rời trong quy trình làm việc hàng ngày của bạn.

### How it works
Một nhánh đại diện cho một dòng phát triển độc lập. Các nhánh đóng vai trò như một sự trừu tượng hóa cho toàn bộ quy trình chỉnh sửa / đưa vào hàng chờ / commit (edit/stage/commit). Bạn có thể coi chúng là một cách để yêu cầu một thư mục làm việc, vùng đệm hàng chờ và lịch sử dự án hoàn toàn mới tinh. Các commit mới sẽ được ghi lại vào lịch sử của nhánh hiện tại, tạo ra một sự rẽ nhánh (fork) trong lịch sử của dự án.

Lệnh git branch cho phép bạn tạo, liệt kê, đổi tên và xóa các nhánh. Nó không cho phép bạn chuyển đổi giữa các nhánh hoặc gắn một lịch sử đã rẽ nhánh quay trở lại làm một. Vì lý do này, git branch được tích hợp chặt chẽ với các lệnh git checkout và git merge.

### Common options
- git branch: Liệt kê tất cả các nhánh trong kho chứa của bạn. Lệnh này đồng nghĩa với git branch --list.

- git branch <branch>: Tạo một nhánh mới có tên là <branch>. Lệnh này chỉ tạo chứ không tự động checkout chuyển sang nhánh mới đó.

- git branch -d <branch>: Xóa nhánh được chỉ định. Đây là một thao tác "an toàn" vì Git sẽ ngăn bạn xóa nhánh nếu nó chứa các thay đổi chưa được gộp (unmerged changes).

- git branch -D <branch>: Ép buộc xóa nhánh được chỉ định, bất kể nó đã được gộp hay chưa. Đây là câu lệnh cần dùng nếu bạn muốn vứt bỏ vĩnh viễn toàn bộ các commit gắn liền với một dòng phát triển cụ thể nào đó.

- git branch -m <branch>: Đổi tên của nhánh hiện tại thành <branch>.

- git branch -a: Liệt kê tất cả các nhánh từ xa (remote branches).

### Creating branches
Điều quan trọng cần thấu hiểu là các nhánh chỉ đơn thuần là những con trỏ trỏ đến các commit. Khi bạn tạo một nhánh, tất cả những gì Git cần làm là tạo ra một con trỏ mới, nó hoàn toàn không làm thay đổi kho chứa theo bất kỳ cách nào khác.

Nếu bạn bắt đầu với một kho chứa trông như thế này:

Sau đó, bạn tạo một nhánh bằng câu lệnh sau:
```
git branch crazy-experiment
```
Lịch sử kho chứa vẫn hoàn toàn giữ nguyên không đổi. Tất cả những gì bạn nhận được là một con trỏ mới tinh cùng trỏ vào cú commit hiện tại:

Lưu ý rằng hành động này chỉ mới tạo ra nhánh mới. Để bắt đầu thêm các commit vào nhánh đó, bạn cần phải lựa chọn nó bằng lệnh git checkout, và sau đó mới sử dụng các lệnh git add và git commit tiêu chuẩn.

### Creating remote branches
Cho đến nay, các ví dụ trên đều minh họa cho các thao tác với nhánh cục bộ. Lệnh git branch cũng hoạt động với các nhánh từ xa. Để thao tác trên các nhánh từ xa, một remote repo phải được cấu hình và thêm vào cài đặt của repo cục bộ trước.

```
# Thêm remote repo vào cấu hình của repo cục bộ
$ git remote add new-remote-repo https://bitbucket.com/user/repo.git

# Đẩy nhánh crazy-experiment lên remote repo đó
$ git push new-remote-repo crazy-experiment
```
Lệnh này sẽ đẩy một bản sao của nhánh cục bộ crazy-experiment lên kho chứa từ xa <remote>.

### Deleting branches
Một khi bạn đã hoàn thành công việc trên một nhánh và đã gộp nó vào nền tảng code chính, bạn có thể tự do xóa nhánh đó đi mà không sợ làm mất bất kỳ lịch sử nào:
```
git branch -d crazy-experiment
```
Tuy nhiên, nếu nhánh đó chưa được gộp, câu lệnh trên sẽ trả về một thông báo lỗi:
```
error: The branch 'crazy-experiment' is not fully merged.
If you are sure you want to delete it, run 'git branch -D crazy-experiment'.
```
Cơ chế này bảo vệ bạn khỏi việc mất quyền truy cập vào toàn bộ dòng phát triển đó. Nếu bạn thực sự muốn xóa nhánh (ví dụ: đó là một cuộc thử nghiệm thất bại), bạn có thể dùng cờ chữ hoa -D:
```
git branch -D crazy-experiment
```
Lệnh này xóa nhánh bất kể trạng thái của nó và không đưa ra cảnh báo, vì vậy hãy sử dụng nó một cách khôn ngoan.

Các lệnh phía trên dùng để xóa bản sao cục bộ của một nhánh. Nhánh đó có thể vẫn đang tồn tại trên các remote repos. Để xóa một nhánh từ xa, hãy thực thi lệnh sau:
```
git push origin --delete crazy-experiment
```
hoặc:
```
git push origin :crazy-experiment
```
Hành động này sẽ gửi một tín hiệu xóa đến kho chứa từ xa origin để kích hoạt việc xóa bỏ nhánh crazy-experiment ở trên mạng.

## Git checkout

Tài liệu này là một bài phân tích sâu về lệnh git checkout. Nó sẽ bao gồm các ví dụ sử dụng thực tế và các trường hợp biên (edge cases).

Theo thuật ngữ của Git, một cú "checkout" là hành động chuyển đổi giữa các phiên bản khác nhau của một thực thể mục tiêu. Lệnh git checkout hoạt động trên ba thực thể riêng biệt: các file, các commit, và các nhánh. Bên cạnh định nghĩa về "checkout", cụm từ "checking out" thường được sử dụng phổ biến để ám chỉ hành động thực thi lệnh git checkout.

Trong các chương trước về chủ đề Hủy bỏ Thay đổi, chúng ta đã thấy cách git checkout được sử dụng để xem lại các commit cũ. Trọng tâm của phần lớn tài liệu này sẽ dành riêng cho các thao tác checkout trên các nhánh (branches).

**Điểm khác biệt cốt lõi:** Việc checkout một nhánh rất giống với việc checkout các commit và file cũ ở chỗ thư mục làm việc (working directory) sẽ được cập nhật để khớp với nhánh/phiên bản được chọn; tuy nhiên, các thay đổi mới sau đó sẽ được lưu lại vào lịch sử dự án — nghĩa là, đây không phải là một thao tác chỉ đọc (read-only).

### Checking out branches
Lệnh git checkout cho phép bạn điều hướng di chuyển giữa các nhánh được tạo ra bởi lệnh git branch. Việc checkout một nhánh sẽ cập nhật các file trong thư mục làm việc sao cho khớp với phiên bản được lưu trữ tại nhánh đó, đồng thời ra lệnh cho Git ghi nhận tất cả các commit mới tiếp theo lên chính nhánh này. Hãy nghĩ về nó như một cách để bạn lựa chọn dòng phát triển nào mà mình muốn tập trung làm việc.

Việc sở hữu một nhánh chuyên dụng cho từng tính năng mới là một sự chuyển dịch mạnh mẽ so với quy trình làm việc truyền thống của SVN. Nó giúp cho việc thử nghiệm các ý tưởng mới trở nên vô cùng dễ dàng mà không sợ làm phá hủy các chức năng sẵn có, và giúp bạn có thể làm việc trên nhiều tính năng hoàn toàn không liên quan đến nhau cùng một lúc. Thêm vào đó, các nhánh cũng tạo điều kiện thuận lợi cho nhiều quy trình làm việc cộng tác nhóm.

**Tránh nhầm lẫn:** Lệnh git checkout đôi khi có thể bị nhầm lẫn với git clone. Sự khác biệt giữa hai lệnh này là: clone chịu trách nhiệm nạp mã nguồn từ một kho chứa từ xa về máy, trong khi checkout hoạt động để chuyển đổi giữa các phiên bản code đã có sẵn trên hệ thống cục bộ.

### Usage: Existing branches
Giả định rằng kho chứa bạn đang làm việc đã có sẵn các nhánh, bạn có thể chuyển đổi qua lại giữa các nhánh này bằng git checkout. Để tìm xem có những nhánh nào đang khả dụng và tên của nhánh hiện tại là gì, hãy thực thi lệnh git branch.

```
# Xem danh sách nhánh hiện có
$ git branch
  main
  another_branch
  feature_inprogress_branch

# Chuyển sang nhánh feature_inprogress_branch
$ git checkout feature_inprogress_branch
```
Ví dụ trên minh họa cách xem danh sách các nhánh khả dụng bằng lệnh git branch, và chuyển sang một nhánh được chỉ định, trong trường hợp này là feature_inprogress_branch.

### New branches
git checkout hoạt động tay trong tay cùng với git branch. Lệnh git branch có thể được dùng để tạo một nhánh mới. Khi bạn muốn bắt đầu một tính năng mới, bạn tạo một nhánh mới từ nhánh main bằng lệnh git branch new_branch. Sau khi tạo xong, bạn có thể dùng lệnh git checkout new_branch để chuyển sang nhánh đó.

Bên cạnh đó, lệnh git checkout tiếp nhận một tham số là -b hoạt động như một phương thức phím tắt tiện lợi giúp vừa tạo nhánh mới vừa lập tức chuyển sang nhánh đó. Bạn có thể làm việc trên nhiều tính năng trong một kho chứa duy nhất bằng cách chuyển đổi giữa chúng qua git checkout.

```
git checkout -b <new-branch>
```
Ví dụ trên đồng thời tạo mới và checkout sang nhánh <new-branch>. Cờ -b là một phím tắt tiện ích ra lệnh cho Git chạy git branch <new-branch> trước khi chạy git checkout <new-branch>.

```
git checkout -b <new-branch> <existing-branch>
```
Mặc định, lệnh git checkout -b sẽ lấy con trỏ HEAD hiện tại làm nền móng để tách nhánh mới. Tuy nhiên, bạn có thể truyền thêm một tham số nhánh tùy chọn vào sau. Ở ví dụ ngay trên, <existing-branch> được truyền vào để làm nền móng tách nhánh <new-branch> thay vì dùng con trỏ HEAD hiện tại.

### Switching branches
Chuyển đổi nhánh là một thao tác rất thẳng thắn. Việc thực thi câu lệnh sau đây sẽ chỉ định con trỏ HEAD trỏ vào ngọn đỉnh (tip) của nhánh <branchname>.
```
git checkout <branchname>
```
Git theo dõi toàn bộ lịch sử của các thao tác checkout này trong bảng nhật ký tham chiếu reflog. Bạn có thể gõ git reflog để xem lại lịch sử dịch chuyển này.

### Git checkout a remote branch
Khi cộng tác với một đội nhóm, việc sử dụng các kho chứa từ xa là điều rất phổ biến. Những kho chứa này có thể được lưu trữ dùng chung trên mạng hoặc có thể là bản sao cục bộ của một đồng nghiệp khác. Mỗi kho chứa từ xa sẽ nắm giữ một tập hợp các nhánh của riêng nó. Để có thể checkout một nhánh từ xa, trước tiên bạn bắt buộc phải nạp nội dung của nhánh đó về máy.
```
git fetch --all
```
Trong các phiên bản hiện đại của Git, bạn có thể tiến hành checkout nhánh từ xa giống hệt như cách làm với một nhánh cục bộ:
```
git checkout <remotebranch>
```
Các phiên bản Git cũ hơn đòi hỏi bạn phải tạo một nhánh mới dựa trên nhánh từ xa đó một cách tường minh:
```
git checkout -b <remotebranch> origin/<remotebranch>
```
Ngoài ra, bạn cũng có thể checkout một nhánh cục bộ mới và thực hiện reset cứng nó về commit mới nhất của nhánh từ xa:
```
git checkout -b <branchname>
git reset --hard origin/<branchname>
```
### Detached HEADs
Bây giờ, sau khi đã đi qua ba cách sử dụng chính của git checkout trên các nhánh, điều quan trọng tiếp theo là thảo luận về trạng thái "detached HEAD".

Hãy nhớ rằng HEAD là cách Git dùng để tham chiếu đến snapshot hiện tại. Về mặt nội bộ, lệnh git checkout đơn giản chỉ cập nhật con trỏ HEAD để trỏ vào một nhánh hoặc một commit được chỉ định. Khi nó trỏ vào một nhánh, Git hoạt động bình thường, nhưng khi bạn checkout thẳng về một mã commit cụ thể, hệ thống sẽ rơi vào trạng thái "detached HEAD".

Hệ thống sẽ đưa ra một cảnh báo cho bạn biết rằng mọi thứ bạn đang làm đều bị "tách rời" khỏi phần phát triển còn lại của lịch sử dự án. Nếu bạn bắt đầu phát triển một tính năng trong khi đang ở trạng thái detached HEAD, sẽ không có một nhánh nào giúp bạn bám đường để quay trở lại với nó. Khi bạn bắt buộc phải checkout sang một nhánh khác (ví dụ: để gộp tính năng của bạn vào code chung), bạn sẽ không còn bất kỳ manh mối hay tham chiếu nào để trỏ ngược lại tính năng mình vừa viết nữa:

**Quy tắc cốt lõi:** Quy trình phát triển code của bạn luôn luôn phải diễn ra trên một nhánh — tuyệt đối không bao giờ được viết code tiếp trong trạng thái detached HEAD. Điều này bảo đảm rằng bạn luôn luôn sở hữu một tham chiếu để tìm lại các commit mới của mình. Tuy nhiên, nếu bạn chỉ đơn thuần là muốn lùi thời gian về để xem lại một commit cũ, thì việc bạn có đang ở trạng thái detached HEAD hay không không thực sự quan trọng.

## Git merge

Gộp nhánh (Merging) là cách Git đưa một lịch sử dự án đã rẽ nhánh (forked history) gắn kết lại làm một. Lệnh git merge cho phép bạn lấy các dòng phát triển độc lập được tạo ra bởi lệnh git branch và tích hợp chúng vào một nhánh duy nhất.

Lưu ý tối quan trọng: Tất cả các lệnh gộp nhánh được trình bày dưới đây đều thực hiện gộp vào nhánh hiện tại (nhánh bạn đang đứng). Nhánh hiện tại sẽ được cập nhật dữ liệu để phản ánh kết quả gộp, trong khi nhánh mục tiêu (nhánh được đem đi gộp) sẽ hoàn toàn không bị ảnh hưởng. Điều này có nghĩa là git merge thường được sử dụng phối hợp cùng với git checkout để chọn nhánh nhận dữ liệu, và git branch -d để xóa bỏ nhánh mục tiêu sau khi nó đã lỗi thời.

### How it works

git merge sẽ kết hợp nhiều chuỗi commit lại thành một lịch sử thống nhất. Trong các kịch bản phổ biến nhất, git merge được dùng để kết hợp hai nhánh. Lệnh git merge tiếp nhận hai con trỏ commit (thường là ngọn đỉnh của hai nhánh) và tiến hành tìm kiếm một commit nền tảng chung (common base commit) giữa chúng. Một khi Git tìm thấy commit tổ tiên chung này, nó sẽ tạo ra một "commit gộp" (merge commit) mới để kết hợp các thay đổi của từng chuỗi commit lại với nhau.

Giả sử chúng ta có một nhánh mới tên là feature được tách ra từ nhánh main. Bây giờ chúng ta muốn gộp nhánh feature này vào main. Việc kích hoạt lệnh gộp sẽ tích hợp nhánh chỉ định feature vào nhánh hiện tại (ở đây ta giả định là main). Git sẽ tự động xác định thuật toán gộp phù hợp.

Các commit gộp (Merge commits) rất độc đáo so với các commit thông thường ở chỗ chúng có tới hai commit cha (parent commits). Khi tạo một commit gộp, Git sẽ cố gắng tự động trộn các lịch sử riêng biệt cho bạn. Nếu Git phát hiện ra một đoạn dữ liệu bị thay đổi ở cả hai lịch sử, nó sẽ không thể tự động kết hợp chúng. Tình huống này được gọi là xung đột phiên bản (version control conflict) và Git sẽ cần sự can thiệp của người dùng để tiếp tục.

### Preparing to merge
Trước khi thực hiện gộp nhánh, có một vài bước chuẩn bị cần thực hiện để đảm bảo quá trình gộp diễn ra suôn sẻ:

1. Xác nhận nhánh nhận dữ liệu: Thực thi lệnh git status để đảm bảo con trỏ HEAD đang trỏ đúng vào nhánh muốn nhận dữ liệu gộp. Nếu cần, hãy gõ git checkout <receiving> để chuyển sang nhánh nhận. Trong trường hợp này, chúng ta sẽ gõ: git checkout main.

1. Tải về các commit từ xa mới nhất: Hãy đảm bảo nhánh nhận và nhánh đem đi gộp đều đã được cập nhật các thay đổi mới nhất trên mạng. Thực thi lệnh git fetch để tải về các commit từ xa mới nhất. Khi lệnh fetch hoàn tất, hãy bảo đảm nhánh main có các cập nhật mới nhất bằng cách gõ git pull.

Sau khi các bước chuẩn bị trên đã hoàn thành, một lệnh gộp nhánh có thể được khởi động bằng cách thực thi cú pháp: git merge <branch name> (trong đó <branch name> là tên của nhánh sẽ được đem đi gộp vào nhánh hiện tại).

### Fast forward merge
Fast-forward merge có thể xảy ra khi có một đường thẳng tuyến tính chạy liên tục từ ngọn của nhánh hiện tại đến ngọn của nhánh mục tiêu. Thay vì thực hiện gộp nhánh một cách "thực sự", tất cả những gì Git cần làm để tích hợp lịch sử chỉ là di chuyển fast forward con trỏ của nhánh hiện tại lên bằng với con trỏ ngọn của nhánh mục tiêu. Hành động này kết hợp hai lịch sử một cách hiệu quả, vì tất cả các commit có thể tiếp cận được từ nhánh mục tiêu giờ đây đều khả dụng thông qua nhánh hiện tại.
Tuy nhiên, một cú gộp tiến thẳng sẽ không thể thực hiện được nếu các nhánh đã bị rẽ hướng (diverged). Khi không có một đường thẳng tuyến tính nối tới nhánh mục tiêu, Git không có lựa chọn nào khác ngoài việc kết hợp chúng thông qua một cú Gộp 3 đường (3-way merge).
Cơ chế gộp 3 đường sử dụng một commit chuyên dụng để buộc chặt hai lịch sử lại với nhau. Tên gọi này xuất phát từ thực tế là Git phải sử dụng tới ba commit khác nhau để tạo ra commit gộp: hai con trỏ ngọn của hai nhánh và một commit tổ tiên chung của chúng.
Mặc dù bạn có thể sử dụng bất kỳ chiến lược nào trong hai chiến lược gộp này, nhiều nhà phát triển thích sử dụng gộp fast-forward (được hỗ trợ thông qua rebase) cho các tính năng nhỏ hoặc sửa lỗi nhanh, trong khi giữ lại gộp 3 đường cho việc tích hợp các tính năng chạy dài hạn. Trong kịch bản sau, commit gộp sinh ra hoạt động giống như một biểu tượng dán nhãn kết nối hai nhánh.

#### Ví dụ 1: Kịch bản fast foward
Ví dụ đầu tiên này minh họa một cú gộp tiến thẳng. Đoạn mã bên dưới tạo một nhánh mới, thêm hai commit vào đó, rồi tích hợp nó vào dòng chính bằng một cú gộp fast-forward:
```
# 1. Bắt đầu một tính năng mới
git checkout -b new-feature main

# 2. Chỉnh sửa một số file và commit lượt một
git add <file>
git commit -m "Start a feature"

# 3. Chỉnh sửa tiếp một số file và commit lượt hai
git add <file>
git commit -m "Finish a feature"

# 4. Gộp nhánh new-feature vào nhánh main
git checkout main
git merge new-feature

# 5. Xóa bỏ nhánh new-feature sau khi dùng xong
git branch -d new-feature
```
Đây là quy trình làm việc rất phổ biến cho các nhánh tính năng ngắn hạn (short-lived topic branches), vốn được sử dụng như một không gian phát triển cô lập hơn là một công cụ tổ chức cho các tính năng dài hạn.

Cần lưu ý thêm rằng Git sẽ không đưa ra lời phàn nàn nào khi bạn gõ git branch -d, bởi vì toàn bộ các commit của new-feature giờ đây đã có thể truy cập được từ nhánh main.

#### Mẹo: Ép buộc tạo Commit gộp bằng --no-ff
Trong trường hợp bạn bắt buộc phải yêu cầu có một commit gộp xuất hiện trong quy trình gộp fast-foward để phục vụ cho mục đích lưu trữ nhật ký ghi nhận, bạn có thể thêm tham số --no-ff: 
```
git merge --no-ff <branch>
```
Lệnh này gộp nhánh chỉ định vào nhánh hiện tại nhưng luôn luôn tạo ra một commit gộp mới (ngay cả khi về mặt lý thuyết nó có thể gộp tiến thẳng). Điều này hữu ích để lưu lại tài liệu minh chứng cho tất cả các lượt gộp nhánh diễn ra trong kho chứa của bạn.

#### 3-way merge
Ví dụ tiếp theo rất giống ví dụ trước, nhưng bắt buộc phải áp dụng cơ chế gộp 3 đường vì nhánh main đã tiến thêm các commit mới trong lúc nhánh tính năng đang được phát triển. Đây là kịch bản rất phổ biến đối với các tính năng lớn hoặc khi có nhiều lập trình viên cùng đồng thời làm việc trong một dự án.
```
# 1. Bắt đầu một tính năng mới
git checkout -b new-feature main
git add <file>
git commit -m "Start a feature"
git add <file>
git commit -m "Finish a feature"

# 2. Nhánh main phát triển thêm commit mới trong lúc này
git checkout main
git add <file>
git commit -m "Make some super-stable changes to main"

# 3. Gộp nhánh new-feature vào main (Kích hoạt gộp 3 đường)
git merge new-feature
git branch -d new-feature
```

Lúc này, Git không thể thực hiện một cú gộp tiến thẳng được nữa, vì không có cách nào để đẩy con trỏ main tiến lên new-feature mà không phải đi giật lùi lịch sử.

Đối với hầu hết các quy trình làm việc, new-feature sẽ là một tính năng lớn mất nhiều thời gian để phát triển, đó là lý do tại sao các commit mới lại xuất hiện trên main trong khoảng thời gian đó. Nếu nhánh tính năng của bạn thực sự nhỏ như ví dụ trên, giải pháp tốt nhất là bạn nên rebase nó lên trên main rồi thực hiện một cú gộp tiến thẳng. Việc này giúp ngăn chặn các commit gộp thừa thãi làm lộn xộn lịch sử của dự án.

### Resolving conflicts
Nếu hai nhánh bạn đang cố gắng gộp cùng thay đổi vào một vị trí giống nhau của cùng một file, Git sẽ không thể tự định đoạt nên sử dụng phiên bản nào. Khi tình huống đó xảy ra, hệ thống sẽ lập tức dừng lại ngay trước khi tạo commit gộp để bạn tự tay giải quyết xung đột một cách thủ công.

Điểm tuyệt vời trong quy trình gộp nhánh của Git là nó sử dụng chính quy trình làm việc quen thuộc edit/ stage / commit để giải quyết các xung đột gộp nhánh. Khi bạn đối mặt với một xung đột, gõ lệnh git status sẽ hiển thị chính xác những file nào đang cần được cứu vãn.

Ví dụ, nếu cả hai nhánh cùng sửa đổi một phân đoạn trong file hello.py, bạn sẽ thấy thông báo hiện ra trông như thế này:
```
On branch main
Unmerged paths:
  (use "git add/rm <file>..." as appropriate to mark resolution)

	both modified:   hello.py
```
### Cách các xung đột được hiển thị trong file
Khi Git gặp xung đột trong lúc merge, nó sẽ trực tiếp chỉnh sửa nội dung của file bị ảnh hưởng bằng các ký hiệu trực quan để đánh dấu ranh giới của hai luồng nội dung xung đột. Các dấu mốc trực quan đó là: <<<<<<<, =======, và >>>>>>>. Bạn nên tìm kiếm các ký hiệu này trong file để biết chính xác nơi cần xử lý:
```
here is some content not affected by the conflict
<<<<<<< main
this is conflicted text from main
=======
this is conflicted text from feature branch
>>>>>>> feature branch
```
Thông thường, phần nội dung nằm trước vạch ngăn cách ======= thuộc về nhánh nhận dữ liệu (nhánh hiện tại bạn đang đứng), và phần nội dung nằm sau nó thuộc về nhánh đem đi gộp.

Một khi bạn đã xác định được các phân đoạn xung đột, bạn có thể vào xóa các ký hiệu rác kia đi và sửa lại đoạn code theo đúng ý muốn của mình. Khi đã sẵn sàng để hoàn tất cú gộp nhánh, tất cả những gì bạn cần làm là gõ lệnh git add lên các file vừa sửa để báo cho Git biết chúng đã được giải quyết xong xuoi. Sau đó, bạn gõ lệnh git commit như bình thường để hệ thống tự động sinh ra commit gộp. Quy trình này hoàn toàn giống hệt việc commit một ảnh chụp thông thường.

## Git merge conflicts
Các hệ thống quản lý phiên bản đều xoay quanh việc quản lý các đóng góp giữa nhiều tác giả phân tán (thường là các lập trình viên). Đôi khi, nhiều lập trình viên có thể cố gắng chỉnh sửa cùng một nội dung. Nếu Lập trình viên A cố gắng sửa đoạn code mà Lập trình viên B cũng đang sửa, một sự xung đột (conflict) có thể xảy ra. Để giảm thiểu sự xuất hiện của xung đột, các lập trình viên sẽ làm việc trên các nhánh biệt lập riêng biệt. Trách nhiệm chính của lệnh git merge là kết hợp các nhánh riêng rẽ và giải quyết bất kỳ chỉnh sửa xung đột nào.

### Understanding merge conflicts
Xung đột nói chung phát sinh khi hai người cùng thay đổi vào các dòng giống nhau trong một file, hoặc nếu một lập trình viên xóa file đó đi trong khi một lập trình viên khác lại đang sửa đổi nó. Trong những trường hợp này, Git không thể tự động quyết định xem nội dung nào là chính xác. Xung đột chỉ ảnh hưởng trực tiếp đến lập trình viên đang tiến hành gộp nhánh, các thành viên còn lại trong đội hoàn toàn không biết gì về xung đột này. Git sẽ đánh dấu file đó là đang bị xung đột và tạm dừng quy trình gộp. Sau đó, trách nhiệm giải quyết xung đột thuộc về các lập trình viên.
### Types of merge conflicts
Một cú gộp nhánh có thể rơi vào trạng thái xung đột tại hai thời điểm tách biệt: Khi bắt đầu và Trong quá trình gộp. Dưới đây là bài thảo luận về cách giải quyết từng kịch bản xung đột này.

1. Fails to start the merge  

Một cú gộp nhánh sẽ thất bại ngay khi bắt đầu nếu Git nhìn thấy đang có các thay đổi chưa commit nằm trong Thư mục làm việc (Working Directory) hoặc Hàng chờ (Staging Area) của dự án hiện tại. Git từ chối khởi động lệnh gộp vì những thay đổi đang làm dở này có nguy cơ bị ghi đè bởi các commit sắp được gộp vào.

Khi điều này xảy ra, nguyên nhân không phải vì xung đột với mã nguồn của lập trình viên khác, mà là xung đột với chính các thay đổi chưa lưu của bạn. Trạng thái cục bộ cần phải được đưa về mức ổn định bằng cách sử dụng git stash, git checkout, git commit hoặc git reset. Thất bại khi bắt đầu gộp sẽ xuất ra thông báo lỗi sau:
```
error: Entry '<fileName>' not uptodate. Cannot merge. (Changes in working directory)
```
2. Fails during the merge

Một thất bại diễn ra TRONG QUÁ TRÌNH gộp biểu thị cho sự xung đột giữa nhánh cục bộ hiện tại và nhánh đang được đem đi gộp vào. Điều này báo hiệu một sự xung đột trực tiếp với code của lập trình viên khác. Git sẽ cố gắng hết sức để tự động trộn các file, nhưng sẽ để lại những vị trí xung đột trong file để bạn tự tay giải quyết thủ công. Thất bại giữa chừng này sẽ xuất ra thông báo lỗi sau:
```
error: Entry '<fileName>' would be overwritten by merge. Cannot merge. (Changes in staging area)
```
### Creating a merge conflict

Để trở nên thực sự quen thuộc với các xung đột gộp nhánh, phần tiếp theo sẽ mô phỏng một tình huống xung đột để chúng ta kiểm tra và giải quyết. Ví dụ dưới đây sử dụng giao diện dòng lệnh Git của Unix để thực thi mô phỏng:
```
$ mkdir git-merge-test
$ cd git-merge-test
$ git init .
$ echo "this is some content to mess with" > merge.txt
$ git add merge.txt
$ git commit -am"we are commiting the inital content"
[main (root-commit) d48e74c] we are commiting the inital content
1 file changed, 1 insertion(+)
create mode 100644 merge.txt
```
Chuỗi câu lệnh trên hoàn thành các bước sau:

Tạo một thư mục mới tên là git-merge-test, chuyển vào thư mục đó, và khởi tạo nó thành một repo Git mới.

Tạo một file văn bản mới merge.txt với một ít nội dung bên trong.

Thêm merge.txt vào repo và commit nó.

Bây giờ chúng ta đã có một repo mới với một nhánh tên là main và một file merge.txt chứa nội dung. Tiếp theo, chúng ta sẽ tạo một nhánh mới để làm nhánh gây xung đột khi gộp về sau:
```
$ git checkout -b new_branch_to_merge_later
$ echo "totally different content to merge later" > merge.txt
$ git commit -am"edited the content of merge.txt to cause a conflict"
[new_branch_to_merge_later 6282319] edited the content of merge.txt to cause a conflict
1 file changed, 1 insertion(+), 1 deletion(-)
```
Chuỗi lệnh tiếp diễn này đạt được các mục đích:

Tạo và chuyển sang một nhánh mới tên là new_branch_to_merge_later.

Ghi đè hoàn toàn nội dung mới vào file merge.txt.

Commit nội dung mới này.

Với nhánh mới new_branch_to_merge_later này, chúng ta đã tạo ra một commit ghi đè lên nội dung cũ của file merge.txt.

```
$ git checkout main
Switched to branch 'main'
$ echo "content to append" >> merge.txt
$ git commit -am"appended content to merge.txt"
[main 24fbe3c] appended content to merge.txt
1 file changed, 1 insertion(+)
```
Chuỗi lệnh này chuyển quay trở lại nhánh main, ghi nối thêm nội dung vào file merge.txt, và commit nó. Hành động này đưa repo ví dụ của chúng ta rơi vào trạng thái sở hữu 2 commit mới khác nhau: Một commit nằm trên nhánh main và một commit nằm trên nhánh new_branch_to_merge_later.

Tại thời điểm này, hãy cùng chạy lệnh git merge new_branch_to_merge_later và xem chuyện gì xảy ra!
```
$ git merge new_branch_to_merge_later
Auto-merging merge.txt
CONFLICT (content): Merge conflict in merge.txt
Automatic merge failed; fix conflicts and then commit the result.
```
Một sự xung đột đã xuất hiện

### How to identify merge conflicts
Như chúng ta vừa trải nghiệm từ ví dụ trên, Git sẽ đưa ra một số thông báo mô tả chi tiết để chúng ta biết rằng một CONFLICT (XUNG ĐỘT) đã xảy ra. Chúng ta có thể có được cái nhìn sâu hơn bằng cách chạy lệnh git status:

```
$ git status
On branch main
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

	both modified:   merge.txt
```
Đầu ra từ git status chỉ ra rằng đang có các đường dẫn chưa được gộp do xung đột (unmerged paths). File merge.txt hiện đang xuất hiện ở trạng thái bị sửa đổi. Hãy cùng kiểm tra file xem có những gì bị thay đổi bằng lệnh cat:
```
$ cat merge.txt
<<<<<<< HEAD
this is some content to mess with
content to append
=======
totally different content to merge later
>>>>>>> new_branch_to_merge_later
```
Hãy nghĩ về những dòng mới này như những "vạch ngăn cách xung đột". Dòng dấu bằng ======= chính là "tâm điểm" của sự xung đột. Toàn bộ nội dung nằm giữa tâm điểm và dòng <<<<<<< HEAD là nội dung đang tồn tại ở nhánh hiện tại main (nơi con trỏ tham chiếu HEAD đang trỏ vào). Ngược lại, toàn bộ nội dung nằm giữa tâm điểm và dòng >>>>>>> new_branch_to_merge_later là nội dung đang có mặt ở nhánh được đem đi gộp của chúng ta.

### How to resolve merge conflicts using the command line

Cách trực tiếp nhất để giải quyết một xung đột gộp nhánh là mở file bị xung đột ra để chỉnh sửa. Hãy mở file merge.txt bằng trình soạn thảo văn bản yêu thích của bạn. Đối với ví dụ này, chúng ta sẽ đơn giản là xóa bỏ sạch sành sanh tất cả các vạch ngăn cách xung đột đi. Nội dung file merge.txt sau khi sửa đổi trông sẽ gọn gàng như sau:

```
this is some content to mess with
content to append
totally different content to merge later
```
Một khi file đã được chỉnh sửa xong theo đúng ý muốn, hãy sử dụng lệnh git add merge.txt để đưa nội dung gộp mới này vào hàng chờ Staging Area. Để chốt hạ hoàn tất cú gộp nhánh, hãy tạo một commit mới bằng cách thực thi:

```
git commit -m "merged and resolved the conflict in merge.txt"
```

Git sẽ nhận biết rằng xung đột đã được giải quyết ổn thỏa và tiến hành khởi tạo một commit gộp mới để kết thúc quy trình.

### Git commands that can help resolve merge conflicts

#### General tools

- git status: Câu lệnh này được sử dụng với tần suất thường xuyên trong quá trình làm việc với Git, và trong suốt một cú merge, nó sẽ giúp định vị chính xác những file nào đang bị xung đột.

- git log --merge: Việc truyền thêm tham số --merge vào lệnh git log sẽ xuất ra một bảng nhật ký chứa danh sách các commit đang gây ra xung đột trực tiếp giữa các nhánh gộp.

- git diff: Giúp tìm ra sự sai lệch giữa các trạng thái của kho chứa hoặc các file. Lệnh này cực kỳ hữu ích để dự đoán và phòng ngừa trước các xung đột gộp nhánh.

#### Tools for when git fails to start a merge
- git checkout: Có thể được dùng để hủy bỏ các thay đổi của file, hoặc dùng để chuyển đổi qua lại giữa các nhánh.

- git reset --mixed: Có thể được dùng để hoàn tác các thay đổi đối với cả thư mục làm việc lẫn hàng chờ.

#### Tools for when git conflicts arise during a merge

- git merge --abort: Thực thi lệnh git merge với tùy chọn --abort sẽ ngay lập tức thoát khỏi quy trình gộp nhánh và trả toàn bộ trạng thái của nhánh hiện tại quay về mốc an toàn nguyên bản trước khi lệnh merge bắt đầu.

- git reset: Có thể được sử dụng trong lúc xảy ra xung đột để đưa các file bị xung đột quay trở về một trạng thái tốt được xác nhận từ trước.

## Merge strategies
Khi một phần công việc đã hoàn thành, được kiểm thử và sẵn sàng để gộp ngược trở lại dòng phát triển chính (main line), đội ngũ của bạn sẽ có một vài lựa chọn về mặt chính sách cần phải đưa ra. Các tùy chọn về chiến lược gộp nhánh của bạn là gì? Trong bài viết này, chúng ta sẽ xem xét các khả năng đó và sau đó cung cấp một số ghi chú về cách Atlassian vận hành. Hy vọng rằng đến cuối bài, bạn sẽ có đủ công cụ để quyết định phương án nào hoạt động tốt nhất cho đội nhóm của mình.

### Git merge strategies
merge xảy ra khi kết hợp hai nhánh với nhau. Git sẽ lấy hai (hoặc nhiều hơn) con trỏ commit và cố gắng tìm một commit nền tảng chung (common base commit) giữa chúng. Git có một vài phương thức khác nhau để tìm commit nền tảng này, và các phương thức này được gọi là "chiến lược gộp nhánh" (merge strategies).

Một khi Git tìm thấy một commit nền tảng chung, nó sẽ tạo ra một "commit gộp" (merge commit) mới để kết hợp các thay đổi của các commit chỉ định. Về mặt kỹ thuật, một commit gộp là một commit thông thường nhưng có điểm đặc biệt là sở hữu hai commit cha (parent commits).

Lệnh git merge sẽ tự động lựa chọn một chiến lược gộp nhánh trừ khi bạn chỉ định nó một cách tường minh. Các lệnh git merge và git pull có thể tiếp nhận thêm tùy chọn -s (strategy). Theo sau cờ -s, bạn có thể viết kèm tên của chiến lược gộp nhánh mong muốn. Nếu không được chỉ định rõ ràng, Git sẽ tự động chọn chiến lược phù hợp nhất dựa trên các nhánh được cung cấp. Dưới đây là danh sách các chiến lược gộp nhánh khả dụng:

1. Recursive
```
git merge -s recursive branch1 branch2
```
Chiến lược này hoạt động trên hai đầu ngọn nhánh (heads). Recursive là chiến lược gộp nhánh mặc định khi bạn thực hiện pull hoặc merge một nhánh đơn lẻ. Thêm vào đó, chiến lược này có khả năng tự động phát hiện và xử lý các lượt gộp nhánh có liên quan đến việc đổi tên file (renames), nhưng hiện tại chưa thể tận dụng các file bị sao chép (detected copies).

2. Resolve
```
git merge -s resolve branch1 branch2
```
Chiến lược này chỉ có thể giải quyết hai đầu ngọn nhánh bằng thuật toán gộp 3 đường (3-way merge). Nó cố gắng phát hiện một cách cẩn thận các điểm mập mờ trong các lượt gộp nhánh chéo nhau (cris-cross merge) và được đánh giá là giải pháp nói chung an toàn và nhanh chóng.

3. Octopus
```
git merge -s octopus branch1 branch2 branch3 branchN
```
Đây là chiến lược gộp nhánh mặc định khi có nhiều hơn hai đầu ngọn nhánh. Khi bạn truyền vào nhiều hơn một nhánh, chiến lược octopus sẽ tự động được kích hoạt. Nếu cú gộp nhánh xuất hiện xung đột (conflicts) đòi hỏi phải xử lý thủ công bằng tay, chiến lược octopus sẽ lập tức từ chối và hủy bỏ lượt gộp đó. Nó chủ yếu được sử dụng để gom cụm các đầu ngọn của những nhánh tính năng tương tự lại với nhau.

4. Ours 
```
git merge -s ours branch1 branch2 branchN
```
Chiến lược Ours hoạt động trên một số lượng nhiều $N$ nhánh khác nhau. Kết quả gộp đầu ra luôn luôn khớp chính xác với code của nhánh hiện tại (HEAD). Từ khóa "ours" ám chỉ sự ưu tiên tuyệt đối, hệ thống sẽ lờ đi và bỏ qua toàn bộ tất cả các thay đổi đến từ tất cả các nhánh khác. Nó được thiết kế để sử dụng cho việc kết hợp lịch sử của các nhánh tính năng tương đồng nhau.
5. Subtree
```
git merge -s subtree branchA branchB
```
Đây là một phiên bản mở rộng của chiến lược đệ quy (recursive). Khi gộp nhánh A và nhánh B, nếu B là một cây con (child subtree) của A, nhánh B trước tiên sẽ được cập nhật để phản ánh đúng cấu trúc cây của A. Sự cập nhật này cũng được áp dụng cho cả cây tổ tiên chung được chia sẻ giữa A và B.

### Types of git merge strategies
#### Explicit merges
Explicit merges là kiểu gộp mặc định của hệ thống. Phần explicit có nghĩa chúng tự động tạo 1 commit gộp mới. Hành động này làm biến đổi lịch sử commit và hiển thị rõ ràng trên sơ đồ nơi mà một lệnh merge đã được thực thi. Nội dung của commit gộp cũng rất minh bạch vì nó chỉ rõ những commit nào đóng vai trò là cha của commit gộp đó. Một số đội ngũ thường né tránh kiểu gộp tường minh này vì họ cho rằng các commit gộp tự sinh sẽ tạo ra các "tiếng ồn" (rác thông tin) làm rối lịch sử của dự án.  
#### Implicit merge via rebase or fast-forward merge (Gộp ẩn dòng)
(Kiểu gộp này tích hợp các thay đổi bằng cách di chuyển con trỏ hoặc viết lại lịch sử thông qua rebase/fast-forward mà không đẻ ra commit gộp).

#### Squash on merge (Nén khi gộp)
(Kiểu gộp nén toàn bộ các commit của nhánh tính năng thành một commit duy nhất và đặt vào nhánh chính, nói chung không tạo ra commit gộp tường minh).

## Comparing Workflows
Git là hệ thống quản lý phiên bản được sử dụng phổ biến nhất hiện nay. Một quy trình làm việc Git (Git workflow) là một công thức hoặc khuyến nghị về cách sử dụng Git để hoàn thành công việc một cách nhất quán và hiệu quả. Các quy trình này khuyến khích các lập trình viên và đội ngũ DevOps tận dụng Git một cách hiệu quả và đồng bộ.

Git cung cấp rất nhiều sự linh hoạt trong cách người dùng quản lý các thay đổi. Do tập trung vào tính linh hoạt, Git không có một quy trình tiêu chuẩn cố định nào về cách tương tác. Khi làm việc với một đội nhóm trong một dự án do Git quản lý, điều quan trọng là phải đảm bảo toàn đội đều thống nhất về cách áp dụng luồng thay đổi. Để đảm bảo mọi người cùng chung một hướng đi, một quy trình Git workflow thống nhất cần được xây dựng hoặc lựa chọn. Có một vài quy trình Git workflow phổ biến có thể sẽ là mảnh ghép phù hợp cho đội nhóm của bạn. Tại đây, chúng ta sẽ thảo luận về các tùy chọn đó.

Hàng loạt các quy trình khả thi có thể khiến bạn khó biết nên bắt đầu từ đâu khi triển khai Git tại nơi làm việc. Trang tài liệu này cung cấp một điểm khởi đầu bằng cách khảo sát các Git workflow phổ biến nhất cho các đội ngũ phần mềm.

Khi bạn đọc qua, hãy nhớ rằng các quy trình này được thiết kế để làm hướng dẫn chỉ đường chứ không phải là những quy tắc bất biến. Chúng tôi muốn chỉ cho bạn những gì khả thi, để bạn có thể kết hợp và tùy biến các khía cạnh từ các quy trình khác nhau nhằm phục vụ nhu cầu cá nhân của mình.

### Thế nào là một Git workflow thành công?
Khi đánh giá một quy trình làm việc cho đội nhóm, điều quan trọng nhất là bạn phải cân nhắc đến văn hóa của đội. Bạn muốn quy trình đó nâng cao hiệu suất của đội chứ không phải là một gánh nặng làm hạn chế năng suất. Một số điều cần cân nhắc khi đánh giá một Git workflow là:

Quy trình này có thể mở rộng quy mô khi quy mô nhân sự của đội tăng lên không?

Quy trình này có giúp dễ dàng hoàn tác các sai lầm và lỗi logic không?

Quy trình này có áp đặt thêm bất kỳ áp lực tư duy (cognitive overhead) không cần thiết nào lên đội nhóm không?

### Centralized workflow
Quy trình Centralized Workflow là một mô hình tuyệt vời cho các đội nhóm đang chuyển dịch từ hệ thống SVN sang. Giống như Subversion, Centralized Workflow sử dụng một kho chứa trung tâm (central repository) duy nhất đóng vai trò là điểm tiếp nhận duy nhất cho mọi thay đổi của dự án. Thay vì gọi là nhánh trunk, nhánh phát triển mặc định trong Git được gọi là main và tất cả các thay đổi đều được commit thẳng vào nhánh này. Quy trình này không đòi hỏi bất kỳ nhánh nào khác ngoài nhánh main.

Việc chuyển đổi sang một hệ thống quản lý phiên bản phân tán có vẻ là một nhiệm vụ đáng sợ, nhưng bạn không nhất thiết phải thay đổi quy trình làm việc sẵn có của mình để tận dụng lợi thế của Git. Đội nhóm của bạn có thể phát triển các dự án theo cách chính xác giống như họ từng làm với Subversion.

Tuy nhiên, sử dụng Git để vận hành quy trình phát triển vẫn mang lại một vài lợi thế vượt trội so với SVN:

Thứ nhất: Nó cung cấp cho mỗi lập trình viên một bản sao cục bộ hoàn chỉnh của toàn bộ dự án. Môi trường cô lập này giúp mỗi lập trình viên làm việc độc lập với tất cả các thay đổi khác — họ có thể thoải mái thêm các commit vào kho chứa cục bộ và hoàn toàn không cần bận tâm đến những tiến triển trên server cho đến khi thấy thuận tiện.

Thứ hai: Nó giúp bạn tiếp cận mô hình phân nhánh và gộp nhánh cực kỳ mạnh mẽ của Git. Không giống như SVN, các nhánh Git được thiết kế để làm một cơ chế bảo hiểm an toàn trong việc tích hợp code và chia sẻ các thay đổi giữa các kho chứa.

Centralized Workflow tương tự như các quy trình khác ở việc sử dụng một kho chứa lưu trữ trên máy chủ từ xa để các lập trình viên thực hiện push và pull. So với các quy trình khác, Centralized Workflow không định nghĩa bất kỳ mô hình Pull Request hoặc Forking nào. Quy trình này nhìn chung phù hợp hơn cho các đội nhóm đang di cư từ SVN sang Git hoặc các đội ngũ có quy mô nhỏ.

### How it works

Các lập trình viên bắt đầu bằng việc clone kho chứa trung tâm về máy. Trong bản sao cục bộ của mình, họ chỉnh sửa các file và commit các thay đổi giống hệt như khi làm với SVN; tuy nhiên, các commit mới này được lưu trữ cục bộ dưới máy — hoàn toàn tách biệt khỏi kho chứa trung tâm. Điều này cho phép lập trình viên trì hoãn việc đồng bộ hóa lên server cho đến khi họ đạt tới một mốc nghỉ thuận tiện.

Để xuất bản các thay đổi lên dự án chính thức, lập trình viên "push" nhánh main cục bộ của họ lên kho chứa trung tâm. Hành động này tương đương với lệnh svn commit, ngoại trừ việc nó sẽ đẩy toàn bộ các commit cục bộ chưa có mặt trên nhánh main trung tâm lên server.

### Initialize the central repository  

Đầu tiên, một thành viên cần phải khởi tạo kho chứa trung tâm trên một máy chủ server. Nếu đó là một dự án mới tinh, bạn có thể khởi tạo một kho chứa trống. Ngược lại, bạn sẽ cần nhập dữ liệu từ một kho chứa Git hoặc SVN sẵn có.

Các kho chứa trung tâm phải luôn luôn là các kho chứa trần (bare repositories - kho chứa không có thư mục làm việc working directory), bạn có thể khởi tạo như sau:

```
ssh user@host git init --bare /path/to/repo.git
```

Hãy đảm bảo sử dụng một tên người dùng SSH hợp lệ cho user, tên miền hoặc địa chỉ IP server cho host, và đường dẫn nơi bạn muốn lưu trữ repo cho /path/to/repo.git. Lưu ý rằng phần mở rộng .git theo quy ước được gắn thêm vào tên kho chứa để biểu thị đó là một kho chứa trần.

### Hosted central repositories  

Các kho chứa trung tâm thường được tạo thông qua các dịch vụ lưu trữ Git bên thứ ba như Bitbucket Cloud. Quy trình khởi tạo một kho chứa trần thảo luận ở trên sẽ được dịch vụ lưu trữ tự động xử lý. Dịch vụ lưu trữ sau đó sẽ cung cấp một địa chỉ đường link URL của kho chứa trung tâm để bạn truy cập từ kho chứa cục bộ của mình.

### Clone the central repository

Tiếp theo, mỗi lập trình viên tạo một bản sao cục bộ của toàn bộ dự án trên máy mình thông qua câu lệnh git clone:
```
git clone ssh://user@host/path/to/repo.git
```
Khi bạn clone một kho chứa, Git sẽ tự động tạo ngầm một phím tắt tên là origin trỏ ngược về kho chứa "cha" đó, với giả định rằng bạn sẽ muốn tương tác với nó trong chặng đường tiếp theo.

### Make changes and commit  

Khi kho chứa đã được clone về máy local, lập trình viên có thể thực hiện các thay đổi bằng quy trình commit tiêu chuẩn của Git: chỉnh sửa, đưa vào hàng chờ, và commit (edit, stage, commit). Nếu bạn chưa quen với khu vực hàng chờ (Staging Area), thì đây là một cách để chuẩn bị cho một commit mà không bắt buộc phải gom tất cả mọi thay đổi trong thư mục làm việc vào. Điều này giúp bạn tạo ra các commit có tính tập trung cao, ngay cả khi bạn đã thực hiện rất nhiều chỉnh sửa dưới máy local.
```
git status          # Xem trạng thái hiện tại của repo
git add <some-file> # Đưa một file vào hàng chờ Staging Area
git commit          # Chốt commit file đó dưới máy local
```

Remember rằng vì các lệnh này chỉ tạo ra các commit cục bộ dưới máy cá nhân, John có thể lặp lại quy trình này bao nhiêu lần tùy ý mà không cần lo lắng về những gì đang diễn ra trong kho chứa trung tâm. Điều này rất hữu ích cho các tính năng lớn cần được chia nhỏ thành các phần đơn giản hơn, có tính nguyên tử hơn.

### Push new commits to central repository  

Một khi kho chứa cục bộ đã được commit các thay đổi mới, các thay đổi này sẽ cần được push lên mạng để chia sẻ với các lập trình viên khác trong dự án:
```
git push origin main
```
Lệnh này sẽ đẩy các thay đổi mới đã commit lên kho chứa trung tâm. Khi push các thay đổi lên kho chứa trung tâm, có khả năng một lập trình viên khác đã push các cập nhật của họ lên trước đó và chứa đoạn code xung đột với các cập nhật bạn định push. Git sẽ xuất ra một thông báo chỉ thị sự xung đột này. Trong tình huống đó, bạn sẽ bắt buộc phải thực thi lệnh git pull trước. Kịch bản xung đột này sẽ được mở rộng trong phần tiếp theo.

### Managing conflicts  

Kho chứa trung tâm đại diện cho dự án chính thức, vì vậy lịch sử commit của nó phải được coi là bất khả xâm phạm và không thể thay đổi. Nếu các commit cục bộ của một lập trình viên bị lệch hướng rẽ nhánh so với kho chứa trung tâm, Git sẽ từ chối push các thay đổi đó vì hành động này sẽ ghi đè lên các commit chính thức của server.

Trước khi lập trình viên có thể xuất bản tính năng của mình, họ cần phải tải về các commit trung tâm cập nhật và rebase các thay đổi của mình lên trên đỉnh ngọn của chúng. Việc này giống như tuyên bố: "Tôi muốn thêm các thay đổi của tôi vào những gì mà mọi người đã hoàn thành trước đó." Kết quả trả về sẽ là một lịch sử tuyến tính hoàn hảo, giống hệt như trong quy trình làm việc SVN truyền thống.

Nếu các thay đổi cục bộ xung đột trực tiếp với các commit thượng nguồn, Git sẽ tạm dừng quy trình rebase và trao cho bạn cơ hội giải quyết xung đột bằng tay một cách thủ công. Điểm tuyệt vời của Git là nó sử dụng chính các lệnh git status và git add quen thuộc cho cả việc tạo commit lẫn việc giải quyết xung đột gộp nhánh. Điều này giúp các lập trình viên mới dễ dàng tự quản lý các lượt gộp của mình. Plus, nếu họ rơi vào rắc rối, Git giúp việc hủy bỏ toàn bộ quy trình rebase (git rebase --abort) để thử lại từ đầu trở nên vô cùng dễ dàng (hoặc đi tìm sự trợ giúp).

### Example

Hãy cùng xem một ví dụ tổng quát về cách một đội ngũ nhỏ hợp tác bằng quy trình này. Chúng sau đây sẽ thấy cách hai lập trình viên, John và Mary, có thể làm việc trên các tính năng riêng biệt và chia sẻ đóng góp của họ thông qua một kho chứa trung tâm.

#### John works on his feature

Trong kho chứa cục bộ của mình, John phát triển các tính năng bằng quy trình commit tiêu chuẩn: chỉnh sửa, đưa vào hàng chờ, và commit. Remember rằng vì các lệnh này chỉ tạo ra các commit cục bộ dưới máy cá nhân, John có thể lặp lại quy trình này bao nhiêu lần tùy ý mà không cần lo lắng về những gì đang diễn ra trên server trung tâm.

##### Mary works on her feature

Trong lúc đó, Mary cũng đang bận rộn làm việc trên tính năng của riêng mình trong kho chứa cục bộ của cô ấy bằng quy trình tương tự. Giống như John, cô ấy không cần quan tâm đến những gì đang diễn ra trong kho chứa trung tâm, và cô ấy lại càng không quan tâm John đang làm gì dưới máy của anh ấy, vì tất cả các kho chứa cục bộ đều mang tính riêng tư.

#### John publishes his feature

Ngay khi John hoàn thành tính năng của mình, anh ấy xuất bản các commit cục bộ lên kho chứa trung tâm để các thành viên khác có thể tiếp cận. Anh ấy thực hiện bằng lệnh git push:
```
git push origin main
```
Hãy nhớ rằng origin là kết nối từ xa tới kho chứa trung tâm mà Git đã tự động tạo ra khi John clone dự án. Tham số main ra lệnh cho Git cố gắng làm cho nhánh main của origin trông giống hệt như nhánh main cục bộ của anh ấy. Vì kho chứa trung tâm chưa từng được cập nhật kể từ ngày John clone nó về, hành động này sẽ không sinh ra bất kỳ xung đột nào và lệnh push hoạt động mượt mà như mong đợi.

#### Mary tries to publish her feature

Hãy cùng xem chuyện gì xảy ra nếu Mary cố gắng push tính năng của cô ấy lên sau khi John đã xuất bản thành công các thay đổi của anh ấy lên server trung tâm. Cô ấy gõ chính xác câu lệnh push:
```
git push origin main
```
Nhưng vì lịch sử cục bộ của cô ấy đã bị lệch hướng rẽ nhánh so với server trung tâm, Git sẽ thẳng thừng từ chối yêu cầu kèm theo một thông báo lỗi khá dài dòng:
```
error: failed to push some refs to '/path/to/repo.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
hint: before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
Cơ chế này ngăn Mary ghi đè lên các commit chính thức. Cô ấy cần phải kéo các cập nhật của John vào kho chứa của mình, tích hợp chúng với các thay đổi cục bộ, rồi mới thử push lại.

#### Mary rebases on top of John’s commit(s)
Mary có thể sử dụng lệnh git pull để hợp nhất các thay đổi thượng nguồn vào kho chứa của mình. Lệnh này giống như svn update — nó kéo toàn bộ lịch sử commit thượng nguồn vào kho chứa local của Mary và cố gắng tích hợp nó với các commit cục bộ của cô ấy:
```
git pull --rebase origin main
```
Tùy chọn --rebase ra lệnh cho Git di chuyển toàn bộ các commit cục bộ của Mary lên trên đỉnh ngọn của nhánh main sau khi đã đồng bộ hóa nó với các thay đổi từ kho chứa trung tâm, như minh họa dưới đây:

Cú pull vẫn sẽ chạy được nếu bạn lỡ quên tùy chọn này, nhưng bạn sẽ kết thúc với một commit gộp (merge commit) thừa thãi xuất hiện mỗi khi có ai đó cần đồng bộ hóa với server trung tâm. Đối với quy trình này, việc sử dụng rebase luôn luôn tốt hơn là đẻ ra một commit gộp.

#### Mary resolves a merge conflict

Cơ chế của rebase hoạt động bằng cách dịch chuyển từng commit cục bộ sang nhánh main đã cập nhật tại một thời điểm. Điều này có nghĩa là bạn sẽ phát hiện và xử lý các xung đột gộp nhánh trên cơ sở từng commit một, thay vì phải giải quyết tất cả chúng trong một commit gộp khổng lồ duy nhất. Việc này giúp giữ cho các commit của bạn có tính tập trung cao nhất có thể và tạo ra một lịch sử dự án sạch sẽ. Hệ quả là việc tìm ra vị trí phát sinh lỗi bug trở nên dễ dàng hơn nhiều và nếu cần thiết, bạn có thể hoàn tác (rollback) các thay đổi với mức độ ảnh hưởng tối thiểu tới dự án.

Nếu Mary và John đang làm việc trên các tính năng không liên quan đến nhau, quy trình rebase sẽ rất hiếm khi sinh ra xung đột. Nhưng nếu có, Git sẽ lập tức tạm dừng việc rebase tại chính commit lỗi đó và xuất ra thông báo sau kèm theo các hướng dẫn liên quan:
```
CONFLICT (content): Merge conflict in <some-file>
```

Điểm tuyệt vời của Git là bất kỳ ai cũng có thể tự giải quyết xung đột của chính mình. Trong ví dụ của chúng ta, Mary chỉ cần chạy lệnh git status để xem rắc rối nằm ở đâu. Các file bị xung đột sẽ xuất hiện trong mục Unmerged paths:

```
# Unmerged paths:
#   (use "git reset HEAD <some-file>..." to unstage)
#   (use "git add/rm <some-file>..." as appropriate to mark resolution)
#
#	both modified:   <some-file>
```
Sau đó, cô ấy sẽ mở file ra chỉnh sửa theo đúng ý muốn. Khi đã hài lòng với kết quả, cô ấy đưa file vào hàng chờ như thường lệ và ra lệnh cho git rebase tiếp tục xử lý phần còn lại:
```
git add <some-file>
git rebase --continue
```

Và đó là toàn bộ quy trình. Git sẽ di chuyển sang commit tiếp theo và lặp lại quy trình trên cho bất kỳ commit nào khác phát sinh xung đột.

Nếu bạn đi đến bước này và nhận ra mình hoàn toàn hoang mang không hiểu chuyện gì đang xảy ra, đừng hoảng loạn. Chỉ cần thực thi câu lệnh sau và bạn sẽ lập tức được trả về chính xác vị trí an toàn trước khi gõ lệnh pull:

```
git rebase --abort
```

#### Mary successfully publishes her feature

Sau khi hoàn tất việc đồng bộ hóa với kho chứa trung tâm, Mary sẽ có thể xuất bản các thay đổi của mình lên mạng một cách thành công:
```
git push origin main
```
### Where to go from here

Như bạn có thể thấy, việc tái lập một môi trường phát triển Subversion truyền thống chỉ bằng cách sử dụng một vài câu lệnh Git là điều hoàn toàn khả thi. Điều này rất tuyệt vời cho các đội nhóm đang trong giai đoạn chuyển giao từ SVN sang, nhưng nó lại chưa tận dụng được bản chất phân tán của Git.

Mô hình Centralized Workflow rất tuyệt cho các đội nhóm nhỏ. Quy trình giải quyết xung đột chi tiết ở trên có thể tạo ra một nút thắt cổ chai (bottleneck) khi đội ngũ của bạn mở rộng quy mô nhân sự lớn hơn. Nếu đội nhóm của bạn đã cảm thấy thoải mái với Centralized Workflow nhưng muốn tinh gọn hóa các nỗ lực cộng tác của mình, thì việc khám phá những lợi ích của Feature Branch Workflow chắc chắn là điều rất xứng đáng. Bằng cách dành riêng một nhánh cô lập cho từng tính năng, bạn có thể khởi xướng các cuộc thảo luận chuyên sâu xoay quanh các đoạn code mới trước khi chính thức tích hợp chúng vào dự án chung.

### Other common workflows 

Quy trình Centralized Workflow về cơ bản là một viên gạch nền móng để xây dựng nên các Git workflow khác. Hầu hết các quy trình Git phổ biến đều sẽ sở hữu một dạng repo trung tâm nào đó để các lập trình viên thực hiện push và pull. Dưới đây chúng ta sẽ thảo luận ngắn gọn về một số quy trình Git phổ biến khác. Những quy trình mở rộng này cung cấp các mô hình chuyên biệt hơn trong việc quản lý các nhánh phục vụ phát triển tính năng, sửa lỗi nóng, và phát hành phiên bản:

#### Feature branching

Feature Branching là một bước mở rộng logic của Centralized Workflow. Ý tưởng cốt lõi phía sau Feature Branch Workflow là tất cả các công việc phát triển tính năng đều phải diễn ra trên một nhánh dành riêng biệt thay vì nhánh main. Sự bao bọc này giúp nhiều lập trình viên dễ dàng làm việc trên một tính năng cụ thể mà không làm xáo trộn nền tảng code chính. Điều này cũng đồng nghĩa với việc nhánh main sẽ không bao giờ chứa code lỗi, mang lại một lợi thế khổng lồ cho các môi trường tích hợp liên tục (Continuous Integration).

### gitflow workflow

Mô hình Gitflow Workflow lần đầu tiên được xuất bản trong một bài đăng blog năm 2010 được đánh giá rất cao từ Vincent Driessen tại nvie. Quy trình Gitflow định nghĩa một mô hình phân nhánh nghiêm ngặt được thiết kế xung quanh việc phát hành phiên bản của dự án. Quy trình này không thêm bất kỳ khái niệm hay câu lệnh mới nào vượt ra ngoài những gì Quy trình Feature Branch đòi hỏi. Thay vào đó, nó gán các vai trò rất cụ thể cho các nhánh khác nhau và định nghĩa cách thức cũng như thời điểm chúng nên tương tác với nhau.

### Forking Workflow

Quy trình Forking Workflow về mặt nền tảng khác biệt hoàn toàn so với các quy trình khác được thảo luận trong tài liệu này. Thay vì sử dụng một kho chứa duy nhất trên server để làm nền tảng code "trung tâm", nó cung cấp cho mỗi lập trình viên một kho chứa riêng trên server. Điều này có nghĩa là mỗi người đóng góp sẽ sở hữu không phải một, mà là hai kho chứa Git: Một kho chứa riêng tư cục bộ dưới máy local và một kho chứa công khai nằm trên server từ xa.

### Guidelines

Không có một quy trình Git workflow nào là vạn năng phù hợp cho tất cả mọi người. Như đã tuyên bố, điều quan trọng là phải xây dựng một Git workflow mang lại sự gia tăng năng suất cho đội nhóm của bạn. Bên cạnh văn hóa đội ngũ, một quy trình làm việc cũng cần phải bổ trợ cho lịch trình vận hành của doanh nghiệp. Các tính năng của Git như nhánh (branches) và nhãn (tags) nên bổ trợ cho kế hoạch phát hành của doanh nghiệp. Nếu đội của bạn đang sử dụng phần mềm quản lý dự án theo dõi tác vụ, bạn có thể muốn sử dụng các nhánh có tên tương ứng với các tác vụ đang được xử lý. Thêm vào đó, có một số hướng dẫn cần cân nhắc khi quyết định chọn một quy trình làm việc là:

Short-lived branches (Nhánh tuổi thọ ngắn): Một nhánh sống tách biệt khỏi nhánh sản xuất (production branch) càng lâu thì nguy cơ xảy ra xung đột gộp nhánh và các thử thách khi triển khai (deployment) càng cao. Các nhánh có tuổi thọ ngắn sẽ thúc đẩy các lượt gộp nhánh và triển khai sạch sẽ hơn.

Minimize and simplify reverts (Tối thiểu và đơn giản hóa hoàn tất hoàn tác): Điều quan trọng là phải có một quy trình làm việc giúp chủ động ngăn chặn các lượt gộp nhánh mà sau đó bắt buộc phải gõ lệnh hoàn tác (revert). Một quy trình yêu cầu kiểm thử chạy thử một nhánh trước khi cho phép nó được gộp vào nhánh main là một ví dụ điển hình. Tuy nhiên, tai nạn vẫn có thể xảy ra. Do đó, việc có một quy trình cho phép hoàn tác dễ dàng mà không làm gián đoạn luồng làm việc của các thành viên khác là điều vô cùng có lợi.

Match a release schedule (Khớp lịch trình phát hành): Một quy trình làm việc nên bổ trợ cho chu kỳ phát hành phát triển phần mềm của doanh nghiệp bạn. Nếu bạn lên kế hoạch phát hành sản phẩm nhiều lần trong một ngày, bạn sẽ muốn giữ cho nhánh main của mình luôn ở trạng thái cực kỳ ổn định. Nếu lịch trình phát hành của bạn ít thường xuyên hơn, bạn có thể cân nhắc việc sử dụng các nhãn Git (Git tags) để đánh dấu một nhánh gắn liền với một phiên bản cụ thể.

## Git feature branch workflow

Ý tưởng cốt lõi phía sau Quy trình Feature Branch Workflow là toàn bộ công việc phát triển tính năng đều phải diễn ra trên một nhánh dành riêng biệt (dedicated branch) thay vì nhánh main. Sự bao bọc cô lập này giúp nhiều lập trình viên dễ dàng làm việc trên một tính năng cụ thể mà không làm xáo trộn nền tảng code chính. Điều này cũng đồng nghĩa với việc nhánh main sẽ không bao giờ chứa code lỗi, mang lại một lợi thế khổng lồ cho các môi trường tích hợp liên tục (Continuous Integration - CI).

Việc bao bọc quá trình phát triển tính năng cũng tạo điều kiện để tận dụng các Yêu cầu kéo (pull requests), vốn là một cách để khởi xướng các cuộc thảo luận xung quanh một nhánh. Chúng trao cho các lập trình viên khác cơ hội để ký duyệt phê duyệt (sign off) một tính năng trước khi nó được tích hợp vào dự án chính thức. Hoặc, nếu bạn bị mắc kẹt ở giữa một tính năng, bạn có thể mở một pull request để xin ý kiến gợi ý từ các đồng nghiệp của mình. Điểm mấu chốt là, pull request giúp đội nhóm của bạn bình luận về công việc của nhau một cách vô cùng dễ dàng.

Quy trình Git Feature Branch Workflow là một quy trình có tính lắp ghép cao (composable workflow), có thể được tận dụng bởi các quy trình làm việc Git cấp cao khác. Quy trình Git Feature Branch Workflow tập trung trọng tâm vào mô hình phân nhánh (branching model focused), nghĩa là nó đóng vai trò như một khung hướng dẫn cho việc quản lý và tạo các nhánh. Các quy trình làm việc khác thì tập trung nhiều hơn vào cấu trúc repo. Quy trình Git Feature Branch Workflow có thể được tích hợp vào các quy trình khác; các mô hình Gitflow và Git Forking Workflows theo truyền thống đều sử dụng một quy trình Git Feature Branch Workflow đối với các mô hình phân nhánh của họ.

### How it works

Quy trình Feature Branch Workflow giả định một kho chứa trung tâm (central repository), và nhánh main đại diện cho lịch sử dự án chính thức. Thay vì commit trực tiếp trên nhánh main cục bộ của họ, các lập trình viên tạo ra một nhánh mới mỗi khi họ bắt đầu làm việc trên một tính năng mới. Các nhánh tính năng nên có những cái tên mang tính mô tả rõ ràng, ví dụ như animated-menu-items hoặc issue-#1061. Ý tưởng là gán một mục đích rõ ràng, tập trung cao độ cho từng nhánh. Git không tạo ra sự khác biệt nào về mặt kỹ thuật giữa nhánh main và các nhánh tính năng, vì vậy các lập trình viên có thể chỉnh sửa, đưa vào hàng chờ và commit các thay đổi lên một nhánh tính năng như bình thường.

Thêm vào đó, các nhánh tính năng có thể (và nên) được push lên kho chứa trung tâm. Việc này giúp chia sẻ một tính năng với các lập trình viên khác mà không cần chạm vào bất kỳ đoạn code chính thức nào. Vì main là nhánh "đặc biệt" duy nhất, việc lưu trữ nhiều nhánh tính năng trên kho chứa trung tâm không hề gây ra bất kỳ vấn đề gì. Tất nhiên, đây cũng là một cách thuận tiện để sao lưu (backup) các commit cục bộ của mọi người. Dưới đây là phần đi qua từng bước về vòng đời của một nhánh tính năng.

### Start with the main branch

Tất cả các nhánh tính năng đều được tạo ra từ trạng thái code mới nhất của một dự án. Hướng dẫn này giả định trạng thái này được duy trì và cập nhật trong nhánh main.
```
git checkout main
git fetch origin 
git reset --hard origin/main
```
Lệnh này chuyển kho chứa sang nhánh main, nạp các commit mới nhất và thiết lập lại (reset) bản sao cục bộ của nhánh main để khớp chính xác với phiên bản mới nhất trên mạng.

### Create a new-branch 

Sử dụng một nhánh riêng biệt cho từng tính năng hoặc sự cố lỗi mà bạn xử lý. Sau khi tạo một nhánh, hãy checkout sang nó ở máy cục bộ để bất kỳ thay đổi nào bạn thực hiện sau đó đều nằm trên nhánh đó.
```
git checkout -b new-feature
```
Lệnh này thực hiện checkout một nhánh tên là new-feature dựa trên nền của nhánh main, và cờ -b ra lệnh cho Git tạo nhánh đó nếu nó chưa tồn tại.

### Update, add, commit, and push changes

Trên nhánh này, hãy chỉnh sửa, đưa vào hàng chờ và commit các thay đổi theo cách thông thường, xây dựng tính năng với bao nhiêu commit tùy ý. Hãy làm việc trên tính năng và tạo các commit giống như bất kỳ lúc nào bạn sử dụng Git.
```
git status
git add <some-file>
git commit
```
### Push feature branch to remote

Việc đẩy nhánh tính năng lên kho chứa trung tâm là một ý tưởng rất tốt. Nó đóng vai trò như một bản sao lưu thuận tiện; khi cộng tác với các lập trình viên khác, hành động này sẽ cấp cho họ quyền truy cập để xem các commit trên nhánh mới.
```
git push -u origin new-feature
```
Câu lệnh này đẩy nhánh new-feature lên kho chứa trung tâm (origin), và cờ -u thiết lập nó thành một nhánh theo dõi từ xa (remote tracking branch). Sau khi thiết lập xong nhánh theo dõi, bạn có thể gọi lệnh git push mà không cần truyền thêm bất kỳ tham số nào để tự động đẩy nhánh new-feature lên server.

Để nhận phản hồi về nhánh tính năng mới, hãy tạo một pull request trong một giải pháp quản lý kho chứa như Bitbucket Cloud hoặc GitHub. Từ đó, bạn có thể thêm những người rà soát (reviewers) và đảm bảo mọi thứ đều ổn thỏa trước khi gộp nhánh.

### Resolve feedback

Bây giờ các đồng nghiệp sẽ bình luận và phê duyệt các commit đã được push. Hãy giải quyết các bình luận của họ dưới máy local, commit và push các thay đổi được gợi ý lên hệ thống. Các cập nhật của bạn sẽ tự động xuất hiện trong pull request.

### Merge your pull request

Trước khi gộp nhánh, bạn có thể phải giải quyết các xung đột gộp nhánh (merge conflicts) nếu những người khác đã thực hiện các thay đổi trên repo. Khi pull request của bạn đã được phê duyệt và không còn xung đột, bạn có thể đưa code của mình vào nhánh main thông qua việc thực hiện gộp nhánh trực tiếp từ giao diện pull request trên web.

### Pull requests

Bên cạnh việc cô lập quá trình phát triển tính năng, các nhánh giúp cho việc thảo luận về các thay đổi thông qua pull request trở nên khả thi. Một khi ai đó hoàn thành một tính năng, họ không lập tức gộp nó vào main. Thay vào đó, họ push nhánh tính năng lên máy chủ trung tâm và gửi một pull request yêu cầu gộp các phần bổ sung của họ vào main. Điều này trao cho các lập trình viên khác cơ hội rà soát các thay đổi trước khi chúng trở thành một phần của nền tảng code chính.

Rà soát code (Code review) là một lợi ích lớn của pull request, nhưng chúng thực chất được thiết kế để làm một phương thức tổng quát nhằm thảo luận về code. Bạn có thể coi pull request như một cuộc thảo luận dành riêng cho một nhánh cụ thể. Điều này có nghĩa là chúng cũng có thể được sử dụng từ rất sớm trong quy trình phát triển.

Ví dụ, nếu một lập trình viên cần sự trợ giúp với một tính năng cụ thể, tất cả những gì họ cần làm là gửi một pull request. Các bên liên quan sẽ được thông báo một cách tự động, và họ sẽ có thể nhìn thấy câu hỏi nằm ngay cạnh các commit có liên quan.

Một khi pull request được chấp nhận, hành động thực tế của việc xuất bản một tính năng về cơ bản tương tự như trong Centralized Workflow. Đầu tiên, bạn cần đảm bảo nhánh main cục bộ đã được đồng bộ với upstream main. Sau đó, bạn gộp nhánh tính năng vào main và push nhánh main đã cập nhật ngược trở lại kho chứa trung tâm.

### Example

Dưới đây là một ví dụ về loại kịch bản mà trong đó quy trình phân nhánh tính năng được sử dụng. Tình huống là một đội ngũ thực hiện rà soát code xung quanh một pull request của tính năng mới.

#### Mary begins a new feature

Trước khi bắt đầu phát triển một tính năng, Mary cần một nhánh cô lập để làm việc. Cô ấy yêu cầu một nhánh mới bằng câu lệnh sau:
```
git checkout -b marys-feature main
```
Lệnh này checkout một nhánh tên là marys-feature dựa trên main, và cờ -b ra lệnh cho Git tạo nhánh nếu nó chưa tồn tại. Trên nhánh này, Mary chỉnh sửa, đưa vào hàng chờ và commit các thay đổi theo cách thông thường, xây dựng tính năng của mình với số lượng commit tùy ý:
```
git status
git add <some-file>
git commit
```
#### Mary goes to lunch

Mary thêm một vài commit vào tính năng của cô ấy suốt buổi sáng. Trước khi rời đi ăn trưa, việc push nhánh tính năng lên kho chứa trung tâm là một ý tưởng hay. Việc này đóng vai trò như một bản sao lưu thuận tiện, nhưng nếu Mary đang hợp tác với các lập trình viên khác, hành động này cũng sẽ cho họ quyền truy cập vào các commit ban đầu của cô ấy.
```
git push -u origin marys-feature
```
Lệnh này đẩy nhánh marys-feature lên kho chứa trung tâm (origin), và cờ -u thiết lập nó thành nhánh theo dõi từ xa. Sau khi thiết lập xong nhánh theo dõi, Mary có thể gọi git push mà không cần tham số nào để đẩy tính năng của mình lên.

#### Mary finishes her feature

Khi Mary quay trở lại sau bữa trưa, cô ấy hoàn thành tính năng của mình. Trước khi gộp nó vào main, cô ấy cần gửi một pull request để thông báo cho phần còn lại của đội biết cô ấy đã làm xong. Nhưng trước tiên, cô ấy nên đảm bảo kho chứa trung tâm đã có các commit gần đây nhất của mình:
```
git push
```
Sau đó, cô ấy gửi một pull request trong giao diện Git của mình yêu cầu gộp marys-feature vào main, và các thành viên trong đội sẽ tự động nhận được thông báo. Điểm tuyệt vời của pull request là chúng hiển thị các bình luận ngay cạnh các commit liên quan, giúp dễ dàng đặt câu hỏi về các tập hợp thay đổi cụ thể.

#### Bill receives the pull request

Bill nhận được pull request và xem xét nhánh marys-feature. Anh ấy quyết định muốn thực hiện một vài thay đổi trước khi tích hợp nó vào dự án chính thức, và anh ấy cùng Mary có một số cuộc thảo luận qua lại ngay trong pull request.

#### Mary makes the changes

Để thực hiện các thay đổi, Mary sử dụng chính xác quy trình giống như cô ấy đã làm để tạo ra phiên bản đầu tiên của tính năng. Cô ấy chỉnh sửa, đưa vào hàng chờ, commit và push các cập nhật lên kho chứa trung tâm. Toàn bộ hoạt động của cô ấy hiển thị trong pull request, và Bill vẫn có thể đưa ra các bình luận trong suốt quá trình đó.

Nếu muốn, Bill hoàn toàn có thể kéo (pull) nhánh marys-feature vào kho chứa cục bộ của mình và tự tay làm việc trên đó. Bất kỳ commit nào anh ấy thêm vào cũng sẽ hiển thị trong pull request.

#### Mary publishes her feature

Một khi Bill đã sẵn sàng chấp nhận pull request, ai đó cần phải gộp tính năng này vào dự án ổn định (việc này có thể được thực hiện bởi Bill hoặc Mary):
```
git checkout main
git pull
git pull origin marys-feature
git push
```
Quy trình này thường kết thúc bằng một commit gộp (merge commit). Một số lập trình viên thích điều này vì nó giống như một biểu tượng liên kết tính năng với phần còn lại của nền tảng code. Tuy nhiên, nếu bạn là người thiên về một lịch sử tuyến tính (linear history), bạn hoàn toàn có thể rebase tính năng lên trên đỉnh ngọn của main trước khi thực thi lệnh merge, kết quả trả về sẽ là một cú gộp tiến thẳng (fast-forward merge).

Một số giao diện đồ họa (GUIs) sẽ tự động hóa quy trình chấp nhận pull request bằng cách chạy toàn bộ các câu lệnh này chỉ bằng việc nhấp vào nút “Accept”. Nếu công cụ của bạn không có, nó ít nhất cũng phải có khả năng tự động đóng pull request khi nhánh tính năng được gộp vào main.

#### Meanwhile, John is doing the exact same thing

Trong khi Mary và Bill đang làm việc trên nhánh marys-feature và thảo luận về nó trong pull request của cô ấy, John cũng đang thực hiện điều chính xác tương tự với nhánh tính năng của riêng anh ấy. Bằng cách cô lập các tính năng vào các nhánh riêng biệt, mọi người đều có thể làm việc độc lập, tuy nhiên việc chia sẻ các thay đổi với các lập trình viên khác khi cần thiết vẫn là điều vô cùng đơn giản.

## Gitflow workflow

Gitflow là một quy trình làm việc Git truyền thống (legacy workflow), ban đầu từng là một chiến lược mang tính đột phá và mới lạ để quản lý các nhánh Git. Hiện nay, Gitflow đã giảm dần mức độ phổ biến để nhường chỗ cho các quy trình dựa trên nhánh chính (trunk-based workflows) - vốn được coi là thực hành tốt nhất (best practices) cho quy trình phát triển phần mềm liên tục và DevOps hiện đại. Gitflow cũng có thể gặp nhiều thách thức khi áp dụng cùng với hệ thống CI/CD. Bài viết này sẽ chi tiết hóa Gitflow nhằm mục đích ghi nhận lịch sử.

### What is Gitflow?

Gitflow là một mô hình phân nhánh Git thay thế, sử dụng các nhánh tính năng (feature branches) và nhiều nhánh chính sơ cấp (primary branches). Mô hình này lần đầu tiên được xuất bản và làm cho trở nên phổ biến bởi Vincent Driessen tại nvie. So với mô hình phát triển trunk-based, Gitflow sở hữu nhiều nhánh có tuổi thọ lâu hơn và kích thước commit lớn hơn.

Dưới model này, các lập trình viên tạo một nhánh tính năng và trì hoãn việc gộp nó vào nhánh chính cho đến khi tính năng đó hoàn thành hoàn toàn. Những nhánh tính năng có tuổi thọ dài này đòi hỏi sự cộng tác nhiều hơn khi gộp nhánh và có nguy cơ cao bị rẽ hướng lệch pha so với nhánh chính, đồng thời có thể gây ra các cập nhật xung đột.

Gitflow có thể được sử dụng cho các dự án có chu kỳ phát hành phiên bản cố định (scheduled release cycle) và áp dụng cho thực hành tốt nhất DevOps về phân phối liên tục (continuous delivery). Quy trình này không thêm bất kỳ khái niệm hay câu lệnh mới nào vượt ra ngoài những gì Quy trình Feature Branch đòi hỏi. Thay vào đó, nó gán các vai trò rất cụ thể cho các nhánh khác nhau và định nghĩa cách thức cũng như thời điểm chúng nên tương tác với nhau.

Bên cạnh các nhánh tính năng, nó sử dụng các nhánh riêng lẻ cho việc chuẩn bị, bảo trì và ghi lại các phiên bản phát hành. Tất nhiên, bạn cũng được tận dụng toàn bộ lợi ích của Quy trình Feature Branch: các pull request, các thử nghiệm cô lập và quy trình cộng tác hiệu quả hơn.

### How it works
#### Develop and main branches

Thay vì chỉ sử dụng một nhánh main duy nhất, quy trình làm việc này sử dụng hai nhánh để ghi lại lịch sử của dự án. Nhánh main lưu trữ lịch sử phát hành chính thức (official release history), và nhánh develop đóng vai trò là nhánh tích hợp cho các tính năng mới. Việc gắn thẻ tag số phiên bản cho tất cả các commit trong nhánh main cũng rất tiện lợi.

Bước đầu tiên là bổ sung một nhánh develop song song với nhánh main mặc định. Một cách đơn giản để thực hiện việc này là một lập trình viên tạo một nhánh develop trống cục bộ dưới máy rồi push nó lên server:

```
git branch develop
git push -u origin develop
```
Nhánh này sẽ chứa toàn bộ lịch sử đầy đủ của dự án, trong khi main sẽ chứa một phiên bản rút gọn. Các lập trình viên khác lúc này nên clone kho chứa trung tâm về và tạo một nhánh theo dõi (tracking branch) cho develop.

Khi sử dụng thư viện mở rộng git-flow, việc thực thi lệnh git flow init trên một repo sẵn có sẽ tự động khởi tạo nhánh develop:

```
$ git flow init

Initialized empty Git repository in ~/project/.git/
No branches exist yet. Base branches must be created now.
Branch name for production releases: [main]
Branch name for "next release" development: [develop]

How to name your supporting branch prefixes?
Feature branches? [feature/]
Release branches? [release/]
Hotfix branches? [hotfix/]
Support branches? [support/]
Version tag prefix? []

$ git branch
* develop
  main
```
#### Feature branches

Mỗi tính năng mới nên nằm trên nhánh riêng của nó, nhánh này có thể được push lên kho chứa trung tâm để sao lưu hoặc cộng tác nhóm. Tuy nhiên, thay vì tách nhánh ra từ main, các nhánh tính năng sẽ sử dụng develop làm nhánh cha của chúng. Khi một tính năng hoàn thành, nó sẽ được gộp ngược trở lại vào develop. Các tính năng tuyệt đối không bao giờ được tương tác trực tiếp với main.

Lưu ý rằng các nhánh tính năng khi kết hợp với nhánh develop về mặt bản chất chính là Quy trình Feature Branch. Tuy nhiên, quy trình Gitflow không dừng lại ở đó.

Các nhánh tính năng nhìn chung được tạo ra từ nhánh develop mới nhất.

#### Creating a feature branch

Khi không sử dụng công cụ mở rộng git-flow:
```
git checkout develop
git checkout -b feature_branch
```

Khi sử dụng công cụ mở rộng git-flow:
```
git flow feature start feature_branch
```
Sau đó tiếp tục công việc của bạn và sử dụng Git như bình thường.
#### Finishing a feature branch

Khi bạn đã hoàn tất công việc phát triển trên tính năng đó, bước tiếp theo là gộp feature_branch vào develop.

Khi không sử dụng công cụ mở rộng git-flow:
```
git checkout develop
git merge feature_branch
```
Khi sử dụng công cụ mở rộng git-flow:
```
git flow feature finish feature_branch
```
Khi bạn đã hoàn tất công việc phát triển trên tính năng đó, bước tiếp theo là gộp feature_branch vào develop.

Khi không sử dụng công cụ mở rộng git-flow:
```
git checkout develop
git merge feature_branch
```
Khi sử dụng công cụ mở rộng git-flow:
```
git flow feature finish feature_branch
```

#### Release branches
Một khi nhánh develop đã tích lũy đủ các tính năng cho một đợt phát hành (hoặc một ngày phát hành định sẵn đang đến gần), bạn sẽ tách một nhánh phát hành (release branch) ra từ develop. Việc tạo nhánh này sẽ khởi động chu kỳ phát hành tiếp theo, vì vậy không có tính năng mới nào được phép thêm vào kể từ thời điểm này — chỉ có các bản sửa lỗi (bug fixes), viết tài liệu hướng dẫn và các tác vụ hướng tới việc phát hành khác mới được phép đưa vào nhánh này.

Một khi đã sẵn sàng để xuất bản, nhánh phát hành sẽ được gộp vào main và đánh dấu tag với một số phiên bản. Thêm vào đó, nó cũng phải được gộp ngược trở lại vào develop (vì nhánh develop có thể đã tiến triển thêm các commit khác kể từ ngày nhánh phát hành được khởi tạo).

Việc sử dụng một nhánh chuyên dụng để chuẩn bị cho các đợt phát hành giúp một đội nhóm có thể trau chuốt phiên bản hiện tại trong khi một đội nhóm khác vẫn tiếp tục xây dựng các tính năng cho đợt phát hành kế tiếp. Nó cũng tạo ra các giai đoạn phát triển được định nghĩa rõ ràng (ví dụ, thật dễ dàng để tuyên bố: "Tuần này chúng ta chuẩn bị cho phiên bản 4.0," và thực sự nhìn thấy cấu trúc đó hiển thị trên kho chứa dữ liệu).

Việc tạo các nhánh phát hành cũng là một thao tác phân nhánh thẳng thắn. Giống như các nhánh tính năng, các nhánh phát hành được dựa trên nền tảng của nhánh develop. Một nhánh phát hành mới có thể được tạo bằng các phương thức sau:

Khi không sử dụng công cụ mở rộng git-flow:
```
git checkout develop
git checkout -b release/0.1.0
```
Khi sử dụng công cụ mở rộng git-flow:
```
$ git flow release start 0.1.0
Switched to a new branch 'release/0.1.0'
```
Một khi phiên bản phát hành đã sẵn sàng xuất bản, nó sẽ được gộp vào main và develop, sau đó nhánh phát hành sẽ bị xóa bỏ. Việc gộp ngược lại vào develop là cực kỳ quan trọng vì các cập nhật sửa lỗi quan trọng có thể đã được thêm vào nhánh phát hành và chúng cần phải có sẵn cho các tính năng mới sau này. Nếu tổ chức của bạn chú trọng việc rà soát code (code review), đây sẽ là vị trí lý tưởng cho một pull request.

Để hoàn thành một nhánh phát hành, sử dụng các phương thức sau:

Khi không sử dụng công cụ mở rộng git-flow:
```
git checkout main
git merge release/0.1.0
```
Hoặc với công cụ mở rộng git-flow:
```
git flow release finish '0.1.0'
```
#### Hotfix branches

Các nhánh bảo trì hoặc nhánh sửa lỗi nóng (hotfix branches) được sử dụng để nhanh chóng vá lỗi cho các phiên bản phát hành chính thức (production releases). Các nhánh hotfix rất giống với các nhánh phát hành và nhánh tính năng, ngoại trừ việc chúng dựa trên nền tảng của nhánh main thay vì develop. Đây là nhánh duy nhất được phép tách trực tiếp ra từ main.

Ngay khi việc sửa lỗi hoàn tất, nó phải được gộp vào cả main và develop (hoặc nhánh phát hành hiện tại), và nhánh main cần được đánh dấu tag với một số phiên bản cập nhật mới.

Việc có một dòng phát triển chuyên dụng cho các bản sửa lỗi giúp đội ngũ của bạn xử lý các sự cố mà không làm gián đoạn phần còn lại của quy trình làm việc hoặc phải chờ đợi chu kỳ phát hành tiếp theo. Bạn có thể coi các nhánh bảo trì giống như các nhánh phát hành đặc biệt (ad hoc release branches) làm việc trực tiếp với main. Một nhánh hotfix có thể được tạo bằng các phương thức sau:

Khi không sử dụng công cụ mở rộng git-flow:
```
git checkout main
git checkout -b hotfix_branch
```
Khi sử dụng công cụ mở rộng git-flow:
```
$ git flow hotfix start hotfix_branch
```
Tương tự như việc hoàn thành một nhánh phát hành, một nhánh hotfix sẽ được gộp vào cả main và develop.

Khi không sử dụng công cụ mở rộng git-flow:
```
git checkout main
git merge hotfix_branch
git checkout develop
git merge hotfix_branch
git branch -d hotfix_branch
```
Khi sử dụng công cụ mở rộng git-flow:
```
git flow hotfix finish hotfix_branch
```

## Forking workflow  
Quy trình Forking Workflow về mặt nền tảng khác biệt hoàn toàn so với các quy trình làm việc Git phổ biến khác. Thay vì sử dụng một kho chứa duy nhất trên máy chủ (server-side repository) để đóng vai trò là nền tảng code "trung tâm", nó cung cấp cho mỗi lập trình viên một kho chứa riêng trên server. Điều này có nghĩa là mỗi người đóng góp sẽ sở hữu không phải một, mà là hai kho chứa Git: Một kho chứa riêng tư cục bộ dưới máy local và một kho chứa công khai nằm trên server từ xa. Quy trình Forking Workflow thường được nhìn thấy phổ biến nhất trong các dự án mã nguồn mở công khai (public open source projects).

Ưu điểm chính của Forking Workflow là các đóng góp có thể được tích hợp vào hệ thống mà không bắt buộc tất cả mọi người phải push chung vào một kho chứa trung tâm duy nhất. Các lập trình viên tiến hành push code lên kho chứa trên server của riêng họ, và chỉ duy nhất người quản trị dự án (project maintainer) mới có quyền push vào kho chứa chính thức. Điều này cho phép người quản trị chấp nhận các commit từ bất kỳ lập trình viên nào mà không cần phải cấp quyền ghi (write access) vào nền tảng code chính thức cho họ.

Quy trình Forking Workflow thường tuân theo một mô hình phân nhánh dựa trên Quy trình Gitflow Workflow. Điều này có nghĩa là các nhánh tính năng hoàn chỉnh sẽ được nhắm mục tiêu để gộp vào kho chứa của người quản trị dự án gốc. Kết quả trả về là một quy trình làm việc phân tán, mang lại phương thức linh hoạt cho các đội nhóm lớn, có tính chất mở rộng tự nhiên (bao gồm cả các bên thứ ba chưa được cấp quyền tin cậy) hợp tác với nhau một cách an toàn. Điều này cũng biến nó trở thành một quy trình lý tưởng cho các dự án mã nguồn mở.

### How it works

Giống như các quy trình làm việc Git khác, Forking Workflow bắt đầu với một kho chứa công khai chính thức được lưu trữ trên một máy chủ server. Nhưng khi một lập trình viên mới muốn bắt đầu tham gia vào dự án, họ không tiến hành clone trực tiếp từ kho chứa chính thức đó.

Thay vào đó, họ thực hiện sao chép bản sao (fork) kho chứa chính thức để tạo ra một bản sao của nó nằm trên server. Bản sao mới này phục vụ như một kho chứa công khai cá nhân của riêng họ — không có lập trình viên nào khác được phép push code vào đó, nhưng họ có thể kéo (pull) các thay đổi từ nó về. Sau khi đã tạo xong bản sao trên server, lập trình viên mới thực thi lệnh git clone để lấy một bản sao của nó về máy tính cục bộ của mình. Đây sẽ là môi trường phát triển riêng tư của họ, giống hệt như các quy trình làm việc khác.

Khi họ đã sẵn sàng xuất bản một commit cục bộ, họ tiến hành push commit đó lên kho chứa công khai của riêng mình — chứ không phải kho chứa chính thức. Sau đó, họ gửi một Pull Request tới kho chứa chính thức, giúp thông báo cho người quản trị dự án biết rằng một bản cập nhật đã sẵn sàng để được tích hợp. Pull request này cũng đóng vai trò như một luồng thảo luận thuận tiện nếu có bất kỳ vấn đề gì xảy ra với đoạn code được đóng góp. Dưới đây là ví dụ từng bước chi tiết của quy trình này:

Lập trình viên 'fork' một kho chứa 'chính thức' trên server. Việc này tạo ra một bản sao của riêng họ trên server.

Bản sao mới trên server được clone về hệ thống máy cục bộ của họ.

Một đường dẫn Git remote trỏ tới kho chứa 'chính thức' được thêm vào bản sao clone cục bộ.

Một nhánh tính năng cục bộ mới được tạo ra.

Lập trình viên thực hiện các thay đổi trên nhánh mới đó.

Các commit mới được tạo ra cho các thay đổi này.

Nhánh tính năng được push lên bản sao trên server của chính lập trình viên đó.

Lập trình viên mở một Pull Request từ nhánh mới hướng tới kho chứa 'chính thức'.

Pull request được phê duyệt gộp nhánh và được tích hợp vào kho chứa gốc trên server.

Để tích hợp tính năng vào nền tảng code chính thức, người quản trị dự án sẽ kéo (pull) các thay đổi của người đóng góp vào kho chứa cục bộ của họ, kiểm tra kỹ để đảm bảo nó không làm hỏng dự án, gộp nó vào nhánh main cục bộ, rồi push nhánh main này lên kho chứa chính thức trên server. Đóng góp đó hiện đã trở thành một phần của dự án, và các lập trình viên khác nên tiến hành pull từ kho chứa chính thức về để đồng bộ hóa kho chứa cục bộ của mình.

Điều quan trọng cần thấu hiểu là khái niệm về một kho chứa "chính thức" trong Forking Workflow đơn thuần chỉ là một sự quy ước. Trên thực tế, điều duy nhất khiến kho chứa chính thức trở nên chính thức là vì nó là kho chứa công khai của người quản trị dự án.

### Forking vs cloning

Cần lưu ý rằng các kho chứa được "fork" và hành động "forking" không phải là các thao tác gì quá đặc biệt. Các kho chứa được fork thực chất được tạo ra bằng lệnh git clone tiêu chuẩn. Bản fork nhìn chung là các "bản sao trên server" (server-side clones) và thường được quản lý, lưu trữ bởi một dịch vụ Git bên thứ ba như Bitbucket hoặc GitHub. Không có một câu lệnh Git độc nhất nào để tạo ra các kho chứa được fork. Thao tác clone về cơ bản là một sự sao chép của một kho chứa và lịch sử của nó.

### Branching in the forking workflow  

Tất cả các kho chứa công khai cá nhân này thực ra chỉ là một phương thức thuận tiện để chia sẻ các nhánh với các lập trình viên khác. Mọi người vẫn nên sử dụng các nhánh để cô lập từng tính năng riêng lẻ, giống hệt như trong Quy trình Feature Branch và Quy trình Gitflow. Khác biệt duy nhất nằm ở cách thức các nhánh đó được chia sẻ. Trong Forking Workflow, chúng được kéo (pull) vào kho chứa cục bộ của một lập trình viên khác, trong khi ở quy trình Feature Branch và Gitflow, chúng được đẩy (push) trực tiếp lên kho chứa chính thức.

### Fork a repository

Tất cả các lập trình viên mới tham gia vào một dự án Forking Workflow đều cần phải fork kho chứa chính thức. Như đã tuyên bố trước đó, fork chỉ là một thao tác git clone tiêu chuẩn trên server. Bạn hoàn toàn có thể làm việc này bằng cách đăng nhập SSH vào server và chạy lệnh git clone để sao chép nó sang một vị trí khác trên server. Các dịch vụ lưu trữ Git phổ biến như Bitbucket hay GitHub cung cấp tính năng fork repo giúp tự động hóa bước này trên giao diện.

### Clone your fork

Giả định việc sử dụng Bitbucket để lưu trữ các kho chứa này, các lập trình viên trong dự án nên có tài khoản Bitbucket riêng và họ tiến hành clone bản sao đã fork của mình bằng lệnh:
```
git clone https://user@bitbucket.org/user/repo.git
```

### Adding a remote

Trong khi các quy trình làm việc Git khác chỉ sử dụng một remote duy nhất là origin trỏ về kho chứa trung tâm, thì Forking Workflow đòi hỏi phải có hai remote — một cái cho kho chứa chính thức, và một cái cho kho chứa cá nhân trên server của lập trình viên.

Mặc dù bạn có thể đặt tên cho các remote này là bất kỳ thứ gì bạn muốn, một quy ước phổ biến là sử dụng origin làm remote cho kho chứa đã fork của bạn (tên này được tạo tự động khi bạn chạy lệnh git clone) và upstream cho kho chứa chính thức.

```
git remote add upstream https://bitbucket.org/maintainer/repo
```
Bạn sẽ cần phải tự tay tạo remote upstream bằng câu lệnh trên. Việc này sẽ giúp bạn dễ dàng giữ cho kho chứa cục bộ của mình luôn được cập nhật mới nhất khi dự án chính thức tiến triển. Lưu ý rằng nếu kho chứa upstream của bạn có bật chế độ xác thực (nghĩa là nó không phải mã nguồn mở hoàn toàn), bạn sẽ cần cung cấp thêm tên người dùng:
```
git remote add upstream https://user@bitbucket.org/maintainer/repo.git
```
Cấu hình này yêu cầu người dùng phải cung cấp mật khẩu hợp lệ trước khi thực hiện lệnh clone hoặc pull từ nền tảng code chính thức.

### Working in a branch: making & pushing changes

Trong bản sao cục bộ dưới máy của kho chứa đã fork, lập trình viên có thể chỉnh sửa code, commit các thay đổi và tạo các nhánh giống hệt như các quy trình làm việc Git khác:
```
git checkout -b some-feature
# Tiến hành chỉnh sửa một số đoạn code
git commit -a -m "Add first draft of some feature"
```
Toàn bộ các thay đổi của họ sẽ hoàn toàn riêng tư cho đến khi họ push nó lên kho chứa công khai của mình. Và nếu dự án chính thức có thêm những commit mới, họ có thể truy cập và nạp các commit mới đó bằng lệnh git pull:
```
git pull upstream main
```
Vì các lập trình viên luôn làm việc trên một nhánh tính năng chuyên dụng, hành động này nhìn chung sẽ kết thúc bằng một cú gộp tiến thẳng (Fast-forward merge).

### Making a pull request

Một khi lập trình viên đã sẵn sàng chia sẻ tính năng mới của mình, họ cần phải thực hiện hai việc.

Đầu tiên, họ phải làm cho đóng góp của mình có thể tiếp cận được bởi các lập trình viên khác bằng cách push nó lên kho chứa công khai của riêng họ. Remote origin của họ đã được thiết lập sẵn từ trước, vì vậy tất cả những gì họ cần làm là gõ lệnh:
```
git push origin feature-branch
```
Hành động này lệch khỏi các quy trình khác ở chỗ con trỏ remote origin đang trỏ tới kho chứa cá nhân trên server của lập trình viên, chứ không phải nền tảng code chính thức.

Thứ hai, họ cần phải thông báo cho người quản trị dự án biết rằng họ muốn gộp tính năng của mình vào nền tảng code chính thức. Bitbucket hay GitHub cung cấp một nút bấm “pull request” dẫn đến một biểu mẫu yêu cầu bạn chỉ định rõ nhánh nào bạn muốn gộp vào kho chứa chính thức. Thông thường, bạn sẽ muốn tích hợp nhánh tính năng (feature-branch) của mình vào nhánh chính main của remote thượng nguồn (upstream).  