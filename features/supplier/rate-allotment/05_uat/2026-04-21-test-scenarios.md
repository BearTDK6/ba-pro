# Kịch Bản UAT

| Scenario ID | Requirement Ref | Kịch bản | Điều kiện tiên quyết | Bước thực hiện | Kết quả mong đợi | Tester | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| UAT-01 | BR-01, FR-01, AC-01 | Tạo rate hợp lệ cho room type | Đã có ít nhất 1 room type | Chọn room, nhập meal plan, market, loại giá, giá, date range, tiền tệ rồi lưu | Rate được tạo thành công |  | Not Started |
| UAT-02 | BR-02, FR-03, FR-04, RULE-02, AC-02 | Chặn cancellation policy overlap | Có form cancellation | Tạo 2 interval cancellation bị overlap rồi lưu | Hệ thống chặn lưu và chỉ rõ đoạn thời gian lỗi |  | Not Started |
| UAT-03 | BR-01, FR-09, RULE-01, AC-03 | Request active bị chặn khi chưa có rate hợp lệ | Hotel chưa có rate hợp lệ | Mở review summary hoặc bấm request active | Hệ thống hiển thị thiếu điều kiện rate |  | Not Started |
| UAT-04 | BR-03, FR-08, RULE-03, AC-04 | Booking mode là On Request khi không có allotment | Có rate hợp lệ nhưng chưa nhập allotment | Lưu bước mà không cấu hình allotment | Booking mode hiển thị là `On Request` |  | Not Started |
| UAT-05 | BR-03, FR-07, FR-08, RULE-04, AC-05 | Booking mode là Instant Confirm khi có allotment | Có rate hợp lệ | Nhập allotment theo ngày hoặc range rồi lưu | Booking mode hiển thị là `Instant Confirm` |  | Not Started |
| UAT-06 | BR-04, FR-02, FR-05, FR-06, AC-06 | Các phần optional không chặn luồng chính | Có form season, surcharge, promotion | Bỏ qua các phần optional rồi tiếp tục | Hệ thống không chặn vì các mục optional chưa nhập |  | Not Started |
