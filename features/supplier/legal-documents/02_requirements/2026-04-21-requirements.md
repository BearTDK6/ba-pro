# Gói Yêu Cầu

## Tóm Tắt Phạm Vi

Module `legal-documents` cho phép supplier upload hồ sơ pháp lý, xem review summary và gửi `Request Active` khi đã đạt đủ điều kiện tối thiểu để admin review.

## Business Requirements

| ID | Yêu cầu | Lý do | Độ ưu tiên | Nguồn |
| --- | --- | --- | --- | --- |
| BR-01 | Hệ thống phải cho phép upload nhiều file hồ sơ pháp lý. | Cần thu thập chứng từ trước review. | Must Have | BRD |
| BR-02 | Hệ thống phải hỗ trợ review summary trước khi submit. | Cần giúp supplier tự kiểm tra hồ sơ còn thiếu. | Must Have | BRD |
| BR-03 | Hệ thống chỉ cho phép `Request Active` khi đủ điều kiện tối thiểu toàn flow. | Cần tránh gửi hồ sơ thiếu. | Must Have | BRD |
| BR-04 | Sau khi `Request Active`, hệ thống phải chuyển trạng thái sang `Pending Review` và hiển thị thông điệp admin liên hệ trong 48 giờ. | Cần xác nhận giao dịch rõ ràng với supplier. | Must Have | BRD |

## Functional Requirements

| ID | Yêu cầu | Actor | Trigger | Kết quả mong đợi | Độ ưu tiên |
| --- | --- | --- | --- | --- | --- |
| FR-01 | Cho phép upload nhiều file PDF, ảnh hoặc Word cho các loại hồ sơ như GPĐKKD, chứng nhận sao, hợp đồng phân phối hoặc mua bán dịch vụ khách sạn, giấy ủy quyền nếu có. | Supplier | Mở step legal documents | File hợp lệ được upload. | Must Have |
| FR-02 | Hiển thị hướng dẫn upload và danh sách loại hồ sơ gợi ý cho supplier. | Supplier | Mở step legal documents | Supplier hiểu cần upload gì. | Should Have |
| FR-03 | Hiển thị review summary với checklist điều kiện mở bán tối thiểu trước khi submit. | Supplier | Mở review summary | Supplier thấy mục nào đạt hoặc thiếu. | Must Have |
| FR-04 | Chỉ cho phép `Request Active` khi đạt đủ các điều kiện tối thiểu: account verified, hotel info, ít nhất 1 room, ít nhất 1 rate, đủ 3 contact, bank info, ít nhất 1 document hợp lệ. | Hệ thống | Supplier bấm `Request Active` | Hệ thống chặn hoặc cho submit đúng điều kiện. | Must Have |
| FR-05 | Sau khi submit thành công, chuyển trạng thái onboarding sang `Pending Review`, điều hướng về dashboard hoặc home, và hiển thị thông điệp thành công. | Hệ thống | `Request Active` thành công | Supplier được xác nhận kết quả rõ ràng. | Must Have |
| FR-06 | Sau khi tạo thành công hồ sơ khách sạn, hiển thị nội dung hướng dẫn upload pháp lý với tên account và tên khách sạn. | Supplier | Mở step sau khi hotel đã khởi tạo | Supplier thấy thông điệp dẫn dắt đúng ngữ cảnh. | Should Have |

## Non-Functional Requirements

| ID | Nhóm | Yêu cầu | Chỉ số | Độ ưu tiên |
| --- | --- | --- | --- | --- |
| NFR-01 | Upload | Upload file phải hỗ trợ progress, validate định dạng và dung lượng. | Supplier biết file nào thành công hoặc thất bại. | Must Have |
| NFR-02 | Usability | Review summary phải dễ hiểu và chỉ rõ mục thiếu để quay lại sửa. | Supplier không mơ hồ khi bị chặn submit. | Must Have |
| NFR-03 | Auditability | Hành động upload tài liệu và request active phải có lịch sử truy vết. | Hỗ trợ review và support. | Should Have |

## Business Rules

| Rule ID | Phát biểu rule | Áp dụng cho | Nguồn | Ghi chú |
| --- | --- | --- | --- | --- |
| RULE-01 | Phải có ít nhất 1 document hợp lệ để `Request Active`. | Legal documents | BRD | Bắt buộc |
| RULE-02 | `Request Active` chỉ được phép khi toàn bộ điều kiện tối thiểu của onboarding đã đạt. | Request Active | BRD | Bắt buộc |
| RULE-03 | Sau khi gửi thành công, trạng thái chuyển sang `Pending Review`. | Status transition | BRD | Bắt buộc |

## Candidate User Stories

### US-01

Là supplier,
Tôi muốn upload hồ sơ pháp lý theo nhiều định dạng,
Để hoàn tất phần pháp lý của onboarding.

### US-02

Là supplier,
Tôi muốn thấy review summary trước khi submit,
Để tự kiểm tra và sửa các mục còn thiếu.

### US-03

Là supplier,
Tôi muốn gửi `Request Active` và nhận thông báo kết quả rõ ràng,
Để biết hồ sơ đã chuyển sang review nội bộ.

## Acceptance Criteria

| AC ID | Story Ref | Acceptance Criteria |
| --- | --- | --- |
| AC-01 | US-01 | Given supplier upload file PDF, ảnh hoặc Word hợp lệ, when upload hoàn tất, then hệ thống lưu file thành công và hiển thị progress hoặc trạng thái upload. |
| AC-02 | US-02 | Given supplier mở review summary, when một hoặc nhiều điều kiện mở bán chưa đạt, then hệ thống hiển thị checklist thiếu rõ ràng và không cho submit. |
| AC-03 | US-03 | Given tất cả điều kiện tối thiểu đã đạt và có ít nhất 1 document hợp lệ, when supplier bấm `Request Active`, then hệ thống submit thành công, chuyển trạng thái sang `Pending Review` và điều hướng về dashboard hoặc home. |
| AC-04 | US-03 | Given `Request Active` thành công, when thông báo được hiển thị, then supplier thấy nội dung admin sẽ liên hệ trong vòng 48 giờ. |

## Dependencies

- Shared rule về điều kiện tối thiểu để Request Active
- Chính sách file upload
- Dashboard để điều hướng sau submit

## Open Questions

- Có cần phân loại document theo type bắt buộc hoặc optional ngay tại upload UI không?
- Có cho phép upload lại hoặc thay thế file đã nộp sau khi vào `Pending Review` không?
