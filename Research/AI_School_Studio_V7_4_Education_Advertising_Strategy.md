# AI School Studio V7.4
# Education Advertising & Sponsored Credit Strategy

## 1. Mục tiêu

Tạo thêm doanh thu quảng cáo để:
- Trợ giá cho giáo viên Việt Nam.
- Tăng tỷ lệ dùng thử và quay lại hằng ngày.
- Tạo nguồn doanh thu ngoài credit trả phí.
- Kết nối thương hiệu giáo dục với đúng nhóm giáo viên.

Định vị:
- Đây là chương trình tài trợ giáo dục, không phải mạng quảng cáo đại trà.
- Chỉ nhận đối tác và sản phẩm liên quan trực tiếp đến giáo dục.
- Không bán dữ liệu cá nhân của giáo viên hoặc học sinh.
- Không để quảng cáo ảnh hưởng đến kết quả AI hoặc nội dung bài giảng.

---

## 2. Nguyên tắc sản phẩm

- Quảng cáo nhận thưởng phải hoàn toàn tự nguyện.
- Người dùng mua credit không bị ép xem quảng cáo.
- Mọi nội dung thương mại phải có nhãn `Được tài trợ` hoặc `Quảng cáo`.
- Không chèn quảng cáo vào file PDF, PPT hoặc MP4 xuất ra.
- Không đặt quảng cáo trong editor, trang thanh toán hoặc luồng thao tác quan trọng.
- Mỗi màn hình chỉ có tối đa một vị trí tài trợ.
- Chỉ cấp thưởng sau khi hệ thống xác nhận lượt xem hợp lệ.
- Tách promotional credit khỏi purchased credit.

Thông điệp ưu tiên:

> Nhận 1 credit miễn phí do đối tác giáo dục tài trợ.

Không dùng thông điệp gây áp lực như:

> Bạn phải xem quảng cáo để tiếp tục.

---

## 3. Danh mục quảng cáo

### Được chấp nhận

- Nhà xuất bản và sách giáo dục.
- Công cụ, phần mềm và nền tảng EdTech.
- Thiết bị dạy học và thiết bị trường học.
- Văn phòng phẩm.
- Khóa đào tạo, bồi dưỡng giáo viên.
- Trung tâm ngoại ngữ và tổ chức giáo dục uy tín.
- Hội thảo, cuộc thi và sự kiện giáo dục.
- Học liệu có bản quyền.

### Không chấp nhận

- Cá cược, cờ bạc hoặc trò chơi đổi thưởng.
- Tài chính rủi ro, vay nóng hoặc đầu tư thiếu minh bạch.
- Thực phẩm chức năng và tuyên bố sức khỏe chưa được kiểm chứng.
- Nội dung chính trị hoặc tuyên truyền không liên quan đến giáo dục.
- Sản phẩm người lớn hoặc nội dung không phù hợp môi trường trường học.
- Quảng cáo nhắm trực tiếp tới trẻ em.
- Sản phẩm vi phạm bản quyền hoặc sử dụng hình ảnh giáo viên/học sinh trái phép.

Platform có quyền từ chối hoặc dừng chiến dịch nếu nội dung làm giảm niềm tin của giáo viên.

---

## 4. Hình thức quảng cáo

### Sponsor Card

Một thẻ tài trợ nhẹ tại:
- Dashboard.
- Trang khám phá tài nguyên.
- Marketplace.
- Màn hình chờ render.

Sponsor Card có:
- Logo đối tác.
- Thông điệp ngắn.
- Nhãn `Được tài trợ`.
- Một CTA rõ ràng.
- Nút ẩn hoặc báo cáo quảng cáo.

### Rewarded Sponsored Credit

Luồng đề xuất:

1. Giáo viên bấm `Nhận 1 credit miễn phí`.
2. Hệ thống hiển thị nội dung tài trợ 15-30 giây.
3. Giáo viên xem đủ điều kiện hoặc hoàn tất tương tác hợp lệ.
4. Backend xác nhận completion event.
5. Hệ thống cộng 1 promotional credit.
6. Hiển thị thời điểm có thể nhận lượt tiếp theo.

Giới hạn mặc định:
- Tối đa 1 promotional credit/ngày/tài khoản.
- Có thể tăng lên 2/ngày cho chiến dịch đặc biệt nếu economics cho phép.
- Không tự động phát video khi người dùng chưa bấm nhận thưởng.

### Featured Marketplace

Đối tác hoặc creator trả phí để:
- Đưa học liệu lên vị trí nổi bật.
- Tài trợ một danh mục môn học.
- Quảng bá khóa đào tạo hoặc sự kiện giáo dục.

