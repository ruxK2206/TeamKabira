# Team Kabira Tracker — 5 Minute Setup

Get your tracker live on Netlify in **5 minutes**.

## ⚡ Super Fast Setup

### Step 1️⃣: Create Firebase (2 min)

1. Go to https://console.firebase.google.com/
2. **Create project** → Name: `team-kabira`
3. Skip Google Analytics
4. **Build** → **Realtime Database** → **Create**
5. Select **Production mode**
6. Go to **Settings** ⚙️ → **Project Settings**
7. Scroll down → Copy your web config (the big JavaScript object)
8. **That's it!**

### Step 2️⃣: Update Code (30 sec)

1. Open `index.html` in any text editor
2. Find: `const firebaseConfig = {` (around line 113)
3. Paste your Firebase config there
4. **Save**

### Step 3️⃣: Deploy to Netlify (1 min)

**Option A: Drag & Drop (Easiest)**

1. Go to https://netlify.com/drop
2. Drag `index.html` into the box
3. Done! ✅ You get a live URL

**Option B: GitHub (Recommended)**

1. Create GitHub repo
2. Push `index.html`, `README.md`, `netlify.toml`
3. Go to https://app.netlify.com/
4. **Add new site** → **Import an existing project**
5. Connect GitHub
6. Select your repo
7. **Deploy** (takes 1 minute)
8. You get a live URL! 🎉

### Step 4️⃣: Test It

1. Open your Netlify URL
2. Sign in with your name
3. Log a shoot
4. **Refresh page** → Data still there? ✅
5. Share URL with your team!

---

## 🎯 That's it! You're done.

Your team can now:
- ✅ Log shoots from anywhere
- ✅ Track pay & travel expenses
- ✅ Admin can search & export
- ✅ All data persists forever

## 🆘 Quick Troubleshooting

**Q: Data not saving?**
- Check Firebase config was pasted correctly
- Go to Firebase Console → Realtime Database → Rules
- Make sure you can see "members" and "entries" in the data section

**Q: Admin login not working?**
- Passcode is: `KABIRA2026`
- Check spelling (caps matter)

**Q: Page loads slowly?**
- Firebase is loading in background, totally normal
- First time is slowest, then it's instant

**Q: Can I change the admin passcode?**
- Yes! Edit line 111 in `index.html`
- Change `"KABIRA2026"` to your code

---

## 📋 File Checklist

You need:
- ✅ `index.html` (the app)
- ✅ Firebase config added to `index.html`
- ✅ `netlify.toml` (optional, for deployment)
- ✅ `README.md` (documentation)

## 🚀 Production Checklist

- [ ] Firebase project created ✅
- [ ] Config added to index.html ✅
- [ ] Tested locally (works?)
- [ ] Deployed to Netlify ✅
- [ ] Tested live URL ✅
- [ ] Shared with team ✅

## 💡 Pro Tips

1. **Offline works** — App caches data locally
2. **Mobile ready** — Works great on phone too
3. **Instant updates** — Firebase syncs in real-time
4. **Export anytime** — Admin can download Excel

## 📚 More Info

- Full setup guide: `README.md`
- Firebase details: `FIREBASE_SETUP.md`
- Troubleshooting: `README.md` → Troubleshooting section

---

**Questions?** Check the README or Firebase docs.

**Ready? Start with Step 1 above!** 🚀
