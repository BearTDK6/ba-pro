# Tóm Tắt Dự Án

## Kiểm Soát Tài Liệu

- Domain: Supplier
- Feature: Rate & Allotment
- Prepared by: Codex
- Date: 2026-04-21
- Status: Draft
- Priority: Mandatory

## Đầu Vào Đã Xác Nhận

- Module: Rate & Allotment
- Mục tiêu: Tạo giá, cancellation, allotment
- Bắt buộc: Có
- Ghi chú: Surcharge và promotion là optional

## Bài Toán Nghiệp Vụ

Supplier cần cấu hình giá mở bán và booking mode một cách đơn giản nhưng đủ chính xác. Nếu không có rate hợp lệ, date range và cancellation policy đúng, hotel không thể mở bán thực tế.

## Mục Tiêu

- Tạo ít nhất một rate hợp lệ gắn với một room type
- Cho phép cấu hình cancellation policy không overlap
- Cho phép cấu hình allotment để xác định booking mode
- Giữ các phần season, surcharge, promotion ở mức optional