Nội dung tài trợ không được thay thế xếp hạng tự nhiên và phải có nhãn rõ ràng.

### Sponsored Campaign

Các chiến dịch lớn:
- Tặng credit theo môn học hoặc tỉnh/thành.
- Webinar dành cho giáo viên.
- Cuộc thi thiết kế bài giảng.
- Bộ template đồng thương hiệu.
- Chương trình trải nghiệm công cụ giáo dục.

---

## 5. Promotional Credit

Promotional credit phải có ledger riêng.

Quy tắc:
- Ưu tiên tiêu promotional credit trước purchased credit.
- Chỉ dùng cho phân tích, quiz, worksheet và Teacher Notes.
- Có thể dùng cho Text Lesson Package nếu ngân sách chiến dịch cho phép.
- Không dùng cho Kling, Wan, Veo hoặc video cao cấp.
- Không chuyển nhượng, quy đổi tiền hoặc trả cho creator.
- Hết hạn sau 7-30 ngày tùy chiến dịch.
- Mỗi credit phải liên kết với `campaign_id` và `sponsor_id`.

Mục tiêu giá vốn:
- 100-250đ cho mỗi promotional credit đã sử dụng.
- Credit hết hạn hoặc chưa sử dụng không phát sinh chi phí API.

---

## 6. Kinh tế chiến dịch

Chỉ ưu tiên hợp đồng trực tiếp với đối tác giáo dục. Không phụ thuộc vào mạng banner đại trà trong giai đoạn đầu.

### Giá bán thử nghiệm

| Gói | Completion hợp lệ | Giá đề xuất | Doanh thu/completion |
|---|---:|---:|---:|
| Pilot | 10.000 | 4-6 triệu đồng | 400-600đ |
| Growth | 30.000 | 10-15 triệu đồng | 333-500đ |
| Scale | 100.000 | 30-45 triệu đồng | 300-450đ |

Giá cuối cùng phụ thuộc vào:
- Mức độ nhắm đúng môn học hoặc nhóm giáo viên.
- Định dạng video, landing page hoặc khảo sát.
- Cam kết số completion.
- Thời gian và vị trí hiển thị.
- Báo cáo và yêu cầu sáng tạo nội dung.

### Ví dụ Pilot

Giả định:
- 10.000 completion.
- Hợp đồng 5 triệu đồng.
- 10.000 promotional credit được cấp.
- 80% credit thực sự được dùng.
- Giá vốn trung bình 200đ/credit đã dùng.
- Chi phí vận hành và chống gian lận 500.000đ.

Kết quả:

```text
Doanh thu                  = 5.000.000đ
Giá vốn credit             = 10.000 x 80% x 200đ = 1.600.000đ
Vận hành/chống gian lận    = 500.000đ
Lãi gộp chiến dịch         = 2.900.000đ
Biên gộp                   = 58%
```

### Điều kiện nhận hợp đồng

```text
Expected gross profit = contract revenue
                      - expected redeemed credit cost
                      - creative/operation cost
                      - payment/tax allocation
                      - fraud reserve
```

Chỉ nhận chiến dịch khi:
- Biên gộp dự kiến ít nhất 40%.
- Doanh thu trên mỗi completion lớn hơn giá vốn kỳ vọng ít nhất 2 lần.
- Có trần ngân sách và số promotional credit rõ ràng.

---

## 7. Chống gian lận

- Một tài khoản chỉ nhận thưởng một lần/ngày theo mặc định.
- Yêu cầu xác minh email; cân nhắc số điện thoại khi có dấu hiệu bất thường.
- Rate limit theo account, IP, device fingerprint và campaign.
- Không cấp thưởng nếu video bị bỏ qua hoặc completion callback không hợp lệ.
- Không cấp thưởng nhiều lần khi refresh hoặc gửi lại request.
- Dùng idempotency key cho reward transaction.
- Phát hiện nhiều tài khoản trên cùng thiết bị hoặc hành vi tự động.
- Tạm khóa rewarded ads thay vì khóa tài khoản chính khi nghi ngờ gian lận.
- Dành fraud reserve trong ngân sách chiến dịch.

Không dùng biện pháp fingerprint vượt quá nhu cầu bảo mật hoặc trái với chính sách quyền riêng tư.

---

## 8. Dữ liệu và kiến trúc

### Core Tables

- Sponsors
- AdCampaigns
- AdCreatives
- AdPlacements
- AdImpressions
- AdCompletions
- PromotionalCreditLedger
- AdFraudSignals

