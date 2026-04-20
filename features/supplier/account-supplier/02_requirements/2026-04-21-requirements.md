# Gói Yêu Cầu

## Tóm Tắt Phạm Vi

Module `account-supplier` hỗ trợ supplier đăng ký hoặc đăng nhập, đi qua bước verify cần thiết, được phân loại theo quy tắc nghiệp vụ, và được hệ thống auto-generate `Supplier ID`.

## Business Requirements

| ID | Yêu cầu | Lý do | Độ ưu tiên | Nguồn |
| --- | --- | --- | --- | --- |
| BR-01 | Hệ thống phải cho phép supplier mới đăng ký tài khoản và khởi tạo hồ sơ supplier. | Cần có entry point cho supplier mới. | Must Have | User input |
| BR-02 | Hệ thống phải cho phép supplier hiện hữu đăng nhập để truy cập lại vào hệ thống. | Cần có entry point cho supplier quay lại. | Must Have | User input |
| BR-03 | Hệ thống phải hỗ trợ verify supplier theo yêu cầu nghiệp vụ trước khi supplier đạt trạng thái sử dụng mục tiêu. | Cần kiểm soát tính hợp lệ của supplier. | Must Have | User input |
| BR-04 | Hệ thống phải phân loại supplier theo rule nghiệp vụ đã được xác nhận. | Cần quản lý supplier theo nhóm phù hợp. | Must Have | User input |
| BR-05 | Hệ thống phải auto-generate `Supplier ID` cho supplier hợp lệ mà không cần nhập tay. | Cần định danh chuẩn, giảm lỗi dữ liệu. | Must Have | User input |

## Functional Requirements

| ID | Yêu cầu | Actor | Trigger | Kết quả mong đợi | Độ ưu tiên |
| --- | --- | --- | --- | --- | --- |
| FR-01 | Cho phép supplier mới chọn loại supplier giữa `Chủ sở hữu/Quản lý khách sạn` và `Đối tác phân phối dịch vụ khách sạn`. | Supplier mới | Supplier bắt đầu `Sign up` | Loại supplier được ghi nhận để phục vụ onboarding. | Must Have |
| FR-02 | Auto-generate `Supplier ID` ở backend sau khi loại supplier được chọn theo rule đã xác nhận. | Hệ thống | Loại supplier được xác nhận | `Supplier ID` được tạo và gắn vào hồ sơ supplier. | Must Have |
| FR-03 | Cho phép supplier mới nhập email đăng nhập, họ tên, số điện thoại và mật khẩu khi đăng ký. | Supplier mới | Supplier chọn `Sign up` | Hệ thống ghi nhận dữ liệu đăng ký ban đầu. | Must Have |
| FR-04 | Hỗ trợ xác thực OTP qua điện thoại hoặc verify email, đồng thời yêu cầu đồng ý điều khoản sử dụng trước khi hoàn tất đăng ký. | Supplier mới | Supplier gửi đăng ký | Tài khoản chỉ hoàn tất khi verify và chấp thuận điều khoản hợp lệ. | Must Have |
| FR-05 | Cho phép supplier hiện hữu đăng nhập bằng email và password hợp lệ. | Supplier hiện hữu | Supplier chọn `Log in` | Supplier truy cập được vào trạng thái phù hợp của tài khoản. | Must Have |
| FR-06 | Hỗ trợ `Quên mật khẩu` cho supplier hiện hữu. | Supplier hiện hữu | Supplier chọn `Forgot password` | User có thể khởi động luồng khôi phục password. | Should Have |
| FR-07 | Sau khi đăng nhập lại, hiển thị hồ sơ dở dang và CTA `Tiếp tục` để resume onboarding. | Supplier hiện hữu | Login success từ lần thứ hai | User thấy resume state và tiếp tục đúng flow. | Must Have |
| FR-08 | Ghi nhận và hiển thị trạng thái verify của supplier trong từng giai đoạn xử lý. | Supplier, Ops | Hồ sơ supplier được tạo hoặc được xử lý verify | Trạng thái verify rõ ràng, hỗ trợ theo dõi và xử lý tiếp. | Must Have |
| FR-09 | Hỗ trợ verify supplier theo các rule và dữ liệu bắt buộc đã được xác nhận. | Ops, hệ thống, supplier | Supplier gửi hồ sơ hoặc đến bước verify | Supplier được đánh dấu `Verified`, `Pending`, hoặc trạng thái tương đương theo rule. | Must Have |
| FR-10 | Phân loại supplier theo rule nghiệp vụ hoặc ma trận classification đã được xác nhận. | Hệ thống, Ops | Supplier đạt điều kiện classification | Supplier được gán classification phù hợp. | Must Have |
| FR-11 | Không cho supplier tự nhập hoặc tự sửa `Supplier ID`. | Supplier | Supplier xem hoặc cập nhật hồ sơ | `Supplier ID` chỉ hiển thị dạng read-only hoặc không cho chỉnh sửa. | Must Have |
| FR-12 | Hiển thị thông báo hoặc trạng thái phù hợp cho các trường hợp đăng ký thành công, verify pending, verify failed, hoặc classification completed. | Supplier | Có thay đổi trạng thái chính trong lifecycle | Supplier hiểu bước tiếp theo hoặc trạng thái hiện tại. | Should Have |
| FR-13 | Kiểm soát đăng ký trùng trên các trường định danh chính nếu rule duplicate check được xác nhận. | Hệ thống | Supplier gửi đăng ký mới | Giảm nguy cơ tạo nhiều hồ sơ cho cùng một supplier. | Should Have |

