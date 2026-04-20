# Phác Thảo Giải Pháp

## Mục Tiêu

Thiết kế module `account-supplier` để supplier có thể đăng ký hoặc đăng nhập, đi qua verify, được phân loại đúng, và nhận `Supplier ID` do hệ thống generate tự động.

## Luồng Mục Tiêu

1. Supplier chọn `Sign up` hoặc `Log in`
2. Supplier mới cung cấp thông tin đăng ký và tạo hồ sơ ban đầu
3. Hệ thống hoặc ops xử lý bước verify theo rule
4. Supplier được gán classification khi đủ điều kiện
5. Hệ thống generate `Supplier ID` tại thời điểm trigger đã được xác nhận
6. Hệ thống hiển thị trạng thái và quyền truy cập phù hợp

## Hành Vi To-Be

- Supplier mới hiểu cách bắt đầu quy trình đăng ký.
- Supplier hiện hữu có thể đăng nhập và tiếp tục quy trình phù hợp với trạng thái hiện tại.
- Trạng thái verify được hiển thị rõ và có thể theo dõi.
- Classification của supplier không phụ thuộc vào nhập tay tùy ý.
- `Supplier ID` được generate tự động, duy nhất, và không cho supplier chỉnh sửa.

## Ghi Chú UX Và Nghiệp Vụ

- Tách rõ CTA `Sign up` và `Log in`.
- Trạng thái verify nên dùng wording rõ như `Pending`, `Verified`, `Rejected`, hoặc bộ trạng thái tương đương đã được business phê duyệt.
- Nếu supplier chưa đủ điều kiện truy cập đầy đủ, UI cần nói rõ nguyên nhân và bước tiếp theo.
- `Supplier ID` chỉ nên hiển thị sau khi được generate thành công.

## Ghi Chú Dữ Liệu

- Cần trường dữ liệu tối thiểu cho account, supplier profile, verify status, classification, và `Supplier ID`.
- Cần policy unique cho `Supplier ID`.
- Cần log thay đổi trạng thái để phục vụ audit.

## Quyết Định Thiết Kế Cần Chốt

- Trigger generate `Supplier ID`: sau đăng ký, sau verify, hay sau approve.
- Format của `Supplier ID`: có tiền tố nghiệp vụ hay chỉ cần unique string.
- Bước classification là tự động, bán tự động, hay thủ công hoàn toàn.
- Quyền truy cập của supplier theo từng verify status.
