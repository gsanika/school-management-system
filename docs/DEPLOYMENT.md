# Deployment Guide

## Backend Deployment

### Option 1: Railway (Recommended)

```bash
# Install Railway CLI
npm install -g @railway/cli

# Login to Railway
railway login

# Link repository
cd backend
railway init

# Set environment variables
railway variables set FIREBASE_API_KEY=...
railway variables set FIREBASE_PROJECT_ID=...
railway variables set JWT_SECRET=...
# Set all other variables

# Deploy
git push
```

### Option 2: Render

1. Go to https://render.com
2. Create new Web Service
3. Connect GitHub repository
4. Set environment variables:
   - FIREBASE_API_KEY
   - FIREBASE_PROJECT_ID
   - FIREBASE_SERVICE_ACCOUNT_KEY (paste content)
   - JWT_SECRET
   - NODE_ENV=production
5. Deploy

### Option 3: Heroku

```bash
# Install Heroku CLI
# Login
heroku login

# Create app
heroku create school-mgmt-backend

# Set environment variables
heroku config:set FIREBASE_API_KEY=...
heroku config:set FIREBASE_PROJECT_ID=...
# Set all variables

# Deploy
git push heroku main

# View logs
heroku logs --tail
```

## Frontend Deployment

### Option 1: Vercel (Recommended)

```bash
# Install Vercel CLI
npm install -g vercel

# Go to frontend directory
cd frontend

# Deploy
vercel

# Follow prompts and set:
# REACT_APP_FIREBASE_API_KEY
# REACT_APP_FIREBASE_PROJECT_ID
# REACT_APP_API_BASE_URL
```

### Option 2: Netlify

```bash
# Build frontend
cd frontend
npm run build

# Deploy via Netlify CLI
npm install -g netlify-cli
netlify deploy --prod --dir=build

# Set environment variables in Netlify UI
```

### Option 3: GitHub Pages

```bash
# Add to package.json
"homepage": "https://gsanika.github.io/school-management-system"

# Install gh-pages
npm install --save-dev gh-pages

# Add scripts
"deploy": "npm run build && gh-pages -d build"

# Deploy
npm run deploy
```

## Production Checklist

- [ ] Download Firebase Service Account Key
- [ ] Set all environment variables
- [ ] Test all API endpoints
- [ ] Configure Firestore security rules
- [ ] Set up Firebase authentication methods
- [ ] Enable CORS on backend
- [ ] Test authentication flow
- [ ] Test database operations
- [ ] Set up monitoring/logging
- [ ] Configure backups
- [ ] Load test with 1000+ concurrent users
- [ ] Set up SSL/HTTPS
- [ ] Configure CDN for frontend
- [ ] Set up error tracking (Sentry)
- [ ] Configure analytics

## Monitoring

### Backend Monitoring

```bash
# Check application logs
railway logs

# Monitor performance
# Set up New Relic or DataDog
```

### Frontend Monitoring

```bash
# Set up error tracking
# npm install @sentry/react @sentry/tracing
```

## Scaling

### Database Scaling
- Use Firestore composite indexes
- Implement query optimization
- Use batch operations
- Archive old data

### Backend Scaling
- Use load balancer
- Implement caching
- Use Redis for sessions
- Horizontal scaling with multiple instances

### Frontend Optimization
- Minify and bundle
- Use CDN
- Lazy load components
- Optimize images

---

**For more help, check the main README.md**