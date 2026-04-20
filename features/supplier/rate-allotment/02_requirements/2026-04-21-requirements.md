# Gói Yêu Cầu

## Tóm Tắt Phạm Vi

Module `rate-allotment` cho phép supplier cấu hình rate, cancellation policy, allotment và booking mode; đồng thời hỗ trợ season, surcharge và promotion ở mức optional.

## Business Requirements

| ID | Yêu cầu | Lý do | Độ ưu tiên | Nguồn |
| --- | --- | --- | --- | --- |
| BR-01 | Hệ thống phải cho phép tạo ít nhất 1 rate hợp lệ gắn với 1 room type. | Cần có dữ liệu giá để mở bán. | Must Have | BRD |
| BR-02 | Hệ thống phải hỗ trợ cancellation policy đủ chuẩn để booking xử lý đúng. | Cần tránh tranh chấp điều kiện hủy. | Must Have | BRD |
| BR-03 | Hệ thống phải hỗ trợ allotment để xác định booking mode. | Cần phân biệt `On Request` và `Instant Confirm`. | Must Have | BRD |
| BR-04 | Hệ thống nên cho phép season, surcharge và promotion ở mức optional. | Cần linh hoạt nhưng không làm cản luồng chính. | Should Have | BRD |

## Functional Requirements

| ID | Yêu cầu | Actor | Trigger | Kết quả mong đợi | Độ ưu tiên |
| --- | --- | --- | --- | --- | --- |
| FR-01 | Cho phép chọn room type, meal plan ưu tiên 5 loại đầu, thị trường khách lưu trú, loại giá TA hoặc OTA, giá phòng hoặc đêm, date range áp dụng và tiền tệ. | Supplier | Tạo rate mới | Rate draft được tạo. | Must Have |
| FR-02 | Cho phép bỏ qua cấu hình mùa nếu supplier không sử dụng. | Supplier | Vào phần season | User có thể skip mà không chặn luồng chính. | Should Have |
| FR-03 | Cho phép tạo nhiều điều kiện cancellation nối tiếp nhau. | Supplier | Cấu hình cancellation policy | Policy được lưu thành nhiều interval hợp lệ. | Must Have |
| FR-04 | Validate cancellation policy không overlap và không để hở khoảng thời gian theo rule được xác nhận. | Hệ thống | Supplier lưu cancellation | Hệ thống chặn policy không hợp lệ. | Must Have |
| FR-05 | Cho phép cấu hình phụ phí ở mức optional. | Supplier | Vào phần surcharge | User có thể nhập hoặc bỏ qua surcharge. | Should Have |
| FR-06 | Cho phép cấu hình khuyến mãi early bird, last minute, stay pay, long stay ở mức optional. | Supplier | Vào phần promotion | Promotion được lưu nếu supplier cấu hình. | Should Have |
| FR-07 | Cho phép cấu hình allotment theo ngày hoặc theo range. | Supplier | Vào phần allotment | Allotment được lưu thành công. | Must Have |
| FR-08 | Xác định booking mode là `On Request` khi không có allotment và `Instant Confirm` khi có allotment. | Hệ thống | Allotment được lưu hoặc bỏ trống | Booking mode được tính đúng và hiển thị rõ. | Must Have |
| FR-09 | Chỉ đánh dấu step đủ điều kiện khi có ít nhất 1 rate hợp lệ gắn với room type, có date range và cancellation policy. | Hệ thống | Review summary hoặc request active | Điều kiện rate được tính đúng. | Must Have |

## Non-Functional Requirements

| ID | Nhóm | Yêu cầu | Chỉ số | Độ ưu tiên |
| --- | --- | --- | --- | --- |
| NFR-01 | Auditability | Tạo hoặc sửa rate, allotment và cancellation phải có khả năng truy vết. | Hỗ trợ support và vận hành. | Should Have |
| NFR-02 | Usability | UI phải giúp supplier hiểu booking mode đang áp dụng. | Supplier biết hotel đang `On Request` hay `Instant Confirm`. | Must Have |
| NFR-03 | Validation clarity | Lỗi overlap hoặc gap trong cancellation phải được giải thích rõ. | User biết cần sửa đoạn thời gian nào. | Must Have |

## Business Rules

| Rule ID | Phát biểu rule | Áp dụng cho | Nguồn | Ghi chú |
| --- | --- | --- | --- | --- |
| RULE-01 | Phải có ít nhất 1 rate hợp lệ gắn với 1 room type, có date range và cancellation policy. | Request Active condition | BRD | Bắt buộc |
| RULE-02 | Cancellation policy không được overlap và nên được validate đầy đủ các khoảng. | Cancellation | BRD | Bắt buộc |
| RULE-03 | Không có allotment thì booking mode mặc định là `On Request`. | Booking mode | BRD | Bắt buộc |
| RULE-04 | Có allotment thì booking mode mặc định là `Instant Confirm`. | Booking mode | BRD | Bắt buộc |

## Candidate User Stories

### US-01

Là supplier,
Tôi muốn tạo rate hợp lệ cho room type,
Để hotel có thể mở bán.

### US-02

Là supplier,
Tôi muốn cấu hình allotment và hiểu booking mode,
Để chủ động cách nhận booking.

## Acceptance Criteria

| AC ID | Story Ref | Acceptance Criteria |
| --- | --- | --- |
| AC-01 | US-01 | Given supplier chọn room type và nhập đủ trường rate bắt buộc, when lưu rate, then rate được tạo thành công. |
| AC-02 | US-01 | Given supplier tạo cancellation policy có khoảng thời gian overlap, when lưu policy, then hệ thống chặn lưu và hiển thị lỗi rõ ràng. |
| AC-03 | US-01 | Given supplier chưa tạo rate hợp lệ hoặc thiếu cancellation policy, when review summary hoặc request active, then hệ thống hiển thị thiếu điều kiện rate. |
| AC-04 | US-02 | Given supplier không cấu hình allotment, when lưu bước này, then booking mode mặc định là `On Request`. |
| AC-05 | US-02 | Given supplier cấu hình allotment hợp lệ, when lưu bước này, then booking mode mặc định là `Instant Confirm`. |
| AC-06 | US-02 | Given season, surcharge hoặc promotion không được nhập, when supplier tiếp tục flow, then hệ thống không chặn step bắt buộc chỉ vì các mục optional. |

## Dependencies

- Danh mục meal plan, market, room type
- Rule coverage của cancellation policy
- Logic booking mode dùng chung

## Open Questions

- 5 meal plan ưu tiên đầu có danh sách canonical nào?
- Gap trong cancellation có bắt buộc phủ 100% timeline hay chỉ cảnh báo?
