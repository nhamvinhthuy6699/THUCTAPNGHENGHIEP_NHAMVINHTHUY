# BASE 64

base64 là phương thức convert dạng mã hóa 2 chiều từ binary sang string để có thể gửi đi được trong network một cách dễ dàng. Các binary lúc này sẽ được thể hiện bằng các ký tự mã ASCII .

Base64 được sử dụng rộng rãi trong:

Email và tệp đính kèm MIME.
Dữ liệu truyền qua HTTP.
Chuỗi JSON hoặc XML.
Data URI trong HTML/CSS.
Chứng thư số, khóa và token.

Tên gọi Base64 xuất phát từ việc bảng mã sử dụng 64 ký tự khác nhau.

## Base64 hoạt động như thế nào?

Quá trình thực hiện theo 4 bước.

    Dữ liệu nhị phân được sắp xếp theo từng khối 24 bit (3 byte) liên tục.

    Mỗi đoạn 24 bit được nhóm thành bốn phần 6 bit mỗi phần.

    Mỗi nhóm 6 bit được chuyển đổi thành các giá trị ký tự Base64 tương ứng của chúng. Mã hóa Base64 chuyển đổi ba octet thành bốn ký tự được mã hóa. (mỗi octet có 8bits dữ liệu)

    Người nhận sẽ phải đảo ngược quá trình này để khôi phục thông điệp ban đầu

## Mã hóa Base64
Mã hóa Base64 cho chữ Hello:

Chuyển sang hệ nhị phân và ghép chuỗi lại 

Cách đổi sang hệ nhị phân:
Bước 1: xác định xem chữ đó nằm ở số mấy trong bảng mã Ascii

ví dụ H:72

Nhẩm nhanh để có nhị phân:

128,64,32,16,8,4,2,1

ta xét nhanh xem số 72 có chứa các số đó không, ví dụ:
72 không chứa 128 ->0
72 chứa 64 (72-64=8) ->1
8 không chứa 32 ->0
8 không chứa 16 ->0
8 chứa 8 (8-8=0)->1
các vị trí khác do đã dư nên điền 0 hết
=> 0100 1000

H: 0100 1000 
e: 0110 0101
l: 0110 1100
l: 0110 1100
o: 0110 1111

ghép lại chuỗi bit liên tục:
010010 000110 010101 101100 011011 000110 1111

Bước 2: Cắt thành nhóm 6-bit và quy đổi thập phân

nhóm 1: 010010 -> thập phân: 16+2=18 => kí tự S (Kiểm tra trong bảng tra cứu base64)  
nhóm 2: 000110 -> thập phân: 4+2=6 => kí tự G
nhóm 3: 010101 -> thập phân: 16+4+2=22 => kí tự V
nhóm 4: 101100 -> thập phân: 32+8+4=44 => kí tự s 
nhóm 5: 011011 -> thập phân: 16+8+2+1=27 => kí tự b
nhóm 6: 000110 -> thập phân: 4+2=6 => kí tự G
nhóm 7: 111100 -> thập phân: 32+16+8+4=60 => kí tự 8 
nhóm 8: 000000 -> thay kí tự cuối bằng = 

kết quả Hello = SGVsbG8=

## Giải mã Base64 
Để giải mã chuỗi Base64 SGVsbG8=
S = 18
G = 6
V = 21
s = 44
b = 27
G = 6
8 = 60

18 = 010 010
6 = 000 110
21 = 010 101
44 = 101 100
27 = 011 011
6 = 000 110
60 = 111 100

ghép lại và cắt theo nhóm 8-bit

vì chuỗi gốc ban đầu là 8 bit, nên phải cắt theo 8 bit
01001000 01100101 01101100 01101100 01101111 00 (bỏ 2 số 0 vì đây là phần thừa để làm tròn)

Đổi nhị phân sang thập phân và tra bảng ASCII

nhóm 1: 0110 1000 => 64+8=72 -> H
nhóm 2: 0110 0101 => 64+32+4+1=101 ->e
nhóm 3: 0110 1100 => 64+32+8+4=108 ->l
nhóm 4: 0110 1100 => 64+32+8+4=108 ->l
nhóm 5: 0110 1111 => 64+32+8+4+2+1=111 -> o

# Hex

Hex (viết tắt của hexadecimal) là hệ đếm cơ số 16, sử dụng 16 ký tự gồm các số từ 0 đến 9 và các chữ cái từ A đến F. Trong đó, A tương ứng với 10 và F tương ứng với 15 trong hệ thập phân.

Cấu trúc của hệ cơ số 16:

Hệ cơ số 16 bao gồm 16 ký tự: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 và A, B, C, D, E, F. Trong đó, A tương ứng với 10, B là 11, C là 12, D là 13, E là 14 và F là 15 trong hệ thập phân.

## Mã hóa hex

