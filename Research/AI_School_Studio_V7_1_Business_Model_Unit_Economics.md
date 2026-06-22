# AI School Studio V7.1
# Business Model & Unit Economics

## 1. Mô hình doanh thu

### Credit Pay-as-you-go (Core)

Người dùng nạp credit và chỉ trả cho tác vụ thực tế sử dụng.

Nguyên tắc:
- Không bắt buộc subscription trong giai đoạn đầu.
- Hiển thị số credit trước khi tạo nội dung.
- Chỉ trừ credit khi job thành công.
- Job lỗi do hệ thống được hoàn credit tự động.
- Video tính theo model, độ phân giải, thời lượng và audio.
- Không cung cấp gói video không giới hạn.

### School Credit Pool

Truong hoc mua mot quy credit dung chung cho giao vien.

Muc tieu:
- Giam chi phi ban hang tren moi giao vien.
- Tang doanh thu tra truoc.
- Co the dat han muc theo giao vien, mon hoc hoac thang.

### Project Storage

- Lưu miễn phí 7 ngày sau generation.
- Gia hạn chủ động theo project/30 ngày.
- Không tính theo section/ngày.
- Không tự động trừ credit nếu người dùng chưa opt-in auto-renew.
- Sau khi không đủ credit: grace period 3 ngày rồi xóa media nặng.

| Dung lượng project | Phí | Chu kỳ |
|---:|---:|---:|
| Dưới 250MB | 1 credit | 30 ngày |
| 250MB-1GB | 2 credit | 30 ngày |
| 1GB-5GB | 8 credit | 30 ngày |

Với R2 khoảng $0.015/GB-tháng và tỷ giá giả định 26.000đ/USD, giá storage thô khoảng 390đ/GB-tháng trước request/operation overhead. Cần theo dõi actual stored bytes và operation cost thay vì xem toàn bộ phí storage credit là lợi nhuận.

### Marketplace (Future)

Chi trien khai sau khi co it nhat 1.000 giao vien active.

Revenue share de xuat:
- Creator: 70%
- Platform: 30%

### TeacherGPT (Future)

Tinh credit theo luot su dung nang cao. Khong dua vao du phong doanh thu MVP.

---

## 2. Giá API tham chiếu

Ngay kiem tra: 22/06/2026.

Gia dinh quy doi:
- 1 USD = 26.000d.
- Chi phi ben duoi chua bao gom VAT va phi thanh toan.
- Gia fal.ai co the thay doi; he thong phai luu gia von thuc te cua tung job.

### fal.ai

| API | Don gia USD | Chi phi quy doi |
|---|---:|---:|
| Flux 2 Flash | $0.005/megapixel | 130d/anh 1MP |
| xAI TTS | $0.015/1.000 ky tu | 390d/1.000 ky tu |
| ElevenLabs Multilingual v2 | $0.10/1.000 ky tu | 2.600d/1.000 ky tu |
| Wan 2.2 480p | $0.04/giay | 1.040d/giay |
| Wan 2.2 580p | $0.06/giay | 1.560d/giay |
| Wan 2.2 720p | $0.08/giay | 2.080d/giay |
| Kling 2.6 Pro, khong audio | $0.07/giay | 1.820d/giay |
| Kling 2.6 Pro, co audio | $0.14/giay | 3.640d/giay |
| Veo 3.1 Lite 720p, khong audio | $0.03/giay | 780d/giay |
| Veo 3.1 Lite 720p, co audio | $0.05/giay | 1.300d/giay |
| Veo 3.1 Lite 1080p, khong audio | $0.05/giay | 1.300d/giay |
| Veo 3.1 Lite 1080p, co audio | $0.08/giay | 2.080d/giay |
| Veo 3.1 Fast, khong audio | $0.10/giay | 2.600d/giay |
| Veo 3.1 Fast, co audio | $0.15/giay | 3.900d/giay |
| Veo 3.1 Standard, khong audio | $0.20/giay | 5.200d/giay |
| Veo 3.1 Standard, co audio | $0.40/giay | 10.400d/giay |

Nguon:
- https://fal.ai/models/fal-ai/flux-2/flash
- https://fal.ai/models/xai/tts/v1
- https://fal.ai/models/fal-ai/elevenlabs/tts/multilingual-v2
- https://fal.ai/models/fal-ai/wan/v2.2-a14b/text-to-video
- https://fal.ai/models/fal-ai/kling-video/v2.6/pro/text-to-video
- https://fal.ai/models/fal-ai/veo3.1/lite
- https://fal.ai/models/fal-ai/veo3.1/fast

