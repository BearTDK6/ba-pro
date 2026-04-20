# Phác Thảo Giải Pháp

## Mục Tiêu

Thiết kế step `Hotel Setup` theo hướng nhập dữ liệu tối thiểu nhưng đủ chuẩn để tạo hoặc claim hồ sơ khách sạn và chuẩn bị cho các bước room, rate, payment và legal.

## Cấu Trúc Đề Xuất

1. Hotel Overview
2. Hotel Policy / Facilities / USP
3. Hotel Media Upload

## Ghi Chú UX

- Duplicate popup phải có 2 CTA rõ ràng: `Claim existing hotel` và `Chỉnh lại thông tin`.
- Map pin là thành phần bắt buộc của overview.
- Media upload nên hỗ trợ reorder, set cover, delete, retry.

## Quyết Định Cần Chốt

- Ngưỡng ảnh tối thiểu
- Rule duplicate matching
- Trigger tạo hoặc gắn `Hotel ID`
