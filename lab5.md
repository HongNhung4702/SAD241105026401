# ***Thiết kế các hệ thống con cho hệ thống `Payroll System`***

## 1. Distribute subsystem behavior to subsystem elements  
Hệ thống con và hành vi chính:

**a) UI Subsystem:**

- Cung cấp giao diện tương tác cho người dùng.
- Thu thập và gửi dữ liệu đầu vào từ người dùng đến các hệ thống khác.
- Hiển thị kết quả từ các quy trình xử lý.

**b)Authentication Subsystem:**

- Xác thực thông tin đăng nhập của nhân viên.
- Quản lý phiên làm việc.

**c) Timecard Management Subsystem:**

- Cập nhật và quản lý bảng chấm công của nhân viên.
- Xử lý dữ liệu giờ làm việc và mã công việc.

**d) Payroll Processing Subsystem:**

- Tính toán lương dựa trên dữ liệu bảng chấm công.
- Quản lý và lưu trữ thông tin về lương.

**e) Database Subsystem:**

- Lưu trữ và truy xuất dữ liệu (tài khoản, bảng chấm công, bảng lương).
- Cung cấp dữ liệu đồng bộ cho các hệ thống con.


## 2. Document subsystem elements
**a) UI Subsystem**
- Thành phần: LoginUI, TimecardForm, PayrollUI:
    + LoginUI: Xử lý đăng nhập, thu thập thông tin người dùng.
    + TimecardForm: Giao diện để nhập và sửa bảng chấm công.
    + PayrollUI: Hiển thị thông tin tổng quan về lương.

**b)Authentication Subsystem**
- Thành phần: AuthSystem:
    + AuthSystem: Xác minh thông tin tài khoản và quản lý phiên làm việc.

**c) Timecard Management Subsystem**
- Thành phần: TimecardController, Timecard:
    + TimecardController: Điều phối logic liên quan đến chấm công.
    + Timecard: Lưu trữ thông tin bảng chấm công của nhân viên.

**d) Payroll Processing Subsystem**
- Thành phần: PayrollController, Employee, PayrollDatabase:
    + PayrollController: Xử lý tính toán lương.
    + Employee: Đại diện dữ liệu nhân viên (lương cơ bản, thông tin cá nhân).
    + PayrollDatabase: Lưu kết quả tính toán lương.

**e) Database Subsystem**
- Thành phần: CentralDatabase:
    + CentralDatabase: Lưu trữ toàn bộ dữ liệu liên quan (tài khoản, chấm công, lương).


## 3. Describe subsystem dependencies

- UI Subsystem -> Authentication Subsystem, Timecard Subsystem, Payroll Subsystem
- Authentication -> Subsystem	Database Subsystem
- Timecard Management -> Subsystem	Database Subsystem
- Payroll Processing -> Subsystem	Timecard Management Subsystem, Database Subsystem
- Database Subsystem -> Không phụ thuộc

**- Mô tả mối quan hệ:**
- UI Subsystem là lớp giao tiếp giữa người dùng và các hệ thống con phía sau.
- Authentication Subsystem dựa vào dữ liệu tài khoản từ Database Subsystem để xác thực.
- Timecard Management Subsystem phụ thuộc vào dữ liệu từ Database Subsystem để quản lý chấm công.
- Payroll Processing Subsystem sử dụng dữ liệu từ Timecard Management Subsystem và Database Subsystem để xử lý lương.

**- Biểu đồ mô tả các sự phụ thuộc giữa các subsystem:**
![Diagram](https://www.planttext.com/api/plantuml/png/Z5H1JiCm4Bpx5LOkdFe13gYeKAaIIAWbtBVEqhWuTcGxI1NYPHnu4b_0Rft43ab4ZhipdjdPLNw-lfV6WhPD9KWDx0qEIBCdE6ab1DsTZCKgen-4kgzhvnkwQ_OcQVgF2J26FgW3b_bcK7tc5JBGnLhfQj0AQe7oILAnsyQMA2rdOBcISy8UUN4y-b3hW3w2T8NAFJhtMWjVAMczFTGJWE4qMXsHsLxa3YpimU2egJPfns9e39U7EKy1FMafz6SLs-QSpdrL2tL2zDY9gKTQaNfGTjfNT8lYl3fJyjgGS1rqiRY95aQlaqLZbk3Ys_78IxPTEGLtr-IHsqQsXOn4SXuO3-cnBo1uuRJfIcFXZO0m6KcqOpFz4Zmvhy_Ktj88B6Q7CNZTY7_n9g_gF2LQpV7TEIz1ks1Mga1dlKyYoYMr7Swkp-WlQkWwDxrTwbrCaORvhj6oiglIZNnLKzJ17NlspYgDRIEGoH9buNzSlm000F__0m00)
## 4. Checkpoints
**a) UI Subsystem:**
- Kiểm tra khả năng hiển thị đúng các giao diện (đăng nhập, chấm công, tính lương).
- Đảm bảo dữ liệu đầu vào được truyền đúng tới các hệ thống con.

**b) Authentication Subsystem:**
- Xác thực thông tin tài khoản chính xác.
- Quản lý phiên làm việc hợp lệ.

**c) Timecard Management Subsystem:**
- Đảm bảo dữ liệu bảng chấm công được cập nhật và lưu trữ đúng cách.
- Xử lý các lỗi nhập liệu (mã công việc không hợp lệ, giờ làm việc âm, v.v.).

**d) Payroll Processing Subsystem:**
- Tính toán lương chính xác theo bảng chấm công.
- Lưu trữ thông tin lương đúng cách và hiển thị kết quả.

**e) Database Subsystem:**
- Đảm bảo dữ liệu đồng bộ giữa các hệ thống con.
- Đảm bảo an toàn và bảo mật cho dữ liệu.
​
