# Gói Yêu Cầu

## Tóm Tắt Phạm Vi

Module `room-setup` cho phép supplier tạo, chỉnh sửa và clone room type, khai báo sức chứa, loại giường, tiện ích phòng, USP và ảnh phòng để đáp ứng điều kiện tối thiểu cho mở bán.

## Business Requirements

| ID | Yêu cầu | Lý do | Độ ưu tiên | Nguồn |
| --- | --- | --- | --- | --- |
| BR-01 | Hệ thống phải cho phép tạo ít nhất 1 room type cho mỗi hotel onboarding. | Cần dữ liệu phòng để mở bán. | Must Have | BRD |
| BR-02 | Hệ thống phải đảm bảo dữ liệu room phản ánh đúng sức chứa và tiện ích chính. | Cần hỗ trợ booking và hiển thị chuẩn. | Must Have | BRD |
| BR-03 | Hệ thống nên hỗ trợ clone room để tăng tốc nhập liệu. | Cần tối ưu UX cho supplier. | Should Have | BRD |

## Functional Requirements

| ID | Yêu cầu | Actor | Trigger | Kết quả mong đợi | Độ ưu tiên |
| --- | --- | --- | --- | --- | --- |
| FR-01 | Cho phép tạo room type với tên hạng phòng, diện tích, loại giường, kích thước giường, số giường phụ tối đa, sức chứa tiêu chuẩn NL hoặc TE và sức chứa tối đa NL hoặc TE. | Supplier | Tạo room mới | Room draft được tạo. | Must Have |
| FR-02 | Cho phép upload ảnh phòng cho từng room type. | Supplier | Tạo hoặc sửa room | Room có media phù hợp. | Must Have |
| FR-03 | Cho phép chọn loại view và tiện ích phòng từ danh mục chuẩn. | Supplier | Cập nhật room details | Dữ liệu tiện ích phòng được lưu. | Must Have |
| FR-04 | Cho phép chọn USP phòng từ danh mục chuẩn và thêm custom text ngắn. | Supplier | Cập nhật USP phòng | USP phòng được lưu. | Should Have |
| FR-05 | Cho phép clone room từ room type hiện có để tạo room mới. | Supplier | Chọn hành động clone | Một room draft mới được tạo từ dữ liệu nguồn. | Should Have |
| FR-06 | Validate sức chứa tối đa lớn hơn hoặc bằng sức chứa tiêu chuẩn. | Hệ thống | Supplier lưu room | Hệ thống chặn dữ liệu không hợp lệ. | Must Have |
| FR-07 | Chỉ cho phép tiếp tục request active khi hotel có ít nhất 1 room type hợp lệ. | Hệ thống | Supplier review summary hoặc request active | Điều kiện room được tính đúng. | Must Have |

## Non-Functional Requirements

| ID | Nhóm | Yêu cầu | Chỉ số | Độ ưu tiên |
| --- | --- | --- | --- | --- |
| NFR-01 | Usability | Form room phải hỗ trợ nhập nhanh và dễ hiểu với user không chuyên hệ thống. | User hoàn tất ít nhất một room type mà không cần giải thích kỹ thuật sâu. | Must Have |
| NFR-02 | Upload | Upload ảnh phòng phải có trạng thái tiến trình và xử lý lỗi rõ ràng. | User biết ảnh nào thành công hay thất bại. | Should Have |
| NFR-03 | Auditability | Tạo, sửa, clone room cần có khả năng truy vết. | Hỗ trợ vận hành và support. | Should Have |

## Business Rules

| Rule ID | Phát biểu rule | Áp dụng cho | Nguồn | Ghi chú |
| --- | --- | --- | --- | --- |
| RULE-01 | Sức chứa tối đa của phòng phải lớn hơn hoặc bằng sức chứa tiêu chuẩn. | Room capacity | BRD | Bắt buộc |
| RULE-02 | Phải có ít nhất 1 room type hợp lệ để tiếp tục request active. | Request Active condition | BRD | Bắt buộc |
| RULE-03 | Clone room là tính năng nên có để tăng tốc nhập liệu. | UX optimization | BRD | Should Have |

## Candidate User Stories

### US-01

Là supplier,
Tôi muốn tạo room type với thông tin sức chứa và tiện ích rõ ràng,
Để tôi có thể cấu hình giá và mở bán chính xác.

### US-02

Là supplier,
Tôi muốn clone room type tương tự,
Để tôi không phải nhập lại toàn bộ dữ liệu cho nhiều phòng giống nhau.

## Acceptance Criteria

| AC ID | Story Ref | Acceptance Criteria |
| --- | --- | --- |
| AC-01 | US-01 | Given supplier nhập thông tin room type, when dữ liệu bắt buộc hợp lệ, then hệ thống lưu room type thành công. |
| AC-02 | US-01 | Given supplier nhập sức chứa tối đa nhỏ hơn sức chứa tiêu chuẩn, when lưu room, then hệ thống chặn lưu và hiển thị lỗi rõ ràng. |
| AC-03 | US-01 | Given room type có ảnh phòng hợp lệ, when lưu room, then room đáp ứng điều kiện media cơ bản cho step này. |
| AC-04 | US-02 | Given đã có một room type nguồn, when supplier chọn clone room, then hệ thống tạo room draft mới kế thừa dữ liệu nguồn để chỉnh sửa tiếp. |
| AC-05 | US-01 | Given hotel chưa có room type hợp lệ, when supplier review summary hoặc request active, then hệ thống hiển thị thiếu điều kiện room và không cho hoàn tất yêu cầu mở bán. |

## Dependencies

- Danh mục view, tiện ích phòng, USP phòng
- Rule media tối thiểu cho room
- Rule request active dùng chung

## Open Questions

- Có yêu cầu tối thiểu số ảnh cho từng room type không?
- Clone room sẽ clone cả ảnh hay chỉ clone text data?
