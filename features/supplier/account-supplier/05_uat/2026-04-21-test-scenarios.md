# Kịch Bản UAT

| Scenario ID | Requirement Ref | Kịch bản | Điều kiện tiên quyết | Bước thực hiện | Kết quả mong đợi | Tester | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| UAT-01 | BR-01, FR-01, RULE-01, AC-01 | Supplier mới đăng ký thành công | Màn hình `Sign up` khả dụng | Mở `Sign up`, nhập đủ thông tin bắt buộc, gửi đăng ký | Hệ thống tạo account hoặc hồ sơ supplier ban đầu theo rule đã xác nhận |  | Not Started |
| UAT-02 | BR-02, FR-02, RULE-01, AC-02 | Supplier hiện hữu đăng nhập thành công | Supplier có credential hợp lệ | Mở `Log in`, nhập credential hợp lệ, gửi đăng nhập | Supplier đăng nhập thành công và vào đúng trạng thái được phép |  | Not Started |
| UAT-03 | BR-03, FR-03, FR-04, RULE-03, AC-03 | Supplier được verify đúng theo rule bắt buộc | Có supplier cần verify và đủ dữ liệu required | Thực hiện quy trình verify theo checklist đã xác nhận | Trạng thái verify được cập nhật đúng theo rule |  | Not Started |
| UAT-04 | BR-03, FR-03, FR-08, AC-07 | Supplier nhìn thấy trạng thái khi verify pending hoặc failed | Có supplier ở trạng thái pending hoặc failed | Mở hồ sơ hoặc màn hình trạng thái của supplier | Hệ thống hiển thị trạng thái rõ ràng và hướng xử lý tiếp theo nếu có |  | Not Started |
| UAT-05 | BR-04, FR-05, RULE-04, AC-04 | Supplier được phân loại đúng | Rule classification đã được cấu hình hoặc xác nhận | Thực hiện xử lý classification cho supplier đủ điều kiện | Supplier được gán đúng classification theo rule |  | Not Started |
| UAT-06 | BR-05, FR-06, FR-07, RULE-02, RULE-05, AC-05, AC-06 | Hệ thống auto-generate `Supplier ID` và không cho chỉnh sửa tay | Supplier đạt điều kiện generate ID | Hoàn tất các bước đến trigger generate ID, sau đó mở hồ sơ supplier | `Supplier ID` được tạo tự động, là duy nhất, và không thể chỉnh sửa bởi supplier |  | Not Started |
| UAT-07 | FR-09, AC-08 | Hệ thống xử lý đăng ký trùng theo rule duplicate check | Rule duplicate check đã được xác nhận | Gửi đăng ký với thông tin định danh trùng hồ sơ đã tồn tại | Hệ thống chặn hoặc cảnh báo đúng theo rule duplicate handling |  | Not Started |