Tra cứu mã ascii và quy đổi về HEX

H(72) = 0100 1000 -> 48
e(101) = 0110 0101 -> 65 
l(108) = 0110 1100 -> 6C 
l = 6C = 0110 1100 -> 6C
o = 6F = 0110 1111 -> 6F

=> 48 65 6C 6C 6F

Giải mã ngược chỉ cần đổi lại như giải mã và tra mã ascii là được 

# AES
AES (Advanced Encryption Standard) là thuật toán mã hóa đối xứng mã khối (Block cipher). AES trở thành 1 trong những thuật toán mã hóa phổ biến nhất trong sử dụng khóa mã đối xứng để mã hóa và giải mã.

## Mã hóa AES Encrypt

Các thông số bắt buộc: 

**Key (Khóa bảo mật)**: Đóng vai trò là mật khẩu chính 
**IV (Initialization vector)**: Dãy ký tự độ dài cố định 16 byte được nạp vào để xáo trộn khối dữ liệu đầu tiên. IV có vai trò đảm bảo tính ngẫu nhiên: Dù bạn mã hóa cùng một từ `hello` nhiều lần với cùng một Key, nhưng mỗi lần dùng một IV khác nhau thì kết quả xuất ra sẽ là các chuỗi mã hoàn toàn khác nhau.

## Quy trình thực hành

 **Bước 1**: Nhập chuỗi chữ cần giấu `hello` vào ô **Input**.
**Bước 2**: Tìm kiếm lệnh `AES Encrypt` ở cột ngoài cùng bên trái, kéo và thả vào khung **Recipe** ở giữa.
**Bước 3**: Cấu hình chính xác thông số đầu vào:
  * **Key**: Chuyển định dạng từ *HEX* sang **`UTF8`**, nhập mật khẩu: `NhamVinhThuy6924`
  * **IV**: Chuyển định dạng từ *HEX* sang **`UTF8`**, nhập chuỗi khởi tạo: `nhamvinhthuy6924`
**Bước 4**: Nhận chuỗi mật mã thu được ở ô **Output** (Độ dài chuỗi HEX sẽ ngắn, vừa khít tương ứng với số byte của dữ liệu gốc).

## Quy trình giải mã ngược

**Bước 1**: Sao chép toàn bộ chuỗi mật mã HEX nhận được ở bước trước và dán vào khung **Input**.
**Bước 2**: Tìm kiếm lệnh `AES Decrypt` ở cột ngoài cùng bên trái, kéo và thả vào khung **Recipe** trống.
**Bước 3**: Cấu hình các thông số giải mã đồng nhất:
  **Key**: Nhập lại đúng `NhamVinhThuy6924` (Định dạng chọn **`UTF8`**).
  **IV**: Nhập lại đúng `nhamvinhthuy6924` (Định dạng chọn **`UTF8`**).
**Bước 4**: Nhìn xuống ô **Output** để nhận lại văn bản gốc ban đầu (`hello`).

## Các thành phần cần tìm hiểu trước của AES

### Plaintext và cyphertext

Plaintext= dữ liệu ban đầu  
cyphertext= dữ liệu sau mã hóa

### Key  
Key là khóa bí mật

ví dụ: Khóa AES cần đúng 16 byte:  
1234567890abcdef

Độ dài: 16 kí tự ASCII x 8 bit = 128 bit

AES-192 cần 24 byte và AEES-256 cần 32 byte

### IV và nonce

IV là viết tắt của Initialization Vector, nghĩa là giá trị khởi tạo.

Nonce là viết tắt của Number Used Once, nghĩa là một giá trị chỉ được sử dụng một lần.

IV và nonce không phải là khóa bí mật. Chúng thường có thể được gửi kèm với ciphertext. Tuy nhiên, chúng phải được sử dụng đúng theo yêu cầu của từng mode.

Trong CyberChef, ô có tên IV được dùng chung cho cả IV và nonce

### Padding  

AES xử lý khối 16 byte. Nếu dữ liệu không đủ bội số của 16, một số mode cần bổ sung dữ liệu đệm.

Ví dụ plaintext có 5 byte:

Hello

Cần thêm 11 byte để đủ 16 byte.

Padding phổ biến là PKCS#7. Nếu thiếu 11 byte thì thêm 11 byte, mỗi byte có giá trị 0B:

48 65 6C 6C 6F 0B 0B 0B 0B 0B 0B 0B 0B 0B 0B 0B

## Các mode cần quan tâm

### ECB - Mã hóa từng khối riêng
ECB mã hóa từng khối plaintext độc lập:

P1 → AES → C1
P2 → AES → C2
P3 → AES → C3

Đặc điểm:

Không cần IV.
Thường cần padding.
Các khối plaintext giống nhau tạo ciphertext giống nhau.
Làm lộ cấu trúc và mẫu lặp của dữ liệu.
Có thể mã hóa, giải mã song song.
Không cung cấp tính toàn vẹn.

