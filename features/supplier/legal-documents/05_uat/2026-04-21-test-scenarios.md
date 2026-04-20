# Kịch Bản UAT

| Scenario ID | Requirement Ref | Kịch bản | Điều kiện tiên quyết | Bước thực hiện | Kết quả mong đợi | Tester | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| UAT-01 | BR-01, FR-01, FR-02, AC-01 | Upload hồ sơ pháp lý đa định dạng thành công | Có file PDF, ảnh hoặc Word hợp lệ | Upload từng loại file vào step legal documents | Hệ thống lưu file thành công và hiển thị trạng thái upload rõ ràng |  | Not Started |
| UAT-02 | BR-02, BR-03, FR-03, FR-04, RULE-02, AC-02 | Review summary chặn submit khi thiếu điều kiện | Thiếu ít nhất một điều kiện mở bán | Mở review summary rồi bấm request active | Hệ thống hiển thị checklist thiếu rõ ràng và chặn submit |  | Not Started |
| UAT-03 | BR-03, BR-04, FR-04, FR-05, RULE-01, RULE-03, AC-03 | Request active thành công khi đủ điều kiện | Đã đủ điều kiện tối thiểu toàn flow và có ít nhất 1 document hợp lệ | Bấm `Request Active` | Hệ thống chuyển sang `Pending Review` và điều hướng về dashboard hoặc home |  | Not Started |
| UAT-04 | BR-04, FR-05, AC-04 | Hiển thị đúng thông điệp sau Request Active | Request active vừa thành công | Quan sát success state hoặc notification | Supplier thấy thông điệp admin sẽ liên hệ trong vòng 48 giờ |  | Not Started |
