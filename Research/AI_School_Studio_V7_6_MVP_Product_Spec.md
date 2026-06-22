# AI School Studio V7.6
# MVP Product Specification

## 1. Product Goal

Giúp giáo viên Việt Nam biến PDF hoặc ảnh bài học thành bộ bài dạy có thể chỉnh sửa trong dưới 5 phút.

Giá trị cốt lõi:
- Giảm thời gian chuẩn bị bài.
- Tạo đầu ra dùng ngay thay vì một đoạn chat dài.
- Giữ giáo viên trong vòng kiểm duyệt cuối cùng.
- Giá đủ thấp để mua theo từng bài.

---

## 2. Primary User

Giáo viên phổ thông Việt Nam:
- Chuẩn bị bài mới hằng tuần.
- Có PDF hoặc ảnh tài liệu đầu vào.
- Dùng Word/PowerPoint nhưng không muốn học prompt engineering.
- Cần nội dung bám đúng môn, khối và thời lượng tiết học.

Secondary User:
- Tổ trưởng chuyên môn.
- Trung tâm ngoại ngữ/STEM.
- Trường mua shared credit pool.

---

## 3. Hero Workflow

```text
Upload PDF/Image
        ↓
Confirm Subject/Grade/Topic
        ↓
Choose Lesson Duration and Output
        ↓
Generate Editable Lesson Package
        ↓
Teacher Review by Section
        ↓
Export PDF/PPT/DOCX-compatible content
```

Lesson Package MVP:
- Lesson plan.
- Slide outline.
- Quiz/assessment và đáp án.
- Worksheet và đáp án.
- Teacher Notes/hoạt động trên lớp.

Optional paid add-on:
- Voice 5 phút.
- Template motion video.
- Một clip Veo Lite.

---

## 4. MVP Scope

### Must Have

- Đăng ký, đăng nhập và hồ sơ giáo viên.
- Upload PDF và ảnh.
- OCR/extract text.
- Xác nhận môn, khối, chủ đề và thời lượng.
- Tạo năm đầu ra core.
- Chỉnh sửa từng section.
- Regenerate từng section, không tạo lại toàn bộ package.
- Credit estimate trước khi chạy.
- Credit ledger và hoàn credit khi job lỗi.
- Review checklist trước export.
- Export PDF và nội dung tương thích PowerPoint.
- Cost tracking cho mỗi job.
- Thông báo lưu trữ miễn phí 7 ngày và ngày hết hạn.
- Tải xuống project trước khi hết hạn.
- Grace period 3 ngày khi không gia hạn.

### Should Have

- Lưu template theo giáo viên.
- Voice 5 phút.
- Export PPTX trực tiếp.
- Asset Library nội bộ.
- Cache theo source hash.
- Chia sẻ read-only link.

### Not in MVP

- Marketplace mở.
- Self-service advertising.
- TeacherGPT.
- Knowledge Graph toàn quốc.
- Fine-tuning/VietnamEduLM.
- Kling/Wan/Veo Fast mặc định.
- Student account và student analytics.
- Word/PPT upload nếu làm trễ luồng PDF/ảnh.

---

## 5. Product Decisions

- PDF/ảnh là input ưu tiên; Word/PPT vào phase sau.
- Text Lesson Package là sản phẩm core.
- Video không phải Hero Feature cho đến khi validation chứng minh ngược lại.
- Người dùng xem preview trước khi phát sinh render video.
- Mỗi section có source reference để giáo viên kiểm tra.
- Không tự động đưa nội dung người dùng vào marketplace hoặc training.

---

## 6. User Stories

### Upload

Là giáo viên, tôi muốn tải PDF/ảnh và thấy hệ thống nhận diện môn, khối, bài để sửa trước khi tạo.

Acceptance:
- Báo rõ trang lỗi hoặc không đọc được.
- Không gọi generation API trước khi xác nhận metadata.
- Hiển thị ước tính credit.

### Generate

Là giáo viên, tôi muốn chọn đầu ra và thời lượng để không trả tiền cho phần không cần.

Acceptance:
- Có checkbox cho từng output.
- Hiển thị credit trước khi xác nhận.
- Không trừ credit hai lần khi retry request.

### Review

Là giáo viên, tôi muốn sửa/regenerate từng phần và xem nguồn để giảm rủi ro sai kiến thức.

Acceptance:
- Chỉnh sửa trực tiếp.
- Regenerate theo section.
- Lưu version gần nhất.
- Báo lỗi theo section.

### Export

Là giáo viên, tôi muốn xuất tài liệu dễ sửa bằng công cụ quen thuộc.

Acceptance:
- PDF không lỗi font tiếng Việt.
- Slide outline có cấu trúc rõ ràng.
- Đáp án tách khỏi bản phát cho học sinh.

### Storage

Là giáo viên, tôi muốn biết project được giữ đến ngày nào và tải xuống/gia hạn trước khi bị xóa.

Acceptance:
- Hiển thị expiry date trên project và dashboard.
- Thông báo ngày 5, 6, 7 và trước khi xóa.
- Auto-renew tắt mặc định.
- Hiển thị dung lượng, số credit và chu kỳ 30 ngày trước opt-in.
- Không đủ credit chuyển sang grace period 3 ngày, không trừ âm.
- Sau grace period chỉ xóa media nặng; dữ liệu lesson nhẹ tuân theo retention policy.

---

## 7. Non-functional Requirements

- P95 thao tác UI thông thường < 2 giây.
- Hiển thị progress cho job dài.
- Job generation có idempotency key.
- Upload mã hóa khi truyền và lưu private mặc định.
- Có timeout, retry cap và cost cap.
- Log không chứa toàn bộ tài liệu hoặc dữ liệu học sinh.
- Có audit trail cho credit và export.
- Storage renewal/deletion scheduler phải idempotent.
- Shared/cache asset chỉ bị xóa khi không còn reference.

---

## 8. Eight-week Delivery Plan

### Week 1-2

- Authentication, teacher profile.
- Credit ledger skeleton.
- PDF/image upload và private storage.

### Week 3

- OCR/extraction.
- Subject/grade/topic confirmation.
- Source hashing và analysis cache.

### Week 4

- Lesson planner.
- Structured output schema.
- Model routing và cost estimation.

### Week 5

- Quiz, worksheet, answer keys.
- Teacher Notes và activities.
- Section-level regeneration.

### Week 6

- Review UI.
- Quality checklist.
- PDF export và slide outline.

### Week 7

- Payment integration.
- Credit purchase/refund.
- Actual API cost tracking.

### Week 8

- Private beta 20 giáo viên.
- Fix quality/reliability issues.
- Concierge support và measurement.

Voice/template video chỉ vào sprint nếu core workflow đạt acceptance criteria trước Week 7.

---

## 9. Launch Gates

Beta đạt yêu cầu khi:
- 20 giáo viên tạo ít nhất một lesson.
- 80% paid jobs hoàn thành không cần hỗ trợ kỹ thuật.
- 60% package được dùng sau tối đa hai vòng sửa.
- Median time-to-first-package < 5 phút.
- Basic text package contribution margin > 60%.
- Không có credit double-charge.
- Không có lỗi nghiêm trọng về quyền riêng tư/bản quyền.

Không mở rộng scope khi core completion rate < 70%.