ví dụ:

P1 = chuyenkhoan_10m
P2 = chuyenkhoan_10m
P3 = chuyenkhoan_20m

thì mã hóa bằng AES-ECB của bản mã khối 1 = bản mã khối 2, bản mã khối 3 khác biệt

Lỗ hổng thực tế: Kẻ tấn công dù không biết khóa để giải mã chữ chuyenkhoan_10m nhưng khi nhìn vào 2 bản mã thì đều biết nội dung giống nhau và chuyển khoản cùng giá tiền

Kết luận: ECB đơn giản nhưng không an toàn cho văn bản, tệp và hình ảnh. Nên tránh sử dụng.

### CBC - Trộn với ciphertext trước rồi mã hóa

Là chế độ mã hóa liên kết khối. Mỗi plaintext được XOR với ciphertext của khối trước rồi mới mã hóa:

P1 XOR IV → AES → C1
P2 XOR C1 → AES → C2
P3 XOR C2 → AES → C3

Đặc điểm:

Cần IV dài 16 byte.
IV nên ngẫu nhiên và không thể đoán trước.
Thường cần padding.
Khối giống nhau không nhất thiết tạo ciphertext giống nhau.
Quá trình mã hóa phụ thuộc khối trước.


Nếu ciphertext bị sửa, plaintext sau giải mã cũng sẽ bị thay đổi.

Kết luận: CBC an toàn hơn ECB nhưng phải kết hợp thêm cơ chế xác thực. Trong ứng dụng mới thường ưu tiên GCM.

### CFB - mã hóa IV hoặc ciphertext trước để tạo khóa

CFB biến AES từ mã hóa khối thành dạng gần giống mã hóa dòng.

Khối đầu tiên:

AES(IV) XOR P1 → C1

Khối tiếp theo:  
AES(C1) XOR P2 → C2
AES(C2) XOR P3 → C3

CFB lấy ciphertext của khối trước làm dữ liệu đầu vào cho AES.

Đặc điểm:

Cần IV dài 16 byte.
Không cần padding.
Có thể mã hóa dữ liệu không đủ 16 byte.
Mã hóa phụ thuộc ciphertext trước.
Có khả năng tự đồng bộ lại sau một số lỗi truyền.
Không cung cấp tính toàn vẹn.

Kết luận: CFB phù hợp với dữ liệu dạng dòng nhưng hiện nay ít được chọn cho hệ thống mới.

### OFB - Lấy đầu ra AES trước để tạo dòng khóa tiếp theo
OFB cũng biến AES thành dạng mã hóa dòng. Khác CFB, OFB sử dụng đầu ra của AES để tạo dòng khóa:

IV → AES → O1
O1 → AES → O2
O2 → AES → O3

Sau đó XOR với plaintext:

P1 XOR O1 → C1
P2 XOR O2 → C2
P3 XOR O3 → C3

Đặc điểm:

Cần IV dài 16 byte.
Không cần padding.
Mã hóa và giải mã dùng cùng một dòng khóa.
Một bit ciphertext bị sai chỉ làm sai một bit plaintext tương ứng.
Không tự đồng bộ nếu dữ liệu bị mất hoặc thêm.
Không cung cấp tính toàn vẹn.

Cùng một key tuyệt đối không được dùng lại cùng IV. Nếu tái sử dụng IV, hai thông điệp sẽ dùng chung dòng khóa và có thể bị phân tích.

### CTR - Mã hóa các số đếm để tạo dòng khóa

CTR tạo dòng khóa bằng cách mã hóa các giá trị bộ đếm:

AES(Nonce + Counter 1) → K1
AES(Nonce + Counter 2) → K2
AES(Nonce + Counter 3) → K3

sau đó XOR với plaintext:

P1 XOR K1 → C1
P2 XOR K2 → C2
P3 XOR K3 → C3

Đặc điểm:

Trong CyberChef, nonce/counter được nhập vào ô IV  
Không cung cấp tính toàn vẹn
Có thể truy cập và giải mã từng khối riêng.

Không được tái sử dụng cùng nonce và counter với cùng key. Nếu tái sử dụng, hai thông điệp tạo cùng dòng khóa và có thể làm lộ plaintext.

### GCM - CTR để mã hóa, thêm tag để kiểm tra

GCM kết hợp:

CTR -> mã hóa dữ liệu
GHASH -> kiểm tra tính toàn vẹn

Kết quả mã hóa gồm:

Ciphertext + Authentication Tag

Khi giải mã, hệ thống cần kiểm tra tag:  
Tag đúng -> trả về plaintext
Tag sai -> từ chối giải mã

# MD6

