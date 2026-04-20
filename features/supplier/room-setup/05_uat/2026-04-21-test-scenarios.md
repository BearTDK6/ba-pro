# Kịch Bản UAT

| Scenario ID | Requirement Ref | Kịch bản | Điều kiện tiên quyết | Bước thực hiện | Kết quả mong đợi | Tester | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| UAT-01 | BR-01, BR-02, FR-01, FR-03, FR-04, AC-01 | Tạo room type hợp lệ | Hotel đã có `Hotel ID` | Nhập thông tin room, tiện ích, USP rồi lưu | Room type được tạo thành công |  | Not Started |
| UAT-02 | BR-02, FR-06, RULE-01, AC-02 | Validation sức chứa hoạt động đúng | Form room đang mở | Nhập sức chứa tối đa nhỏ hơn sức chứa tiêu chuẩn rồi lưu | Hệ thống chặn lưu và hiển thị lỗi đúng |  | Not Started |
| UAT-03 | BR-02, FR-02, AC-03 | Upload ảnh phòng thành công | Có file ảnh hợp lệ | Upload ảnh cho room rồi lưu | Ảnh được lưu và gắn với room type |  | Not Started |
| UAT-04 | BR-03, FR-05, RULE-03, AC-04 | Clone room tạo draft mới đúng dữ liệu | Đã có room nguồn | Chọn clone room và mở room mới | Room draft mới được tạo từ room nguồn để chỉnh sửa tiếp |  | Not Started |
| UAT-05 | BR-01, FR-07, RULE-02, AC-05 | Request active bị chặn khi chưa có room hợp lệ | Hotel chưa có room hợp lệ | Mở review summary hoặc thử request active | Hệ thống hiển thị thiếu điều kiện room và chặn request active |  | Not Started |