### LLM gia dinh

Mot lesson package 20 trang su dung Gemini 2.5 Flash:

| Tac vu | Token input/output gia dinh | Chi phi |
|---|---:|---:|
| Phan tich tai lieu | 15K/1.5K | 215d |
| Lesson planner | 5K/2K | 169d |
| Quiz | 4K/2K | 161d |
| Worksheet | 5K/3K | 234d |
| Teacher notes | 5K/3K | 234d |
| Kich ban video | 8K/4K | 322d |
| Tong LLM | 42K/15.5K | 1.335d |

Can ghi nhan token thuc te thay vi mac dinh moi bai deu co cung chi phi.

---

## 3. Chiến lược tối ưu chi phí

Thứ tự ưu tiên khi tạo nội dung:

1. Tái sử dụng cache và Asset Library.
2. Dùng template motion, FFmpeg và hiệu ứng pan/zoom.
3. Dùng Veo Lite 720p không audio cho motion phổ thông.
4. Chỉ dùng Kling, Wan hoặc Veo Fast khi người dùng chủ động trả thêm credit.

Nguyên tắc:
- Basic Package chỉ gồm voice 5 phút; thời lượng thêm được tính credit riêng.
- Clip motion phổ thông dài 4 giây và không tạo native audio.
- Voice xAI TTS được ghép sau để rẻ hơn và đồng nhất toàn bài.
- Model routing: Flash-Lite cho trích xuất/JSON, Flash cho nội dung chính.
- Không gửi toàn bộ tài liệu vào mọi bước; sử dụng knowledge summary.
- Preview trước, chỉ render MP4 sau khi người dùng xác nhận.
- Khi sửa bài, chỉ render lại scene thay đổi.
- Tối đa một retry tự động cho mỗi tác vụ API.

Mục tiêu giảm chi phí LLM từ khoảng 1.335đ xuống 300-600đ cho mỗi bài.

---

## 4. Giá vốn tối ưu theo tác vụ

Giả định:
- Voice 5 phút: khoảng 4.500 ký tự xAI TTS.
- Ảnh: Flux 2 Flash, 1MP.
- Motion phổ thông: Veo Lite 720p, 4 giây, không audio.
- Giá vốn package đã bao gồm render/storage nhỏ và dự phòng retry.

| Tác vụ | Giá vốn ước tính |
|---|---:|
| Phân tích tài liệu | 100-200đ |
| Quiz | 100-200đ |
| Worksheet | 150-250đ |
| Teacher Notes | 150-250đ |
| Text Lesson Package | 500-800đ |
| Voice 5 phút | Khoảng 1.800đ |
| Voice 10 phút | Khoảng 3.500đ |
| Ảnh Flux 1MP | Khoảng 130đ |
| Basic: text + voice 5 phút + 5 ảnh + template | Khoảng 3.500đ |
| Plus: Basic + 1 clip Veo Lite 4 giây | Khoảng 7.000đ |
| Premium Lite: Basic + 3 clip Veo Lite 4 giây | Khoảng 14.000đ |
| Premium Kling: Basic + 3 clip Kling 5 giây | Khoảng 34.000đ |
| Premium Wan: Basic + 3 clip Wan 720p 5 giây | Khoảng 39.000đ |
| Cinematic Fast: Basic + 3 clip Veo Fast 8 giây | Khoảng 78.000-114.000đ |

---

## 5. Gói nạp credit đề xuất

Quy uoc: 1 credit co gia ban thuc te tu 832d den 950d.

| Gia nap | Credit | Gia/credit |
|---:|---:|---:|
| 19.000d | 20 | 950d |
| 49.000d | 52 | 942d |
| 99.000d | 110 | 900d |
| 199.000d | 230 | 865d |
| 499.000d | 600 | 832d |

Goi 49.000d la goi vao cua. Goi 99.000d nen duoc gan nhan "Tiet kiem".

---

## 6. Bảng giá tác vụ đề xuất

