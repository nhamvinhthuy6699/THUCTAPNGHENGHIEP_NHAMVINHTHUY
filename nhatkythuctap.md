# NHẬT KÝ THỰC TẬP 
**Họ và tên:** Nhâm Vĩnh Thủy  
**MSSV:** 2213743  
**Lớp:** CTK46B  
**Chuyên ngành:** Công nghệ thông tin  
**Cơ sở thực tập:** Trung tâm CNTT&NN - Trường Đại học Thông tin liên lạc  

## Tuần 1: (2/6/2026 - 7/6/2026)

### Ngày 2/6/2026
**Nội dung công việc**
- Làm quen với môi trường làm việc, gặp gỡ cán bộ hướng dẫn
- Tìm hiểu quy trình, nội quy cơ sở thực tập  
- Được giới thiệu về hệ thống mạng nội bộ của cơ sở thực tập  
- Trình bày các nội dung đã viết trong CV, viết báo cáo tổng bên trong CV    
**Kết quả đạt được**
- Tìm hiểu thực tế cơ sở thực tập và vị trí thực tập  
- bắt đầu thích nghi được với công việc mới  
### Ngày 3/6/2026  
**Nội dung công việc**  
- Ôn tập lại các kiến thức bên trong Kali, thực hiện lại 1 số đề án trong thời gian học để phục vụ báo cáo   
- Hoàn thiện hồ sơ, báo cáo chuyên môn theo yêu cầu của đơn vị thực tập  
**Kết quả đạt được**
- Hoàn thành hồ sơ báo cáo chuyên môn được giao
### Ngày 4/6/2026
**Nội dung công việc**
- Ôn tập, tìm hiểu lại nội dung liên quan tới Git
- Thực hiện các công việc được giao của cơ sở thực tập
### Ngày 5/6/2026
**Nội dung công việc**
- Tiếp tục ôn tập, tìm hiểu lại nội dung liên quan tới Git
- Thực hiện các công việc được giao của cơ sở thực tập

## Tuần 2:(8/6/2026 - 13/6/2026)

### Ngày 8/6/2026
**Nội dung công việc**
- Tiếp tục ôn tập, tìm hiểu lại nội dung liên quan tới Git
- Thực hiện các công việc được giao của cơ sở thực tập
### Ngày 9/6/2026
**Nội dung công việc**
- Tiếp tục ôn tập, tìm hiểu lại nội dung liên quan tới Git
- Thực hiện các công việc được giao của cơ sở thực tập
### Ngày 10/6/2026
**Nội dung công việc**
- Tiếp tục ôn tập, tìm hiểu lại nội dung liên quan tới Git
- Làm 1 vài dự án như báo cáo thực tập rồi sử dụng kiến thức mình đã học để làm project Git
- Thực hiện các công việc được giao của cơ sở thực tập
### Ngày 11/6/2026
**Nội dung công việc**
- Xuống phòng máy làm việc
- Thực hiện các yêu cầu của cơ sở thực tập 
### Ngày 12/6/2026
**Nội dung công việc**
- Nghiên cứu NTP server, client
- Cấu hình NTP cho hệ thống của cơ sở 
- Tiếp tục thực hiện các công việc được giao của cơ sở thực tập 
- Tiếp tục nghiên cứu cách đồng bộ hóa từ 1 máy cho toàn bộ tất cả 
### Ngày 13/6/2026
**Nội dung công việc**
- Nghiên cứu WOL để thao tác trên 1 máy chủ 
- Tiếp tục nghiên cứu bật máy tự động chỉ cần ngồi trên 1 máy làm server
## Tuần 3:(15/6/2026 - 19/6/2026)

### Ngày 15/6/2026
**Nội dung công việc**
- Triển khai trên toàn bộ các phòng máy của cơ sở thực tập
- Test nhiều lần để xem các rủi ro có thể xảy ra và lỗi  

**Chi tiết công việc**
- Vì sao không chọn WOL cho phòng máy:
 + Có 1 vài máy đường truyền cho dây sẽ không ổn định, tắt mất dây LAN hoặc cả 1 phòng có thể không bật lên được nếu không sử dụng trong nhiều ngày 
 + Cấu hình ngay bên trong bios sẽ ổn định hơn, đúng ngày đúng giờ là tự bật nếu như đã cung cấp nguồn điện cho nó 
 + Viết script bootstrap lên các máy client, mở cổng 445 và ssh tới để làm tự động hóa 
 + Thực hiện các yêu cầu cần thiết như mở tự động, tắt hàng loạt toàn bộ các máy của dãy nhà
