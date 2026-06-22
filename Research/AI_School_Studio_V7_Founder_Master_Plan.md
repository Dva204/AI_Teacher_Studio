# AI School Studio V7 - Founder Master Plan

## Tầm nhìn
AI Lesson Studio dành cho giáo viên Việt Nam.

Lộ trình:
Validation → Manual Service → CRM → Lesson Package MVP → Asset Library → School Plan → Marketplace → TeacherGPT → Vietnam Education Platform

---

## Định vị sản phẩm

Không phải:
- AI Video Generator
- PPT Generator

Mà là:
- AI Lesson Studio
- Lesson Package Generator

Input:
- PDF
- PPT
- Word
- Ảnh SGK

Output:
- Video bài giảng
- Quiz
- Game
- Worksheet
- Teacher Notes

---

## Workflow V6

Teacher Upload
↓
AI Analyzer
↓
Knowledge Graph
↓
Lesson Planner
↓
Asset Search
↓
Prompt Builder
↓
Content Generator
↓
Lesson Package Builder
↓
Review
↓
Export
↓
Asset Library

---

## Giai đoạn 0 - Validation

Mục tiêu:
- 30 cuộc phỏng vấn giáo viên
- Tìm Hero Feature
- Xác định WTP (Willingness To Pay)

Không code.

---

## Giai đoạn 1 - Manual Service

Bán thủ công:
- Lesson Package
- Animation
- Video bài giảng

Mục tiêu:
- 30 khách hàng trả tiền
- 5-10 khách mua lần 2

Thu thập:
- CRM
- Feedback
- Asset

---

## Giai đoạn 2 - Teacher CRM

Lưu:
- Giáo viên
- Trường học
- Môn học
- Khối lớp
- Lịch sử sử dụng
- Feedback

---

## Giai đoạn 3 - Lesson Package MVP

Hero Feature:

Tài liệu
↓
Lesson Package

Bao gồm:
- Video
- Quiz
- Worksheet
- Game

---

## Giai đoạn 4 - Asset Library

Mục tiêu:
- 1000+ Asset

Lưu:
- Video
- Quiz
- Animation
- Worksheet
- Template

---

## Giai đoạn 5 - Knowledge Graph

Cấu trúc:

Môn
↓
Chương
↓
Bài
↓
Khái niệm
↓
Từ khóa
↓
Chuẩn đầu ra

Không lưu nguyên SGK.

---

## Giai đoạn 6 - School Plan

Triển khai trước Marketplace.

Mục tiêu:
- 5 trường
- 20 trường
- 100 trường

---

## Giai đoạn 7 - Marketplace

Điều kiện:
- 1000+ teacher active

Revenue:
- Creator 70%
- Platform 30%

---

## Education Advertising & Sponsored Credit

Nguyên tắc:
- Chỉ nhận quảng cáo liên quan trực tiếp đến giáo dục.
- Ưu tiên hợp đồng trực tiếp với nhà xuất bản, EdTech và nhà cung cấp giáo dục.
- Một Sponsor Card nhẹ trên dashboard/marketplace.
- Giáo viên chủ động xem nội dung tài trợ để nhận promotional credit.
- Người mua credit không bị ép xem quảng cáo.
- Promotional credit chỉ dùng cho tác vụ text giá vốn thấp.
- Không chèn quảng cáo vào editor hoặc file xuất.
- Không bán dữ liệu giáo viên hoặc học sinh.

Mục tiêu:
- Biên gộp chiến dịch tối thiểu 40%.
- Dùng doanh thu tài trợ để giảm giá cho giáo viên và tăng conversion sang credit trả phí.

Chiến lược chi tiết:
`AI_School_Studio_V7_4_Education_Advertising_Strategy.md`

---

## Giai đoạn 8 - TeacherGPT

Dữ liệu:
- Teacher Database
- Knowledge Graph
- Asset Library
- Marketplace

---

## Công nghệ dự kiến

Frontend:
- Next.js
- TailwindCSS

Backend:
- FastAPI

Database:
- PostgreSQL

Queue:
- Redis
- Celery

Storage:
- Cloudflare R2

AI:
- Gemini Flash-Lite + Flash theo model routing
- xAI TTS qua fal.ai
- Flux 2 Flash
- Veo Lite cho motion phổ thông
- Kling/Wan/Veo Fast cho add-on cao cấp

---

## Unit Economics V2

Mô hình core:
- Credit pay-as-you-go.
- 1 credit có giá bán thực tế 832-950đ.
- Chỉ trừ credit khi job thành công.
- Mục tiêu biên gộp sau phí và khuyến mại: tối thiểu 40%.
- Project được lưu miễn phí 7 ngày; gia hạn 1-8 credit/project/30 ngày theo dung lượng.
- Auto-renew storage tắt mặc định; không tính phí theo section/ngày.
- Không đủ credit có grace period 3 ngày trước khi xóa media nặng.

Chiến lược: Cache/Asset Library → template motion → video AI.

Giá vốn tối ưu:
- Basic, voice 5 phút: ~3.500đ; giá 15 credit.
- Plus, 1 clip Veo Lite 4 giây: ~7.000đ; giá 25 credit.
- Premium Lite, 3 clip 4 giây: ~14.000đ; giá 45 credit.
- Premium Kling: ~34.000đ; giá 90 credit.
- Premium Wan: ~39.000đ; giá 100 credit.
- Cinematic Fast: 78.000-114.000đ; giá 190-275 credit.

Bảng giá API, gói nạp và công thức lợi nhuận chi tiết:
`AI_School_Studio_V7_1_Business_Model_Unit_Economics.md`

---

## MOAT

Teacher Database
↓
Knowledge Graph
↓
Asset Library
↓
School Network
↓
Marketplace
↓
TeacherGPT
↓
VietnamEduLM

---

## Việc cần làm ngay

1. Hoàn thành 30 cuộc phỏng vấn.
2. Bán 30 đơn thủ công đầu tiên.
3. Thu thập CRM.
4. Chạy forced-ranking và pricing test để xác định Hero Feature.
5. Chỉ xây MVP PDF/ảnh → lesson plan + slide outline + quiz + worksheet + notes.
6. Hoàn thiện policy credit/refund và bản quyền trước nhận thanh toán public.
7. Xây gold set QA 50 bài trước private beta.
8. Đo repeat purchase, contribution margin và CAC theo cohort.

---

## Bộ tài liệu quyết định

- Business model và giá vốn:
  `AI_School_Studio_V7_1_Business_Model_Unit_Economics.md`
- Technical architecture:
  `AI_School_Studio_V7_2_Technical_Architecture.md`
- MVP roadmap:
  `AI_School_Studio_V7_3_MVP_Build_Roadmap.md`
- Education advertising:
  `AI_School_Studio_V7_4_Education_Advertising_Strategy.md`
- Market research và validation:
  `AI_School_Studio_V7_5_Market_Research_Product_Validation.md`
- MVP product specification:
  `AI_School_Studio_V7_6_MVP_Product_Spec.md`
- Credit, payment và refund:
  `AI_School_Studio_V7_7_Credit_Payment_Refund_Policy.md`
- Data, copyright và asset license:
  `AI_School_Studio_V7_8_Data_Copyright_Asset_License.md`
- Growth metrics và full unit economics:
  `AI_School_Studio_V7_9_Growth_Metrics_Unit_Economics.md`
- Content quality và safety:
  `AI_School_Studio_V7_10_Quality_Assurance_Safety.md`
