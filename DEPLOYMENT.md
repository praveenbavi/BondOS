# BondOS - Deployment Guide

## 🚀 Quick Start Deployment

### Option 1: Local Development with Docker (Recommended for Testing)

```bash
# Clone the repository
git clone https://github.com/praveenbavi/BondOS.git
cd BondOS

# Start all services
docker-compose up -d

# Services will be available at:
# - Frontend: http://localhost:5173
# - Backend API: http://localhost:8000
# - API Docs: http://localhost:8000/docs
# - Database: PostgreSQL on localhost:5432
```

### Option 2: Deploy Frontend to Vercel (Free Tier)

1. **Sign up** at [vercel.com](https://vercel.com)
2. **Connect GitHub** repository
3. **Configure environment:**
   - Go to Settings → Environment Variables
   - Add `VITE_API_URL`: Your backend URL (e.g., `https://your-backend.railway.app`)
4. **Deploy** - Automatic on push to main

**Auto-generated URL:** `https://your-project.vercel.app`

### Option 3: Deploy Backend to Railway (Free Tier)

1. **Sign up** at [railway.app](https://railway.app)
2. **Connect GitHub** repository
3. **Add PostgreSQL Database:**
   - Click "New" → "Database" → "PostgreSQL"
   - Railway generates credentials automatically
4. **Configure environment variables:**
   ```
   DATABASE_URL=<Railway-generated>
   SECRET_KEY=<generate-a-secure-key>
   CORS_ORIGINS=["https://your-vercel-domain.vercel.app"]
   ```
5. **Deploy** - Automatic on push to main

**Auto-generated URL:** `https://your-backend.railway.app`

### Option 4: Full-Stack Deployment (Production Ready)

#### Using Docker + AWS/GCP/Azure:

1. **Build Docker images:**
   ```bash
   docker build -f backend/Dockerfile -t bondos-backend:latest ./backend
   docker build -f frontend/Dockerfile -t bondos-frontend:latest ./frontend
   ```

2. **Push to Docker Hub:**
   ```bash
   docker tag bondos-backend:latest <your-username>/bondos-backend:latest
   docker push <your-username>/bondos-backend:latest
   ```

3. **Deploy to your preferred cloud platform:**
   - AWS ECS/Fargate
   - Google Cloud Run
   - Azure Container Instances
   - DigitalOcean App Platform

---

## 📋 Environment Variables

### Backend (.env)
```
DATABASE_URL=postgresql://user:password@host:5432/bondos
SECRET_KEY=your-secret-key-here
DEBUG=False (for production)
CORS_ORIGINS=["https://your-frontend-domain"]
```

### Frontend (.env)
```
VITE_API_URL=https://your-backend-url
VITE_APP_TITLE=BondOS
```

---

## 🗄️ Database Setup

### PostgreSQL on Railway (Recommended)
- Free tier includes 5GB storage
- Automatic backups
- Connection string provided in Railway dashboard

### Local PostgreSQL with Docker
```bash
docker-compose up postgres
```

---

## 🔐 Security Checklist

- [ ] Change `SECRET_KEY` to a secure random string
- [ ] Set `DEBUG=False` in production
- [ ] Configure CORS origins properly
- [ ] Use HTTPS for all production URLs
- [ ] Set strong database password
- [ ] Enable SSL certificates (free with Let's Encrypt)

---

## 📊 Monitoring & Logs

### Vercel
- Dashboard: https://vercel.com/dashboard
- View logs: Click project → Deployments → View logs

### Railway
- Dashboard: https://railway.app
- View logs: Click service → Logs tab

---

## 🆘 Troubleshooting

**Frontend not connecting to backend:**
- Check `VITE_API_URL` environment variable
- Ensure backend CORS includes frontend URL
- Check browser console for errors

**Database connection failed:**
- Verify `DATABASE_URL` is correct
- Check database is running
- Verify firewall/security group settings

**Build fails on Vercel:**
- Check Node version compatibility
- Clear cache and redeploy
- Check build logs in Vercel dashboard

---

## 📞 Support

For issues:
1. Check GitHub Issues
2. Review logs on deployment platform
3. Verify environment variables
4. Test locally with docker-compose first

---

## 🎯 Features Ready to Deploy

✅ User Authentication
✅ Dashboard & Analytics
✅ Mood Tracking
✅ Reminders System
✅ Chat Functionality
✅ Moments Sharing
✅ Push Notifications
✅ User Settings

---

**Happy deploying! 🚀**
