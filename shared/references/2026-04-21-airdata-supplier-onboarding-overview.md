# Tổng Quan Onboarding Supplier AirData

## Mục Đích

Tài liệu tổng hợp phần dùng chung của BRD cho hệ thống Web/App Suppliers mở bán khách sạn trên AirData. Tài liệu này đóng vai trò nguồn tham chiếu chung cho BA, UI/UX, Dev, QA để tránh lặp lại ở từng feature.

## Tóm Tắt Sản Phẩm

Hệ thống cho phép supplier hoặc khách sạn tự phục vụ quy trình onboarding gồm:

- tạo account supplier
- khởi tạo hồ sơ khách sạn
- tạo phòng
- tạo giá và allotment
- khai báo contact vận hành và thanh toán
- upload hồ sơ pháp lý
- gửi yêu cầu kích hoạt mở bán

Thiết kế ưu tiên:

- số bước tối thiểu
- save draft và resume flow
- validation rõ ràng
- tách trải nghiệm Web và App

## Mục Tiêu Sản Phẩm

- Rút ngắn thời gian khởi tạo khách sạn
- Tăng tỷ lệ hoàn tất onboarding
- Chuẩn hóa dữ liệu đầu vào cho booking, price, allotment, payment và legal review
- Giảm lỗi khi go-live
- Hỗ trợ cả Web và App

## Non-Scope

- Channel manager hai chiều
- Revenue management nâng cao
- Hợp đồng điện tử
- Dynamic packaging
- Đa property một lần nhập
- Cấu hình tax hoặc fee phức tạp theo từng quốc gia
- AI content generation

## Nhóm Người Dùng

- Supplier là chủ sở hữu hoặc quản lý khách sạn
- Đối tác phân phối dịch vụ khách sạn
- Nội bộ gồm BDs, RSVN, Kế toán để review, yêu cầu bổ sung, kích hoạt mở bán và đối soát

## Kênh Triển Khai

### Web

- Wizard full-page
- Stepper ngang cố định ở đầu trang
- Phù hợp nhập nhiều dữ liệu và upload hàng loạt

### App

- Task checklist theo card
- Màn hình ngắn, CTA sticky ở cuối màn hình
- Tối ưu camera hoặc gallery, bottom sheet và quick pick

## Luồng Nghiệp Vụ Tổng Thể

1. Landing và bắt đầu
2. Đăng ký hoặc đăng nhập supplier
3. Khởi tạo khách sạn
4. Khởi tạo phòng
5. Tạo giá và allotment
6. Booking contact và thanh toán
7. Upload hồ sơ pháp lý và gửi Request Active

## Danh Sách Module

| Module | Mục tiêu |
| --- | --- |
| Landing | Giới thiệu lợi ích và hướng dẫn chuẩn bị hồ sơ |
| Account & Supplier | Đăng ký, đăng nhập, verify, phân loại supplier |
| Hotel Setup | Khởi tạo hồ sơ khách sạn |
| Room Setup | Tạo ít nhất 1 room type |
| Rate & Allotment | Tạo giá, cancellation, allotment |
| Booking & Payment | 3 contact, payment term, bank info |
| Legal Documents | Upload hồ sơ pháp lý, review summary, Request Active |
| Dashboard | Resume flow, theo dõi trạng thái, checklist thiếu |

## Danh Sách Màn Hình Đề Xuất

### Web

- `WEB-01` Landing / Introduction
- `WEB-02` Register / Verify
- `WEB-03` Login
- `WEB-04` Hotel Overview
- `WEB-05` Hotel Policy / Facilities / USP
- `WEB-06` Hotel Media Upload
- `WEB-07` Room Setup
- `WEB-08` Rate & Allotment
- `WEB-09` Booking Contact & Payment
- `WEB-10` Documents & Review Summary
- `WEB-11` Dashboard / Status

### App

- `APP-01` Home / Login
- `APP-02` Supplier Type
- `APP-03` Hotel Basic Info
- `APP-04` Facilities & USP
- `APP-05` Hotel Images
- `APP-06` Room Setup
- `APP-07` Rate Setup
- `APP-08` Policy & Allotment
- `APP-09` Contact & Payment
- `APP-10` Documents & Submit

## Success Metrics Dùng Chung

- Tỷ lệ hoàn tất onboarding từ account verified tới Request Active
- Thời gian trung bình từ đăng ký tới Request Active
- Tỷ lệ hồ sơ bị trả về do thiếu thông tin
- Tỷ lệ hotel activated thành công
- Số lượng room và rate trung bình trên mỗi hotel mới
