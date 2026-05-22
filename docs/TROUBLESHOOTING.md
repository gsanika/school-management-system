# Troubleshooting Guide

## Common Issues and Solutions

### Backend Issues

#### Issue: Port 5000 already in use

**Solution:**
```bash
# Find process using port 5000
lsof -ti:5000

# Kill the process
lsof -ti:5000 | xargs kill -9

# Or use a different port
PORT=5001 npm run dev
```

#### Issue: Firebase connection error

**Solution:**
```bash
# Verify serviceAccountKey.json exists in backend folder
ls -la backend/serviceAccountKey.json

# Check .env file for correct Firebase credentials
cat backend/.env

# Verify Firebase project is active
# Go to Firebase Console → gsproject-d85dc
```

#### Issue: CORS error

**Solution:**
```bash
# CORS is already enabled in Express
# Check if backend is running
curl http://localhost:5000/health

# Verify frontend API_BASE_URL
cat frontend/.env | grep API_BASE_URL
```

#### Issue: npm install fails

**Solution:**
```bash
# Clear npm cache
npm cache clean --force

# Remove node_modules and lock file
rm -rf node_modules package-lock.json

# Reinstall
npm install

# Check Node version
node --version  # Should be v16+
npm --version   # Should be v7+
```

### Frontend Issues

#### Issue: Firebase authentication not working

**Solution:**
```bash
# Check Firebase config
cat frontend/src/services/firebase.js

# Verify .env credentials
cat frontend/.env

# Create test user in Firebase Console
# Go to Firebase Console → Authentication → Add User
```

#### Issue: API calls returning 401 Unauthorized

**Solution:**
```bash
# Ensure user is logged in
# Check localStorage for auth token
# Verify JWT token is valid

# In browser console:
localStorage.getItem('firebase_token')

# Create new user and login again
```

#### Issue: React app won't start

**Solution:**
```bash
# Clear cache
cd frontend
rm -rf node_modules package-lock.json
npm cache clean --force
npm install

# Start again
npm start

# Check for port conflicts
lsof -ti:3000
```

#### Issue: Tailwind CSS not working

**Solution:**
```bash
# Rebuild Tailwind
cd frontend
npm run build

# Check tailwind.config.js
cat tailwind.config.js

# Verify CSS is imported
grep -r "@tailwind" src/
```

### Database Issues

#### Issue: Firestore collections not appearing

**Solution:**
```bash
# Go to Firebase Console
# Navigate to Firestore Database
# Create collections manually:
# - users
# - students
# - teachers
# - courses
# - classes
# - grades
# - attendance
# - fees
# - timetables
```

#### Issue: Database write errors

**Solution:**
```bash
# Check Firestore security rules
# Go to Firebase Console → Firestore → Rules

# Temporarily allow all (for testing)
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write;
    }
  }
}

# Verify user is authenticated
```

### Environment & Configuration

#### Issue: Environment variables not loading

**Solution:**
```bash
# Backend - Create .env file
cd backend
cp .env.example .env
# Edit and add credentials

# Frontend - Create .env file
cd frontend
cp .env.example .env
# Edit and add credentials

# Restart both servers after updating .env
```

#### Issue: Different behavior in development vs production

**Solution:**
```bash
# Check NODE_ENV
echo $NODE_ENV

# Set to production
export NODE_ENV=production

# Check environment-specific configs
# Look for conditional logic in code
```

### Git & Deployment Issues

#### Issue: Git authentication failed

**Solution:**
```bash
# Set up SSH key
ssh-keygen -t ed25519 -C "your-email@example.com"

# Add to GitHub
# Settings → SSH and GPG keys → Add SSH key

# Test connection
ssh -T git@github.com
```

#### Issue: Deployment fails

**Solution:**
```bash
# Check deployment logs
railway logs
# or
heroku logs --tail
# or
netlify logs

# Verify environment variables are set
# Check build scripts in package.json
# Test locally: npm run build
```

### Performance Issues

#### Issue: Slow API responses

**Solution:**
```bash
# Check Firebase query efficiency
# Look for N+1 queries
# Add indexes in Firestore
# Use pagination

# Profile with:
curl -w "\nTotal time: %{time_total}s\n" http://localhost:5000/api/students
```

#### Issue: High memory usage

**Solution:**
```bash
# Monitor memory
node --max-old-space-size=2048 src/index.js

# Check for memory leaks
# Use memory profiler
# Reduce batch sizes in queries
```

### Authentication Issues

#### Issue: Token expired

**Solution:**
```bash
# Refresh token
# Implement token refresh logic
# See firebase.js for implementation
```

#### Issue: Role-based access denied

**Solution:**
```bash
# Verify user role in Firebase
# Go to Firebase Console → Users
# Check custom claims or user data

# Update user role via backend
```

---

## Getting Help

### Resources
- [Firebase Documentation](https://firebase.google.com/docs)
- [Express.js Docs](https://expressjs.com/)
- [React Documentation](https://react.dev)
- [GitHub Issues](https://github.com/gsanika/school-management-system/issues)

### Reporting Bugs

1. Go to GitHub Issues
2. Click "New Issue"
3. Provide:
   - Error message
   - Steps to reproduce
   - Environment details
   - Screenshots/logs

---

**Still having issues? Check the main README.md or ask in GitHub Discussions!**