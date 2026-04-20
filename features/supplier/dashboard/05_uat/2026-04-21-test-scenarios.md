# Kịch Bản UAT

| Scenario ID | Requirement Ref | Kịch bản | Điều kiện tiên quyết | Bước thực hiện | Kết quả mong đợi | Tester | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| UAT-01 | BR-01, BR-04, FR-01, FR-05, RULE-01, RULE-02, AC-01 | Dashboard hiển thị đúng resume summary sau login | Supplier đã có hồ sơ onboarding dở dang | Đăng nhập lại và vào dashboard | Dashboard hiển thị `Hotel ID`, tên khách sạn, trạng thái, `% hoàn thành`, CTA tiếp tục |  | Not Started |
| UAT-02 | BR-02, FR-02, AC-02 | Checklist chỉ rõ phần còn thiếu | Hồ sơ thiếu một hoặc nhiều step | Mở dashboard | Checklist hiển thị đúng room, rate, contact, payment hoặc document đang thiếu |  | Not Started |
| UAT-03 | BR-02, FR-03, AC-03 | CTA chính điều hướng đúng chỗ thiếu | Có ít nhất một mục thiếu | Bấm `Tiếp tục hoàn tất` hoặc CTA tương ứng | Hệ thống điều hướng đúng module cần làm tiếp |  | Not Started |
| UAT-04 | BR-03, FR-04, RULE-03, AC-04 | Notification center hiển thị revision hoặc review status | Có notification từ admin hoặc review flow | Vào dashboard | Notification center hiển thị đúng nội dung và trạng thái liên quan |  | Not Started |
| UAT-05 | BR-01, BR-04, FR-06, AC-05 | Dashboard phản ánh đúng lifecycle status | Trạng thái onboarding đã thay đổi | Reload dashboard | Trạng thái mới hiển thị đúng theo lifecycle |  | Not Started |