### Trường dữ liệu quan trọng

AdCampaigns:
- sponsor_id
- status
- start_at
- end_at
- contracted_completions
- budget_vnd
- reward_credit_per_completion
- max_rewards_per_user_per_day
- eligible_actions
- reward_expiry_days

AdCompletions:
- campaign_id
- user_id
- impression_id
- idempotency_key
- completed_at
- verification_status
- reward_transaction_id
- estimated_reward_cost_vnd

Không gửi cho đối tác:
- Nội dung tài liệu giáo viên tải lên.
- Thông tin học sinh.
- Prompt, bài giảng hoặc dữ liệu riêng tư.
- Email, số điện thoại hoặc danh tính cá nhân nếu chưa có đồng ý rõ ràng.

---

## 9. Quy trình vận hành

1. Kiểm tra đối tác và ngành hàng.
2. Duyệt nội dung, landing page và quyền sử dụng hình ảnh.
3. Tính economics và đặt trần ngân sách.
4. Ký hợp đồng và nhận tối thiểu 50% thanh toán trước.
5. Tạo campaign, creative và reward pool.
6. Chạy pilot trên nhóm người dùng nhỏ.
7. Kiểm tra completion, fraud và chi phí credit.
8. Mở rộng chiến dịch nếu đạt KPI.
9. Gửi báo cáo và đối soát.
10. Xóa hoặc lưu dữ liệu theo chính sách retention.

---

## 10. KPI

### Sản phẩm

- Reward opt-in rate.
- Completion rate.
- Promotional credit redemption rate.
- D1/D7 retention của người nhận credit.
- Tỷ lệ chuyển từ promotional sang purchased credit.
- Tỷ lệ ẩn hoặc báo cáo quảng cáo.

### Tài chính

- Revenue per valid completion.
- Redeemed credit cost per completion.
- Fraud-adjusted gross margin.
- Sponsor renewal rate.
- Revenue per 1.000 active teachers.

### Guardrails

- Biên gộp chiến dịch >= 40%.
- Fraud rate < 5% completion.
- Tỷ lệ báo cáo quảng cáo < 1% impression.
- Không làm giảm paid conversion hoặc lesson completion rate quá 5%.

---

## 11. Lộ trình triển khai

### Phase A - Sponsor Card Pilot

Điều kiện:
- Có tối thiểu 100 giáo viên active.
- Có một đối tác giáo dục phù hợp.

Triển khai:
- Một vị trí trên dashboard.
- Theo dõi impression và click.
- Chưa cấp rewarded credit.

### Phase B - Rewarded Credit Pilot

Triển khai:
- 1 promotional credit/ngày.
- Chỉ dùng cho tác vụ text giá vốn thấp.
- Giới hạn 1.000-10.000 completion.
- Đối soát thủ công mỗi tuần.

### Phase C - Direct Sponsorship Platform

Triển khai:
- Dashboard cho sponsor.
- Campaign budget và completion cap.
- Báo cáo tự động.
- Featured Marketplace và sponsored campaign.

Không mở self-service advertising trước khi quy trình duyệt, chống gian lận và đối soát đã ổn định.

---

## 12. Điều khoản hợp đồng tối thiểu

- Phạm vi ngành hàng và nội dung được phép.
- Vị trí, thời gian và số completion/impression cam kết.
- Giá trị hợp đồng và lịch thanh toán.
- Thanh toán trước tối thiểu 50%.
- Không cam kết doanh số nếu chỉ bán nhận diện hoặc traffic.
- Quyền từ chối hoặc dừng creative không phù hợp.
- Quy định dữ liệu, quyền riêng tư và bảo mật.
- Quy trình xử lý click/completion gian lận.
- Quyền sử dụng logo, hình ảnh và nội dung.
- Phương pháp báo cáo và đối soát.
- Chính sách hủy, hoàn ngân sách và sự kiện bất khả kháng.

---

## 13. Quyết định chiến lược

Mô hình ưu tiên:

```text
Direct Education Sponsor
        ↓
Optional Rewarded Ad
        ↓
Restricted Promotional Credit
        ↓
Teacher Tries Low-cost Features
        ↓
Conversion to Purchased Credit
```

Không tối ưu theo số quảng cáo hiển thị. Tối ưu theo:
- Giá trị tài trợ thực nhận.
- Chi phí promotional credit đã sử dụng.
- Tỷ lệ giáo viên quay lại và mua credit.
- Niềm tin lâu dài của cộng đồng giáo viên.
