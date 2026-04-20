# Tóm Tắt Dự Án

## Kiểm Soát Tài Liệu

- Domain: Supplier
- Feature: Account & Supplier
- Prepared by: Codex
- Date: 2026-04-21
- Status: Draft
- Priority: Mandatory

## Đầu Vào Đã Xác Nhận

- Module: Account & Supplier
- Mục tiêu: Hỗ trợ đăng ký/đăng nhập, verify, phân loại supplier
- Bắt buộc: Có
- Ghi chú: Auto generate `Supplier ID`

## Bài Toán Nghiệp Vụ

Cần một module thống nhất để supplier có thể đăng ký hoặc đăng nhập, đi qua bước verify cần thiết, được phân loại đúng theo quy tắc nghiệp vụ, và được gán `Supplier ID` tự động. Nếu không có luồng này, dữ liệu supplier dễ bị thiếu nhất quán, khó kiểm soát trạng thái xác minh, và phát sinh xử lý thủ công trong vận hành.

## Mục Tiêu Và Chỉ Số Thành Công

### Mục Tiêu

- Cho phép supplier mới đăng ký tài khoản và khởi tạo hồ sơ supplier.
- Cho phép supplier hiện hữu đăng nhập để tiếp tục sử dụng hệ thống.
- Xác minh supplier theo yêu cầu nghiệp vụ trước khi đi vào trạng thái sử dụng mục tiêu.
- Phân loại supplier theo tiêu chí được cấu hình hoặc phê duyệt bởi business.
- Tự động generate `Supplier ID` duy nhất, giảm nhập tay và tránh sai lệch dữ liệu.

### Chỉ Số Thành Công Dự Kiến

- Tỷ lệ đăng ký thành công của supplier mới
- Tỷ lệ đăng nhập thành công của supplier hiện hữu
- Tỷ lệ supplier hoàn tất verify
- Tỷ lệ supplier được phân loại đúng ngay từ lần đầu
- Tỷ lệ trùng hoặc lỗi `Supplier ID` bằng 0

## Phạm Vi

### In Scope

- Đăng ký tài khoản supplier mới
- Đăng nhập tài khoản supplier hiện hữu
- Verify account hoặc supplier theo yêu cầu nghiệp vụ
- Phân loại supplier
- Auto-generate `Supplier ID`
- Hiển thị trạng thái xử lý liên quan đến đăng ký, verify, và phân loại

### Out Of Scope

- Quản lý catalog hoặc sản phẩm của supplier
- Quản lý hợp đồng, thanh toán, hoặc đối soát
- Quy trình admin nội bộ ngoài phần liên quan trực tiếp đến verify và classification
- Tích hợp sâu với hệ thống thứ ba nếu chưa được xác nhận trong phạm vi này

## Đối Tượng Sử Dụng

| Stakeholder | Vai trò | Mối quan tâm | Ảnh hưởng | Ghi chú |
| --- | --- | --- | --- | --- |
| Supplier mới | Đăng ký và tạo hồ sơ | Tạo tài khoản nhanh, biết trạng thái hồ sơ | Cao | Người dùng đầu vào chính |
| Supplier hiện hữu | Đăng nhập và tiếp tục sử dụng | Truy cập ổn định, không bị nhầm trạng thái | Cao | Người dùng quay lại |
| Ops hoặc Verification team | Xử lý verify và classification | Có dữ liệu rõ ràng, giảm thao tác tay | Cao | Có thể là nhóm back-office |
| Product hoặc Business owner | Xác định rule classify | Đúng logic nghiệp vụ | Cao | Cần chốt tiêu chí phân loại |

## Giả Định

- `Verify` bao gồm một hoặc nhiều bước xác minh account, liên hệ, hoặc hồ sơ pháp lý của supplier.
- Supplier phải đi qua tối thiểu một trạng thái xác minh trước khi được công nhận là supplier hợp lệ trong hệ thống.
- `Supplier ID` được hệ thống generate tự động và không do supplier tự nhập.
- Tiêu chí phân loại supplier tồn tại hoặc sẽ được business xác nhận riêng.

## Ràng Buộc

- Module là bắt buộc.
- `Supplier ID` phải duy nhất trong toàn hệ thống supplier.
- Luồng đăng ký/đăng nhập phải đủ rõ để không gây nhầm lẫn giữa supplier mới và supplier hiện hữu.

## Rủi Ro Và Câu Hỏi Mở

### Rủi Ro

- Phạm vi `verify` không rõ sẽ dẫn đến yêu cầu chức năng bị thiếu hoặc test không đủ.
- Rule phân loại supplier không rõ sẽ làm sai kết quả classification.
- Thời điểm generate `Supplier ID` không rõ sẽ dẫn đến tạo ID rác hoặc khó trace.
- Có nguy cơ tạo trùng supplier nếu không có rule kiểm tra trùng thông tin đăng ký.

### Câu Hỏi Mở

- `Verify` bao gồm những bước nào: email, phone, hồ sơ pháp lý, hay manual approval?
- Supplier được phân loại theo loại hình, mức độ, trạng thái, hay nhiều chiều kết hợp?
- `Supplier ID` được generate tại thời điểm đăng ký, sau verify, hay sau approve?
- Có cần cơ chế chống đăng ký trùng theo email, số điện thoại, mã số thuế, hay giấy phép kinh doanh không?
- Supplier chưa verify có được đăng nhập và xem phần nào của hệ thống hay không?

## Bước Tiếp Theo Ngay Lập Tức

- Xác nhận phạm vi `verify` và owner của quy trình này.
- Xác nhận ma trận classification của supplier.
- Xác nhận format hoặc policy generate `Supplier ID`.
- Xác nhận rule xử lý duplicate supplier.
