# AI School Studio - Project Structure Guide

## 1. Mục tiêu cấu trúc

Cấu trúc này dành cho MVP gồm:
- Next.js web application.
- FastAPI backend.
- PostgreSQL.
- Redis/Celery background jobs.
- Cloudflare R2 production storage.
- Local storage khi phát triển.

Nguyên tắc:
- Một repository cho toàn bộ MVP.
- Frontend không gọi trực tiếp AI provider hoặc storage secret.
- Backend sở hữu credit, payment, generation và data policy.
- Background job nằm cùng backend trong MVP; chưa tách microservice.
- Schema giao tiếp được lưu tập trung trong `packages/contracts`.

---

## 2. Cây thư mục

```text
AI_School_Studio/
├── apps/
│   ├── web/
│   │   ├── public/
│   │   ├── src/
│   │   │   ├── app/
│   │   │   ├── components/
│   │   │   ├── features/
│   │   │   │   ├── auth/
│   │   │   │   ├── projects/
│   │   │   │   ├── lessons/
│   │   │   │   └── credits/
│   │   │   ├── lib/
│   │   │   └── styles/
│   │   └── tests/
│   └── api/
│       ├── app/
│       │   ├── api/routes/
│       │   ├── core/
│       │   ├── db/
│       │   ├── models/
│       │   ├── schemas/
│       │   ├── repositories/
│       │   ├── services/
│       │   │   ├── ai/
│       │   │   ├── storage/
│       │   │   ├── export/
│       │   │   └── quality/
│       │   ├── tasks/
│       │   └── utils/
│       └── tests/
│           ├── unit/
│           └── integration/
├── packages/
│   └── contracts/
│       ├── schemas/
│       └── examples/
├── infra/
│   ├── docker/
│   ├── migrations/
│   └── monitoring/
├── scripts/
├── tests/
│   ├── e2e/
│   └── fixtures/
├── docs/
│   ├── architecture/
│   ├── api/
│   ├── operations/
│   └── decisions/
├── storage/local/
│   ├── uploads/
│   ├── generated/
│   ├── exports/
│   └── cache/
└── Research/
```

---

## 3. Trách nhiệm từng vùng

### `apps/web`

Chứa giao diện giáo viên:
- Đăng ký/đăng nhập.
- Dashboard và project.
- Upload PDF/ảnh.
- Xác nhận môn, khối, chủ đề.
- Theo dõi generation job.
- Review/edit theo section.
- Credit history và storage expiry.

Feature-specific code đặt trong `src/features`. Component dùng chung mới đặt trong `src/components`.

### `apps/api`

Chứa business logic và API:
- Authentication/authorization.
- Project và lesson lifecycle.
- Credit ledger.
- Upload/storage.
- AI routing và generation.
- Quality validation.
- Export.
- Payment webhook.
- Storage expiry/cleanup.

Không đặt business rule trong route handler. Route gọi service; service dùng repository; repository truy cập database.

### `apps/api/app/tasks`

Background tasks:
- OCR/analyze.
- Lesson generation.
- Voice/media generation.
- Export.
- Cost reconciliation.
- Storage notification, renewal và cleanup.

Mỗi task phải idempotent vì queue có thể giao lại job.

### `packages/contracts`

Nguồn sự thật cho contract giữa web, API và worker:
- Lesson Package schema.
- Job status.
- Error codes.
- Credit quote.
- Quality issue.

`schemas` chứa định nghĩa; `examples` chứa payload mẫu để review và test.

### `infra`

- `docker`: môi trường local PostgreSQL/Redis.
- `migrations`: database migrations hoặc tài liệu migration.
- `monitoring`: dashboard, alert và log configuration.

### `tests`

- `e2e`: luồng từ upload đến export/refund.
- `fixtures`: tài liệu được phép dùng cho test.

Gold-set nội dung có thể đặt dưới `tests/fixtures/gold-set` khi bắt đầu QA.

### `storage/local`

Chỉ dùng khi phát triển local:
- Không commit upload hoặc output thật.
- Cấu trúc phải mô phỏng R2 object key.
- Có lifecycle cleanup giống production.

### `Research`

Giữ product strategy, policy và nghiên cứu thị trường. Không import các file này vào runtime application.

---

## 4. Thứ tự khởi tạo

### Bước 1 - Repository rules

Chuẩn bị:
- `.gitignore`.
- `.editorconfig`.
- README gốc.
- Quy ước environment variable.
- Không commit secret hoặc tài liệu người dùng.

### Bước 2 - Backend skeleton

Khởi tạo FastAPI và chỉ làm:
- Health endpoint.
- Settings/environment validation.
- Database connection.
- Migration workflow.
- Test runner.

Không tích hợp AI trước khi database và test chạy ổn định.

### Bước 3 - Frontend skeleton

Khởi tạo Next.js và chỉ làm:
- Layout.
- Authentication shell.
- API client.
- Error/loading states.
- Component test setup.

### Bước 4 - First vertical slice

Hoàn thành một luồng nhỏ end-to-end:

```text
Create project
→ upload one PDF/image
→ extract text
→ confirm metadata
→ store result
→ show it on web
```

Chưa tạo full Lesson Package ở bước này.

### Bước 5 - Structured Lesson Package

Thêm lần lượt:
1. Lesson plan.
2. Quiz và answer key.
3. Worksheet và answer key.
4. Teacher Notes.
5. Slide outline.

Mỗi output có schema, example, validator và test riêng.

### Bước 6 - Credit và cost

Thêm credit quote, reserve, capture, release và refund trước payment thật.

Mỗi AI job phải lưu:
- Estimated cost.
- Actual cost.
- Credits charged.
- Retry count.
- Cache hit.

### Bước 7 - Payment và private beta

Chỉ tích hợp payment khi:
- Job thành công ổn định.
- Refund tự động đã test.
- Credit ledger không double-charge.
- Terms/refund policy đã được review.

---

## 5. Không tạo sớm

Chưa cần:
- Microservices riêng cho worker.
- Kubernetes.
- Marketplace runtime.
- Ad platform.
- TeacherGPT.
- Vector database nếu search đơn giản vẫn đủ.
- Fine-tuning.
- Kling/Wan/Veo Fast trong core workflow.

Chỉ thêm khi MVP metrics chứng minh nhu cầu.

---

## 6. Definition of Done cho mỗi feature

Một feature hoàn thành khi:
- Có acceptance criteria.
- Có authorization/tenant check.
- Có success, empty, error và retry state.
- Có unit/integration test phù hợp.
- Có analytics event không chứa private content.
- Có cost impact nếu gọi provider.
- Có data retention/deletion behavior.
- Có hướng rollback hoặc disable.

---

## 7. Bước build đầu tiên

Chọn một môn/khối pilot và chuẩn bị 10 tài liệu test có quyền sử dụng. Sau đó khởi tạo backend/frontend skeleton và hoàn thành vertical slice upload → extract → confirm metadata trước khi xây generation pipeline.
