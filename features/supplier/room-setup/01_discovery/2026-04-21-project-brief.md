# Tóm Tắt Dự Án

## Kiểm Soát Tài Liệu

- Domain: Supplier
- Feature: Room Setup
- Prepared by: Codex
- Date: 2026-04-21
- Status: Draft
- Priority: Mandatory

## Đầu Vào Đã Xác Nhận

- Module: Room Setup
- Mục tiêu: Tạo ít nhất 1 room type
- Bắt buộc: Có
- Ghi chú: Clone room là nên có

## Bài Toán Nghiệp Vụ

Supplier cần tạo ít nhất một room type đủ chuẩn để tiếp tục bước pricing và đủ điều kiện request active. Nếu step này quá chậm hoặc lặp lại nhiều thao tác tay, user dễ bỏ dở onboarding.

## Mục Tiêu

- Cho phép tạo ít nhất một room type hợp lệ
- Giảm thời gian nhập liệu bằng clone room
- Đảm bảo dữ liệu sức chứa, tiện ích và ảnh phòng nhất quán

## Rủi Ro Chính

- Room data thiếu chuẩn gây lỗi downstream cho rate hoặc booking
- Validation sức chứa không rõ làm sai inventory
- Không có clone room làm UX chậm với hotel có nhiều hạng phòng tương tự
