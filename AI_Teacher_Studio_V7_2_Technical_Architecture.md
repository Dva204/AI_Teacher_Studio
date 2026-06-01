
# AI Teacher Studio V7.2
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

## Queue

Redis + Celery

Jobs:
- AI Analyze
- Voice Generation
- Video Render
- Asset Processing

## Storage

Cloudflare R2

Folders:
- uploads/
- generated/
- assets/
- marketplace/

## AI Pipeline

Upload
↓
Analyze
↓
Knowledge Graph
↓
Lesson Planner
↓
Prompt Builder
↓
Content Generator
↓
Lesson Package Builder
↓
Export

## Future

- TeacherGPT
- Fine Tuning
- VietnamEduLM
