
# Abar Nosto – Community Issue Monitoring Platform

A full‑stack MERN application that enables citizens to report, track, and discuss local civic issues (potholes, broken lights, drainage, flooding, etc.) while providing administrators with tools to manage reports, update statuses, and maintain a user reputation system.

## Features

**Module 1 – Reporting & Community Engagement**
- Submit reports with location picker (GPS + map), photos, and CAPTCHA
- Upvote / downvote issues to show community support
- Comment on issues (with edit/delete)
- Live activity feed showing new issues, comments, votes, and status changes
- Duplicate detection – warns if a similar issue exists nearby

**Module 2 – Reputation System**
- Users earn reputation points for creating reports (+10) and receiving upvotes (+1)
- Admins can manually adjust reputation and view full history
- Reputation badges and leaderboard (optional admin panel)

**Module 3 – Authority Directory, Drafts & Admin Tools**
- Browse ward/councillor/authority contacts with search/filter
- Admins can manage authority contacts and government service links
- Report drafts are auto‑saved locally (offline‑capable) with a “load draft” reminder
- Users can request the latest update on an issue (admin notification)
- Admin‑generated issue summary (priority‑based, downloadable)

**Additional features**
- Follow issues and receive notifications (teammate’s module)
- Interactive map with real‑time issue markers (teammate’s module)
- Secure authentication (JWT) with role‑based access (admin / user)

## Tech Stack

| Layer       | Technology                          |
|-------------|-------------------------------------|
| Frontend    | React (Vite), TailwindCSS           |
| Backend     | Node.js, Express.js                 |
| Database    | MongoDB (Mongoose ODM)              |
| Real‑time   | Polling (activity feed every 10s)   |
| Map         | OpenStreetMap + Leaflet             |
| CAPTCHA     | Google reCAPTCHA (or custom)        |

## Project Structure

```
backend/
├── config/                 # Database, reputation constants, etc.
├── controllers/            # Auth, issue, report, admin, etc.
├── middleware/             # Auth, reputation, upload, captcha
├── models/                 # Mongoose schemas (User, Report, Activity, etc.)
├── routes/                 # API route definitions
├── utils/                  # Helpers, email service, draft storage
└── server.js

frontend/
├── public/                 # Static assets
├── src/
│   ├── components/         # Reusable UI (VoteButton, CommentSection, etc.)
│   ├── hooks/              # Custom hooks (useDraft, etc.)
│   ├── pages/              # Dashboard, complaint details, admin panels
│   ├── services/           # API client, auth, draft storage
│   ├── App.jsx
│   └── main.jsx
└── index.html
```

## Installation & Setup

### Prerequisites
- Node.js (v18+)
- MongoDB (local or Atlas)
- Git

### 1. Clone the repository
```bash
git clone https://github.com/your-username/abar-nosto.git
cd abar-nosto
```

### 2. Backend setup
```bash
cd backend
npm install
```

Create a `.env` file in the `backend/` folder:
```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
# Optional: ImageKit keys (if using photo upload)
IMAGEKIT_PUBLIC_KEY=...
IMAGEKIT_PRIVATE_KEY=...
IMAGEKIT_URL_ENDPOINT=...
```

Start the backend server:
```bash
npm run dev   # or node server.js
```

### 3. Frontend setup
```bash
cd frontend
npm install
```

Create a `.env` file in the `frontend/` folder:
```env
VITE_API_URL=http://localhost:5000
```

Start the frontend development server:
```bash
npm run dev
```

### 4. Seed initial authority data (optional)
```bash
cd backend
node scripts/seedAuthorities.js
```

## API Endpoints (Main ones)

| Method | Endpoint                     | Description                       | Access      |
|--------|------------------------------|-----------------------------------|-------------|
| POST   | `/api/auth/register`         | User registration                 | Public      |
| POST   | `/api/auth/login`            | User login                        | Public      |
| GET    | `/api/auth/me`               | Get current user (reputation)     | User        |
| POST   | `/api/reports`               | Create a new report               | User        |
| GET    | `/api/issues`                | List all issues                   | User        |
| POST   | `/api/issues/:id/upvote`     | Upvote an issue                   | User        |
| POST   | `/api/issues/:id/comments`   | Add a comment                     | User        |
| GET    | `/api/issues/activities/feed`| Live activity feed                | User        |
| GET    | `/api/admin/users`           | List all users (reputation)       | Admin       |
| POST   | `/api/admin/users/:userId/reputation` | Adjust user reputation    | Admin       |
| GET    | `/api/authorities`           | Get authority contacts            | User        |
| POST   | `/api/authorities`           | Add authority (admin only)        | Admin       |
| GET    | `/api/drafts`                | Get user’s draft report           | User        |
| POST   | `/api/drafts`                | Save draft report                 | User        |
| POST   | `/api/issues/:id/request-update` | Request latest update         | User        |
| GET    | `/api/summary/issues/:id/summary` | Generate issue summary        | Admin       |

> A full API collection is available in the project documentation.

## Screenshots (optional)
Add screenshots of the dashboard, map, admin panel, and reputation leaderboard here.

## Team & Contribution

This project was developed collaboratively by:
- Pretom Areefin Pranto
- Farah Tasnim 
- Tasneem Jahan Masum 
- Sabbir Hossain Prince
- 
Each team member implemented their assigned modules independently. The main branch contains the integrated work.

## License

This project is for educational purposes. All rights reserved.

## Acknowledgements

- Supervisors for guidance and feedback
- OpenStreetMap for map tiles
- ImageKit for image hosting (if used)
- All team members for their dedication

---
**Repository:** [https://github.com/your-username/abar-nosto](https://github.com/your-username/abar-nosto)
```

---

Adjust the repository URL, your name, and team member details as needed. This README is ready to copy‑paste into your GitHub repo.
