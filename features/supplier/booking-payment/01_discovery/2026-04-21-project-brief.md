# Tóm Tắt Dự Án

## Kiểm Soát Tài Liệu

- Domain: Supplier
- Feature: Booking & Payment
- Prepared by: Codex
- Date: 2026-04-21
- Status: Draft
- Priority: Mandatory

## Đầu Vào Đã Xác Nhận

- Module: Booking & Payment
- Mục tiêu: 3 contact + payment term + bank info
- Bắt buộc: Có
- Ghi chú: Điều kiện tối thiểu để request active

## Bài Toán Nghiệp Vụ

Supplier cần khai báo contact vận hành và thanh toán đủ chuẩn để hệ thống có thể gửi booking, thương mại và xử lý tài chính sau go-live. Thiếu thông tin này sẽ làm vận hành booking và thanh toán lỗi ngay từ đầu.

## Mục Tiêu

- Thu thập đủ 3 vai trò contact bắt buộc
- Thu thập payment term theo 2 lựa chọn cố định
- Thu thập thông tin nhận thanh toán và hóa đơn
- Chặn request active khi thiếu contact hoặc payment info
