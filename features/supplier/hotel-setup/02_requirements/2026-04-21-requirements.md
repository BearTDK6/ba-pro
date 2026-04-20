# Gói Yêu Cầu

## Tóm Tắt Phạm Vi

Module `hotel-setup` cho phép supplier nhập thông tin tổng quan khách sạn, xử lý duplicate check, thiết lập policy, facilities, USP và media để hình thành hồ sơ khách sạn đủ chuẩn cho onboarding.

## Business Requirements

| ID | Yêu cầu | Lý do | Độ ưu tiên | Nguồn |
| --- | --- | --- | --- | --- |
| BR-01 | Hệ thống phải cho phép supplier khởi tạo hồ sơ khách sạn với dữ liệu nền tảng cần thiết. | Cần tạo hotel profile phục vụ mở bán. | Must Have | BRD |
| BR-02 | Hệ thống phải ngăn tạo trùng khách sạn và hỗ trợ claim hotel hiện có khi phát hiện nghi ngờ trùng. | Cần giữ sạch dữ liệu master hotel. | Must Have | BRD |
| BR-03 | Hệ thống phải tạo mới `Hotel ID` hoặc gắn `Hotel ID` hiện có với `Supplier ID` sau phần tổng quan. | Cần định danh và liên kết dữ liệu chuẩn. | Must Have | BRD |
| BR-04 | Hệ thống phải thu thập đủ policy, facilities, USP và media để đánh giá mức hoàn tất step. | Cần đủ dữ liệu cho request active. | Must Have | BRD |

## Functional Requirements

| ID | Yêu cầu | Actor | Trigger | Kết quả mong đợi | Độ ưu tiên |
| --- | --- | --- | --- | --- | --- |
| FR-01 | Cho phép nhập loại hình khách sạn, phạm vi dịch vụ, tên tiếng Việt, tên tiếng Anh, tiêu chuẩn sao, địa chỉ, map pin, địa danh gần khách sạn và mô tả ngắn. | Supplier | Bắt đầu step Hotel Setup | Hồ sơ tổng quan khách sạn được lưu. | Must Have |
| FR-02 | Thực hiện duplicate check khi supplier nhập tên khách sạn tiếng Việt. | Hệ thống | Supplier nhập tên tiếng Việt | Hệ thống gợi ý các khách sạn hiện có nếu nghi ngờ trùng. | Must Have |
| FR-03 | Hiển thị popup với hai lựa chọn `claim/link hotel` hoặc quay lại chỉnh tên khi phát hiện trùng. | Supplier | Duplicate check trả về kết quả nghi ngờ trùng | Supplier có hướng xử lý rõ ràng. | Must Have |
| FR-04 | Tạo mới `Hotel ID` hoặc gắn `Hotel ID` hiện có với `Supplier ID` sau phần tổng quan theo rule backend. | Hệ thống | Tổng quan khách sạn hợp lệ hoặc claim thành công | Hồ sơ được định danh đúng. | Must Have |
| FR-05 | Cho phép nhập giờ check-in, giờ check-out, chính sách phụ thu và hướng dẫn thủ tục nhận phòng. | Supplier | Supplier vào phần quy định chung | Policy khách sạn được lưu. | Must Have |
| FR-06 | Cho phép chọn facilities từ danh mục chuẩn với ngưỡng tối thiểu 3 đến 5 lựa chọn theo rule được xác nhận. | Supplier | Supplier vào phần cơ sở vật chất | Facilities được lưu và đạt ngưỡng tối thiểu. | Must Have |
| FR-07 | Cho phép chọn USP từ danh mục chuẩn và thêm mô tả custom ngắn. | Supplier | Supplier vào phần USP | USP được lưu. | Should Have |
| FR-08 | Cho phép upload ảnh tổng quan, ảnh cover, video link hoặc video ngắn; hiển thị hướng dẫn kích thước, dung lượng và số lượng. | Supplier | Supplier vào phần media | Media được upload theo guideline. | Must Have |
| FR-09 | Hỗ trợ reorder ảnh, set cover, xóa ảnh và retry upload thất bại. | Supplier | Supplier quản lý media đã upload | Media list phản ánh đúng lựa chọn của user. | Should Have |
| FR-10 | Chỉ đánh dấu step hoàn tất khi có dữ liệu tổng quan, map pin, mô tả ngắn, facilities tối thiểu và số ảnh tối thiểu. | Hệ thống | Supplier lưu step | Step status được tính đúng. | Must Have |

