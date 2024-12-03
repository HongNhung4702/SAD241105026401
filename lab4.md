## Sơ đồ ca sử dụng (Use Case Diagram)
![diagram](https://www.planttext.com/api/plantuml/png/R99DIWGn48NtEKMH_Lp0XOoA2y61mT6r5EcY9tIdqgJIIf_DXKVo2YOn8QYp25Izzxty5Fdw-DnBn11NDoiqqGVGzswP_KQa0GLQqym3CeuKYbVhPjqYJt3Q998hTkv_saOSW-LOmxLMQXKoA0JwqO-MY_TozrgQxXqmqMd1itL92aFZMj_HfvNXY5lmyzoW95L5gVOWsEsk-q5_rROjNALvv7l2sQz1uDs7YGQjwjCluJVB4lmRGQoQ_AFxTJB_m3PQZ0HBrLBSa8ZbKQlVTCxtgURmYNZ8GKSS8GPaIQEsdkLIj8uyvqgPW-PCPahqFcsK_y0t0000__y30000)
## Sơ đồ lớp (Class Diagram)
![diagram](https://www.planttext.com/api/plantuml/png/V5HBRjim4Dth54HM2L3d05e4GUm6CT021joYwoavbWdp8mmf5qRGatNH8_KA9IcAfXqb0YG8d3VlpRmPwT-Vlu_E0_b1guOhS8vziPqqpvOqUsrOkj1ufEyEoO36JS3yiYHkxtBq24eAyBWa504fGRaG-zrakczI8mSIcMt1KFVAdX3NgvP9u_FftWxaVbWwe6ZPJbdmcRv3lq8FCh6EHqCVzLvYnfpIqXfFLYcaqe66e1Jk2LAe0ljo3zJXqWeyAq3VaprY1Iyg6pX5yXaH6amE5XuEYWyg51i2bQP16i_u7ldXeedFsPrYbnIrJN42BNEUfEcAdy6SgxCUJZhCuYlwlHKNiTJoPWoVVQsxIpKLUT1sCBuUoO95zrks2izCsGTwFwMET3Bkp0uuilKJcCFsv3oUDqfWRvtqjrDE6ojERv_Opm1VcvrjsLD-koRSHBajqb5oB9IfXbd2545gsJRPK7LRLIQ3xnXDSHyMN5irqbvaVb1PoYpJNImUpbz6osuq6EZGtJGpItoDvMCeWD_kOiGMaOYT5j15GzZEqdjPPV8XQzhGMOdx-uVQelSGjHND8neH_p3_0G00__y30000)
## Giải thích thiết kế

## Sơ đồ ca sử dụng:

- **Login**: Đảm bảo rằng chỉ người dùng hợp lệ (nhân viên, quản lý) được phép truy cập hệ thống.
- **Maintain Timecard**: Nhân viên nhập thông tin giờ làm việc, quản lý duyệt bảng chấm công.
- **Run Payroll**: Quản lý khởi chạy quá trình trả lương, bao gồm việc gửi thông tin đến hệ thống ngân hàng và in phiếu lương.

## Sơ đồ lớp:

### Boundary Classes:
- **LoginForm**: Giao diện để người dùng nhập thông tin đăng nhập.
- **TimecardForm**: Giao diện để nhân viên/ quản lý thao tác với bảng chấm công.
- **Printer** và **BankSystem**: Tương tác với thiết bị và hệ thống bên ngoài.

### Control Classes:
- **TimecardController**: Điều phối các thao tác liên quan đến bảng chấm công.
- **PayrollController**: Điều phối quá trình trả lương và quản lý phiếu lương.

### Entity Classes:
- **Employee**: Lưu thông tin nhân viên.
- **Timecard**: Lưu thông tin giờ làm việc.
- **Paycheck**: Lưu thông tin phiếu lương.

## Quan hệ giữa các lớp:

- **Employee** và **Timecard**: Quan hệ một-nhiều, mỗi nhân viên có thể có nhiều bảng chấm công.
- **PayrollController** sử dụng **Paycheck** và các giao diện **IBankSystem**, **IPrintService** để xử lý thanh toán và in phiếu lương.

## Ưu điểm của thiết kế này:

- **Tính mở rộng**: Dễ dàng tích hợp các hệ thống ngân hàng hoặc thiết bị in khác thông qua các giao diện **IBankSystem** và **IPrintService**.
- **Tái sử dụng**: Các lớp và giao diện được tách biệt rõ ràng, có thể tái sử dụng trong các hệ thống khác.
- **Đáp ứng yêu cầu**: Thiết kế này dựa trực tiếp trên phân tích ca sử dụng từ tài liệu, đảm bảo đáp ứng đầy đủ các chức năng yêu cầu.
