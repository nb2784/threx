# UYIR Health Application

A health management application with separated frontend and backend servers.

## Architecture

- **Frontend**: React + Vite (runs on port 5173)
- **Backend**: Express.js API Server (runs on port 3001)
- **Database**: Supabase (PostgreSQL)

## Setup Instructions

### 1. Install Dependencies

Install dependencies for both frontend and backend:

```bash
npm run install:all
```

Or install separately:

```bash
# Frontend dependencies
npm install

# Backend dependencies
cd server
npm install
cd ..
```

### 2. Environment Variables

#### Frontend (.env in root directory)

Create a `.env` file in the root directory:

```env
VITE_API_URL=http://localhost:3001/api
VITE_SUPABASE_URL=your_supabase_url_here
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key_here
```

#### Backend (server/.env)

Create a `.env` file in the `server` directory:

```env
BACKEND_PORT=3001
FRONTEND_URL=http://localhost:5173
VITE_SUPABASE_URL=your_supabase_url_here
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key_here
```

### 3. Run the Application

#### Option 1: Run Both Servers Together

```bash
npm run dev:all
```

This will start both frontend and backend servers concurrently.

#### Option 2: Run Servers Separately

**Terminal 1 - Backend:**
```bash
npm run dev:backend
```

**Terminal 2 - Frontend:**
```bash
npm run dev:frontend
```

### 4. Access the Application

- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:3001/api
- **Health Check**: http://localhost:3001/api/health

## Project Structure

```
threx_files/
├── server/                 # Backend Express API Server
│   ├── server.js          # Main server file
│   ├── package.json       # Backend dependencies
│   └── .env              # Backend environment variables
├── src/                   # Frontend React Application
│   ├── services/
│   │   ├── apiService.js  # Frontend API client (calls backend)
│   │   └── supabaseService.js  # Legacy (kept for reference)
│   ├── pages/            # React pages/components
│   └── ...
├── package.json           # Frontend dependencies
└── .env                  # Frontend environment variables
```

## API Endpoints

All API endpoints are prefixed with `/api`:

- **Auth**: `/api/auth/*`
- **Profiles**: `/api/profiles/*`
- **SOS Logs**: `/api/sos/logs/*`
- **Doctors**: `/api/doctors/*`
- **Appointments**: `/api/appointments/*`
- **Medical History**: `/api/medical-history/*`
- **Community**: `/api/community/*`

## Notes

- The frontend uses Supabase client directly for:
  - Authentication tokens (sent to backend)
  - Realtime subscriptions (WebSocket-based)
- All database operations go through the backend API
- CORS is configured to allow frontend-backend communication

## Development

- Frontend hot-reloads on changes
- Backend requires manual restart on changes (or use nodemon)
