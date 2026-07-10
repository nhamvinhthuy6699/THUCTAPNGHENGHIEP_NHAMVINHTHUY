# SEB - SAFE EXAM BROWSER
### KHÁI NIỆM
Safe Exam Browser là một môi trường trình duyệt web giúp thực hiện các bài kiểm tra một cách an toàn. Phần mềm này tạm thời biến bất kỳ máy tính nào thành một trạm an toàn. Chúng kiểm soát quyền truy cập như chức năng hệ thống, các trang web và ứng dụng khác, Đồng thời ngăn chặn sử dụng trái phép các tài nguyên trong quá trình thi cử.

### THÔNG TIN TÁC GIẢ  
Safe Exam Browser là một ứng dụng được phát triển bởi ETH Zurich (Viện Công nghệ Liên bang Thụy Sĩ tại Zurich) để tiến hành các kỳ thi trực tuyến an toàn và được hỗ trợ bởi một 1 nhóm các nhà nghiêm cứu và kĩ sư. Safe Exam Browser được sử dụng bởi hàng nghìn trường đại học và tổ chức học thuật trên toàn thế giới, bao gồm Đại học Oxford, Hội đồng Anh, v.v.  
Trình duyệt thi an toàn © 2010-2026 ETH Zurich, Dịch vụ CNTT. Dựa trên ý tưởng ban đầu về Trình duyệt thi an toàn của Stefan Schneider, Đại học Giessen
Ý tưởng dự án: Tiến sĩ Thomas Piendl, Daniel R. Schneider, Damian Büchel, Tiến sĩ Dirk Bauer, Kai Reuter, Tobias Halbherr, Karsten Burger, Marco Lehre, Brigitte Schmucki, Oliver Rahs.  

### HOÀN CẢNH RA ĐỜI  
Phần mềm Safe Exam Browser (SEB) giúp các tổ chức giảm thiểu việc sử dụng các tài nguyên trái phép trong các kỳ thi trực tuyến. Tùy thuộc vào nền tảng và cấu hình, nó có thể chạy ở chế độ toàn màn hình hoặc với nhiều cửa sổ trình duyệt không bao gồm các yếu tố điều hướng tiêu chuẩn. 
SEB có thể hạn chế truy cập vào các trang web, trang hoặc tài nguyên được phê duyệt thông qua lọc URL. Nó cũng có thể vô hiệu hóa kiểm tra chính tả và tra cứu từ điển, mặc dù các tính năng này có thể được cho phép khi cần thiết. Các biện pháp kiểm soát này làm cho nó hữu ích cho các kỳ thi mà sinh viên phải ở trong một môi trường kỹ thuật số được xác định.  

### VẤN ĐỀ SEB GIẢI QUYẾT
- Học sinh chỉ có thể làm bài kiểm tra nếu sử dụng Trình duyệt bài kiểm tra an toàn.
- Cửa sổ trình duyệt sẽ không có URL hoặc trường tìm kiếm và bạn có thể tắt chức năng điều hướng tiến/lùi và tải lại trang.
- Trình duyệt Safe Exam Browser không thể đóng cho đến khi bài kiểm tra được nộp.
- Việc chuyển sang các ứng dụng khác bị vô hiệu hóa theo mặc định, nhưng bạn vẫn có thể cho phép sử dụng các ứng dụng của bên thứ ba cụ thể trong quá trình thi.
- Các phím tắt như Win+Tab, Alt+Tab, Ctrl+Alt+Del, Alt+F4, Print Screen, Cmd+Tab bị vô hiệu hóa hoặc không thể sử dụng để đóng Trình duyệt thi an toàn hoặc chuyển sang tài khoản người dùng khác trên máy tính. Chức năng chụp ảnh màn hình đã bị vô hiệu hóa.
- Bộ nhớ tạm sẽ được xóa khi khởi động và thoát khỏi Trình duyệt Kỳ thi An toàn.
- Menu ngữ cảnh của trình duyệt đã bị vô hiệu hóa.
- Bạn có thể cấu hình để truy cập các trang web/trang/tài nguyên cụ thể trong suốt kỳ thi bằng cách sử dụng bộ lọc URL.
- Chức năng kiểm tra chính tả và tra cứu từ điển bị vô hiệu hóa, nhưng có thể được cho phép tùy chọn.

