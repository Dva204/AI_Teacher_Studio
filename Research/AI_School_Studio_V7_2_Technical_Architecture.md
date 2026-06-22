
# AI School Studio V7.2
# Technical Architecture

## Frontend

- Next.js
- TailwindCSS
- Shadcn UI

## Backend

- FastAPI
- Python

## Database

PostgreSQL

Core Tables:
- Users
- Teachers
- Schools
- Lessons
- Assets
- MarketplaceAssets
- Transactions
- Credits
- CreditLedger
- GenerationJobs
- JobCosts
- ProviderPrices
- CacheEntries
- StoragePlans
- ProjectStorageSubscriptions
- StorageLifecycleEvents

Cost fields required for every generation job:
- provider
- model
- estimated_cost_usd
- actual_cost_usd
- actual_cost_vnd
- credits_charged
- cache_hit
- retry_count
- max_api_cost_vnd

## Queue

Redis + Celery

Jobs:
- AI Analyze
- Voice Generation
- Video Render
- Asset Processing
- Cost Reconciliation
- Cache Cleanup
- Storage Expiry Notification
- Storage Renewal
- Project Grace-period Cleanup
- Orphaned Asset Cleanup

## Storage

Cloudflare R2

Folders:
- uploads/
- generated/
- assets/
- marketplace/

## Storage Lifecycle

Project states:
- `active_free`
- `active_paid`
- `grace_period`
- `media_deleted`
- `deleted`

Lifecycle:

```text
Generation completed
→ 7 days free storage
→ explicit 30-day renewal or 3-day grace period
→ delete heavy media after grace period
→ retain lightweight structured lesson data when allowed
```

Rules:
- Auto-renew is off by default and requires explicit opt-in.
- Charge per project/storage tier, never per section/day.
- Renewal and cleanup jobs are idempotent.
- Notify on day 5, day 6, day 7 and before deletion.
- Use object tags/metadata for project, expiry and retention class.
- Maintain reference counts before deleting shared/cache assets.
- Delete media independently from immutable payment/audit ledgers.
- Record bytes before/after cleanup and storage credits charged.

## AI Pipeline

Upload
↓
Source Hash + Cache Lookup
↓
Analyze or Reuse Analysis
↓
Knowledge Graph
↓
Lesson Planner
↓
Asset Library Search
↓
Prompt Builder + Cost Estimate
↓
Content Generator with Model Routing
↓
Template Motion Builder
↓
Optional Paid AI Video
↓
Scene Cache + Lesson Package Builder
↓
Export

## Cost Optimization Rules

- Asset-first: search approved reusable assets before calling generation APIs.
- Use Gemini Flash-Lite for extraction/JSON and Flash for main content.
- Normalize prompts and cache by provider, model, settings and source hash.
- Generate voice in reusable segments instead of one monolithic file.
- Default motion uses FFmpeg templates, pan/zoom and transitions.
- Default AI motion uses Veo Lite 720p, 4 seconds, audio off.
- Mix xAI TTS after video generation; native video audio is a paid option.
- Render preview first and MP4 only after user confirmation.
- Re-render only changed scenes.
- Allow at most one automatic API retry.
- Reject a job before execution when estimated cost exceeds `max_api_cost_vnd`.

## Asset Rights

Each reusable asset must store:
- source_type
- source_owner_id
- license_type
- reuse_scope
- marketplace_asset_id
- content_hash

Marketplace assets are reusable only when the creator license permits it.

## Future

- TeacherGPT
- Fine Tuning
- VietnamEduLM
