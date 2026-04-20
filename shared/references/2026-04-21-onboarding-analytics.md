# Event Tracking Và Analytics Cho Onboarding Supplier

## Mục Đích

Danh sách event dùng chung để theo dõi drop-off, conversion và chất lượng onboarding supplier.

## Event List

| Event | Ý nghĩa |
| --- | --- |
| `click_register` | User bắt đầu đăng ký |
| `verify_success` | Verify account hoặc supplier thành công |
| `login_success` | Đăng nhập thành công |
| `hotel_overview_saved` | Lưu phần tổng quan khách sạn |
| `duplicate_hotel_popup_shown` | Hệ thống hiển thị popup nghi ngờ trùng khách sạn |
| `map_pin_set` | User đã set map pin |
| `hotel_image_uploaded` | Upload ảnh khách sạn thành công |
| `room_created` | Tạo room thành công |
| `room_cloned` | Clone room thành công |
| `rate_created` | Tạo rate thành công |
| `cancellation_saved` | Lưu cancellation policy thành công |
| `allotment_saved` | Lưu allotment thành công |
| `contact_saved` | Lưu contact thành công |
| `payment_info_saved` | Lưu payment info thành công |
| `documents_uploaded` | Upload hồ sơ pháp lý thành công |
| `request_active_clicked` | User bấm Request Active |
| `request_active_success` | Request Active thành công |
| `revision_requested` | Admin yêu cầu bổ sung |
| `hotel_activated` | Hotel được activated |

## Gợi Ý Áp Dụng

- Mỗi module nên map event chính vào requirement hoặc NFR analytics
- Nên track thêm context tối thiểu gồm `supplier_id`, `hotel_id`, `channel`, `step`, `status`
- Event dùng để đo conversion theo step, thời gian hoàn tất và nguyên nhân drop-off
