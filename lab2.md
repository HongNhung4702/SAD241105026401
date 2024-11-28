
# Phân tích Sơ đồ Trình tự "Run Payroll"

## Actor và Participants
- **SystemClock (SC):** Kích hoạt hệ thống chạy bảng lương vào mỗi thứ Sáu hoặc ngày làm việc cuối tháng.
- **PayrollSystem (PS):** Hệ thống chính thực hiện xử lý bảng lương.
- **TimecardDatabase (TCD):** Lưu giữ thông tin thẻ chấm công.
- **ProjectDatabase (PD):** Lưu trữ dữ liệu dự án.
- **BankSystem (BS):** Xử lý các giao dịch gửi tiền trực tiếp.
- **Printer (P):** In séc lương cho nhân viên không sử dụng giao dịch điện tử.
- **PayrollAdmin (PA):** Nhận thông báo lỗi hoặc thông tin hoàn thành.

---

## Trình tự Tương Tác
1. **Kích hoạt chạy bảng lương:**  
   Hệ thống được kích hoạt tự động bởi đồng hồ hệ thống.
   
2. **Xử lý thẻ chấm công:**  
   Hệ thống truy vấn cơ sở dữ liệu thẻ chấm công để lấy dữ liệu.  
   - Nếu không có dữ liệu, quản trị viên được thông báo để kiểm tra.

3. **Truy xuất dữ liệu dự án:**  
   Dữ liệu dự án được lấy từ cơ sở dữ liệu để tính toán.  
   - Lỗi truy cập cơ sở dữ liệu sẽ dừng quy trình và thông báo cho quản trị viên.

4. **Giao dịch ngân hàng:**  
   Xử lý giao dịch gửi tiền trực tiếp cho nhân viên.  
   - Nếu hệ thống ngân hàng không khả dụng, thông báo lỗi sẽ được gửi tới quản trị viên.

5. **In séc:**  
   In séc lương cho nhân viên không sử dụng chuyển khoản.

6. **Hoàn thành:**  
   Hệ thống thông báo cho quản trị viên rằng quy trình đã hoàn tất.

---

## Các Tình Huống Thay Thế
- Xử lý các lỗi như:
  - Thiếu dữ liệu thẻ chấm công.
  - Thiếu dữ liệu dự án.
  - Không thể kết nối ngân hàng.
- Tất cả các lỗi kích hoạt thông báo tới quản trị viên để xử lý thủ công.

---

## Ý Nghĩa Của Sơ Đồ
- Minh họa rõ ràng luồng xử lý bảng lương.
- Nhấn mạnh việc xử lý tự động và cơ chế xử lý lỗi.
- Đảm bảo tính toàn vẹn và sự chính xác trong các giao dịch tài chính.
  ## Sơ Đồ Trình Tự (Sequence Diagram)
