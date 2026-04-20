# Business Rules Dùng Chung Cho Onboarding Supplier

## Điều Kiện Tối Thiểu Để Request Active

Supplier chỉ được gửi `Request Active` khi đạt đủ các điều kiện sau:

- account supplier đã verify
- có dữ liệu khách sạn tối thiểu gồm tên, địa chỉ, map pin, sao, mô tả ngắn, facilities tối thiểu, ảnh tổng quan tối thiểu
- có ít nhất 1 room type hợp lệ
- có ít nhất 1 rate active hợp lệ, có date range và cancellation policy
- có đủ 3 contact với vai trò `RSVN`, `Sales`, `Kế toán`
- có payment term và bank info
- có ít nhất 1 hồ sơ pháp lý hợp lệ

## Duplicate Hotel Rule

- Không cho tạo trùng khách sạn khi hệ thống đã có hotel tương ứng
- Khi có nghi ngờ trùng theo tên khách sạn, hệ thống phải gợi ý hotel hiện có
- Supplier phải có 2 hướng xử lý rõ ràng: `claim existing hotel` hoặc quay lại chỉnh tên

## Booking Mode Rule

- Không có allotment thì booking mode mặc định là `On Request`
- Có allotment thì booking mode mặc định là `Instant Confirm`
- UI phải giúp supplier hiểu booking mode đang được áp dụng

## Room Capacity Rule

- Sức chứa tối đa của phòng phải lớn hơn hoặc bằng sức chứa tiêu chuẩn

## Cancellation Policy Rule

- Cho phép nhiều điều kiện hủy nối tiếp nhau
- Không cho overlap
- Không để hở khoảng thời gian nếu policy yêu cầu phủ toàn bộ timeline

## Save Draft Và Resume Flow

- Mọi step đều có `Lưu nháp`
- Hệ thống auto-save định kỳ
- Hệ thống auto-save khi user chuyển step
- Từ lần đăng nhập thứ hai phải hiển thị thông tin resume gồm `Hotel ID`, tên khách sạn, trạng thái khởi tạo, phần trăm hoàn thành và CTA tiếp tục

## Progress Model

### Trạng Thái Step

- `Not Started`
- `In Progress`
- `Incomplete`
- `Completed`

### Trạng Thái Onboarding Chính

- `Draft`
- `Incomplete`
- `Pending Documents`
- `Pending Review`
- `Need Revision`
- `Approved`
- `Activated`
- `Rejected`
- `Suspended`

## UX Rules Dùng Chung

- Web bắt buộc có progress bar hoặc stepper ở top page
- App ưu tiên checklist theo card kết hợp progress summary và phần trăm hoàn thành
- Trước `Request Active` phải có màn `Review Summary`
- Error message phải có ở field level và error summary ở đầu màn khi submit fail
- Phải có loading state, empty state, success state, revision state trong wireframe chi tiết
