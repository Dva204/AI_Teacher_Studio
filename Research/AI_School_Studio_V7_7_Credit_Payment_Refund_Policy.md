# AI School Studio V7.7
# Credit, Payment & Refund Policy

## 1. Phạm vi

Tài liệu này định nghĩa product policy và yêu cầu hệ thống. Nội dung pháp lý, thuế và kế toán phải được luật sư/kế toán Việt Nam rà soát trước khi phát hành công khai.

---

## 2. Loại credit

### Purchased Credit

- Được mua bằng tiền.
- Hạn sử dụng đề xuất: 12 tháng kể từ ngày mua.
- Không chuyển nhượng hoặc đổi thành tiền mặt.
- Không dùng để trả cho creator trừ khi marketplace có policy riêng.

### Promotional Credit

- Được tặng khi đăng ký, referral hoặc quảng cáo tài trợ.
- Hạn sử dụng: 7-30 ngày.
- Chỉ dùng cho tác vụ được campaign cho phép.
- Không dùng cho video cao cấp, marketplace payout hoặc rút tiền.
- Liên kết với promotion/campaign nguồn.

### School Credit

- Thuộc credit pool của trường.
- Admin trường phân bổ hạn mức cho giáo viên.
- Không chuyển sang tài khoản cá nhân khi rời trường.
- Hạn dùng theo hợp đồng.

---

## 3. Chính sách lưu trữ bằng credit

### Thời gian miễn phí

- Mỗi project được lưu miễn phí toàn bộ trong 7 ngày kể từ khi generation hoàn tất.
- Hiển thị thời điểm hết hạn ngay trên project.
- Gửi thông báo vào ngày 5, ngày 6 và trước thời điểm hết hạn ngày 7.
- Người dùng luôn có thể tải xuống trước khi hết hạn.

### Gia hạn chủ động

Không tự động trừ credit nếu người dùng chưa bật `Tự động gia hạn` hoặc xác nhận gia hạn thủ công.

| Dung lượng project | Phí lưu trữ | Chu kỳ |
|---:|---:|---:|
| Dưới 250MB | 1 credit | 30 ngày |
| 250MB-1GB | 2 credit | 30 ngày |
| 1GB-5GB | 8 credit | 30 ngày |
| Trên 5GB | Báo giá theo dung lượng | 30 ngày |

Không tính phí theo section/ngày.

### Không đủ credit

- Không cho số dư âm.
- Project chuyển sang trạng thái `grace_period` trong 3 ngày.
- Trong grace period, người dùng được tải xuống, nạp credit và khôi phục.
- Không cho tạo thêm media/render mới trên project hết hạn.
- Sau 3 ngày không gia hạn, hệ thống xóa media nặng và intermediate artifacts.
- Giữ lesson JSON, quiz, worksheet, notes và metadata nhẹ nếu policy dữ liệu cho phép.
- Xóa hoàn toàn project khi người dùng yêu cầu hoặc theo retention policy.

### Tự động gia hạn

- Tắt mặc định.
- Người dùng phải opt-in rõ ràng theo từng project hoặc toàn tài khoản.
- Hiển thị số credit, dung lượng và ngày trừ tiếp theo.
- Gửi thông báo trước lần trừ ít nhất 24 giờ.
- Cho phép tắt bất kỳ lúc nào; việc tắt có hiệu lực từ chu kỳ tiếp theo.
- Mỗi renewal dùng idempotency key và tạo ledger entry riêng.

---

## 4. Thứ tự tiêu credit

1. Promotional credit sắp hết hạn và đủ điều kiện.
2. School credit nếu job thuộc workspace trường.
3. Purchased credit, ưu tiên lô hết hạn trước.

Hiển thị rõ nguồn credit được sử dụng trước khi xác nhận job.

---

## 5. Trừ và hoàn credit

### Trừ credit

- Reserve credit khi người dùng xác nhận.
- Capture credit khi job thành công theo định nghĩa output contract.
- Release reservation khi job bị hủy trước API call.
- Refund tự động khi lỗi thuộc hệ thống/provider.

### Không hoàn tự động

