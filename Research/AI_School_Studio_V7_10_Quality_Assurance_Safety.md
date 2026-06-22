# AI School Studio V7.10
# Content Quality, Review & Safety

## 1. Mục tiêu

Đảm bảo output:
- Đúng kiến thức và phù hợp môn/khối.
- Có cấu trúc sư phạm rõ ràng.
- Không chứa đáp án mâu thuẫn hoặc bịa nguồn.
- An toàn và phù hợp môi trường giáo dục.
- Có thể kiểm tra và sửa theo từng section.

AI không thay thế trách nhiệm duyệt cuối của giáo viên.

---

## 2. Quality Dimensions

| Dimension | Trọng số |
|---|---:|
| Factual correctness | 30 |
| Alignment với nguồn và chủ đề | 20 |
| Grade appropriateness | 15 |
| Assessment/answer consistency | 15 |
| Pedagogical usefulness | 10 |
| Language/readability | 5 |
| Safety/copyright/privacy | 5 |

Quality score:
- 90-100: Ready for teacher review.
- 75-89: Hiển thị cảnh báo và điểm cần kiểm tra.
- <75: Không cho one-click export; yêu cầu regenerate hoặc sửa.
- Critical error: chặn export bất kể score.

---

## 3. Structured Generation

- Dùng schema cố định cho lesson, quiz, worksheet và answer key.
- Tách question ID và answer ID.
- Yêu cầu learning objective cho từng activity.
- Gắn source reference/section cho claim quan trọng.
- Không cho model tự khai báo `passed QA`.
- Validator độc lập với generation prompt.

---

## 4. Automated Checks

### Input

- File type/size/malware.
- OCR confidence.
- Subject/grade/topic confidence.
- PII/student data warning.
- Copyright/publication warning.

### Content

- Missing section.
- Duplicate question.
- Answer key mismatch.
- Multiple-choice có số đáp án bất thường.
- Numerical/unit consistency.
- Unsupported citation hoặc source reference.
- Reading level/grade mismatch.
- Unsafe, discriminatory hoặc adult content.
- Excessive verbatim similarity.

### Export

- Font tiếng Việt.
- Page/slide overflow.
- Đáp án không xuất hiện trong bản học sinh.
- Link/file mở được.
- Media duration và file size đúng giới hạn.

---

## 5. Subject-specific Checks

### Toán/STEM

- Recompute đáp án bằng deterministic code khi khả thi.
- Kiểm tra đơn vị, dấu, rounding và ký hiệu.
- Không dùng LLM làm nguồn duy nhất cho phép tính.

### Ngôn ngữ

- Kiểm tra chính tả và mức độ đọc.
- Phân biệt câu hỏi hiểu bài với câu hỏi chỉ chép lại.
- Kiểm tra đáp án chấp nhận nhiều cách diễn đạt khi cần.

### Lịch sử/Địa lý/Khoa học xã hội

- Gắn nguồn cho ngày tháng, tên riêng và số liệu.
- Cảnh báo claim không có trong tài liệu nguồn.
- Tránh trình bày vấn đề tranh luận như sự thật duy nhất.

### Voice

- Pronunciation dictionary cho tên riêng và ký hiệu.
- Preview đoạn ngắn trước render toàn bài.
- Cho giáo viên sửa cách đọc theo segment.

### Image/Video

- Không dựa vào chữ do image model tạo.
- Kiểm tra hình ảnh không phù hợp/trẻ em thật.
- Không dùng hình ảnh làm bằng chứng kiến thức.
- Gắn asset provenance.

---

## 6. Teacher Review UX

Review theo section:
- Source excerpt.
- Generated content.
- Quality warning.
- Edit.
- Regenerate section.
- Report issue.
- Approve.

Checklist trước export:
- Tôi đã kiểm tra mục tiêu bài học.
- Tôi đã kiểm tra đáp án.
- Tôi đã kiểm tra độ phù hợp với học sinh.
- Tôi hiểu đây là nội dung AI hỗ trợ.

Không dùng checklist để đẩy toàn bộ trách nhiệm hệ thống sang giáo viên; critical checks vẫn phải chạy tự động.

---

## 7. Issue Taxonomy

- factual_error
- answer_mismatch
- grade_mismatch
- source_mismatch
- missing_section
- language_error
- unsafe_content
- copyright_concern
- pii_exposure
- export_broken
- voice_pronunciation
- media_quality

Mỗi issue lưu:
- job/section/model/prompt version.
- severity.
- reporter.
- resolution.
- refund decision.
- regression test ID.

---

## 8. Severity và Response

### P0

- Lộ dữ liệu private.
- Nội dung nguy hiểm/người lớn nghiêm trọng.
- Trừ tiền/credit sai trên diện rộng.

Action:
- Dừng feature/model.
- Thông báo incident owner ngay.
- Điều tra và khắc phục trước khi mở lại.

### P1

- Đáp án sai nghiêm trọng.
- Nội dung bịa đặt có thể gây hại.
- Export hàng loạt bị hỏng.

Action:
- Chặn affected output.
- Refund.
- Fix trong 24 giờ theo mục tiêu nội bộ.

### P2/P3

- Lỗi diễn đạt, layout hoặc preference.
- Xử lý qua queue và regression backlog.

---

## 9. Evaluation Dataset

Trước beta, xây gold set tối thiểu:
- 20 bài tiểu học.
- 20 bài THCS.
- 10 bài THPT.
- Bao phủ Toán, Ngữ văn, Khoa học, Lịch sử/Địa lý và tiếng Anh.

Mỗi bài có:
- Source được phép sử dụng.
- Metadata chuẩn.
- Learning objectives.
- Quiz/worksheet/answer key chuẩn.
- Known failure cases.

Chạy evaluation khi:
- Đổi model.
- Đổi system prompt/schema.
- Đổi OCR/parser.
- Thêm subject/grade.

Không deploy nếu critical accuracy giảm hoặc cost tăng mà không có lợi ích đo được.

---

## 10. Quality Gates

Private beta:
- Schema success >= 99%.
- Answer consistency >= 98% trên gold set.
- Critical error < 1% reviewed package.
- Export success >= 99%.
- 100% P0/P1 tạo alert.

Public launch:
- 60% package được dùng sau tối đa hai vòng sửa.
- Refund vì nội dung < 5% paid jobs.
- Có regression suite cho top 20 issue phổ biến.
- Có reviewer/escalation owner.

---

## 11. Model Change Process

1. Ghi lý do đổi model/prompt.
2. Chạy gold set cũ và candidate.
3. So sánh quality, latency và actual cost.
4. Human blind review mẫu.
5. Canary 5-10% traffic.
6. Theo dõi issue/refund.
7. Roll forward hoặc rollback.

Không đổi model production chỉ vì benchmark marketing của provider.
