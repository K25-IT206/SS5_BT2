# Bài 2: Phân biệt Acceptance Criteria và Definition of Done cho chức năng thanh toán ví điện tử

## Phần 1 - Phân tích

| Phát biểu | AC hay DoD | Đạt/Chưa đạt | Lý do |
|---|---|---|---|
| Đ1. Given số dư ví đủ trả cước, When khách xác nhận thanh toán, Then chuyến chuyển sang "Đã thanh toán" và ví bị trừ đúng số tiền cước. | AC | Đạt | Đây là tiêu chí riêng cho story thanh toán ví, có cấu trúc Given – When – Then và kết quả kiểm chứng được. |
| Đ2. Code được ít nhất 01 Developer khác review trước khi merge. | DoD | Đạt | Đây là tiêu chuẩn chất lượng chung cho mọi story, không riêng cho chức năng thanh toán ví; do Developers xây dựng và thực hiện. |
| Đ3. Thanh toán bằng ví phải nhanh, mượt, khách dùng thấy thích. | AC (nhưng chưa đạt/không kiểm chứng được ở dạng hiện tại) | Chưa đạt | Dạng hiện tại là cảm tính, thiếu số liệu và điều kiện đo được. Đây là tiêu chí riêng cho story nhưng chưa đủ để kiểm thử vì “nhanh”, “mượt”, “thích” không xác định được cách đo. |
| Đ4. Given số dư ví không đủ trả cước, When khách xác nhận thanh toán, Then hệ thống hiển thị "Số dư không đủ" và chuyến vẫn ở trạng thái "Chưa thanh toán". | AC | Đạt | Đây là một story-specific scenario rõ ràng, có Given/When/Then và kết quả cụ thể, có thể chuyển thành test case trực tiếp. |
| Đ5. Story thanh toán ví đã chạy trên staging (môi trường thử nghiệm) và không còn lỗi nghiêm trọng (Blocker/Critical). | DoD | Chưa đạt | Đây là mức chuẩn chất lượng chung cho mọi story; không nhất thiết là sự kiện riêng của một story. Nhưng ở đây chưa được chứng minh vì có lỗi nghiêm trọng đã xảy ra trong thực tế. |

## Phần 2 - Vá lỗi

### Viết lại Đ3 thành AC

Given khách đang thanh toán bằng ví RikkeiPay với kết nối mạng ổn định, When khách xác nhận thanh toán, Then hệ thống phải hiển thị kết quả thanh toán trong vòng 3 giây và không có lỗi treo màn hình hoặc chờ quá lâu.

### Viết lại Đ5 thành tiêu chí DoD chung

Mọi story phải được triển khai lên môi trường staging, chạy smoke test hoặc regression test cần thiết, và không còn lỗi ở mức Blocker/Critical trước khi đánh dấu hoàn thành.

### Kết luận

Story chưa xong vì Đ4 cho thấy số dư không đủ vẫn bị trừ tiền, và Đ5 chưa được đảm bảo (chưa có chứng cứ staging và không còn lỗi nghiêm trọng). Cần sửa logic thanh toán để chặn giao dịch khi số dư không đủ, bổ sung test case cho trường hợp không đủ tiền, và hoàn thành các tiêu chí DoD chung trước khi báo story đã xong.
