
## Overview
- **Backend**: Deploy to Render
- **Frontend**: Deploy to Vercel

## Prerequisites
- GitHub repository set up ✅
- Render account (https://render.com)
- Vercel account (https://vercel.com)
- MongoDB Atlas account (https://www.mongodb.com/cloud/atlas)


## Step 2: Deploy Backend to Render

### 2.1 Create Render Account
- Sign up at https://render.com using your GitHub account

### 2.2 Create New Web Service
1. Click "New +" → "Web Service"
2. Connect your GitHub repository: `TamilselvanRaman/Habit-Tracking`
3. Configure the service:
   - **Name**: `habit-tracker-backend` (or any name you prefer)
   - **Region**: Choose closest to you
   - **Branch**: `main`
   - **Root Directory**: `backend`
   - **Runtime**: `Node`
   - **Build Command**: `npm install`
   - **Start Command**: `npm start`
   - **Instance Type**: `Free`

### 2.3 Add Environment Variables
In Render dashboard, go to "Environment" tab and add:
- **Key**: `MONGODB_URI`  
  **Value**: Your MongoDB connection string from Step 1
  
- **Key**: `JWT_SECRET`  
  **Value**: A random secure string (e.g., `your-super-secret-jwt-key-12345`)
  
- **Key**: `PORT`  
  **Value**: `5000`
  
- **Key**: `NODE_ENV`  
  **Value**: `production`

### 2.4 Deploy
- Click "Create Web Service"
- Wait for deployment to complete (5-10 minutes)
- Copy your backend URL (e.g., `https://habit-tracker-backend-xxxx.onrender.com`)

---

## Step 3: Deploy Frontend to Vercel

### 3.1 Update Environment Variable
Before deploying, update the frontend environment variable:

1. Edit `frontend/.env.production` and replace with your actual Render backend URL:
   ```
   VITE_API_URL=https://your-actual-backend-url.onrender.com
   ```

2. Commit and push changes:
   ```bash
   git add .
   git commit -m "Update production API URL"
   git push
   ```

### 3.2 Deploy to Vercel

1. Go to https://vercel.com and sign in with GitHub
2. Click "Add New" → "Project"
3. Import your repository: `TamilselvanRaman/Habit-Tracking`
4. Vercel should auto-detect the configuration from `vercel.json`
5. Add Environment Variable:
   - **Key**: `VITE_API_URL`
   - **Value**: Your Render backend URL from Step 2.4
6. Click "Deploy"
7. Wait for deployment (2-5 minutes)

### 3.3 Get Your Frontend URL
- Vercel will provide a URL like: `https://habit-tracking-xxxx.vercel.app`
- This is your live application URL!

---

