# AI School Studio V7.9
# Growth Metrics & Full Unit Economics

## 1. Mục tiêu

Phân biệt rõ:
- Doanh thu.
- Giá vốn API.
- Contribution margin.
- Chi phí vận hành.
- CAC và payback.
- Lợi nhuận thực tế.

Không dùng `số user x giá gói` làm projection lợi nhuận.

---

## 2. North Star Metric

`Weekly Used Lesson Packages`

Định nghĩa:
- Lesson Package đã hoàn thành.
- Người dùng đã review/export/share hoặc đánh dấu `Used`.
- Không tính package test, lỗi hoặc không mở lại.

North Star phản ánh giá trị giáo viên nhận được tốt hơn số generation hoặc số đăng ký.

---

## 3. Funnel

```text
Visitor
→ Signup
→ Upload
→ First Preview
→ First Completed Package
→ First Paid Credit
→ First Used Package
→ Repeat Purchase
```

Metrics:
- Visitor-to-signup.
- Signup-to-upload.
- Upload-to-completed-package.
- Time-to-first-value.
- Free-to-paid conversion.
- Paid-to-used-package.
- D7/D30 retention.
- 30/60-day repeat purchase.

---

## 4. Event Definitions

- `upload_completed`
- `metadata_confirmed`
- `generation_started`
- `generation_completed`
- `generation_failed`
- `section_regenerated`
- `package_reviewed`
- `package_exported`
- `package_marked_used`
- `credit_purchased`
- `credit_refunded`
- `support_requested`

Mỗi event có:
- user/workspace
- cohort
- source channel
- subject/grade
- package type
- credits charged
- actual cost
- timestamp

Không đưa private lesson content vào analytics event.

---

## 5. Full Job Economics

```text
Realized revenue
= credits charged x realized VND per credit

Variable cost
= LLM
 + OCR
 + TTS/image/video API
 + retry/failure allocation
 + payment fee allocation
 + storage/render allocation
 + support allocation
 + refund/chargeback allocation

Contribution profit
= realized revenue - variable cost

Contribution margin
= contribution profit / realized revenue
```

Promotional credit có doanh thu bằng 0 ở phía người dùng nhưng có thể được tài trợ bởi sponsor. Phải gắn revenue/cost theo campaign.

---

## 6. CAC và LTV

### CAC

```text
CAC = sales + marketing + promotion cost
      divided by new paying customers
```

Tách theo channel:
- Teacher referral.
- Facebook/Zalo community.
- Content/SEO.
- School sales.
- Sponsored credit.
- Marketplace creator acquisition.

### LTV

```text
Monthly contribution per payer
= monthly realized revenue - monthly variable cost

LTV
= monthly contribution per payer x expected paying lifetime
```

Không dùng gross revenue để tính LTV.

---

## 7. Target Metrics

### Validation

- 30 khách trả tiền.
- Repeat purchase 30 ngày >= 25%.
- Median reported time saved >= 60 phút/bài.
- Một Hero Feature được >= 40% chọn ưu tiên số một.

### Private Beta

- Upload-to-completed >= 80%.
- Median time-to-first-value < 5 phút.
- Free-to-paid >= 10% trong cohort có intent phù hợp.
- D30 payer retention >= 20%.
- Refund rate < 5% job trả phí.

### Unit Economics

- Basic/Plus contribution margin >= 60% trước CAC.
- Toàn hệ thống contribution margin >= 40%.
- Payment/support/refund variable overhead < 15% revenue.
- CAC payback < 3 tháng cho teacher self-serve.
- School CAC payback < 12 tháng.

### Reliability/Quality

- Paid job success >= 98% sau retry.
- Auto-refund accuracy = 100% job đủ điều kiện.
- Critical content error < 1% reviewed package.

---

## 8. Cohort Dashboard

Theo tuần đăng ký và channel:
- Signup.
- First package.
- First purchase.
- Credits purchased/consumed.
- Used packages.
- Repeat purchase.
- Revenue.
- Variable cost.
- Contribution margin.
- Support/refund.

Theo product:
- Text.
- Basic.
- Plus.
- Premium Lite.
- Kling/Wan/Veo add-on.

---

## 9. Pricing Experiments

Mỗi thí nghiệm cần:
- Hypothesis.
- Primary metric.
- Guardrail metric.
- Sample size/time window.
- Segment.
- Decision rule trước khi chạy.

Không chạy nhiều giá khác nhau thiếu audit hoặc gây bất công rõ ràng với cùng cohort.

Thí nghiệm đầu:
- Basic 9.900đ vs 14.900đ vs 19.900đ.
- Credit pack 49.000đ vs 99.000đ default selection.
- Pay-per-output vs bundled Lesson Package.

Guardrails:
- Refund.
- Support ticket.
- Used package rate.
- Repeat purchase.

---

## 10. Forecast Scenarios

Forecast theo payer và credit consumption:

| Scenario | Paying teachers | Revenue/payer/tháng | Contribution margin |
|---|---:|---:|---:|
| Conservative | 100 | 49.000đ | 40% |
| Base | 1.000 | 79.000đ | 50% |
| Growth | 5.000 | 99.000đ | 55% |

Đây là input giả định, không phải projection được chứng minh.

Mỗi scenario phải trừ:
- Fixed payroll.
- Software/observability.
- Legal/accounting.
- Content moderation.
- Sales and support.
- Tax.

---

## 11. Decision Cadence

Hằng ngày:
- Failed jobs.
- Cost spike.
- Negative credit balance.

Hằng tuần:
- Funnel.
- Cohort activation.
- Actual cost/model.
- Refund/support reasons.

Hằng tháng:
- Repeat purchase.
- Contribution margin.
- CAC/payback.
- Cash balance và prepaid API exposure.
- School pipeline.

Stop-loss:
- Tắt model khi contribution margin dưới 20% trong 100 job liên tiếp.
- Tạm dừng channel khi CAC payback vượt mục tiêu hai cohort liên tiếp.
- Không scale acquisition khi repeat purchase dưới 15%.