MD6 là một hàm băm mật mã do Ronald Rivest và cộng sự đề xuất năm 2008 cho cuộc thi tuyển chọn SHA-3 của NIST. MD6 có thể tạo giá trị băm với độ dài đầu ra thay đổi, thay vì cố định ở 128 bit như MD5.

## Mục dích của MD6

MD6 có thể được dùng để:

Kiểm tra tính toàn vẹn của dữ liệu.
So sánh hai tệp có giống nhau hay không.
Phát hiện dữ liệu bị thay đổi.
Tạo dấu vân tay cho dữ liệu.
Nghiên cứu cấu trúc hàm băm mật mã.

## Các thông số của MD6 trong CyberChef

Size
Key
Levels

1. Size

Là độ dài giá trị băm đầu ra, tính bằng bit: 
128 bit  
256 bit  
512 bit

ví dụ: 
size = 256 bit

thì kết quả là 256 / 4 = 64 ký tự HEX

2. Key 

Nếu để trống key, MD6 sẽ hoạt động như hàm băm bình thường

nếu để trống key thì ra hask khác, còn có secret key sẽ ra hash khác

3. Level

Levels điều khiển cấu trúc cây và mức độ xử lý song song của MD6.

MD6 được thiết kế để có khả năng xử lý song song trên dữ liệu lớn. Các phần dữ liệu có thể được băm riêng, sau đó kết hợp lại ở các tầng phía trên.

# SHA3

SHA-3 là một họ hàm băm mật mã được NIST chuẩn hóa năm 2015. SHA-3 được xây dựng từ thuật toán Keccak, do Guido Bertoni, Joan Daemen, Michaël Peeters và Gilles Van Assche phát triển.

SHA-3 nhận dữ liệu đầu vào có đội dài bất kỳ và tạo ra 1 giá trị băm có độ dài cố định

Dữ liệu → SHA-3 → Giá trị băm

Ví dụ:

Hello → SHA3-256 → Hash 256 bit

SHA-3 không phải là thuật toán mã hóa, mà là hàm băm một chiều. Vì vậy, SHA-3 không có thao tác giải mã.

Ứng dụng

SHA-3 được dùng để:

Tạo dấu vân tay cho dữ liệu.
Hỗ trợ chữ ký số.
Kiểm tra tính toàn vẹn của thông điệp.

# DES 

DES là thuật toán mã hóa đối xứng dạng khối, ra đời trước AES.

Mã hóa và giải mã sử dụng cùng một khóa bí mật.

1. Các thành phần của DES

Plaintext  = dữ liệu ban đầu
Ciphertext = dữ liệu sau khi mã hóa

Key: Key là khóa bí mật được dùng cho cả mã hóa và giải mã.

Block: 

DES xử lý dữ liệu theo từng block có kích thước:

8 byte = 64 bit

IV: là viết tắt của Initialization Vector, nghĩa là giá trị khởi tạo

IV được sử dụng cho các mode:  
CBC, CFB, OFB  

Padding  
Nếu plaintext không đủ bội số của 8 byte, ECB và CBC thường phải thêm padding

## Các mode DES

### ECB  
Mã hóa từng block riêng biệt

P1 -> DES -> C1  
P2 -> DES -> C2

Không cần IV  
Cần padding  
Các block giống nhau tạo ciphertext giống nhau  
Không an toàn cho dữ liệu thực tế  

### CBC  

Mỗi block plaintext được XOR với ciphertext của block trước rồi mới đưa vào DES. 

Block đầu tiên dùng IV: 

P1 XOR IV -> DES -> C1

Các block tiếp theo:  

P2 XOR C1 -> DES -> C2  
P3 XOR C2 -> DES -> C3

An toàn hơn ECB nhưng vẫn cần thêm cơ chế xác thực.  
Mỗi block phụ thuộc vào ciphertext trước.  
Cần IV dài 8 byte.  
Cần padding nếu dữ liệu không đủ bội số 8 byte.  

### CFB  

DES mã hóa IV để tạo dòng khóa, sau đó XOR dòng khóa với plaintext.

DES(IV) -> K1  
P1 XOR K1 -> C1

Block tiếp theo  
DES(C1) -> K2  
P2 XOR K2 -> C2

Không cần padding  
Lấy cyphertext trước để tạo dòng khóa tiếp theo  
Một lỗi ciphertext có thể ảnh hưởng block hiện tại và 1 phần block sau.  

### OFB

DES mã hóa IV để tạo dòng khóa. Đầu ra DES trước được dùng để tạo dòng khóa tiếp theo.  

Block đầu tiên:  
DES(IV) -> K1  
P1 XOR K1 -> C1  

Block tiếp theo:  

DES(K1) -> K2  
P2 XOR K2 -> C2  

Một bit ciphertext sai chỉ làm sai một bit plaintext tương ứng. 
Không tự đồng bộ nếu dữ liệu bị mất hoặc thêm.
