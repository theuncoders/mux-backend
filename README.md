# Mux Backend - Render Deployment Guide

Simple backend server for Mux video uploads.

## Fork this repo under your gitub account


---

## 🚀 Quick Deploy to Render (15 minutes)

### Step 1: Get Mux API Keys

1. Go to https://dashboard.mux.com
2. Click **Settings** → **Access Tokens**
3. Click **Generate New Token**
4. Copy your **Token ID** and **Secret Key**

---

### Step 2: Push Code to GitHub

1. Create new repo on GitHub: https://github.com/new
2. Name it: `mux-backend`
3. Upload these files:
   - `server.js`
   - `package.json`

---

### Step 3: Deploy on Render

1. Go to https://render.com and sign up
2. Click **New +** → **Web Service**
3. Connect your GitHub repo
4. Configure:
   - **Name:** `mux-backend`
   - **Runtime:** `Node`
   - **Build Command:** `npm install`
   - **Start Command:** `node server.js`
   - **Plan:** Starter ($7/month)

5. Add Environment Variables:
   - Make sure to select the appropriate hosting region and plan. You can start with the $0/month plan for now and upgrade later when you reach the free tier limits.
   - `MUX_TOKEN_ID` = [Your Token ID]
   - `MUX_TOKEN_SECRET` = [Your Secret Key]
   - `PORT` = `8080`

7. Click **Create Web Service**

---

### Step 4: Get Your URL

Wait 3-5 minutes for deployment. Your URL will be:
```
https://your-app-name.onrender.com
```

Copy this URL - you'll use it in your Adalo component!

---

## ✅ Test It

Open in browser:
```
https://your-app-name.onrender.com
```

You should see:
```json
{
  "message": "Mux Backend Server is running! 🚀",
  "status": "OK"
}
```

---

## 💰 Cost

**Render Starter:** $7/month
- Handles unlimited users
- Supports large video uploads
- No per-user costs

---

## 🔧 API Endpoints

Your backend provides (components use these automatically):

- `POST /api/create-upload` - Create upload URL
- `GET /api/upload/:uploadId` - Check upload status
- `GET /api/asset/:assetId` - Get video details
- `GET /api/videos` - List all videos
- `DELETE /api/asset/:assetId` - Delete video

---

## 📝 Environment Variables

Set these in Render dashboard:

| Variable | Value |
|----------|-------|
| MUX_TOKEN_ID | Your Mux Token ID |
| MUX_TOKEN_SECRET | Your Mux Secret Key |
| PORT | 8080 |

---

## 🎯 Use in Adalo

In your Adalo component, set:
```
Backend Server URL: https://your-app-name.onrender.com
```

**Done!** All users share this one backend.

---

## ❓ Troubleshooting

**Service not starting?**
- Check environment variables are set correctly
- Check Render logs for errors

**Upload failing?**
- Verify Mux credentials are correct
- Check backend URL in Adalo component

**Need help?**
- Check Render logs: Dashboard → Logs tab
