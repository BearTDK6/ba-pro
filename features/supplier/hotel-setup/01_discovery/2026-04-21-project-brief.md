# Tóm Tắt Dự Án

## Kiểm Soát Tài Liệu

- Domain: Supplier
- Feature: Hotel Setup
- Prepared by: Codex
- Date: 2026-04-21
- Status: Draft
- Priority: Mandatory

## Đầu Vào Đã Xác Nhận

- Module: Hotel Setup
- Mục tiêu: Khởi tạo hồ sơ khách sạn
- Bắt buộc: Có
- Ghi chú: Duplicate check, map pin, image upload

## Bài Toán Nghiệp Vụ

Supplier cần một luồng rõ ràng để tạo hoặc claim hồ sơ khách sạn, khai báo thông tin nền tảng và upload media đủ chuẩn. Nếu thiếu bước này, dữ liệu khách sạn dễ bị trùng, thiếu chuẩn và không đủ điều kiện để mở bán.

## Mục Tiêu

- Tạo hoặc gắn hồ sơ khách sạn đúng với supplier
- Hạn chế tạo trùng khách sạn
- Thu thập đủ dữ liệu nền tảng cho downstream room, rate và legal review
- Tạo điều kiện để step được đánh dấu hoàn tất khi đủ dữ liệu tối thiểu

## In Scope

- Thông tin tổng quan khách sạn
- Duplicate check theo tên khách sạn tiếng Việt
- Claim hoặc link hotel hiện có
- Tạo `Hotel ID` mới hoặc gắn `Hotel ID` hiện có với `Supplier ID`
- Quy định chung, facilities, USP
- Upload ảnh hoặc video khách sạn
- Validation dữ liệu tối thiểu

## Out Of Scope

- Cấu hình giá, allotment, contact, payment
- Review pháp lý chi tiết
- Quản trị media nâng cao ngoài phạm vi onboarding

## Giả Định

- Duplicate check chạy khi user nhập tên khách sạn tiếng Việt
- Facilities có danh mục chuẩn dùng chung
- Có rule tối thiểu về số lượng ảnh và số lượng facilities

## Rủi Ro Chính

- Claim flow không rõ làm user tạo trùng hotel
- Upload media không có guideline rõ ràng làm hồ sơ thiếu chuẩn
- Map pin không chính xác làm ảnh hưởng booking và hiển thị

## Bước Tiếp Theo

- Xác nhận rule duplicate matching và claim workflow
- Xác nhận số lượng ảnh tối thiểu và facilities tối thiểu
- Xác nhận trigger tạo `Hotel ID`
