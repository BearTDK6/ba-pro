# Gói Yêu Cầu

## Tóm Tắt Phạm Vi

Module `booking-payment` cho phép supplier khai báo contact vận hành, payment term và bank info để đáp ứng điều kiện tối thiểu trước khi gửi `Request Active`.

## Business Requirements

| ID | Yêu cầu | Lý do | Độ ưu tiên | Nguồn |
| --- | --- | --- | --- | --- |
| BR-01 | Hệ thống phải thu thập đủ 3 contact bắt buộc gồm `RSVN`, `Sales`, `Kế toán`. | Cần đảm bảo đầu mối vận hành và tài chính. | Must Have | BRD |
| BR-02 | Hệ thống phải cho phép supplier chọn payment term theo 2 loại cố định. | Cần chuẩn hóa điều khoản thanh toán. | Must Have | BRD |
| BR-03 | Hệ thống phải thu thập bank info và thông tin xuất hóa đơn. | Cần phục vụ thanh toán và đối soát. | Must Have | BRD |
| BR-04 | Hệ thống phải chặn `Request Active` nếu thiếu 1 trong 3 contact hoặc thiếu bank info. | Cần bảo vệ điều kiện go-live tối thiểu. | Must Have | BRD |

## Functional Requirements

| ID | Yêu cầu | Actor | Trigger | Kết quả mong đợi | Độ ưu tiên |
| --- | --- | --- | --- | --- | --- |
| FR-01 | Cho phép tạo contact với họ tên, email, số điện thoại, chức danh và vai trò. | Supplier | Mở phần contact vận hành | Contact được lưu thành công. | Must Have |
| FR-02 | Bắt buộc có đủ ba vai trò `RSVN`, `Sales`, `Kế toán`. | Hệ thống | Supplier lưu contact hoặc review summary | Hệ thống xác định đủ hoặc thiếu vai trò. | Must Have |
| FR-03 | Hiển thị ghi chú dưới mỗi contact về trách nhiệm nhận booking, thương mại hoặc thanh toán. | Supplier | Xem danh sách contact đã setup | Supplier hiểu vai trò từng contact. | Should Have |
| FR-04 | Chỉ cho phép chọn payment term theo 2 loại: `Trước [01] ngày so với check-in` hoặc `Trong vòng [01] ngày sau check-out`. | Supplier | Chọn payment term | Payment term được lưu theo mẫu cố định. | Must Have |
| FR-05 | Cho phép nhập tên công ty hoặc chủ tài khoản, số tài khoản, tên ngân hàng, chi nhánh, swift code nếu có, loại tiền tệ, mã số thuế và thông tin xuất hóa đơn. | Supplier | Mở phần payment info | Bank info được lưu thành công. | Must Have |
| FR-06 | Chỉ đánh dấu step đủ điều kiện khi có đủ 3 contact bắt buộc và bank info bắt buộc. | Hệ thống | Review summary hoặc request active | Step status được tính đúng. | Must Have |

## Non-Functional Requirements

| ID | Nhóm | Yêu cầu | Chỉ số | Độ ưu tiên |
| --- | --- | --- | --- | --- |
| NFR-01 | Data integrity | Contact role không được bị thiếu hoặc trùng theo cách làm mất một vai trò bắt buộc. | Hệ thống nhận diện đúng ba vai trò bắt buộc. | Must Have |
| NFR-02 | Security | Thông tin ngân hàng và thanh toán phải được bảo vệ theo chính sách bảo mật. | Dữ liệu nhạy cảm không lộ qua UI hoặc log thông thường. | Must Have |
| NFR-03 | Usability | Form contact và payment phải dễ hiểu với supplier không chuyên hệ thống. | Supplier hiểu rõ còn thiếu vai trò hoặc trường nào. | Should Have |

## Business Rules

| Rule ID | Phát biểu rule | Áp dụng cho | Nguồn | Ghi chú |
| --- | --- | --- | --- | --- |
| RULE-01 | Bắt buộc đủ 3 vai trò `RSVN`, `Sales`, `Kế toán`. | Contact roles | BRD | Bắt buộc |
| RULE-02 | Chỉ cho phép 2 loại payment term cố định. | Payment term | BRD | Bắt buộc |
| RULE-03 | Thiếu 1 trong 3 vai trò contact hoặc thiếu bank info thì không được `Request Active`. | Request Active condition | BRD | Bắt buộc |

## Candidate User Stories

### US-01

Là supplier,
Tôi muốn khai báo đúng đầu mối `RSVN`, `Sales`, `Kế toán`,
Để AirData liên hệ đúng người theo từng nghiệp vụ.

### US-02

Là supplier,
Tôi muốn khai báo payment term và bank info,
Để thanh toán và đối soát được xử lý đúng.

## Acceptance Criteria

| AC ID | Story Ref | Acceptance Criteria |
| --- | --- | --- |
| AC-01 | US-01 | Given supplier thêm contact, when chưa đủ 3 vai trò bắt buộc, then hệ thống hiển thị còn thiếu vai trò nào. |
| AC-02 | US-01 | Given supplier đã tạo đủ `RSVN`, `Sales`, `Kế toán`, when lưu step, then điều kiện contact bắt buộc được đánh dấu đạt. |
| AC-03 | US-02 | Given supplier chọn payment term, when lưu step, then chỉ một trong hai lựa chọn chuẩn được chấp nhận. |
| AC-04 | US-02 | Given supplier nhập đủ bank info bắt buộc, when lưu step, then thông tin thanh toán được lưu thành công. |
| AC-05 | US-01, US-02 | Given thiếu contact bắt buộc hoặc thiếu bank info, when review summary hoặc request active, then hệ thống chặn tiếp tục và hiển thị mục còn thiếu rõ ràng. |

## Dependencies

- Danh sách role contact chuẩn
- Quy định field bank info bắt buộc
- Rule request active dùng chung

## Open Questions

- Có cho phép một người kiêm nhiều vai trò không?
- `swift code` là optional cho mọi supplier hay chỉ một số trường hợp?
