
# AI School Studio V7.3
# MVP Build Roadmap

## Phase 0

Validation

Tasks:
- 30 interviews
- Hero Feature
- Pricing validation

---

## Phase 1

Manual Service

Tasks:
- Deliver 30 orders
- Collect CRM
- Save Assets

---

## Phase 2

MVP Development

### Week 1

Project Setup

- Next.js
- FastAPI
- PostgreSQL

### Week 2

Authentication

- Login
- Register
- Profile

### Week 3

Upload System

- PDF
- Image
- Private storage
- OCR/extraction
- PPT/Word are stretch goals after PDF/Image stability

### Week 4

AI Analyzer

- Subject Detection
- Grade Detection
- Topic Detection
- Source hashing
- Analysis cache
- Gemini Flash-Lite/Flash routing

### Week 5

Lesson Planner

- Outline
- Lesson Flow
- Knowledge summary
- Asset Library search before generation
- API cost estimation

### Week 6

Lesson Package Builder

- Lesson Plan
- Slide Outline
- Quiz
- Worksheet
- Teacher Notes
- Credit ledger
- Job cost tracking
- Credit refund for failed jobs
- Section-level edit/regenerate
- Review checklist
- PDF export

### Week 7

Payment + Reliability

- Credit purchase and signed payment webhooks
- Reserve/capture/refund idempotency
- Actual API cost tracking
- Error handling and support reason codes
- Gold-set quality evaluation

### Week 8

Private Beta

- 20 teachers
- Concierge onboarding and support
- Quality/reliability fixes
- Maximum API cost guardrail
- Cost reconciliation dashboard
- Storage expiry banner and notifications
- 7-day free storage lifecycle
- 3-day insufficient-credit grace period
- Idempotent renewal and heavy-media cleanup

Stretch goals only after core acceptance criteria:
- PPTX direct export
- Segmented xAI TTS with cache
- Flux image generation with cache
- FFmpeg motion templates
- Veo Lite 720p, 4 seconds, audio off

---

## Private Beta Target

- 20 teachers create at least one package.
- 10 teachers purchase credit or pay for a concierge order.

## Public Beta Target

- 50 weekly active teachers.
- Activation means completing and reviewing/exporting at least one package.

---

## Success Criteria

- Upload-to-completed package >= 80%.
- Median time-to-first-package < 5 minutes.
- At least 60% of packages are used after no more than two revision rounds.
- 30-day repeat purchase >= 25% after validation cohort.
- Basic Package API cost <= 3.500d
- Plus Package API cost <= 7.000d
- Gross margin after retry >= 60% for Basic and Plus
- Cache hit rate >= 20% after the first 100 completed lessons
- Failed paid jobs refund credit automatically
- Storage auto-renew is opt-in and never charges per section/day
- Expired media cleanup never deletes immutable payment/audit ledgers

Marketplace, self-service advertising and premium AI video are not MVP launch gates.