## Non-Functional Requirements

| ID | Nhóm | Yêu cầu | Chỉ số | Độ ưu tiên |
| --- | --- | --- | --- | --- |
| NFR-01 | Upload | Upload ảnh hoặc video phải có progress và validate định dạng hoặc dung lượng. | User thấy trạng thái upload rõ ràng. | Must Have |
| NFR-02 | Usability | Duplicate popup phải dễ hiểu và đưa ra hướng xử lý rõ ràng. | User không bị kẹt khi phát hiện trùng. | Must Have |
| NFR-03 | Performance | Màn hình thông thường tải dưới ngưỡng mục tiêu chung; không tính upload file lớn. | Theo NFR chung của BRD. | Should Have |
| NFR-04 | Responsive | Trải nghiệm nhập dữ liệu và upload media phải hoạt động tốt trên web và app. | UI phù hợp từng kênh. | Should Have |

## Business Rules

| Rule ID | Phát biểu rule | Áp dụng cho | Nguồn | Ghi chú |
| --- | --- | --- | --- | --- |
| RULE-01 | Không cho tạo trùng khách sạn khi hệ thống đã có hotel tương ứng. | Duplicate check | BRD | Bắt buộc |
| RULE-02 | Khi nghi ngờ trùng, hệ thống phải hỗ trợ claim existing hotel. | Duplicate flow | BRD | Bắt buộc |
| RULE-03 | Sau phần tổng quan, hệ thống tạo `Hotel ID` mới hoặc gắn `Hotel ID` hiện có với `Supplier ID`. | Hotel identity | BRD | Rule backend |
| RULE-04 | Step chỉ được xem là hoàn tất khi đạt đủ dữ liệu tối thiểu của hotel info, map pin, mô tả, facilities và ảnh. | Step completion | BRD | Bắt buộc |

## Candidate User Stories

### US-01

Là supplier,
Tôi muốn tạo hoặc claim hồ sơ khách sạn,
Để tôi có thể tiếp tục onboarding mà không tạo dữ liệu trùng.

### US-02

Là supplier,
Tôi muốn khai báo policy, facilities, USP và media,
Để hồ sơ khách sạn đủ thông tin để mở bán.

## Acceptance Criteria

| AC ID | Story Ref | Acceptance Criteria |
| --- | --- | --- |
| AC-01 | US-01 | Given supplier nhập tên khách sạn tiếng Việt, when hệ thống phát hiện nghi ngờ trùng, then hệ thống hiển thị danh sách khách sạn hiện có và popup hướng dẫn claim hoặc chỉnh tên. |
| AC-02 | US-01 | Given phần tổng quan hợp lệ hoặc claim hợp lệ, when supplier lưu phần tổng quan, then hệ thống tạo hoặc gắn `Hotel ID` đúng với `Supplier ID`. |
| AC-03 | US-02 | Given supplier nhập đủ dữ liệu tổng quan và policy, when lưu step, then dữ liệu khách sạn được lưu dưới dạng draft hoặc completed tùy mức độ đầy đủ. |
| AC-04 | US-02 | Given supplier chọn facilities và USP, when đạt ngưỡng tối thiểu theo rule, then step đáp ứng điều kiện dữ liệu tiện ích và USP. |
| AC-05 | US-02 | Given supplier upload media hợp lệ, when đạt số ảnh tối thiểu và chọn cover, then hồ sơ khách sạn đáp ứng điều kiện media tối thiểu. |
| AC-06 | US-02 | Given dữ liệu hotel info chưa đủ tối thiểu, when supplier cố tiếp tục hoặc review summary, then hệ thống hiển thị step là `Incomplete` cùng lỗi hoặc thiếu tương ứng. |

## Dependencies

- Danh mục loại hình khách sạn, facilities, USP
- Rule duplicate matching và claim flow
- Rule tạo hoặc link `Hotel ID`
- Chính sách upload media

## Open Questions

- Ngưỡng facilities tối thiểu là 3 hay 5 theo từng loại hotel?
- Duplicate matching dùng exact match, fuzzy match, hay thêm địa chỉ?
- Có cần validate video file riêng với video link không?