| Tac vu | Credit | Gia ban hieu dung |
|---|---:|---:|
| Phan tich tai lieu | 1 | 832-950d |
| Quiz | 1 | 832-950d |
| Worksheet | 1 | 832-950d |
| Teacher Notes | 1 | 832-950d |
| Text Lesson Package | 4 | 3.328-3.800d |
| Voice 5 phut | 5 | 4.160-4.750d |
| Voice 10 phut | 9 | 7.488-8.550d |
| Anh Flux 1MP | 1 | 832-950d |
| Basic Package | 15 | 12.480-14.250d |
| Motion Veo Lite 720p 4 giây | 8 | 6.656-7.600d |
| Motion Kling 5 giây | 22 | 18.304-20.900d |
| Motion Wan 720p 5 giây | 25 | 20.800-23.750d |
| Plus, 1 clip Veo Lite 4 giây | 25 | 20.800-23.750d |
| Premium Lite, 3 clip 4 giây | 45 | 37.440-42.750d |
| Premium Kling, 3 clip | 90 | 74.880-85.500d |
| Premium Wan, 3 clip | 100 | 83.200-95.000d |
| Cinematic Fast, khong audio | 190 | 158.080-180.500d |
| Cinematic Fast, co audio | 275 | 228.800-261.250d |

Mục tiêu:
- Basic và Plus có biên gộp trên 60%.
- Các gói video cao cấp có biên gộp trên 50%.
- Biên gộp tối thiểu sau khuyến mại và phí thanh toán là 40%.
- Không giảm giá nếu biên gộp dự kiến xuống dưới 40%.

---

## 7. Gói sản phẩm nên đẩy mạnh

### Bai giang nhanh - 15 credit

Bao gồm:
- Quiz
- Worksheet
- Teacher notes
- Voice 5 phút
- 5 ảnh minh họa
- Video ghép bằng template motion

Gia hieu dung: 12.480-14.250d/bai.

### Bai giang sinh dong - 25 credit

Bao gồm Basic Package và 1 clip Veo Lite 720p, 4 giây, không audio.

Gia hieu dung: 20.800-23.750d/bai.

### Video nang cao - 45 credit

Bao gồm Basic Package và 3 clip Veo Lite 720p, mỗi clip 4 giây, không audio.

Gia hieu dung: 37.440-42.750d/bai.

---

## 8. Cache, Asset Library và bảo vệ lợi nhuận

Cache key đề xuất:

```text
hash(provider + model + normalized_prompt + settings + source_hash)
```

Ưu tiên cache cho:
- Phân tích tài liệu và knowledge summary.
- Voice theo từng đoạn văn đã chuẩn hóa.
- Ảnh khái niệm phổ biến.
- Quiz, worksheet và animation có thể tái sử dụng.
- Scene đã render; chỉ tạo lại scene bị chỉnh sửa.

Asset Library phải lưu nguồn, quyền sử dụng và phạm vi tái sử dụng. Marketplace chỉ được tái dùng asset khi giấy phép của creator cho phép.

Khuyen mai duoc phep:
- Tang 5 credit khi dang ky, chi dung cho text/quiz/worksheet.
- Nap lan dau 49.000d duoc tang toi da 8 credit.
- Gioi thieu ban be: moi ben 5 credit sau khi nguoi duoc moi nap tien.
- Giao vien xac minh truong hoc: tang 10 credit mot lan.

Quy tac:
- Credit khuyen mai khong dung cho Kling, Wan hoac Veo cao cap.
- Luu `provider`, `model`, `actual_cost_usd`, `actual_cost_vnd` va `credits_charged` cho moi job.
- Canh bao khi bien gop cua model thap hon 40%.
- Tang gia credit cua tac vu khi gia API hoac ty gia tang tren 10%.
- Tach credit da mua va credit khuyen mai de kiem soat chi phi.
- Lưu `cache_hit`, `retry_count`, `rendered_scenes` và `max_api_cost_vnd` cho mỗi job.
- Dừng job trước khi gọi API nếu chi phí dự kiến vượt trần.

---

## 9. Công thức theo dõi

```text
Revenue per job = credits_charged x realized_vnd_per_credit

Gross profit per job = revenue per job
                     - API cost
                     - retry cost
                     - payment fee allocation
                     - storage/render allocation

Gross margin = gross profit per job / revenue per job
```

Projection phai dua tren credit thuc te da tieu thu, khong dung so user nhan voi gia subscription.

Storage contribution margin:

```text
Storage realized revenue
= storage credits charged x realized VND per credit

Storage variable cost
= GB-month cost
 + storage operation requests
 + notification/cleanup overhead
 + support/refund allocation

Storage contribution margin
= (storage realized revenue - storage variable cost)
   / storage realized revenue
```
