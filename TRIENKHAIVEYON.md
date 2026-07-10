# TÀI LIỆU TRIỂN KHAI VEYON-PHẦN MỀM QUẢN LÝ PHÒNG MÁY

**TẤT CẢ CÁC BAT PHẢI ĐƯỢC CHẠY BẰNG QUYỀN ADMIN**  
**TẤT CẢ CÁC MÁY GIÁO VIÊN ĐÈU ĐÃ CÓ THƯ MỤC QDA_AUTO VÀ BÊN TRONG ĐÃ CÓ CÁC SCRIPT CẦN THIẾT**  
![thư mục qda](image.png)
**TẤT CẢ ĐỀU ĐƯỢC THỰC HIỆN TRÊN 1 MÁY DUY NHẤT (TỨC MÁY GIÁO VIÊN)**

## QUY TRÌNH CHUẨN BỊ  
### BƯỚC 1: ĐỊNH TUYẾN TĨNH VÀ SETUP MÁY
- Các máy đã được kết nối với mạng LAN, đồng thời được đánh ip tĩnh theo từng máy để dễ dàng quản lý (vì nếu cấp DHCP tự động khó kiểm soát hơn - sử dụng Nmap để lọc sẽ không tối ưu).
- 1 máy được kéo cáp lên bàn giáo viên (máy này chính là master để thực hiện các tác vụ khác).
### BƯỚC 2: QUÉT ĐỊA CHỈ PHÒNG
- Chạy run_scan_rooms.bat ở bên trong qda_auto để quét dải mạng của phòng (Lưu ý để quét dải mạng, vào rooms.txt để kiểm tra xem phòng mình đang ở là phòng nào và có dải mạng là bao nhiêu (ví dụ: 201B=192.168.12.0/24) Đồng thời edit run_scan_rooms.bat để loại bỏ ip đích (tức ip của máy giáo viên)).    
![chạy run_scan_rooms.bat](image-1.png)
![edit, chỉnh sửa set IP_SERVER theo máy giáo viên](image-2.png)
- Kiểm tra xem clients.txt đã có đầy đủ máy ở phòng đó chưa. Nếu chưa thì kiểm tra lại 1 lần phòng xem có máy nào bị tắt hoặc đơ không(Cũng có thể chưa cắm bootstrap lần đầu).

### BƯỚC 3: TẢI VÀ CÀI ĐẶT VEYON TRÊN CÁC MÁY CLIENT 
- Vào bên trong veyon configuration, Nếu máy chưa có phải tải [Tải Veyon](https://veyon.io/en/download/), vào Authentication keys và create key pair. Giữ lại private key và export public key ra ngoài.  
- Vào qda_auto\INSTALLERS\VEYON và thay thế key pem của mình với key pem bên trong (nếu có). Còn lại giữ nguyên.(NHỚ XÓA KEY PEM CŨ VÀ CHỈ GIỮ KEY CỦA MÌNH)
![key public sẽ ở đây](image-3.png)
- Chạy install.bat, đẩy source veyon xuống và tiến hành cài đặt (ở Install menu là số 11, 12).  
![install.bat](image-4.png)
- Sau khi bat báo hoàn thành, đi 1 lượt check từng máy xem đã xuất hiện veyon master chưa.(Có thể chủ động xóa trên màn hình desktop).    
### BƯỚC 4: TIẾN HÀNH LẤY ĐỊA CHỈ IP VÀ MAC, ĐỒNG THỜI IMPORT VÀO BÊN TRONG VEYON CONFIGURATOR   
**TẤT CẢ ĐÃ ĐƯỢC TỰ ĐỘNG HÓA, NẾU CÓ MÁY KHÔNG LẤY ĐƯỢC THÌ VÀO CMD VÀ ipconfig /all**  
- Chạy scan_room_to_veyon.bat để lấy địa chỉ IP và MAC address, in ra file veyon_clients.csv 
![veyon_clients.csv sẽ trông như vậy](image-5.png) 
- Sau khi kiểm tra file veyon_clients.csv, Nếu đã đầy đủ tiếp tục chạy import_veyon_csv.bat
- Sau khi thành công, vào veyon configuration và kiểm tra bên trong Location & computers xem đã có Builtin directory chưa.  
![Location&Computers](image-6.png)
### BƯỚC 5: TRIỂN KHAI VEYON MASTER VÀ BẮT ĐẦU QUẢN LÝ 
- Sau khi đã có locations và đầy đủ Computers, apply veyon config và vào bên trong veyon master
- Ở đây các tài khoản vào đều thuộc quyền admin và phải có pass, đã tạo sẵn nên thay thế thành admintest và pass là 123456.(Lưu ý ở đằng trước sẽ xuất hiện DESKTOP-ULL...\admin, chỉ cần đổi chỗ admin thành admintest, không xóa tất cả).  
![màn hình đăng nhập](image-7.png)
- sau khi giao diện xuất hiện, click vào phòng ở bên Locations/Computers và tiến hành quản lý phòng máy remote.
![giao diện veyon](image-8.png)

## YÊU CẦU 
- MÁY GIÁO VIÊN PHẢI CHUNG ĐỊA CHỈ MẠNG LAN, MỖI PHÒNG 1 MÁY 
- NẾU MUỐN KẾT NỐI TỚI THIẾT BỊ NGOÀI PHẠM VI LAN, CẦN PHẢI PING ĐƯỢC VỚI NHAU VÀ MÁY CLIENTS PHẢI IMPORT KEY PUBLIC CỦA MÁY GIÁO VIÊN GỬI.