### KIẾN TRÚC VÀ NGUYÊN LÝ HOẠT ĐỘNG CỦA SEB
SEB bao gồm một ứng dụng ki-ốt và một phần trình duyệt, đang chạy trên máy tính thi hoặc thiết bị máy tính bảng. Ứng dụng ki-ốt khóa máy tính thi, phần trình duyệt giao tiếp qua internet (hoặc mạng LAN) với mô-đun trắc nghiệm của hệ thống LMS đang chạy trên máy chủ.

- Ứng dụng ki-ốt Khóa máy tính và khởi động trình duyệt SEB cùng các ứng dụng bên thứ ba tùy chọn. Vì ứng dụng này phải điều khiển nhiều chức năng khác nhau của hệ điều hành, nên nó được thiết kế rất chuyên biệt cho từng hệ thống.
- Trình duyệt SEB Trang thi LMS được tải và hiển thị bằng URL được thiết lập sẵn và không hiển thị bất kỳ yếu tố điều hướng nào như thanh địa chỉ, trường công cụ tìm kiếm, v.v. Phiên bản SEB dành cho Windows hiện đang sử dụng công cụ trình duyệt Mozilla Gecko, dưới dạng Firefox hoặc XULRunner. SEB dành cho macOS và iOS sử dụng công cụ trình duyệt WebKit.
- Cái hệ thống quản lý học tập Bao gồm các mô-đun trắc nghiệm, được sử dụng cho các kỳ thi trực tuyến. SEB dựa vào các phần mở rộng/giao diện cho các mô-đun bài kiểm tra trong Hệ thống Quản lý Học tập hoặc bộ công cụ đánh giá điện tử để đảm bảo an toàn cho các kỳ thi. Với các tiện ích mở rộng này, giao diện người dùng của LMS được thu gọn chỉ còn chứa chức năng điều hướng cho kỳ thi (không có liên kết đến các trang khác ngoài bài kiểm tra) và không có các tính năng không mong muốn khác như nhắn tin. Bài thi cũng có thể được cấu hình để chỉ chạy trên SEB, chứ không phải trình duyệt khác. Các tiện ích mở rộng SEB LMS này, ban đầu phải được cài đặt riêng biệt để đạt được khả năng kết nối với SEB, đã được tích hợp vào LMS trong các phiên bản gần đây của OpenOlat, Open edX, ILIAS và Moodle.

### LỊCH SỬ PHIÊN BẢN VÀ THAY ĐỔI QUAN TRỌNG 
- Giai đoạn SEB 1.x (2009 - 2013): Sử dụng nhân WebKit hoặc Internet Explorer, chỉ có tính năng khóa màn hình Kiosk thô sơ, chưa có khóa mã hóa.

- Giai đoạn SEB 2.0 đến 2.3 (2014 - 2019): Chuyển sang nhân Mozilla XULRunner (Firefox), giới thiệu cơ chế Browser Exam Key và Config Key để xác thực với Moodle.

- Phiên bản SEB 2.4 (2020): Là bản cập nhật cuối cùng của thế hệ 2.x, tích hợp sâu vào Moodle 3.9+ và bổ sung tính năng Quét/Tắt tiến trình ngầm (Process Monitoring).

- Giai đoạn SEB 3.0 đến 3.5 (2020 - 2023): Loại bỏ hoàn toàn nhân Firefox, chuyển sang nhân Chromium Embedded Framework (CEF). Tách biệt lõi trình duyệt và lõi hệ thống để chống crash, tích hợp WebRTC để mở Webcam/Microphone phục vụ Giám thị AI (Proctoring).

- Giai đoạn SEB 3.6 đến nay (2024 - 2026): Tương thích hoàn toàn Windows 11, chặn màn hình ảo, chặn kết nối không dây như Miracast/AirPlay và nâng cấp bộ giải mã video bài thi.

### MỐI QUAN HỆ GIỮA SEB VỚI 1 BROWSER THƯỜNG NHƯ FIREFOX

**Bản chất kiến trúc hệ thống:** Safe Exam Browser (SEB) không phải là một trình duyệt độc lập được xây dựng hoàn toàn từ đầu. Kiến trúc của SEB hoạt động theo mô hình tách biệt: Lớp vỏ bảo mật (Security Shell) và Nhân trình duyệt nhúng (Browser Engine).

**Thành phần Lõi (Browser Engine):** SEB mượn hoàn toàn bộ máy xử lý đồ họa web (Engine) của các trình duyệt thông thường để hiển thị trang web thi.

