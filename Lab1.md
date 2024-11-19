# Câu 1: Phân Tích Kiến Trúc
## Đề xuất kiến trúc là một kiến trúc phổ biến cho hệ thống đặt hàng trực tuyến bao gồm các lớp sau:
+ Presentation Layer (UI): Lớp giao diện người dùng để người dùng tương tác với hệ thống.
+ Service Layer: Cung cấp các dịch vụ nghiệp vụ cho ứng dụng và quản lý luồng xử lý nghiệp vụ chính.
+ Business Layer: Xử lý logic nghiệp vụ của hệ thống.
+ Data Access Layer (DAL): Quản lý truy cập và tương tác với cơ sở dữ liệu.
+ Database Layer: Lớp cơ sở dữ liệu để lưu trữ dữ liệu liên quan đến đơn hàng, người dùng, thanh toán, v.v.
## Giải thích lý do lựa chọn và ý nghĩa từng thành phần trong kiến trúc
+ Presentation Layer (UI):
Ý nghĩa: Tương tác với người dùng, cung cấp giao diện và nhận yêu cầu.
Lý do: Tách biệt giao diện giúp dễ bảo trì và nâng cấp mà không ảnh hưởng đến logic nghiệp vụ.
+ Service Layer:
Ý nghĩa: Quản lý các dịch vụ chính, xử lý luồng nghiệp vụ và kết nối với lớp Business.
Lý do: Đảm bảo tính tách biệt giữa giao diện và logic nghiệp vụ, tạo sự nhất quán trong xử lý.
+ Business Layer:
Ý nghĩa: Xử lý logic nghiệp vụ, như kiểm tra hàng tồn, tính giá, quyền hạn người dùng.
Lý do: Dễ thay đổi quy tắc nghiệp vụ mà không ảnh hưởng đến các lớp khác.
+ Data Access Layer (DAL):
Ý nghĩa: Quản lý truy xuất dữ liệu từ cơ sở dữ liệu và lưu trữ dữ liệu mới.
Lý do: Tách biệt lớp truy cập dữ liệu giúp thay đổi hoặc nâng cấp cơ sở dữ liệu dễ dàng.
+ Database Layer:
Ý nghĩa: Lưu trữ dữ liệu của hệ thống (người dùng, đơn hàng, sản phẩm).
Lý do: Đảm bảo lưu trữ dữ liệu cố định và dễ quản lý, không bị ảnh hưởng khi cập nhật phần mềm.
## Biểu đồ package mô tả kiến trúc
![Diagram](https://www.planttext.com/api/plantuml/png/Z9912eCm44NtESNGlLSeMjm8BGh5bRYOng58Qon95AJqP5tqIBr28ureB5YtUM_-_ukydozVQPIwgQxiXlo2Pu9D8acHqAZBMi0UEv8Rk3E0B8royBmjP4UIRSdf2tFsOEEnW-nTB0kIO8cDs3Mg5AJKa66q1BlAzFuHfsKkSzeEA8pIvzcS43L2mBdR6OdMABNirXwaQcNuTESFTgQ6GJo9EQ6YUT-YaSYwQBXUaEPJHcPt38-zwfCe-k_m0G00__y30000)
# Câu 2: Cơ Chế Phân Tích
+ Xác thực và ủy quyền người dùng
+ Lý do: Đảm bảo chỉ người dùng hợp lệ có quyền truy cập vào các chức năng phù hợp (đặt hàng, thanh toán), bảo mật hệ thống và thông tin người dùng.
Quản lý phiên làm việc (Session Management)
+ Lý do: Theo dõi hoạt động của người dùng trong suốt phiên làm việc, lưu trạng thái đăng nhập, giỏ hàng tạm thời, và các lựa chọn khác.
Quản lý tồn kho (Inventory Management)
+ Lý do: Đảm bảo hệ thống luôn cập nhật số lượng hàng tồn kho chính xác, tránh việc bán hàng vượt quá số lượng hàng có sẵn.
Xử lý giao dịch đồng thời (Concurrency Control)
+ Lý do: Đảm bảo tính nhất quán dữ liệu khi nhiều người dùng có thể đặt hàng cùng lúc, tránh việc trừ kho nhiều lần hoặc gây ra xung đột dữ liệu.
Quy trình thanh toán an toàn (Secure Payment Processing)
+ Lý do: Bảo mật giao dịch thanh toán và thông tin thẻ của người dùng, đảm bảo thanh toán đáng tin cậy và tránh gian lận.
Ghi log và giám sát hệ thống (Logging and Monitoring)
+ Lý do: Theo dõi hoạt động của hệ thống, phát hiện lỗi hoặc sự cố sớm, phục vụ cho việc bảo trì và nâng cao hiệu suất.
Thông báo và cập nhật trạng thái đơn hàng (Notification Management)
+ Lý do: Cập nhật trạng thái đơn hàng, gửi thông báo cho người dùng về tiến trình giao hàng hoặc các sự kiện quan trọng khác.
Quản lý dữ liệu người dùng và tuân thủ bảo mật (Data Privacy and Compliance)
+ Lý do: Đảm bảo dữ liệu người dùng được lưu trữ và xử lý tuân thủ các quy định bảo mật (như GDPR), bảo vệ quyền riêng tư người dùng.
# Câu 3: Phân Tích Ca Sử Dụng Select Payment
## a. Xác định các lớp phân tích
- Các lớp phân tích
+ Employee : Lớp đại diện cho nhân viên,lưu trữ các thông tin cá nhân và các phương thức thanh toán
+ PaymentMethoad: Lớp trừu tượng,đại diện cho phương thức thanh toán(mail, direct deposit, pick-up)
              - DirectDepositpayment: Thanh toán bằng cách chuyển tiền trực tiếp vào tài khoản ngân hàng của nhân viên.
              - MailPayment: Thanh tonas bằng cách gửi tiến qua bưu điện tới địa chỉ đươc chỉ định.
              - PickUpPayment: Thanh toán bằng cách nhận trực tiếp tại văn phòng công ty.
+ PayrollAdministrator: Lớp này quản lý các hành động như thêm, sửa, xóa nhân viên và cập nhật thông tin nhân viên
+ PayrollProcessor: Xử lý tính toán và gửi các khoản thanh toán vào mối thứ Sáu hoặc cuối tháng.
##b. Mô tả hành vi thông qua biểu đồ tuần tự
 ![Diagram](https://planttext.com/api/plantuml/png/Z9513e8m44NtSufUW0kmC13YqeH8F42bepIs7UmK3MTpuP6yWZQ461j2NC__x_-PUJsU1GVfms0D05-q4vuO0RQsDpGYYYpRY5gEdemfbTLES_0oaC_57gy3SeXJYow87OQEbAWwwSu8IvuP5kMJEXTDHtTHtgGsycWmWV4_FHeqsAOrLlFZeFRK8dC477ebGneDgMwfV4NkfBrTFy4lOLxeQvxY0Q10fpv_U0C00F__0m00)
## c. Xác định nhiệm vụ của từng lớp phân tích
+ Employee: Đại diện cho nhân viên và lưu trữ các thông tin cá nhân như tên, mã số, địa chỉ, và các phương thức thanh toán.
+ PaymentMethod: Đại diện cho phương thức thanh toán trừu tượng mà nhân viên có thể lựa chọn.
+ PayrollAdministrator: Quản lý dữ liệu nhân viên, bao gồm thêm, sửa, xóa và cập nhật thông tin nhân viên.
+ PayrollProcessor: Xử lý tính toán và gửi khoản thanh toán định kỳ (vào mỗi thứ Sáu hoặc cuối tháng).
## d. Xác dịnh một số thuộc tính và quan hệ giữa các lớp phân tích
# Câu 4: Phân Tích Ca Sử Dụng Maintain Timecard:
+ Employee: Đại diện cho nhân viên, lưu trữ thông tin cá nhân và liên kết với các thẻ chấm công.
+ Timecard: Thẻ chấm công chứa thông tin về ngày làm việc, thời gian bắt đầu và kết thúc, số giờ làm việc.
+ TimecardDAO (Data Access Object): Truy cập và quản lý lưu trữ thông tin thẻ chấm công trong cơ sở dữ liệu.
+ PayrollAdministrator: Thực hiện các tác vụ quản lý thông tin chấm công của nhân viên, bao gồm tạo, chỉnh sửa và xóa thẻ chấm công.
+ PayrollProcessor: Sử dụng thông tin chấm công để tính toán lương.
## Một số thuộc tính và quan hệ giữa các lớp phân tích:
+ Employee
Thuộc tính: employeeID, name, address, timecardList
Quan hệ: 1..* Timecard - Một nhân viên có thể có nhiều thẻ chấm công.
+ Timecard
Thuộc tính: timecardID, date, startTime, endTime, hoursWorked
Quan hệ: 1 Employee - Mỗi thẻ chấm công chỉ thuộc về một nhân viên.
+ TimecardDAO
Thuộc tính: databaseConnection
Quan hệ: Kết nối với Timecard để lưu và truy xuất thông tin chấm công từ cơ sở dữ liệu.
+ PayrollAdministrator
Thuộc tính: adminID, name
Quan hệ: 1..* Timecard - Có thể tạo và cập nhật nhiều thẻ chấm công.
+ PayrollProcessor
Thuộc tính: processorID, payrollDate
Quan hệ: Truy xuất thông tin từ 1..* Timecard để tính toán lương.
# Câu 5: Hợp Nhát Kết Quả Phân Tích
Hệ thống duy trì thẻ chấm công bao gồm các lớp chính với vai trò rõ ràng như Employee, Timecard, PayrollAdministrator, TimecardDAO, và PayrollProcessor. Mỗi lớp có nhiệm vụ riêng biệt nhằm đảm bảo hệ thống chấm công hoạt động hiệu quả, giúp lưu trữ và tính toán lương cho nhân viên một cách chính xác.
