# Deploy to Netlify — Complete Guide

Three ways to deploy your Team Kabira tracker.

## 🟦 Method 1: Drag & Drop (Easiest - 2 Minutes)

Best for: Quick testing, no GitHub account needed

### Steps:

1. Make sure you have `index.html` with Firebase config updated
2. Go to **https://netlify.com/drop**
3. Drag your `index.html` file into the drop zone
4. Wait 10 seconds for upload
5. You get a URL like: `https://random-name-123.netlify.app`
6. **Done!** 🎉

### Pros:
- Super fast
- No account setup needed
- Works immediately

### Cons:
- URL is random (can custom it later)
- Can't auto-deploy updates
- One-time only

### Update later:
- Just drag & drop again to update

---

## 🐙 Method 2: GitHub + Netlify (Recommended - 5 Minutes)

Best for: Team projects, auto-updates, professional

### Step 1: Create GitHub Repo

1. Go to https://github.com/new
2. Repo name: `team-kabira-tracker`
3. Description: "Team shoot log tracker with Firebase"
4. Make it **Public** (or Private if you prefer)
5. Click **Create repository**

### Step 2: Upload Files to GitHub

**Option A: GitHub Web Interface**

1. In your repo, click **Add file** → **Upload files**
2. Select and upload:
   - `index.html` (with Firebase config)
   - `README.md`
   - `netlify.toml`
   - `.gitignore`
3. Click **Commit changes**

**Option B: Git Command Line**

```bash
git clone https://github.com/YOUR_USERNAME/team-kabira-tracker.git
cd team-kabira-tracker

# Copy files to this folder
cp index.html .
cp README.md .
cp netlify.toml .
cp .gitignore .

git add .
git commit -m "Initial commit - Team Kabira tracker"
git push
```

### Step 3: Connect to Netlify

1. Go to https://app.netlify.com/
2. Sign up with GitHub (easiest)
3. Click **Add new site** → **Import an existing project**
4. Choose **GitHub** as your provider
5. Authorize Netlify to access GitHub
6. Select your `team-kabira-tracker` repo
7. Build settings:
   - **Base directory:** (leave empty)
   - **Build command:** (leave empty)
   - **Publish directory:** (leave empty or `.`)
8. Click **Deploy site**
9. Wait 30 seconds... ✅ Live!

### Step 4: Custom Domain (Optional)

1. In Netlify dashboard, go to **Site settings**
2. Click **Domain management**
3. Add custom domain (e.g., `kabira-tracker.com`)
4. Add DNS records (Netlify will guide you)

### Pros:
- Auto-deploy on code changes
- Easy to update
- Professional URL option
- Git history maintained

### Cons:
- Requires GitHub account
- Takes 5 minutes to setup

---

## 🖥️ Method 3: Netlify CLI (For Developers)

Best for: Power users, automation

### Prerequisites:
- Node.js installed
- Command line experience

### Steps:

```bash
# Install Netlify CLI
npm install -g netlify-cli

# Login to your Netlify account
netlify login

# Deploy your site
netlify deploy --prod --dir .

# Or with a message
netlify deploy --prod --dir . --message "Deploy Team Kabira"
```

### View deployment:
```bash
netlify open:site
```

---

## ✅ Verify Deployment

After deploying (any method):

1. Open your Netlify URL
2. Test login functionality
3. Log a test shoot
4. **Refresh page** — Data still there?
5. Open **Admin** → Passcode: `KABIRA2026`
6. Search for your name → See your data?
7. Try **Export to Excel**

If all ✅, you're live!

---

## 🔄 Update Your Site

### Method 1: Drag & Drop
- Just drag new `index.html` again

### Method 2: GitHub
```bash
# Make changes to index.html
git add index.html
git commit -m "Update form fields"
git push
# Netlify auto-deploys! ✅
```

### Method 3: CLI
```bash
netlify deploy --prod --dir .
```

---

## 🚀 Performance Tips

- **CDN enabled** by default on Netlify
- **SSL/HTTPS** automatic
- **Gzip compression** automatic
- Your site loads lightning fast! ⚡

## 🔐 Security After Deploy

1. Go to **Site settings**
2. Check **Build & deploy**
3. Enable **Branch deploys** if needed
4. Consider adding **password protection** if sensitive

## 📊 Monitor Your Site

In Netlify dashboard:
- **Analytics** → See visitor stats
- **Logs** → Check for errors
- **Deploys** → See deployment history
- **Functions** → Add serverless functions (if needed)

## 🆘 Deployment Troubleshooting

### "Page not found" error

- Make sure `netlify.toml` has redirect rules
- Site is deployed at root level
- Try clearing browser cache

### Firebase not connecting

- Check Firebase config in `index.html`
- Open browser console (F12) for errors
- Verify databaseURL is correct

### Getting 403 errors

- Firebase database rules issue
- Go to Firebase Console
- Check Rules are set to allow reads/writes

### Site too slow

- Check Firebase operations
- Limit concurrent users
- Consider caching strategies

### Site won't update

- Hard refresh: **Ctrl+Shift+R** (or Cmd+Shift+R)
- Clear browser cache
- Wait 5 minutes for CDN cache

---

## 💰 Netlify Pricing

| Plan | Price | For You |
|------|-------|---------|
| Free | $0 | ✅ Perfect for small teams |
| Pro | $19/mo | Advanced features |
| Business | $99/mo | Enterprise support |

**You'll stay on free tier!** No charges for your team tracker.

---

## 🎯 Deployment Checklist

- [ ] Files ready (index.html + config)
- [ ] Firebase config added
- [ ] Choose deployment method (1, 2, or 3)
- [ ] Deploy
- [ ] Test live URL
- [ ] Share with team
- [ ] Done! 🎉

---

## 🎓 Next Steps

1. **Customize passcode** — Edit `index.html` line 111
2. **Add team members** — Manually through app or share link
3. **Setup analytics** — Netlify dashboard
4. **Custom domain** — Netlify settings
5. **Backup data** — Export Excel monthly

---

**You're live!** 🚀

Questions? Check `README.md` or Firebase docs.

Happy tracking! 📸