Dưới đây là sơ đồ minh họa luồng hoạt động của trường hợp sử dụng "Run Payroll":
  ![diagram](https://www.planttext.com/api/plantuml/png/Z9D1Si8m34NtFeKkq0jqqG72kfDfk81n1BWuTaPocCdPkkYHUeKgJY0njDDcwQ__zMGhNn-VAuwQOjSufKqC15NF4Pl21NC6pL0LqtcfUmhEhUl6-a4erweLepMsrJvUvT6Tz2hJTxP1ewdUwgZtcd4esHNRF8F2EvguB2dpYetsvxd5fhgpMn-Haasfge2d5w60PzYHFHv5Q4T6eCuh4KGM0j7VC9B52qAS887G1AfPQJUJC-YBjaxl7IgGR_0-NLj8H4V-CG2Tp34dT3xF62dAjIIyXcWFFJIMsVhZBObJ7QLuXRvM4tcPWRVZpK4jLvUWoyN17NVvY9tP4tBc_pzr5lGp-6ReA_46cQ6sbCgn3MmZHDAUPTriyEFT3-yDF3runY0njocAu0-McjoUnbZw_vvYFrGZKQ3VBZsXovQ1EQ4vCnpanmZn9Bk5JUj2ZyYgV0IRgjkqe7FQelLrDKsG78oeLj9s-2c_0G00__y30000)

   # Phân Tích Sơ Đồ Trình Tự "Create Employee Report"

## 1. Actor và Participants
- **Employee (EMP):** Nhân viên yêu cầu hệ thống tạo báo cáo.
- **PayrollSystem (PS):** Hệ thống bảng lương thực hiện quy trình tạo báo cáo.
- **ProjectDatabase (PD):** Lưu trữ dữ liệu dự án (truy xuất khi cần thiết).

---

## 2. Trình Tự Tương Tác
### Yêu cầu tạo báo cáo:
Nhân viên gửi yêu cầu tạo báo cáo nhân viên cho hệ thống.

### Cung cấp tiêu chí:
Hệ thống nhắc nhân viên cung cấp các tiêu chí báo cáo (loại báo cáo, ngày bắt đầu, ngày kết thúc).

#### Các loại báo cáo:
- Tổng số giờ làm việc.
- Tổng giờ làm cho một dự án.
- Nghỉ phép.
- Tổng lương tính đến thời điểm hiện tại.

### Truy xuất dữ liệu dự án:
Nếu nhân viên yêu cầu báo cáo dự án cụ thể, hệ thống sẽ truy xuất dữ liệu từ cơ sở dữ liệu dự án.

### Hiển thị báo cáo:
Hệ thống tạo báo cáo theo tiêu chí và hiển thị cho nhân viên.

### Lưu hoặc loại bỏ báo cáo:
Nhân viên có thể chọn lưu báo cáo hoặc không:
- **Nếu chọn lưu:** Hệ thống nhắc nhập tên và vị trí lưu báo cáo, sau đó xác nhận báo cáo đã được lưu.
- **Nếu không lưu:** Hệ thống thông báo báo cáo bị hủy.

---

## 3. Các Tình Huống Thay Thế
### Dữ liệu dự án không khả dụng:
Nếu không thể truy cập dữ liệu dự án, hệ thống hiển thị thông báo lỗi và kết thúc.

### Thông tin không đầy đủ:
Nếu nhân viên không cung cấp đủ thông tin để tạo báo cáo, hệ thống nhắc bổ sung dữ liệu.

### Báo cáo không được lưu:
Khi nhân viên từ chối lưu báo cáo, hệ thống thông báo rằng báo cáo đã bị loại bỏ.

---

## 4. Ý Nghĩa của Sơ Đồ
- Minh họa rõ ràng luồng xử lý khi nhân viên yêu cầu báo cáo.
- Cho thấy cách hệ thống tương tác với cơ sở dữ liệu dự án và xử lý các tùy chọn của nhân viên.
- Nhấn mạnh sự linh hoạt trong việc tạo báo cáo và xử lý các tình huống lỗi.
  ## Sơ Đồ Trình Tự (Sequence Diagram)
Dưới đây là sơ đồ minh họa luồng hoạt động của trường hợp sử dụng "Run Payroll":
  ![diagram](https://www.planttext.com/api/plantuml/png/R59BJiCm4Dtx5BC4gRr05wWIhLY18dA2mPv8WnpRsDDAEHiBZiGL6CTA8RHPH77cpVibtvzV-oAOvJHwWrPYXkEOV9o800iSdpkJTCgM4mQ13gSSlU-d8ZHMGDUlvpc-avK32hvXcIcwWp5A0zi71SCENkdZH4L08jXCA0Iq26PACOjHc8BhpguIZabWK5zjgaiib1bNf0exiwF_6BYJAT46veJWL6m35DpyT6_G2_I9B0zi8JNd2qCXhoTo1lHgXhh3x5uoqvakUAN21Zh0zZUZd79OOrHtbUo90kKQ7wiXBidZj3JmDrgFvqkktBfhpkjx6yF0ULpvl2fkO4yGS6nIFbeKZc7UkDNX37SaoBvSqJusmKjDQi8PylgfPp-EhETmmyvB51wMV3MknUpgghQorrlz_Nu0003__mC0)

# Phân Tích Sơ Đồ Trình Tự "Login"

## 1. Actor và Participants
- **User (U):** Người dùng muốn truy cập vào hệ thống.
- **LoginSystem (LS):** Hệ thống xác thực thông tin đăng nhập của người dùng.
- **UserDatabase (DB):** Cơ sở dữ liệu chứa thông tin tài khoản người dùng để xác thực.

---

## 2. Trình Tự Tương Tác
### 1. Nhập thông tin đăng nhập:
- Người dùng nhập tên đăng nhập và mật khẩu.

### 2. Xác thực thông tin:
- Hệ thống đăng nhập (LoginSystem) gửi yêu cầu kiểm tra thông tin tới cơ sở dữ liệu người dùng (UserDatabase).
  - Nếu thông tin hợp lệ:
    - Cơ sở dữ liệu trả về kết quả xác thực thành công.
    - Hệ thống cấp quyền truy cập và chuyển người dùng vào hệ thống.
  - Nếu thông tin không hợp lệ:
    - Cơ sở dữ liệu trả về kết quả thất bại.
    - Hệ thống hiển thị thông báo lỗi và yêu cầu người dùng thử lại.

---

## 3. Các Tình Huống Thay Thế
### Thông tin không hợp lệ:
- Khi tên đăng nhập hoặc mật khẩu không đúng, hệ thống hiển thị thông báo lỗi, không cho phép truy cập.

### Cơ sở dữ liệu không khả dụng:
- Nếu cơ sở dữ liệu không phản hồi, hệ thống có thể hiển thị thông báo lỗi kỹ thuật và yêu cầu người dùng thử lại sau.

---

## 4. Ý Nghĩa của Sơ Đồ
- Minh họa quy trình cơ bản của việc xác thực thông tin người dùng trong hệ thống.
- Nhấn mạnh việc phân chia nhiệm vụ giữa các thành phần: giao diện người dùng, hệ thống xác thực, và cơ sở dữ liệu.
- Thể hiện cách hệ thống xử lý các tình huống thông tin hợp lệ và không hợp lệ.

 ## Sơ Đồ Trình Tự (Sequence Diagram)
Dưới đây là sơ đồ minh họa luồng hoạt động của trường hợp sử dụng "Login":
  ![diagram](https://www.planttext.com/api/plantuml/png/T911Ri9034NtSmfVW0jqKI58OSCkIlUVZ8L6camYsw7YR2mu4bV0KrG9K9d5BFoVdorVpvUb6iJc8GVqDWfroa9GwiBazTId2SLeDnvIQKzgFDHmrpwbjQU1OG_b6ZUh43fQV3f77_HLp9MpCmM3voNI1DMVKM9mmB5cvTWtSeemVaCY6ws58nTBo4h7YWVovzsBlrdjtFUi-bk_kpklRgLkYNl4sPTyDANolsk3b6VX5rUJTCeu4OlujGOtui21ImnB_-eTRm000F__0m00)

# Phân Tích Sơ Đồ Trình Tự "Maintain Employee Information"

## 1. Actor và Participants
- **PayrollAdmin (PA):** Quản trị viên bảng lương thực hiện các thao tác quản lý thông tin nhân viên.
- **PayrollSystem (PS):** Hệ thống bảng lương xử lý các yêu cầu từ quản trị viên.
- **EmployeeDatabase (ED):** Cơ sở dữ liệu lưu trữ thông tin nhân viên.

---

## 2. Trình Tự Tương Tác
### Bước 1: Lựa chọn chức năng
- Quản trị viên bảng lương chọn chức năng: Thêm, Cập nhật, hoặc Xóa nhân viên.

### Bước 2: Quy trình cho từng chức năng
#### Thêm Nhân Viên:
1. Hệ thống nhắc quản trị viên nhập thông tin nhân viên mới.
2. Quản trị viên cung cấp các chi tiết của nhân viên.
3. Hệ thống lưu thông tin vào cơ sở dữ liệu và xác nhận với quản trị viên.

#### Cập Nhật Nhân Viên:
1. Hệ thống nhắc quản trị viên nhập mã nhân viên.
2. Quản trị viên cung cấp mã nhân viên cần chỉnh sửa.
3. Hệ thống truy xuất thông tin và hiển thị cho quản trị viên.
4. Quản trị viên gửi thông tin cập nhật.
5. Hệ thống lưu thay đổi vào cơ sở dữ liệu và xác nhận.

#### Xóa Nhân Viên:
1. Hệ thống nhắc quản trị viên nhập mã nhân viên.
2. Quản trị viên cung cấp mã nhân viên cần xóa.
3. Hệ thống truy xuất thông tin nhân viên và yêu cầu xác nhận từ quản trị viên.
4. Sau khi xác nhận, hệ thống đánh dấu nhân viên để xóa trong cơ sở dữ liệu và xác nhận.

---

## 3. Các Tình Huống Thay Thế
### Không tìm thấy nhân viên:
- Nếu mã nhân viên không tồn tại, hệ thống thông báo lỗi và yêu cầu nhập lại mã hợp lệ.

### Hủy thao tác:
- Quản trị viên có thể hủy thao tác ở bất kỳ bước nào trước khi xác nhận cuối cùng.

---

## 4. Ý Nghĩa của Sơ Đồ
- Minh họa rõ ràng các tương tác giữa quản trị viên, hệ thống và cơ sở dữ liệu.
- Thể hiện cách hệ thống quản lý các thao tác thêm, cập nhật và xóa thông tin nhân viên.
- Nhấn mạnh các bước xác nhận nhằm đảm bảo tính chính xác và bảo mật trong quản lý dữ liệu.
    ## Sơ Đồ Trình Tự (Sequence Diagram)
Dưới đây là sơ đồ minh họa luồng hoạt động của trường hợp sử dụng "Maintain Employee Information":
  ![diagram](https://www.planttext.com/api/plantuml/png/r5JBJiCm4BpxA_O8Kli3750ZqWC7f8YA3zZ6Myd2TY9d4vHluy0dyGkiywWRe80G5tB88JCxEpEsylhyicaO0xVEAYov2b1W7ofhC-sC1soWo5Gj15EQ6ZtFyAvlcDo0xnRurjMsweboPDnZGv6opPKgCbXV2nckO4UMIeP3wqisbOUBJEiLFDGQcLQG2yfqgT0o270KL22Fp4ULJ5IAKBbQLCIofoUWYGR6ooU7KNaSIOjbf3EQ4bSJex7DYVGsZmQnewMeMCE19VXwbhkf_C4iLYLt4vOKK6lIYgmqCYRzIR3Zz6t-RPQPacBS4mT3tPcyfqc4sGR_LI-3izmqjSN-3E_aWDkzCmpja5D_F95aSQhY3tkUbevDZtVf7pOznz8nm2StUO7JUpjt61xJYXXleVFhRiTjqgtNQYEl-DDu0m00__y30000)   
  # Phân Tích Sơ Đồ Trình Tự "Maintain Purchase Order"

## 1. Actor và Participants
- **AuthorizedEmployee (AE):** Nhân viên được ủy quyền để thực hiện các thao tác quản lý đơn đặt hàng.
- **PayrollSystem (PS):** Hệ thống bảng lương xử lý các yêu cầu từ nhân viên.
- **PurchaseOrderDatabase (POD):** Cơ sở dữ liệu lưu trữ thông tin đơn đặt hàng.

---

## 2. Trình Tự Tương Tác
### Bước 1: Lựa chọn chức năng
- Nhân viên được ủy quyền chọn chức năng: Tạo, Cập nhật, hoặc Xóa đơn đặt hàng.

### Bước 2: Quy trình cho từng chức năng
#### Tạo Đơn Đặt Hàng:
1. Hệ thống nhắc nhân viên nhập chi tiết đơn đặt hàng.
2. Nhân viên cung cấp các chi tiết cần thiết.
3. Hệ thống lưu thông tin vào cơ sở dữ liệu và xác nhận với nhân viên.

#### Cập Nhật Đơn Đặt Hàng:
1. Hệ thống nhắc nhân viên nhập mã đơn đặt hàng.
2. Nhân viên cung cấp mã đơn đặt hàng cần chỉnh sửa.
3. Hệ thống truy xuất thông tin và hiển thị cho nhân viên.
4. Nhân viên gửi thông tin cập nhật.
5. Hệ thống lưu thay đổi vào cơ sở dữ liệu và xác nhận.

#### Xóa Đơn Đặt Hàng:
1. Hệ thống nhắc nhân viên nhập mã đơn đặt hàng.
2. Nhân viên cung cấp mã đơn đặt hàng cần xóa.
3. Hệ thống truy xuất thông tin đơn đặt hàng và yêu cầu xác nhận từ nhân viên.
4. Sau khi xác nhận, hệ thống đánh dấu đơn đặt hàng để xóa trong cơ sở dữ liệu và xác nhận.

---

## 3. Các Tình Huống Thay Thế
### Không tìm thấy đơn đặt hàng:
- Nếu mã đơn đặt hàng không tồn tại, hệ thống thông báo lỗi và yêu cầu nhập lại mã hợp lệ.

### Hủy thao tác:
- Nhân viên có thể hủy thao tác ở bất kỳ bước nào trước khi xác nhận cuối cùng.

---

## 4. Ý Nghĩa của Sơ Đồ
- Minh họa rõ ràng các tương tác giữa nhân viên, hệ thống, và cơ sở dữ liệu trong quy trình quản lý đơn đặt hàng.
- Thể hiện cách hệ thống quản lý các thao tác tạo, cập nhật, và xóa thông tin đơn đặt hàng.
- Nhấn mạnh các bước xác nhận nhằm đảm bảo tính chính xác và bảo mật dữ liệu.



## Sơ Đồ Trình Tự (Sequence Diagram)
Dưới đây là sơ đồ minh họa luồng hoạt động của trường hợp sử dụng "Maintain Purchase Order":
  ![diagram](https://www.planttext.com/api/plantuml/png/t5H1JiCm4Bpx5Ni4YNw00shLzC01jIBY0TjugreuiULiYiBNEF0ali36Jb0QHAc04paaIdPsTcR7ojlBwxnc3DoKLc71Bi2YuRqBvfdqglJMjKI0DInMoWlC5CPZnR31DZXhyxPcAhlw9Z-kDw7OOqthe2baoBYLbuXRPqejLZ2xaHQuXfmi5GoxfYhOk0ekbe6GwGeUl8xFJ01CbmejGwfza4DaLo2NS0cZy5x39hZI2wDOyGFGTK3Gn6Xi7Hj64gJXO3ITGYTwqTufnWD1HKyJVC89OZRmBbsrCw74pjTKP5-RpYoYGQt8ogUqWH-xlStEDDe3nnxlYOEXm-cTZBrAGnEgxrSODMUczXRRC-F9csrf69gu3VrbBFssffnozFuacNvyIYQToN-Op61UTmQ7vOnq7jNfaxWx38_JIPt_8xhV9f5cInALLdEvTN-kTm000F__0m00)   
  # Phân Tích Sơ Đồ Trình Tự "Delete a Purchase Order"

## 1. Actor và Participants
- **AuthorizedEmployee (AE):** Nhân viên được ủy quyền để thực hiện việc xóa đơn đặt hàng.
- **PayrollSystem (PS):** Hệ thống xử lý yêu cầu xóa đơn đặt hàng.
- **PurchaseOrderDatabase (POD):** Cơ sở dữ liệu chứa thông tin đơn đặt hàng.

---

## 2. Trình Tự Tương Tác
### Bước 1: Nhân viên chọn chức năng xóa
- Nhân viên được ủy quyền chọn chức năng "Delete Purchase Order" từ giao diện hệ thống.

### Bước 2: Cung cấp mã đơn đặt hàng
- Hệ thống nhắc nhân viên nhập mã đơn đặt hàng cần xóa.
- Nhân viên cung cấp mã đơn đặt hàng.

### Bước 3: Truy xuất thông tin đơn đặt hàng
- Hệ thống gửi yêu cầu tới cơ sở dữ liệu để truy xuất thông tin đơn đặt hàng dựa trên mã cung cấp.
- Nếu đơn đặt hàng tồn tại:
  - Hệ thống trả về thông tin chi tiết và hiển thị cho nhân viên để xác nhận.
  - Nhân viên xác nhận thao tác xóa.
  - Hệ thống đánh dấu đơn đặt hàng để xóa trong cơ sở dữ liệu và thông báo hoàn thành.
- Nếu đơn đặt hàng không tồn tại:
  - Hệ thống trả về thông báo lỗi "Purchase order not found" và kết thúc quy trình.

---

## 3. Các Tình Huống Thay Thế
### Không tìm thấy đơn đặt hàng:
- Nếu mã đơn đặt hàng không tồn tại, hệ thống hiển thị thông báo lỗi và yêu cầu nhập lại mã hợp lệ.

### Hủy thao tác:
- Nhân viên có thể hủy thao tác xóa trước khi xác nhận cuối cùng.

---

## 4. Ý Nghĩa của Sơ Đồ
- Minh họa quy trình xóa đơn đặt hàng từ khi chọn chức năng đến khi xác nhận hoàn thành hoặc báo lỗi.
- Thể hiện cách hệ thống xử lý các tình huống khi đơn đặt hàng tồn tại hoặc không tồn tại.
- Đảm bảo tính an toàn và chính xác khi xóa dữ liệu nhờ yêu cầu xác nhận.

## Sơ Đồ Trình Tự (Sequence Diagram)
Dưới đây là sơ đồ minh họa luồng hoạt động của trường hợp sử dụng "Delete a Purchase Order":
  ![diagram](https://www.planttext.com/api/plantuml/png/T98nRiCm34LtdOBmdWjaA1B46Jgq2PeJg1QD29L5WwA3kbVhq2Fr2gMSkd6SneCDW-z_VbBw_lnQ9R4iNHEChOGOrfqSYVq7kctJ1keHmIPORqshcAzyQwF0tlPC8Hpw9DZa-lvmNU-uEjg4EtR8fHNxgZy3jokDMMzXyQ0IMC810rO2HQbVmJyT3CB2AAEayalOCpMjGAqHsv6YJC5ZENLKxkGT_WETpJI1KYyexF5qWpaKwqCoDbo6-2tXkq-I3EYJFHPZGxNgEDup6l3B5ALFRR3z7NgOhg9OUswiU8g3V3BSvbnJNjSrrgTpFLb-cvjdqsl1DFvctcwITcntapOVbZCO4iwtv0WJH9Bpkkvk2vc9v-sUINpTGp6pp6urTT4L1gCpAttbw_e3003__mC0)
# Phân Tích Sơ Đồ Trình Tự "Select Payment Method"

## 1. Actor và Participants
- **Employee (E):** Nhân viên yêu cầu lựa chọn phương thức thanh toán cho lương của mình.
- **PayrollSystem (PS):** Hệ thống bảng lương thực hiện việc xử lý yêu cầu của nhân viên về phương thức thanh toán.
- **PaymentGateway (PG):** Cổng thanh toán xử lý các giao dịch thanh toán của nhân viên.
- **BankSystem (BS):** Hệ thống ngân hàng xử lý các giao dịch chuyển khoản trực tiếp.

---

## 2. Trình Tự Tương Tác
### Bước 1: Nhân viên yêu cầu chọn phương thức thanh toán
- Nhân viên yêu cầu hệ thống cung cấp các phương thức thanh toán có sẵn.

### Bước 2: Hệ thống hiển thị các lựa chọn phương thức thanh toán
- Hệ thống hiển thị các phương thức thanh toán khả dụng như: Chuyển khoản trực tiếp (Direct Deposit), Séc, Tiền mặt.

### Bước 3: Nhân viên chọn phương thức thanh toán
- Nhân viên chọn phương thức thanh toán mà mình muốn.

#### Nếu chọn **Chuyển khoản trực tiếp (Direct Deposit)**:
1. Hệ thống yêu cầu nhân viên cung cấp thông tin ngân hàng (tên ngân hàng, số tài khoản).
2. Nhân viên cung cấp thông tin ngân hàng.
3. Hệ thống gửi thông tin thanh toán cho cổng thanh toán (Payment Gateway).
4. Cổng thanh toán xử lý giao dịch chuyển khoản với ngân hàng.
5. Ngân hàng xác nhận giao dịch đã được xử lý thành công.
6. Hệ thống xác nhận phương thức thanh toán chuyển khoản đã được thiết lập.

#### Nếu chọn **Séc (Check)**:
1. Hệ thống yêu cầu nhân viên cung cấp địa chỉ nhận séc.
2. Nhân viên cung cấp địa chỉ.
3. Hệ thống xử lý thanh toán bằng séc thông qua cổng thanh toán.
4. Cổng thanh toán xác nhận séc đã được phát hành.
5. Hệ thống xác nhận phương thức thanh toán bằng séc đã được thiết lập.

#### Nếu chọn **Tiền mặt (Cash)**:
1. Hệ thống xác nhận phương thức thanh toán bằng tiền mặt.
2. Hệ thống thông báo phương thức thanh toán tiền mặt đã được thiết lập.

---

## 3. Các Tình Huống Thay Thế
### Thiếu thông tin ngân hàng (Chuyển khoản trực tiếp):
- Nếu nhân viên không cung cấp thông tin ngân hàng đầy đủ, hệ thống yêu cầu nhập lại thông tin chính xác.

### Địa chỉ không hợp lệ (Séc):
- Nếu địa chỉ nhận séc không hợp lệ, hệ thống yêu cầu nhân viên cung cấp địa chỉ hợp lệ.

### Lỗi trong quá trình xử lý thanh toán:
- Nếu có lỗi trong quá trình xử lý thanh toán (chuyển khoản hoặc séc), hệ thống thông báo lỗi và yêu cầu thử lại.

---

## 4. Ý Nghĩa của Sơ Đồ
- Minh họa quy trình và các bước tương tác giữa nhân viên, hệ thống bảng lương, cổng thanh toán và ngân hàng trong việc chọn phương thức thanh toán.
- Thể hiện cách hệ thống xử lý các phương thức thanh toán khác nhau (chuyển khoản, séc, tiền mặt) và các bước yêu cầu thêm thông tin từ nhân viên.
- Đảm bảo rằng các giao dịch thanh toán được thực hiện chính xác và hợp lệ.



## Sơ Đồ Trình Tự (Sequence Diagram)
Dưới đây là sơ đồ minh họa luồng hoạt động của trường hợp sử dụng "Select Payment Method":
  ![diagram](https://www.planttext.com/api/plantuml/png/V9D1ReCm44NtFiKi4ocvG1TLcWInYr0vWMDF6YlOflRGYhDrqIFr2XqW9413MR1Wtdp__u6Vh-zD91ceieMGYdo0n9Q5hn51HaX4oJEZJ2aTGIRhu8iYhoEXRSPPFfrRT9HAmazPjq0w0hRINUxRsro81DRFB0DFy8hl5KO2yX2nG4LGTd9WaSvU2wQOJHZDWhSbmOdDZXdm9Hdlua0sVwG5Yxq9pUCzbZuQMi7kZEgo0bRSoNXU2bdmSCG8uElkeRTxv4YWaQGf8YoQW72G5bVmefIl-CH3POyObktwtHP7-30QH-k34xAqjUxqpRXn9zycrfqhFNILDZlRgwx261zHF5_tqZllJYPOe21TvDVEfTsKUeizCvRYbqDLEIdZNnIBY5s_CnLQ3c_S6qYjG-EzIQbk_D_E9loqjhw2LgBlRpRTbUfsKCy4wwXX7lvAvbWUJR_TVyYhgDDYmxVcD_m5003__mC0)
