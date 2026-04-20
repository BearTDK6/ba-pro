# Tóm Tắt Dự Án

## Kiểm Soát Tài Liệu

- Domain: Supplier
- Feature: Legal Documents
- Prepared by: Codex
- Date: 2026-04-21
- Status: Draft
- Priority: Mandatory

## Đầu Vào Đã Xác Nhận

- Module: Legal Documents
- Mục tiêu: Upload hồ sơ pháp lý
- Bắt buộc: Có
- Ghi chú: Đa định dạng file

## Bài Toán Nghiệp Vụ

Supplier cần tải hồ sơ pháp lý, tự rà soát điều kiện tối thiểu và gửi `Request Active`. Đây là điểm chuyển giao từ tự phục vụ sang review nội bộ, nên thông điệp và validation phải rất rõ.

## Mục Tiêu

- Hỗ trợ upload nhiều file pháp lý theo định dạng cho phép
- Hiển thị review summary trước khi submit
- Chỉ cho `Request Active` khi đủ điều kiện tối thiểu
- Chuyển trạng thái hồ sơ sang `Pending Review` và hiển thị thông điệp thành công rõ ràng
