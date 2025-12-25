# Vercel Deployment Guide

## Deploy Backend (API)

1. **Push your code to GitHub** (if not already done)

2. **Go to Vercel**: https://vercel.com
   - Sign in with GitHub

3. **Import Project**:
   - Click "Add New" → "Project"
   - Select your repository: `NextGen-Real-Estate`

4. **Configure Backend Deployment**:
   - Root Directory: `./` (keep default)
   - Framework Preset: Other
   - Build Command: (leave empty)
   - Output Directory: (leave empty)

5. **Add Environment Variables** (IMPORTANT):
   - Click "Environment Variables"
   - Add these variables:
     ```
     MONGO_URI = your_mongodb_connection_string
     JWT_SECRET = your_secret_key_here
     ```

6. **Deploy**: Click "Deploy"

## Deploy Frontend (Client)

1. **Create another Vercel project** for frontend:
   - Click "Add New" → "Project"
   - Select the same repository

2. **Configure Frontend Deployment**:
   - Root Directory: `client`
   - Framework Preset: Vite
   - Build Command: `npm run build`
   - Output Directory: `dist`

3. **Add Environment Variable**:
   - Add your backend API URL:
     ```
     VITE_API_URL = https://your-backend-url.vercel.app
     ```

4. **Deploy**: Click "Deploy"

## After Deployment

Your project will have two URLs:
- **Backend API**: `https://your-backend.vercel.app`
- **Frontend**: `https://your-frontend.vercel.app`

Update the frontend to use the backend URL by adding it to the Vite config or environment variables.

## Important Notes:
- You'll need to connect MongoDB Atlas later for the backend to work
- Make sure to whitelist Vercel's IP addresses in MongoDB Atlas Network Access
- Or simply allow "Access from Anywhere" (0.0.0.0/0) in MongoDB Atlas
