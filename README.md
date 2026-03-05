# CONSOLE — Business Management System

A centralized web-based business management platform built for teams of 150+ developers. Replaces scattered spreadsheets and chat messages with a single source of truth — featuring role-based dashboards, Kanban task management, face-recognition login, real-time updates, and AI-powered financial forecasting.

## Features

### Stage 1: Foundation
- **Smart Login** — Secure JWT auth with face recognition (OpenCV) and role-based access (admin / employer / employee)
- **Role-Based Dashboards** — Completely different views per role
- **Kanban Board** — Drag-and-drop task management (To-Do → In-Progress → Completed)
- **Task Assignment & Monitoring** — Employers assign tasks; employees update status
- **Black Box Recorder** — Immutable audit log of every action (who did what, when, with before/after snapshots)
- **Responsive UI** — Works on phones and desktops

### Stage 2: Automator & Communicator
- **Google Calendar Integration** — Tasks auto-sync to calendar; meetings auto-scheduled based on availability
- **Google Meet Integration** — Auto-generate meeting links
- **Automatic Invoices** — Monthly salary slips & bills generated as PDFs, emailed via Gmail API
- **Local Messaging** — In-app messaging and announcements for fast internal communication

### Stage 3: Live Nerve Center
- **Live Scoreboard** — Real-time dashboard updates via WebSockets (no refresh needed)
- **Active Users** — See who's online and what they're working on

### Bonus: God Mode
- **Burn Rate Prediction** — AI-powered spending forecast using a Hugging Face time-series model
- **Performance Optimization** — Caching, lazy loading, connection pooling

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Next.js 14, TailwindCSS, @dnd-kit, Socket.io-client, Recharts |
| Backend | FastAPI (Python 3.11+), python-socketio, SQLAlchemy 2.0, Alembic |
| Database | PostgreSQL 16 |
| Cache/Broker | Redis 7 |
| Background Jobs | Celery |
| Face Recognition | OpenCV + face_recognition (dlib) |
| ML/AI | Hugging Face Transformers (time-series forecasting) |
| PDF Generation | ReportLab / WeasyPrint |
| Google APIs | Calendar, Meet, Gmail |
| Auth | JWT (python-jose), bcrypt (Passlib) |
| Infrastructure | Docker + Docker Compose |

## Project Structure

```
├── backend/
│   ├── app/
│   │   ├── api/v1/          # Route modules (auth, tasks, audit, invoices, messages, meetings, analytics)
│   │   ├── core/            # Config, security, dependencies
│   │   ├── models/          # SQLAlchemy models
│   │   ├── schemas/         # Pydantic schemas
│   │   ├── services/        # Business logic (face recognition, calendar, gmail, invoices, burn rate)
│   │   └── workers/         # Celery tasks
│   ├── alembic/             # Database migrations
│   ├── requirements.txt
│   └── Dockerfile
├── frontend/
│   ├── src/
│   │   ├── app/             # Next.js App Router pages
│   │   ├── components/      # Reusable UI components
│   │   ├── hooks/           # Custom React hooks
│   │   └── lib/             # API client, socket.io, auth utilities
│   ├── package.json
│   └── Dockerfile
├── docker-compose.yml
└── .env.example
```

## Getting Started

### Prerequisites
- Docker & Docker Compose
- Python 3.11+
- Node.js 18+
- PostgreSQL 16
- Redis 7

### Setup
```bash
# Clone the repository
git clone <repo-url>
cd Kanban

# Copy environment variables
cp .env.example .env

# Start all services
docker compose up --build
```

The frontend will be available at `http://localhost:3000` and the API at `http://localhost:8000`.

## Development Phases

| Phase | Stage | Sprints | Key Deliverables |
|-------|-------|---------|-----------------|
| 1 | Foundation | Sprint 1-2 | Auth, face login, Kanban, Black Box, responsive UI |
| 2 | Automator | Sprint 3-4 | Google integrations, invoices, messaging |
| 3 | Live Center | Sprint 5 | Real-time updates, presence tracking |
| 4 | God Mode | Sprint 6 | Burn rate prediction, optimization |

## License

MIT