- Đối với phiên bản SEB 2.4, lõi được nhúng là Mozilla XULRunner (môi trường thực thi được tách từ nhân của trình duyệt Firefox cũ).

- Đối với phiên bản SEB 3.x (thế hệ mới), lõi đã được chuyển sang Chromium Embedded Framework (CEF - nhân của Google Chrome và Microsoft Edge).

- Đối với hệ điều hành macOS, SEB sử dụng nhân WebKit (nhân của trình duyệt Apple Safari).

**Thành phần Lớp vỏ (Security Shell):** Là phần mã nguồn do đội ngũ SEB phát triển (viết bằng ngôn ngữ C#/.NET trên hệ điều hành Windows). Lớp vỏ này bao bọc bên ngoài nhân trình duyệt để thực hiện các nhiệm vụ can thiệp sâu vào Windows API/Registry nhằm khóa cứng hệ thống (chặn Alt+Tab, Ctrl+Alt+Del, chuột phải, và quét các tiến trình ngầm).

**Mối quan hệ phụ thuộc kỹ thuật:** Lớp vỏ SEB bị ràng buộc và phụ thuộc trực tiếp vào các giới hạn công nghệ của nhân trình duyệt được sử dụng bên trong nó.

**Minh chứng cụ thể từ tài liệu:** "Uploading can only be blocked by SEB when the website is using standard form elements (this is a restriction of the used Firefox browser engine)".

Ý nghĩa: Vì phiên bản SEB 2.4 sử dụng nhân Firefox cũ, nên nếu hệ thống thi sử dụng các phương thức tải tệp lên (Upload) tùy biến nâng cao (bằng Javascript/kéo thả thay vì thẻ Form HTML tiêu chuẩn), nhân Firefox này không thể bắt được sự kiện để báo cho lớp vỏ SEB thực hiện lệnh chặn.

Tóm lại bản chất khi sử dụng SEB 2.4: Khi thí sinh làm bài thi trên SEB 2.4, bản chất là họ đang lướt web bằng một phiên bản tinh giản của trình duyệt Firefox. Tuy nhiên, phiên bản Firefox này đã bị lớp vỏ của SEB tước bỏ hoàn toàn các tính năng tự do (đa nhiệm, mở tab, cài tiện ích mở rộng) để biến máy tính thành một trạm khảo thí an toàn.

### THÔNG TIN REPO, DOCS, ISSUES 
- Trang chủ dự án: https://safeexambrowser.org
- Tài liệu hướng dẫn sử dụng cho Windows: https://safeexambrowser.org/windows/win_usermanual_en.html
- Kho lưu trữ mã nguồn chính thức trên GitHub: https://github.com/SafeExamBrowser
- Kho tải bộ cài và mã nguồn các bản cũ (bao gồm bản 2.4): https://sourceforge.net/projects/seb/files/seb/


# CÀI ĐẶT SAFE EXAM BROWSER SERVER 
## CHUẨN BỊ 
### YÊU CẦU THÀNH PHẦN VÀ PHIÊN BẢN
- Ubuntu (từ 24.04TS trở lên, không nên cấu hình wls hay phần mềm ảo trên windows vì theo tài liệu nó làm tốt nhất trên máy server thực thi)
- DOCKER ENGINE, DOCKER COMPOSE
- MOODLE PHIÊN BẢN 4.5.12
- POSTGRESQL PHIÊN BẢN 16
- SEB SERVER PHIÊN BẢN 2.2 STABLE
- MARIADB PHIÊN BẢN 10.5
- SAFE EXAM BROWSER CLIENT TRÊN WINDOWS PHIÊN BẢN 3.6.X TRỞ LÊN

## CÀI ĐẶT
### CÀI ĐẶT DOCKER 
Cập nhập ubuntu:  
```bash
sudo apt update && sudo apt upgrade -y
```

#### CÀI ĐẶT CÁC GÓI CẦN THIẾT 
```bash
sudo apt install \
ca-certificates \
curl \
gnupg \
lsb-release \
apt-transport-https -y
```

#### THÊM KHÓA GPG CỦA KHO LƯU TRỮ DOCKER CHÍNH THỨC VÀO HỆ THỐNG
```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

#### THÊM KHO LƯU TRỮ DOCKER VÀO MÃ NGUỒN APT
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
- Ubuntu sẽ biết tải Docker từ repo nào

#### CẬP NHẬP REPO 
```bash
sudo apt update
```

#### CÀI ĐẶT DOCKER
```bash
sudo apt install \
docker-ce \
docker-ce-cli \
containerd.io \
docker-buildx-plugin \
docker-compose-plugin -y
```
#### KHỞI ĐỘNG DOCKER
```bash
sudo systemctl enable docker 
sudo systemctl start docker
sudo systemctl status docker
```

#### KIỂM TRA DOCKER 
```bash
docker compose version 
docker version
```

#### CHO PHÉP USER CHẠY DOCKER KHÔNG CẦN SUDO 
```bash
sudo usermod -aG docker $USER
```

### CÀI ĐẶT SAFE EXAM BROWSER SERVER V2.2 BẰNG DOCKER COMPOSE
#### TẢI BỘ CÀI ĐẶT SEB SERVER
```bash 
cd ~
mkdir -p ~/sebserver
cd ~/sebserver
```

#### CLONE REPO CHÍNH THỨC
```bash 
git clone https://github.com/SafeExamBrowser/seb-server-setup.git
```

#### SAU KHI CLONE XONG, VÀO THƯ MỤC BUNDLED PRODUCTION
```bash
cd ~/sebserver/seb-server-setup/docker/prod/bundled
```
- Kiểm tra file xem có doker-compose.yml không, nếu không thấy thì đang sai thư mục

```bash
ls -la
```

#### CẤU HÌNH FILE .env
```bash
nano .env

SEBSERVER_PWD=ttcnttnn@123!
DB_SA_PWD=ttcnttnn@123!
DNS_NAME=192.168.0.229
```

#### SỬA docker-compose.yml ĐỂ CHẠY HTTP PORT 8080
```bash
nano docker-compose.yml
```

- TÌM VÀ SỬA TRONG YML:  
CÁC DÒNG LÚC ĐẦU NHƯ NÀY:  

```bash 
- sebserver_webservice_http_external_scheme=https
- sebserver_webservice_http_external_servername=${DNS_NAME}
- sebserver_webservice_http_external_port=
- sebserver_webservice_autologin_url=https://${DNS_NAME}
```

SỬA THÀNH:  

```bash
- sebserver_webservice_http_external_scheme=http
- sebserver_webservice_http_external_servername=${DNS_NAME}
- sebserver_webservice_http_external_port=8080
- sebserver_webservice_autologin_url=http://${DNS_NAME}:8080
```

LƯU FILE

#### TẢI DOCKER IMAGE VÀ KHỞI ĐỘNG SEB SERVER
- TẢI IMAGE
```bash
sudo docker compose pull
sudo docker compose up -d
```
- **LƯU Ý:** LẦN ĐẦU SẼ KHỞI ĐỘNG HƠI LÂU ĐỂ TẢI CONTAINER, ĐỢI VÀI PHÚT CONTAINER KHỞI ĐỘNG

#### KIỂM TRA CONTAINER
``bash
sudo docker ps
```
- NẾU KHÔNG CHẠY, XEM LOG VÀ CHECK LỖI:
```bash
sudo docker logs seb-server --tail=100
sudo docker logs seb-server-proxy --tail=100
```

##### TRUY CẬP SEB SERVER 
```bash
http://IP_ADDRESS:8080
```
#### ĐĂNG NHẬP LẦN ĐẦU
- Ở lần khởi tạo đầu tiên, SEB Server sẽ tạo tài khoản quản trị ban đầu. Tùy theo version và bundle, tài khoản có thể được sinh dựa vào cấu hình hoặc hiển thị trong log.

```bash
sudo docker logs seb-server --tail=300 | grep -i "admin\|password\|initial\|account"
```
- Sau khi lấy tài khoản và mật khẩu đăng nhập lần đầu, vào thay đổi username và mật khẩu đồng thời tích vào đầy đủ các role 
```bash
SEB Server Administrator
Institutional Administrator
Exam Administrator
Exam Supporter
```

### CÀI ĐẶT MOODLE 4.5 BẰNG DOCKER
**KHÔNG NÊN CÀI TRỰC TIẾP MOODLE TRÊN UBUNTU**
Trong quá trình triển khai thực tế, nếu cài Moodle trực tiếp trên Ubuntu mới, hệ thống có thể gặp lỗi do phiên bản PHP quá mới.

#### TẠO THƯ MỤC TRIỂN KHAI MOODLE

```bash
mkdir -p ~/moodle45-docker
cd ~/moodle45-docker
```

#### TẠO DockerFile cho Moodle
```bash
nano docker-compose

FROM php:8.3-apache

RUN apt-get update && apt-get install -y \
    git unzip zip curl libpq-dev libpng-dev libjpeg-dev libfreetype6-dev \
    libicu-dev libxml2-dev libzip-dev libldap2-dev libxslt1-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install \
    pgsql pdo_pgsql gd intl soap zip opcache exif xsl bcmath ldap \
    && a2enmod rewrite headers

WORKDIR /var/www/html

RUN curl -L https://download.moodle.org/download.php/direct/stable405/moodle-latest-405.tgz -o /tmp/moodle.tgz \
    && tar -xzf /tmp/moodle.tgz -C /tmp \
    && cp -R /tmp/moodle/. /var/www/html/ \
    && chown -R www-data:www-data /var/www/html

RUN echo "max_input_vars=5000" > /usr/local/etc/php/conf.d/moodle.ini \
    && echo "memory_limit=512M" >> /usr/local/etc/php/conf.d/moodle.ini \
    && echo "upload_max_filesize=200M" >> /usr/local/etc/php/conf.d/moodle.ini \
    && echo "post_max_size=200M" >> /usr/local/etc/php/conf.d/moodle.ini
```

#### TẠO docker-compose.yml

```bash
nano docker-compose.yml

services:
  moodle-db:
    image: postgres:16
    container_name: moodle45-postgres
    restart: unless-stopped
    environment:
      POSTGRES_DB: moodle
      POSTGRES_USER: ttcnttnn
      POSTGRES_PASSWORD: ttcnttnn@123!
    volumes:
      - moodle45_db:/var/lib/postgresql/data

  moodle-web:
    build: .
    container_name: moodle45-web
    restart: unless-stopped
    depends_on:
      - moodle-db
    ports:
      - "8081:80"
    volumes:
      - moodle45_data:/var/www/moodledata

volumes:
  moodle45_db:
  moodle45_data:
```

#### BUILD VÀ CHẠY MOODLE
```bash
sudo docker compose build
sudo docker compose up -d
```

- Kiểm tra container  
```bash
sudo docker ps
```

**LƯU Ý NẾU TRÌNH CÀI ĐẶT MOODLE BÁO Data directory (/var/www/moodledata) cannot be created by the installer.**

Vào container:
```bash
sudo docker exec -it moodle45-web bash
```
Kiểm tra:
```bash
ls -ld /var/www/moodledata
```
Nếu thấy:
```bash
root root
```
thì Apache không ghi được.

Sửa quyền:

```bash
chown -R www-data:www-data /var/www/moodledata
chmod -R 770 /var/www/moodledata
```
Kiểm tra lại:
```bash
ls -ld /var/www/moodledata
```
Kết quả đúng:
```bash
www-data www-data /var/www/moodledata
```
Thoát container:
```bash
exit
```
Restart Moodle:
```bash
sudo docker compose restart moodle-web
```

#### CẤU HÌNH DATABASE TRONG TRÌNH DUYỆT
- Ở phần database: 
```bash
chọn PostgreSQL

Database host: moodle-db
Database name: moodle
Database user: ttcnttnn
Database password: ttcnttnn@123!
Database port: để trống
Unix socket: để trống
```

#### TẠO COURSE KIỂM TRA
Đăng nhập Moodle bằng tài khoản admin.

Vào:
```BASH
Site administration
→ Courses
→ Add a new course
```
Tạo course:
```bash
Course full name: TEST SEB SERVER
Course short name: TEST
```

#### TẠO QUIZ KIỂM TRA 
Vào course vừa tạo.

Bật Edit mode.

Chọn:
```BASH
Add an activity or resource
→ Quiz
```
Đặt tên:

KIEM TRA THU
```BASH
Cấu hình thời gian mở và đóng quiz.
```
Ví dụ:
```BASH
Open the quiz: bật
Close the quiz: bật
```
#### THÊM CÂU HỎI VÀO QUIZ
Vào Quiz:
```BASH
KIEM TRA THU
→ Questions
→ Add
→ a new question
```
Chọn:
```BASH
Multiple choice
```
Tạo một câu hỏi mẫu. 
Ví dụ:
```BASH
Question: OSI model has how many layers?
A. 5
B. 6
C. 7
D. 8
Correct answer: C
```

#### TẠO USER 

Vào:
```BASH
Site administration
→ Users
→ Accounts
→ Add a new user
```
Tạo user:
```BASH
Username: hocsinh1
Password: Nhamvinhthuy@0609
Firstname: thuy
Lastname: thuy
Email: thuyvinhnham69@gmail.com
```

#### ENROL USER VÀO COURSE
Vào course:
```BASH
TEST SEB SERVER
→ Participants
→ Enrol users
```
Chọn user:
```bash
hocsinh1
```
Role:
```bash
Student
```
Bấm:
```bash
Enrol users
```
Kiểm tra trong danh sách Participants:
```bash
student01 → Student
```

### CÀI ĐẶT PLUGIN SEB SERVER CHO MOODLE
**Vì Moodle đang chạy trong container moodle45-web, cần kiểm tra bên trong container.**

Chạy trên Ubuntu host:
```BASH
sudo docker exec -it moodle45-web bash
```
KIỂM TRA THƯ MỤC ACCESS RULE CỦA QUIZ
```BASH
ls -la /var/www/html/mod/quiz/accessrule
```
- NẾU THẤY sebserver THÌ OKE, NẾU KHÔNG THÌ

THOÁT CONTAINER
```bash
exit
```

#### TẢI PLUGIN quizaccess_sebserver
Trên Ubuntu host, di chuyển về thư mục home:
```BASH
cd ~
```
Clone plugin từ repository chính thức:
```BASH
git clone https://github.com/ethz-let/moodle-quizaccess_sebserver.git
```
Nếu clone thành công, sẽ có thư mục:
```BASH
~/moodle-quizaccess_sebserver
```
Kiểm tra:
```BASH
ls -la ~/moodle-quizaccess_sebserver
```
Cần thấy các file:
```BASH
version.php
lib.php
rule.php
externallib.php
db/
classes/
lang/
```

#### COPY PLUGIN VÀO MOODLE CONTAINER
```BASH
sudo docker cp ~/moodle-quizaccess_sebserver moodle45-web:/var/www/html/mod/quiz/accessrule/sebserver
```
- SAU ĐÓ SỬA QUYỀN 
```BASH 
sudo docker exec -it moodle45-web bash -lc "chown -R www-data:www-data /var/www/html/mod/quiz/accessrule/sebserver"
```
- KIỂM TRA
```BASH
sudo docker exec -it moodle45-web bash -lc "ls -la /var/www/html/mod/quiz/accessrule/sebserver"
```
- CẦN THẤY
```BASH
version.php
lib.php
rule.php
externallib.php
db
classes
lang
```

#### CHẠY UPGRADE MOODLE ĐỂ NHẬN PLUGIN
Sau khi copy plugin, Moodle cần chạy upgrade database.

Vào container:
```BASH
sudo docker exec -it moodle45-web bash
```
Chạy:
```BASH
php /var/www/html/admin/cli/upgrade.php
```

Sau đó xóa cache:
```BASH
php /var/www/html/admin/cli/purge_caches.php
```
Thoát container:
```BASH
exit
```
Restart Moodle:
```BASH
sudo docker restart moodle45-web
```

#### KIỂM TRA PLUGIN ĐÃ ĐƯỢC MOODLE NHẬN CHƯA
```BASH
sudo docker exec -it moodle45-web bash -lc "php /var/www/html/admin/cli/cfg.php --component=quizaccess_sebserver"
```
- KIỂM TRA VERSIION PLUGIN
```BASH
sudo docker exec -it moodle45-web bash -lc "cat /var/www/html/mod/quiz/accessrule/sebserver/version.php"
```

#### KIỂM TRA WEB SERVICE DO PLUGIN TẠO RA 
Plugin quizaccess_sebserver tạo Web Service tên:
```BASH
SEB-Server Webservice
```
Vào Moodle:
```BASH
Site administration
→ Server
→ Web services
→ External services
```
Tìm service:
```BASH
SEB-Server Webservice
```

#### CẤP QUYỀN AUTHORISED USERS CHO WEB SERVICE
Mặc dù service đã tồn tại, Moodle vẫn chưa cho user nào sử dụng service nếu chưa thêm vào Authorised users.

Vào:
```BASH
Site administration
→ Server
→ Web services
→ External services
```
Tại dòng:
```BASH
SEB-Server Webservice
```
Bấm:
```BASH
Authorised users
```
Thêm user quản trị Moodle, ví dụ:
```BASH
ttcnttnn
```
Role của user này nên là admin hoặc teacher có đủ quyền với khóa học.
Sau khi thêm xong, danh sách cần hiển thị:
```BASH
ttcnttnn
```

#### TẠO TOKEN CHO SEB SERVER
Vào:
```BASH
Site administration
→ Server
→ Web services
→ Manage tokens
```
Bấm:
```BASH
Create token
```
Chọn:
```BASH
User: ttcnttnn
Service: SEB-Server Webservice
```
Không chọn:
```BASH
Moodle mobile web service
```

**LƯU Ý CODE CHỈ HIỆN 1 LẦN KHI GENERATE**
#### BẬT WEB SERVICES TRONG MOODLES
Vào:
```BASH
Site administration
→ Advanced features
```
Bật:
```BASH
Enable web services
```
Sau đó vào:
```BASH
Site administration
→ Server
→ Web services
```

#### Kiểm tra Web Services đã hoạt động
Vào:
```BASH
Site administration
→ Plugins
```
Tìm:
```BASH
SEB Server
```
trong nhóm Quiz access rule.

Bấm vào mục này.

Nếu plugin chưa kết nối với SEB Server, sẽ thấy:
```BASH
The connection is not setup yet
```
Thông báo này là bình thường ở giai đoạn này, vì SEB Server chưa apply full integration.

#### Kiểm tra trong Quiz settings

Mở Quiz đã tạo:
```BASH
Course
→ KIEM TRA THU
→ Settings
```
Cuộn xuống phần:
```BASH
SEB Server
```
Nếu plugin đã cài đúng, phần SEB Server sẽ xuất hiện trong trang cài đặt Quiz.

### KẾT NỐI MOODLE VỚI SEB SERVER
#### TẠO TOKEN CHO SEB SERVER
```BASH
Site administration
→ Server
→ Web services
→ Manage tokens
```
CHỌN 
```BASH
User: ttcnttnn
Service: SEB-Server Webservice
```

#### TẠO ASSESSMENT TOOL SETUP TRÊN SEB SERVER
VÀO SEB SERVER TRÊN GIAO DIỆN:
```BASH
HTTP://IP_ADDRESS:8080
```
Vào:
```BASH
Exam Administration
→ Assessment Tool Setup
```
Bấm:
```BASH
Add Assessment Tool Setup
```
Điền như sau:
```BASH
Name:
moodle

Type:
Moodle with SEB Server Plugin

Assessment Tool Server Address:
http://192.168.0.229:8081

Assessment Tool Server Username:
ttcnttnn

Assessment Tool Server Password:
<mật khẩu Moodle của user ttcnttnn>

Access Token:
<token SEB-Server Webservice vừa tạo>
```
- SAVE VÀO RỒI ACTIVE

#### Test Assessment Tool Connection
Sau khi Save, quay lại danh sách:
```BASH
Assessment Tool Setup
```
NHẤP VÀO SEB SERVER CHỌN VIEW ASSESSMENT TOOL UP

CHỌN:
```BASH
Test Assessment Tool Connection
```
Nếu đúng, SEB Server sẽ báo kết nối thành công.

Sau đó bấm:
```BASH
Activate Assessment Tool Setup
```
để Active cấu hình.
#### KIỂM TRA MOODLE ĐÃ NHẬN CONNECTION CHƯA 
Quay lại Moodle.
Vào:
```BASH
Site administration
→ Plugins
→ Activity modules
→ Quiz
→ SEB Server
```
Nếu chưa kết nối, Moodle sẽ hiện:
```BASH
The connection is not setup yet
```
Nếu kết nối thành công, trang này sẽ hiện các thông tin:
```BASH
Connection ID
Connection endpoint
JWT Token
Templates
```

### TẠO CONFIGURATION TEMPLATE, CONNECTION CONFIGURATION VÀ EXAM TEMPLATE TRÊN SEB SERVER
Sau khi hoàn thành chương này, người triển khai sẽ tạo được các cấu hình nền tảng cần thiết trên SEB Server, bao gồm:

Configuration Template
Connection Configuration
Exam Template

Ba thành phần này là nền móng để SEB Server có thể:

import bài thi từ Moodle;
tự động tạo Exam Configuration;
tạo file .seb;
cho phép Safe Exam Browser client kết nối về server;
theo dõi client trong mục Monitoring.

Trong tài liệu chính thức, SEB Server mô tả Exam Configuration là cấu hình SEB dùng cho một bài thi, còn Configuration Template cho phép tạo sẵn các giá trị mặc định để tái sử dụng khi tạo nhiều Exam Configuration khác nhau.

#### Thứ tự tạo cấu hình
Bước 1: Tạo Configuration Template
        ↓
Bước 2: Tạo Connection Configuration
        ↓
Bước 3: Tạo Exam Template
        ↓
Bước 4: Import Quiz từ Moodle
        ↓
Bước 5: SEB Server tự tạo Exam Configuration

#### TẠO CONFIGURATION TEMPLATE
Vào mục Configuration Template

Đăng nhập SEB Server:
```bash
http://192.168.0.229:8080
```
Vào menu bên trái:
```BASH
Configurations
→ Configuration Template
```
Bấm:
```BASH
Add Configuration Template
```
#### ĐIỀN THÔNG TIN CONFIGURATION TEMPLATE
```BASH
Name:
SEB config

Description:

BỎ TRỐNG CŨNG ĐƯỢC
```
**SAVE VÀ XEM KẾT QUẢ MONG ĐỢI LÀ SEB config xuất hiện trong danh sách Configuration Template.**

### TẠO CONNECTION CONFIGURATION
```BASH
Configurations
→ Connection Configuration
```
CHỌN ADD CONNECTION CONFIGURATION 
```BASH
Name:
SEB connection

Configuration Purpose:
Starting an Exam

Configuration Password:
để trống

Confirm Password:
để trống

Ping Interval:
1000
```
SAVE LẠI VÀ ACTIVE

### TẠO EXAM TEMPLATE
```BASH
EXAM TEMPLATE
ADD EXAM TEMPLATE
```
#### ĐIỀN THÔNG TIN EXAM TEMPLATE
```bash
Name:
EXAM test SEB

Description:
Default exam template for Moodle SEB Server exam
```
EXAM TYPE: CÓ THỂ ĐỂ NOT DEFINED NHƯNG TRONG MÔI TRƯỜNG PHÒNG MÁY NÊN ĐỂ MANAGED DEVICES

Ở ô:
Configuration Template
chọn:
SEB config

Nếu dropdown rỗng, nghĩa là chưa tạo Configuration Template.

Cách sửa:
```BASH
Configurations
→ Configuration Template
→ Add Configuration Template
```
Sau đó quay lại Exam Template.

Ở ô:
```BASH
Connection Configuration
```
chọn:

SEB connection

Nếu dropdown rỗng, nghĩa là chưa có Connection Configuration active.

Cách sửa:
```BASH
Configurations
→ Connection Configuration
→ Add Connection Configuration
→ Purpose: Starting an Exam
→ Activate
```
Sau đó quay lại Exam Template.

### KIỂM TRA TOÀN BỘ LẠI TRƯỚC KHI IMPORT
#### Kiểm tra Configuration Template

Vào:

Configurations
→ Configuration Template

Cần thấy:

SEB config
#### Kiểm tra Connection Configuration

Vào:

Configurations
→ Connection Configuration

Cần thấy:

SEB connection
Purpose: Starting an Exam
Active
#### Kiểm tra Exam Template

Vào:

Exam Template

Cần thấy:

EXAM test SEB

Trong chi tiết template cần có:

Configuration Template: SEB config
Connection Configuration: SEB connection
#### Kết quả mong đợi sau chương này

Sau chương này, hệ thống đã có đủ ba cấu hình cần thiết:

SEB config
SEB connection
EXAM test SEB

Ba cấu hình này sẽ được dùng ở chương tiếp theo khi import Quiz từ Moodle vào SEB Server.

## TÀI LIỆU THAM KHẢO 
Repository SEB Server Setup: https://github.com/SafeExamBrowser/seb-server-setup
Moodle Integration trong SEB Server: https://seb-server.readthedocs.io/en/latest/lms_moodle.html
Cài Docker Engine trên Ubuntu: https://docs.docker.com/engine/install/ubuntu/
Repository plugin moodle-quizaccess_sebserver: https://github.com/ethz-let/moodle-quizaccess_sebserver
Moodle Safe Exam Browser: https://docs.moodle.org/4x/sv/Safe_Exam_Browser