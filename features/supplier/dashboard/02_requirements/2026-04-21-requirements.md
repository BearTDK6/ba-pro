# Gói Yêu Cầu

## Tóm Tắt Phạm Vi

Module `dashboard` hiển thị header summary, checklist hoàn tất, CTA điều hướng nhanh và notification center để supplier resume flow và theo dõi trạng thái onboarding.

## Business Requirements

| ID | Yêu cầu | Lý do | Độ ưu tiên | Nguồn |
| --- | --- | --- | --- | --- |
| BR-01 | Hệ thống phải hiển thị thông tin tổng quan của hotel onboarding sau khi supplier đăng nhập lại. | Cần giúp supplier biết đang ở đâu. | Must Have | BRD |
| BR-02 | Hệ thống phải hỗ trợ resume flow về đúng phần còn thiếu. | Cần giảm ma sát khi quay lại onboarding. | Must Have | BRD |
| BR-03 | Hệ thống phải hiển thị notification về yêu cầu bổ sung, trạng thái review và kích hoạt. | Cần giảm phụ thuộc vào email ngoài hệ thống. | Must Have | BRD |
| BR-04 | Hệ thống phải hiển thị % hoàn thành và step status phù hợp. | Cần giúp supplier hiểu tiến độ. | Must Have | BRD |

## Functional Requirements

| ID | Yêu cầu | Actor | Trigger | Kết quả mong đợi | Độ ưu tiên |
| --- | --- | --- | --- | --- | --- |
| FR-01 | Hiển thị `Tên khách sạn`, `Hotel ID`, `Supplier type`, trạng thái onboarding và `% hoàn thành` tại header summary. | Supplier | Supplier vào dashboard | User thấy tổng quan tức thì. | Must Have |
| FR-02 | Hiển thị checklist các mục còn thiếu như room, rate, contact, payment, document. | Supplier | Supplier vào dashboard | User biết cần quay lại đâu. | Must Have |
| FR-03 | Cung cấp CTA chính như `Tiếp tục hoàn tất`, `Xem booking`, `Xem thanh toán`, `Upload thêm hồ sơ` tùy trạng thái. | Supplier | Supplier vào dashboard | User điều hướng nhanh tới hành động phù hợp. | Must Have |
| FR-04 | Hiển thị notification center cho yêu cầu bổ sung từ admin, trạng thái review và thông báo kích hoạt. | Supplier | Có notification mới hoặc user vào dashboard | User theo dõi trạng thái mà không lệ thuộc email. | Must Have |
| FR-05 | Khi đăng nhập lại từ lần thứ hai, hiển thị `Hotel ID`, tên khách sạn, trạng thái khởi tạo, `% hoàn thành` và CTA tiếp tục. | Supplier | Login success | User có resume card hoặc summary rõ ràng. | Must Have |
| FR-06 | Hiển thị trạng thái onboarding chính như `Draft`, `Incomplete`, `Pending Documents`, `Pending Review`, `Need Revision`, `Approved`, `Activated`, `Rejected`, `Suspended`. | Supplier | User xem dashboard | Trạng thái hiển thị đúng theo lifecycle. | Must Have |

## Non-Functional Requirements

| ID | Nhóm | Yêu cầu | Chỉ số | Độ ưu tiên |
| --- | --- | --- | --- | --- |
| NFR-01 | Usability | Dashboard phải cho biết bước tiếp theo chỉ trong một lần nhìn. | Supplier xác định được CTA ưu tiên và mục thiếu. | Must Have |
| NFR-02 | Performance | Dashboard tải nhanh đủ để làm entry point sau login. | Theo mục tiêu hiệu năng chung. | Should Have |
| NFR-03 | Responsive | Web và app phải trình bày tiến độ phù hợp từng channel. | Web ưu tiên header summary và checklist; app ưu tiên card resume và progress summary. | Must Have |

## Business Rules

| Rule ID | Phát biểu rule | Áp dụng cho | Nguồn | Ghi chú |
| --- | --- | --- | --- | --- |
| RULE-01 | Dashboard phải hiển thị `% hoàn thành` và trạng thái step hoặc onboarding đủ để user resume flow. | Progress model | BRD | Bắt buộc |
| RULE-02 | Login từ lần 2 phải hiển thị thông tin resume gồm `Hotel ID`, tên khách sạn, trạng thái khởi tạo, `% hoàn thành`, CTA tiếp tục. | Resume flow | BRD | Bắt buộc |
| RULE-03 | Notification center phải phản ánh các yêu cầu bổ sung, trạng thái review và kích hoạt. | Notification | BRD | Bắt buộc |

## Candidate User Stories

### US-01

Là supplier quay lại hệ thống,
Tôi muốn thấy tiến độ và phần còn thiếu ngay sau login,
Để tôi tiếp tục onboarding nhanh chóng.

### US-02

Là supplier,
Tôi muốn nhận notification về review và kích hoạt,
Để tôi không bỏ lỡ yêu cầu bổ sung từ admin.

## Acceptance Criteria

| AC ID | Story Ref | Acceptance Criteria |
| --- | --- | --- |
| AC-01 | US-01 | Given supplier đăng nhập lại, when dashboard hiển thị, then user thấy `Hotel ID`, tên khách sạn, trạng thái và `% hoàn thành` cùng CTA tiếp tục. |
| AC-02 | US-01 | Given một hoặc nhiều step còn thiếu, when user xem checklist, then hệ thống chỉ rõ mục thiếu như room, rate, contact, payment hoặc document. |
| AC-03 | US-01 | Given user bấm CTA chính trên dashboard, when điều hướng xảy ra, then user được đưa tới đúng khu vực cần thao tác tiếp. |
| AC-04 | US-02 | Given có notification về review hoặc revision, when user vào dashboard, then notification center hiển thị nội dung và trạng thái liên quan. |
| AC-05 | US-01 | Given trạng thái onboarding thay đổi, when dashboard được tải lại, then trạng thái mới được phản ánh đúng theo lifecycle đã định nghĩa. |

## Dependencies

- Progress model và status model dùng chung
- Notification source từ review hoặc admin flow
- Mapping CTA theo trạng thái onboarding

## Open Questions

- `Xem booking` và `Xem thanh toán` ở phase này có dẫn tới module thật hay chỉ placeholder?
- Notification center có cần phân loại unread hoặc read trong phase 1 không?
