# Kịch Bản UAT

| Scenario ID | Requirement Ref | Kịch bản | Điều kiện tiên quyết | Bước thực hiện | Kết quả mong đợi | Tester | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| UAT-01 | BR-02, FR-02, FR-03, RULE-01, RULE-02, AC-01 | Duplicate check hiển thị claim flow đúng | Có hotel hiện có trùng hoặc gần trùng | Nhập tên khách sạn tiếng Việt trùng dữ liệu đang có | Hệ thống hiển thị gợi ý khách sạn hiện có và popup claim hoặc chỉnh tên |  | Not Started |
| UAT-02 | BR-01, BR-03, FR-01, FR-04, RULE-03, AC-02 | Tạo mới hoặc gắn đúng Hotel ID | Supplier có dữ liệu overview hợp lệ hoặc có claim hợp lệ | Lưu phần tổng quan khách sạn | Hệ thống tạo `Hotel ID` mới hoặc link `Hotel ID` hiện có đúng với `Supplier ID` |  | Not Started |
| UAT-03 | BR-04, FR-05, AC-03 | Lưu policy khách sạn thành công | Có hồ sơ hotel draft | Nhập giờ check-in, check-out, phụ thu, hướng dẫn nhận phòng rồi lưu | Policy được lưu thành công |  | Not Started |
| UAT-04 | BR-04, FR-06, FR-07, AC-04 | Facilities và USP đáp ứng ngưỡng tối thiểu | Danh mục facilities và USP khả dụng | Chọn facilities, USP và mô tả custom ngắn rồi lưu | Hệ thống lưu dữ liệu và xác định đúng nếu đạt ngưỡng tối thiểu |  | Not Started |
| UAT-05 | BR-04, FR-08, FR-09, AC-05 | Upload và quản lý media khách sạn | Có file media hợp lệ | Upload ảnh, set cover, reorder hoặc xóa một ảnh | Media được lưu, cover được cập nhật, số ảnh tối thiểu được tính đúng |  | Not Started |
| UAT-06 | BR-04, FR-10, RULE-04, AC-06 | Step Hotel Setup chuyển `Incomplete` khi chưa đủ dữ liệu tối thiểu | Hồ sơ khách sạn thiếu ít nhất một điều kiện tối thiểu | Mở review summary hoặc cố tiếp tục flow | Hệ thống không đánh dấu `Completed` và hiển thị mục còn thiếu rõ ràng |  | Not Started |
