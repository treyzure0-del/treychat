# EmpowerConnect (treychat)

EmpowerConnect is a school-exclusive social web app (codename: treychat) designed to provide a safe, engaging, and educational communication space for students and staff at Empower International Academy.

Why this project exists
- Replace unsafe public social platforms with a monitored, private school network.
- Encourage positive digital citizenship, creativity, and collaboration.
- Provide school-specific features: announcements, classroom posts, events, achievements, and safe messaging.

Key features
- School Feed (CampusGram): shared feed for school events, photos, class highlights.
- Private Messaging: monitored, safe chats with admin oversight/reporting.
- Events & Announcements: automatic updates and a digital noticeboard.
- Classrooms Corner: teachers post notes and discussion prompts.
- Profiles & Badges: student profiles and gamified achievements.
- Admin Control Panel: content moderation, user management, reports.
- (Optional) AI Study Buddy: in-app chatbot to assist with study summaries and reminders.

Recommended tech stack (opinionated)
- Frontend: React (Next.js) or Vite + React, Tailwind CSS for styling, TypeScript.
- Backend: Node.js with Express or NestJS (TypeScript), or a serverless backend (Vercel/Netlify Functions).
- Database: PostgreSQL (hosted: Supabase, Render, or managed Postgres), or Prisma ORM.
- Authentication: school SSO if available (OAuth / SAML), or Firebase Auth / Supabase Auth for email verification and restricted invite flows.
- Storage: S3-compatible (AWS S3, DigitalOcean Spaces) or Supabase Storage for photos/assets.
- Real-time: WebSockets (Socket.IO) or real-time DB features (Supabase Realtime) for messaging and live updates.
- Optional: OpenAI or a smaller LLM provider for the AI Study Buddy feature (respect privacy & data policy).

Repository layout (suggested)
- /apps/web — frontend (Next.js)
- /apps/api — backend (REST or GraphQL), auth endpoints, moderation APIs
- /packages/shared — shared types, utils
- /infra — IaC (Terraform, Pulumi) & deployment scripts
- /scripts — helper scripts, seed data

Getting started (local dev)
1. Clone:
   ```bash
   git clone https://github.com/treyzure0-del/treychat.git
   ```
2. Create .env.local files for frontend and backend with:
   - DATABASE_URL (Postgres)
   - AUTH_SECRET or service auth keys
   - STORAGE credentials (S3)
3. Start services (example with npm workspaces):
   ```bash
   npm install
   npm run dev
   ```
4. Run migrations:
   ```bash
   npx prisma migrate dev
   ```
5. Seed sample accounts and sample posts for testing.

Security & privacy notes
- Accounts must only be created by verified school members.
- Data retention and parental consent must comply with local laws and school policy.
- Admin monitoring should be transparent: log access, report moderation actions, and provide appeal flow.

Testing & CI
- Unit + integration tests: Jest / Vitest.
- E2E: Playwright or Cypress for critical flows (signup, post creation, messaging).
- CI: GitHub Actions for lint/test/build and deploy previews.

Development roadmap (first milestones)
1. MVP:
   - Authentication (invite / school email verification)
   - Post feed with images
   - Basic profiles and following
   - Admin moderation UI
2. Phase 2:
   - Private messaging (with monitoring)
   - Events & announcements
   - Achievements & badges
3. Phase 3:
   - AI Study Buddy (opt-in, privacy-preserving)
   - Classrooms Corner & study groups
   - Yearbook builder

Contributing
See CONTRIBUTING.md for contribution guidelines, branch strategy, and PR checklist.

License
- Decide a license (e.g., MIT, Apache-2.0). Add LICENSE file when chosen.

Contact / Maintainers
- repo: treyzure0-del/treychat
- If you want, I can open starter issues and a scaffolded Next.js app with basic auth + Postgres integration.