## Non-Functional Requirements

| ID | Nhóm | Yêu cầu | Chỉ số | Độ ưu tiên |
| --- | --- | --- | --- | --- |
| NFR-01 | Security | Thông tin đăng nhập và dữ liệu verify phải được bảo vệ theo chính sách bảo mật của hệ thống. | Không lộ credential hoặc dữ liệu nhạy cảm qua UI hoặc log thông thường. | Must Have |
| NFR-02 | Data integrity | `Supplier ID` phải duy nhất và ổn định sau khi được generate. | Không có trường hợp trùng `Supplier ID`; ID không đổi ngoài quy trình đặc biệt đã được kiểm soát. | Must Have |
| NFR-03 | Auditability | Các thay đổi trạng thái verify, classification, và `Supplier ID` phải có khả năng truy vết. | Có log hoặc lịch sử thay đổi đủ để audit. | Should Have |
| NFR-04 | Usability | Supplier phải hiểu được mình đang ở bước nào của quy trình. | Trạng thái và thông điệp xử lý rõ ràng, dễ hiểu. | Should Have |
| NFR-05 | Performance | Luồng đăng nhập và đăng ký phải phản hồi đủ nhanh để không gây drop-off sớm. | Ngưỡng cụ thể do product và engineering xác nhận. | Should Have |
| NFR-06 | Validation clarity | Email, số điện thoại, password strength và verify state phải có lỗi hoặc hướng dẫn rõ ràng. | User biết vì sao đăng ký hoặc đăng nhập chưa hoàn tất. | Must Have |

## Business Rules

| Rule ID | Phát biểu rule | Áp dụng cho | Nguồn | Ghi chú |
| --- | --- | --- | --- | --- |
| RULE-01 | Module phải hỗ trợ cả `Sign up` và `Log in`. | Account entry points | User input | Bắt buộc |
| RULE-02 | `Supplier ID` phải được generate tự động bởi hệ thống, duy nhất, và không do supplier nhập tay. | Supplier identifier | User input | Bắt buộc |
| RULE-03 | Supplier chỉ được xem là đã verify khi đã hoàn tất các bước xác minh bắt buộc và không được bỏ qua verify. | Verify process | BA interpretation | Cần xác nhận danh sách bước bắt buộc |
| RULE-04 | Classification phải bám theo rule hoặc ma trận do business xác nhận. | Supplier classification | User input | Không được gán tùy ý |
| RULE-05 | Nếu trigger generate `Supplier ID` chưa được chốt, hệ thống không được để người dùng tự nhập ID thay thế. | Supplier identifier | BA proposal | Tránh dữ liệu không chuẩn trong giai đoạn chưa chốt thiết kế |
| RULE-06 | Email phải là duy nhất. | Registration validation | BRD | Bắt buộc |
| RULE-07 | Số điện thoại phải hợp lệ. | Registration validation | BRD | Bắt buộc |
| RULE-08 | Password phải đạt độ mạnh tối thiểu theo chính sách đã xác nhận. | Password policy | BRD | Bắt buộc |

## Candidate User Stories

### US-01

Là supplier mới,
Tôi muốn đăng ký tài khoản và tạo hồ sơ supplier,
Để tôi có thể bắt đầu quá trình onboard vào hệ thống.

