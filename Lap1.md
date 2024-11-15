### 1. Phân tích kiến trúc
**Đề xuất kiến trúc:** Hệ thống Payroll nên được thiết kế với kiến trúc client-server phân tầng. Mỗi tầng sẽ đảm nhiệm chức năng riêng biệt:

- Presentation Layer (UI): Giao diện người dùng dựa trên nền tảng desktop Windows để nhập dữ liệu và báo cáo.
- Business Logic Layer: Xử lý các nghiệp vụ liên quan đến quản lý thông tin thời gian làm việc, tiền lương, và các giao dịch thanh toán.
- Data Access Layer: Kết nối với cơ sở dữ liệu legacy (DB2 trên mainframe IBM) và các hệ thống khác như ngân hàng.
- Integration Mechanism: Sử dụng JDBC cho việc truy cập RDBMS và một giao thức để kết nối với hệ thống ngân hàng.
- Lý do lựa chọn: Kiến trúc phân tầng đảm bảo tính mở rộng, bảo trì và bảo mật, đáp ứng khả năng xử lý nhiều người dùng đồng thời và tích hợp hệ thống hiện tại.

### 2. Cơ chế phân tích
- Cơ chế bảo mật: Chỉ cho phép nhân viên truy cập thông tin cá nhân và quản trị viên có quyền thay đổi dữ liệu nhân viên.
- Tính liên tục: Phải đảm bảo hệ thống hoạt động với độ tin cậy tối thiểu là 98%.
- Tích hợp hệ thống legacy: Kết nối và truy vấn cơ sở dữ liệu DB2 hiện có mà không được cập nhật trực tiếp.
- Quản lý giao dịch tự động: Hệ thống phải chạy payroll tự động vào thứ Sáu hàng tuần và ngày làm việc cuối tháng.
### 3. Phân tích ca sử dụng Select Payment
- Các lớp phân tích:
- Employee: Lớp đại diện cho thông tin nhân viên.
- PaymentMethod: Lớp xác định phương thức thanh toán (nhận trực tiếp, gửi bưu điện, gửi qua ngân hàng).
- PaymentProcessor: Lớp xử lý thông tin và cập nhật phương thức thanh toán.
- Biểu đồ sequence: Miêu tả quy trình từ khi nhân viên chọn phương thức thanh toán đến khi hệ thống cập nhật thông tin.
### 4. Phân tích ca sử dụng Maintain Timecard
- Các lớp phân tích:
- Employee: Lớp chứa thông tin nhân viên.
- Timecard: Lớp lưu thông tin giờ làm việc.
- TimecardValidator: Kiểm tra tính hợp lệ của thời gian làm việc nhập vào.
- DatabaseHandler: Kết nối và lưu dữ liệu timecard.
- Biểu đồ sequence: Minh họa quá trình nhân viên nhập thông tin và gửi timecard, với kiểm tra hợp lệ và lưu trữ trong cơ sở dữ liệu.
### 5. Hợp nhất kết quả phân tích
Hợp nhất hai ca sử dụng trên để tạo ra mô hình hệ thống tổng thể mô tả các lớp phân tích và mối quan hệ giữa chúng.

Để hoàn thiện các biểu đồ và tài liệu chi tiết hơn, cần vẽ sơ đồ package và biểu đồ lớp cho từng ca sử dụng theo mô hình UML.   
![Digram](https://www.planttext.com/api/plantuml/png/Z5DBQiCm4Dtx58FtkK0N9N5IQ8eBWNxsq_7WYEWJ99bYIaxMHO_KArIA4o9RQIbu8xsVvWt-_loQEu_MTqeMUwGTjWpb1djhf8IdtdbM9NmK01VGicFjqGkZeSQUxK0088dEmPtQIzCplwoJoqMZX3xU78hKhEgSq1m8jMa5NRCBRr4XRcCD1Pwn2VGi51FQvXMbQD2FiDC8IvJKoHCsZbwXHrWG7TFpt0Y_eUDxr8tarBhc5gbVLKkZDTCrwxNstDgXeKUcBMhXrDY-GhrRRDQfnnbw2DQPT_WknS9iTfiL0pTGTevTcLEpebBkQJLdpt5hAJ4BZ8f9JP4lmlGMoJju5tuRbNd-lwLJKXHc2uXI6WuEl8cwKOc_g_2u_p_cc-vfY5AgquBGy_cXXsBEkea_qGy0003__mC0)