- Sử dụng PsExec để phục vụ cho việc tự động hóa từ 1 máy tới nhiều máy.
### Ngày 16/6/2026
**Nội dung công việc**
- Tiếp tục triển khai trên các phòng máy của cơ sở thực tập
- Nghiên cứu thêm cho các dòng máy khác, vì không phải chỉ mỗi dòng laptop HP mà còn nhiều dòng máy khác 
**Chi tiết công việc**
- Có thể viết script và điều khiển trực tiếp bios thông qua các phần mềm do các dòng máy cung cấp như DELL_CCTK, HP_BCU
### Ngày 17/6/2026
**Nội dung công việc**
- Thực hiện trên dòng máy khác
- Test các tính năng tự động bật theo thời gian của Bios, shutdown toàn bộ laptop thông qua 1 máy server
- Test các máy thực thi và chạy chương trình ổn định
### Ngày 18/6/2026
**Nội dung công việc**
- Thực hiện test các máy trên phòng 
- Bàn giao lại máy cho cán bộ cơ sở để kiểm tra và phục vụ công tác tiếp theo 
**Kết quả đạt được**
- Đã tìm hiểu và triển khai thành công việc đồng bộ các máy để 1 máy điều khiển
- Kiểm tra lại các rủi ro có thể phát sinh 
- Bàn giao lại để tổ chức cuộc thi đánh giá năng lực của cơ sở.
## Tuần 4:(22/6/2026 - 26/6/2026)
### Ngày 22/6/2026
**Nội dung công việc**
- Tìm hiểu nội dung về Safe Exam Browser
- Tìm hiểu cách thoát SEB an toàn không phải kill process hay ép shutdown
### Ngày 23/6/2026
**Nội dung công việc**
- Làm các nhiệm vụ được cơ sở thực tập giao 
- tiếp tục tìm hiểu nội dung SEB
### Ngày 24/6/2026
**Nội dung công việc**
- Tìm hiểu về SEB server
- Tìm cách xóa hàng loạt 365 office cho các laptop của cơ sở thực tập
- Tìm hiểu cách cài hàng loạt các phần mềm cho máy và chạy được ngay trên máy laptop mà không cần phải chạm lần đầu
### Ngày 25/6/2026
**Nội dung công việc**
- Triển khai trên các phòng máy và kiểm tra xem đã ổn chưa
- Tiếp tục tìm hiểu các nội dung được giao
### Ngày 26/6/2026
**Nội dung công việc**
- Tiếp tục làm các công việc do cơ sở thực tập giao 
- Tìm hiểu về SEB server, dual boot cho máy tính và cài đặt Moodle

## Tuần 4:(29/6/2026 - 3/7/2026)

### Ngày 29/6/2026
**Nội dung công việc**
- Tìm hiểu cách clear máy hoàn toàn sau khi hoàn thành các kì thi của cơ sở
- Tiếp tục tìm hiểu và sử dụng SEB server trên ubuntu, triển khai thành công thi thử và quản lý trên máy từ xa. Hiểu nguyên lý hoạt động của SEB
### Ngày 30/6/2026
**Nội dung công việc**
- Tiến hành viết script tải và cài đặt office 16 lên các máy client, đồng thời xóa hoàn toàn 365 office
- Test và kiểm tra từng máy, xem đã oke chưa để phục vụ công tác của cơ sở
### Ngày 1/6/2026
**Nội dung công việc**
- Tìm hiểu về cách đóng băng ổ đĩa, làm sao để sau khi hoàn thành bất kì kì thi nào, máy sẽ được đưa về sạch hoàn toàn
**CÁC LÝ DO KHÔNG THỂ TRÊN PHIÊN BẢN WINDOWS 11 HOME**
- Các phần mềm hỗ trợ như DEEP FREEZE, SHADOW DEFENDER đều cho dùng thử 30 ngày nhưng sau đó thì trả phí
- Việc xóa toàn bộ có thể mất đi 1 vài tác vụ quan trọng, nên việc viết script tự động không được tối ưu 
**CÁCH TỐI ƯU NHẤT LÀ ẨN Ổ C, CHỈ CHO HỌ SỬ DỤNG CÁC TÁC VỤ CỦA USER ĐÓ, DỄ KIỂM SOÁT HƠN**
### Ngày 3/6/2026
**Nội dung công việc**
- Tìm hiểu về mã nguồn mở Veyon, triển khai trên windows và thực hiện ở phòng máy
- Triển khai lên toàn bộ các phòng máy
**Chi tiết công việc**
- Đây là phần mềm dùng để quản lý, theo dõi hoạt động của các máy client, cực kì phù hợp với quy mô phòng học, trường lớp. Giúp xem được hoạt động của mỗi người.
## Tuần 5:(6/7/2026 - 10/7/2026)
### Ngày 6/7/2026
**Chi tiết công việc**
- Tiếp tục tìm hiểu, viết script triển khai theo nhu cầu của cơ sở.
- Tìm tiếp hướng phát triển với tên dự án QDA_AUTO
### Ngày 7/7/2026
**Chi tiết công việc**
- Viết app để quản lý, giao diện để trực quan hóa cho người dùng. Sau này bàn giao lại cho bên cơ sở thực tập
### Ngày 8/7/2026
**Chi tiết công việc**
- Tìm hiểu thêm về python, viết app và tìm hiểu portable của python cho app
### Ngày 9/7/2026
**Chi tiết công việc**
- Tiếp tục phát triển app để quản lý tập trung các script
- Dễ sử dụng cho người dùng