### US-02

Là supplier hiện hữu,
Tôi muốn đăng nhập vào hệ thống,
Để tôi tiếp tục xử lý hồ sơ hoặc sử dụng các chức năng được phép.

### US-03

Là business hoặc ops,
Tôi muốn supplier được verify và phân loại đúng,
Để dữ liệu supplier nhất quán và phục vụ đúng quy trình vận hành.

### US-04

Là hệ thống quản lý supplier,
Tôi muốn auto-generate `Supplier ID` cho supplier hợp lệ,
Để mỗi supplier có định danh chuẩn và không cần nhập tay.

## Acceptance Criteria

| AC ID | Story Ref | Acceptance Criteria |
| --- | --- | --- |
| AC-01 | US-01 | Given supplier mới chọn `Sign up`, when nhập đủ thông tin bắt buộc và gửi đăng ký, then hệ thống tạo account hoặc hồ sơ supplier ban đầu theo rule đã xác nhận. |
| AC-02 | US-01 | Given supplier mới chọn loại supplier, when xác nhận lựa chọn, then backend generate `Supplier ID` theo rule đã xác nhận. |
| AC-03 | US-01 | Given supplier mới gửi đăng ký, when email, số điện thoại, password và điều khoản đều hợp lệ, then hệ thống tiếp nhận đăng ký để đi vào verify. |
| AC-04 | US-01 | Given supplier mới chưa hoàn tất OTP hoặc verify email, when cố hoàn tất đăng ký, then hệ thống không cho bỏ qua verify. |
| AC-05 | US-02 | Given supplier hiện hữu có email và password hợp lệ, when chọn `Log in`, then supplier đăng nhập thành công và vào đúng trạng thái được phép. |
| AC-06 | US-02 | Given supplier quên mật khẩu, when chọn `Forgot password`, then hệ thống khởi động luồng khôi phục password theo chính sách đã xác nhận. |
| AC-07 | US-02 | Given supplier đăng nhập lại khi đã có hồ sơ dở dang, when login success, then hệ thống hiển thị hồ sơ dở dang và CTA `Tiếp tục`. |
| AC-08 | US-03 | Given hồ sơ supplier đi vào bước verify, when các kiểm tra bắt buộc hoàn tất, then trạng thái verify được cập nhật rõ ràng theo rule nghiệp vụ. |
| AC-09 | US-03 | Given supplier đủ điều kiện classification, when hệ thống hoặc ops xử lý classification, then supplier được gán đúng classification theo rule đã xác nhận. |
| AC-10 | US-04 | Given supplier đạt điều kiện generate ID, when trigger generate `Supplier ID` xảy ra, then hệ thống tự động tạo `Supplier ID` duy nhất và lưu vào hồ sơ supplier. |
| AC-11 | US-04 | Given supplier đã có `Supplier ID`, when supplier xem hoặc cập nhật hồ sơ, then `Supplier ID` không thể bị nhập tay hoặc chỉnh sửa bởi supplier. |
| AC-12 | US-01, US-03 | Given verify chưa hoàn tất hoặc thất bại, when supplier hoặc ops xem trạng thái hồ sơ, then hệ thống hiển thị trạng thái và hướng xử lý tiếp theo một cách rõ ràng. |
| AC-13 | US-01 | Given rule duplicate check được áp dụng, when supplier gửi đăng ký trùng với định danh đã tồn tại, then hệ thống chặn hoặc cảnh báo theo rule đã xác nhận. |

## Dependencies

- Rule xác thực đăng nhập và đăng ký
- Danh sách bước verify bắt buộc
- Ma trận classification của supplier
- Chính sách generate `Supplier ID`
- Rule duplicate check cho supplier
- Quyền của ops hoặc back-office nếu có xử lý verify thủ công
- Chính sách OTP hoặc verify email
- Chính sách forgot password

## Open Questions

- `Verify` có bao gồm manual approval hay chỉ xác minh tự động?
- Classification của supplier gồm những giá trị nào và ai là owner của rule này?
- Trigger generate `Supplier ID` là sau đăng ký, sau verify, hay sau approve?
- `Supplier ID` có format nghiệp vụ cụ thể hay chỉ cần unique key hiển thị?
- Supplier chưa verify có được đăng nhập và truy cập một phần hệ thống hay không?
- OTP qua phone và verify email là lựa chọn thay thế hay bắt buộc hỗn hợp theo từng kênh?
