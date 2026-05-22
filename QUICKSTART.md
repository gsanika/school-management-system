# Quick Start Command Reference

## 🚀 Start Both Services (Development)

### Terminal 1: Backend
```bash
cd backend
npm run dev
```
✅ Runs on: http://localhost:5000

### Terminal 2: Frontend
```bash
cd frontend
npm start
```
✅ Runs on: http://localhost:3000

---

## 📦 Installation

### Backend Setup
```bash
cd backend
npm install
```

### Frontend Setup
```bash
cd frontend
npm install
```

---

## 🧪 Test API Endpoints

### Health Check
```bash
curl http://localhost:5000/health
```

### Get All Students
```bash
curl -X GET http://localhost:5000/api/students \
  -H "Authorization: Bearer YOUR_TOKEN"
```

### Create Student
```bash
curl -X POST http://localhost:5000/api/students \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -d '{
    "enrollmentNumber": "STU001",
    "firstName": "John",
    "lastName": "Doe",
    "email": "john@example.com",
    "classAssigned": "10-A"
  }'
```

---

## 📁 Key Files Location

| File | Location | Purpose |
|------|----------|---------|
| Backend Env | `backend/.env` | ✅ Firebase credentials |
| Frontend Env | `frontend/.env` | ✅ Firebase credentials |
| Service Key | `backend/serviceAccountKey.json` | Download from Firebase |
| Firebase Config | `frontend/src/services/firebase.js` | ✅ Already configured |
| API Service | `frontend/src/services/api.js` | HTTP client setup |
| Redux Store | `frontend/src/store/index.js` | State management |

---

## ✅ Status Check

### Backend Status
- Express Server: ✅ Ready
- Firebase Config: ✅ Ready (needs serviceAccountKey.json)
- API Routes: ✅ Ready (52+ endpoints)
- Authentication: ✅ Ready

### Frontend Status
- React App: ✅ Ready
- Firebase Auth: ✅ Ready
- Redux Setup: ✅ Ready
- Tailwind CSS: ✅ Ready
- API Integration: ✅ Ready

### Firebase Status
- Project: `gsproject-d85dc` ✅
- Database: Firestore ✅
- Authentication: Email/Password ✅
- Storage: Cloud Storage ✅
- Credentials: ✅ Configured

---

## 🎯 Next Priority

1. Download Firebase Service Account Key → `backend/serviceAccountKey.json`
2. Run `npm install` in backend and frontend
3. Start both servers
4. Test login at http://localhost:3000
5. Create test data in Firestore

---

## 📞 Having Issues?

See **SETUP.md** for detailed troubleshooting guide.
