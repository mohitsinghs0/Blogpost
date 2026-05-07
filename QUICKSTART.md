# MERN Blog Quick Start Guide

## One-Time Setup

### Step 1: Install Dependencies

**Backend:**
```bash
cd backend
npm install
```

**Frontend:**
```bash
cd frontend
npm install
```

### Step 2: Configure Environment

The `.env` files are already set up. For MongoDB:
- **Local**: `mongodb://localhost:27017/mern-blog` (default in `.env`)
- **Atlas**: Replace `MONGO_URI` in `backend/.env`

## Running the Application

### Option 1: Two Terminal Windows (Recommended for Development)

**Terminal 1 - Backend:**
```bash
cd backend
npm start
```
Expected: `Server running on port 5000`

**Terminal 2 - Frontend:**
```bash
cd frontend
npm start
```
Expected: Opens `http://localhost:3000` in browser

### Option 2: Development Mode with Auto-reload

**Terminal 1 - Backend (with nodemon):**
```bash
cd backend
npm run dev
```

**Terminal 2 - Frontend:**
```bash
cd frontend
npm start
```

## Testing Checklist

- [ ] Backend running on http://localhost:5000
- [ ] Frontend running on http://localhost:3000
- [ ] MongoDB connection successful
- [ ] Register new user works
- [ ] Login works
- [ ] Create post works
- [ ] View posts works
- [ ] Edit/Delete own posts works
- [ ] Logout works

## Common Issues & Solutions

| Issue | Solution |
|-------|----------|
| "Cannot find module" | Run `npm install` in that directory |
| MongoDB connection error | Start MongoDB or check connection string |
| Port already in use | Change PORT in `.env` or kill process |
| Blank page in browser | Check browser console for errors |
| Cannot POST to backend | Ensure backend is running on port 5000 |

## Project URLs

- Frontend: http://localhost:3000
- Backend: http://localhost:5000
- API Base: http://localhost:5000/api

## Key Files to Understand

**Backend:**
- `server.js` - Main entry point
- `models/User.js` - User schema
- `models/Post.js` - Post schema
- `controllers/authController.js` - Auth logic
- `controllers/postController.js` - Post operations

**Frontend:**
- `App.js` - Main React component
- `services/api.js` - API calls
- `pages/` - Page components
- `components/` - Reusable components

Enjoy building! 🚀