- Người dùng đổi ý sau khi output hợp lệ đã tạo.
- Người dùng sửa prompt và yêu cầu một generation mới.
- Input vi phạm policy hoặc không đủ quyền sử dụng.
- Kết quả không đúng sở thích nhưng đạt output contract; trường hợp chất lượng xử lý qua review policy.

### Hoàn do chất lượng

Hoàn toàn phần hoặc một phần khi:
- Output thiếu section đã mua.
- File export hỏng.
- Đáp án có lỗi nghiêm trọng được xác nhận.
- Provider tạo output rỗng hoặc không sử dụng được.

Mọi quality refund phải gắn `reason_code` và dùng để cải thiện QA.

---

## 6. Thanh toán và hoàn tiền

- Hiển thị giá cuối cùng, VAT/phí nếu có, trước thanh toán.
- Phát hành chứng từ/hóa đơn theo yêu cầu pháp luật và chính sách doanh nghiệp.
- Giao dịch trùng được hoàn về phương thức thanh toán ban đầu.
- Chargeback khóa phần credit chưa dùng của giao dịch liên quan trong lúc điều tra.
- Không hoàn tiền mặt cho promotional credit.
- Hoàn tiền purchased credit chưa dùng phải tuân theo điều khoản công khai và pháp luật áp dụng.

Không ghi nhận toàn bộ tiền nạp là lợi nhuận. Kế toán phải xác định thời điểm ghi nhận doanh thu đối với nghĩa vụ credit chưa sử dụng.

---

## 7. Thay đổi giá

- Giá gói credit đã mua không thay đổi hồi tố.
- Số credit cho một tác vụ có thể thay đổi khi giá API/tỷ giá thay đổi.
- Hiển thị giá mới trước khi người dùng xác nhận.
- Cân nhắc thông báo trước với thay đổi lớn hơn 10%.
- Không giảm số dư credit đã mua.

---

## 8. Ledger Requirements

Mọi thay đổi số dư phải là immutable ledger entry:
- transaction_id
- user_id/workspace_id
- credit_type
- amount
- balance_after
- source_type
- source_id
- expires_at
- idempotency_key
- reason_code
- created_at

Không cập nhật balance mà không tạo ledger entry.

Các event:
- purchase
- promotion_grant
- school_allocation
- reserve
- capture
- release
- refund
- expiry
- chargeback_hold
- manual_adjustment
- storage_reserve
- storage_renewal
- storage_refund

Manual adjustment yêu cầu audit log và quyền admin giới hạn.

---

## 9. Reliability Rules

- Payment webhook phải xác minh chữ ký.
- Mỗi webhook và job dùng idempotency key.
- Reconcile payment provider với ledger hằng ngày.
- Alert khi purchased credit balance âm.
- Alert khi reserve quá timeout.
- Có dead-letter queue cho webhook/job thất bại.
- Không capture credit nếu actual provider response chưa hợp lệ.
- Storage renewal job phải idempotent và không được trừ lặp.
- Reconcile storage subscription với credit ledger hằng ngày.

---

## 10. Customer-facing Summary

- Biết chính xác số credit trước khi tạo.
- Job lỗi hệ thống được hoàn tự động.
- Credit mua có hạn 12 tháng theo đề xuất.
- Credit khuyến mại có hạn ngắn và giới hạn tác vụ.
- Credit không phải tiền điện tử, không chuyển nhượng và không rút tiền.
- Lịch sử cộng/trừ/hoàn luôn xem được trong tài khoản.
- Project được lưu miễn phí 7 ngày; gia hạn cloud theo project/30 ngày.
- Không tự động trừ phí lưu trữ nếu chưa bật tự động gia hạn.
- Project không đủ credit có 3 ngày để tải xuống hoặc khôi phục.

---

## 11. Pre-launch Checklist

- Luật sư duyệt Terms, refund và consumer policy.
- Kế toán duyệt VAT, hóa đơn và revenue recognition.
- Test giao dịch thành công, thất bại, trùng và chargeback.
- Test reserve/capture/refund idempotency.
- Test hết hạn từng loại credit.
- Test promotional restriction.
- Test school allocation.
- Test free period, renewal, insufficient-credit grace period và deletion.
- Test storage auto-renew opt-in/opt-out và duplicate scheduler execution.
- Customer support có reason code và playbook.
