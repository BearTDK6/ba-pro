# Kịch Bản UAT

| Scenario ID | Requirement Ref | Kịch bản | Điều kiện tiên quyết | Bước thực hiện | Kết quả mong đợi | Tester | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| UAT-01 | BR-01, FR-01, FR-02, RULE-01, AC-01 | Hệ thống nhận diện thiếu vai trò contact bắt buộc | Có step contact trống hoặc chưa đủ role | Tạo 1 hoặc 2 contact nhưng chưa đủ 3 vai trò | Hệ thống hiển thị còn thiếu vai trò nào |  | Not Started |
| UAT-02 | BR-01, FR-02, FR-03, AC-02 | Đủ 3 role contact được đánh dấu đạt | Có form contact | Tạo đủ `RSVN`, `Sales`, `Kế toán` rồi lưu | Điều kiện contact được đánh dấu đạt |  | Not Started |
| UAT-03 | BR-02, FR-04, RULE-02, AC-03 | Payment term chỉ chấp nhận 2 loại chuẩn | Có form payment term | Chọn một trong hai payment term chuẩn rồi lưu | Hệ thống lưu thành công; giá trị ngoài danh sách không được chấp nhận |  | Not Started |
| UAT-04 | BR-03, FR-05, AC-04 | Bank info được lưu thành công | Có form payment info | Nhập đủ dữ liệu ngân hàng và hóa đơn rồi lưu | Bank info được lưu |  | Not Started |
| UAT-05 | BR-04, FR-06, RULE-03, AC-05 | Request active bị chặn khi thiếu contact hoặc bank info | Thiếu ít nhất một role hoặc thiếu bank info | Mở review summary hoặc bấm request active | Hệ thống chặn tiếp tục và chỉ rõ mục còn thiếu |  | Not Started |
