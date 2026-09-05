# Team Kabira — Shoot Log Tracker

A professional shoot logging system for content creators with persistent cloud storage. Built with vanilla JavaScript + Firebase for real-time data sync.

## 🎯 Features

- **Team Member Management** — Add & track multiple team members
- **Comprehensive Logging** — Brand, content type, location, approvals, coordinator, pay, travel
- **Real-Time Sync** — All data saves to Firebase instantly
- **Admin Dashboard** — Overview, member analytics, member search with calculations
- **Excel Export** — Export all data to spreadsheet
- **Persistent Storage** — Data persists across browser sessions and page refreshes
- **Offline Support** — LocalStorage backup for quick access
- **Professional UI** — Dark theme, responsive design

## 🚀 Quick Start

### 1. Clone or Download

```bash
git clone <your-repo-url>
cd team-kabira-tracker
```

### 2. Setup Firebase

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Create a new project (or use existing)
3. Enable **Realtime Database**
4. Create database in production mode
5. Copy your Firebase config

### 3. Update Firebase Config

Edit `index.html` and find this section (around line 113):

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  databaseURL: "YOUR_DATABASE_URL",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_STORAGE_BUCKET",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

Replace with your actual Firebase config from the Firebase Console.

### 4. Deploy to Netlify

#### Option A: GitHub + Netlify (Recommended)

1. Push your code to GitHub
2. Go to [netlify.com](https://netlify.com) and sign up
3. Click "New site from Git"
4. Connect your GitHub repo
5. Basic settings:
   - **Build command:** (leave empty)
   - **Publish directory:** (leave empty or set to `.`)
6. Click "Deploy site"
7. Your site goes live! 🎉

#### Option B: Manual Deploy

1. Go to [netlify.com](https://netlify.com)
2. Drag & drop the `index.html` file
3. Done! You get a live URL

#### Option C: Netlify CLI

```bash
npm install -g netlify-cli
netlify init
netlify deploy --prod
```

### 5. Test the App

- Open your Netlify URL
- Sign in with a team member name
- Log a shoot
- Refresh the page — **data persists!**
- Try Admin dashboard (passcode: `KABIRA2026`)

## 📋 Database Structure

Firebase Realtime Database structure:

```
/
├── members/
│   ├── 0: "Member Name 1"
│   └── 1: "Member Name 2"
└── entries/
    ├── 1234567890: {
    │   ├── member: "Member Name"
    │   ├── date: "2024-01-15"
    │   ├── brand: "Nike"
    │   ├── contentType: "Reel"
    │   ├── location: "Studio"
    │   ├── status: "Delivered"
    │   ├── notes: "..."
    │   ├── approvedBy: "Client"
    │   ├── coordinator: "John Doe"
    │   ├── reelTopic: "Product Launch"
    │   ├── pay: 5000
    │   └── travel: 1000
    └── 1234567891: { ... }
```

## 🔐 Security

### Firebase Rules

Replace your Firebase Realtime Database rules with:

```json
{
  "rules": {
    "members": {
      ".read": true,
      ".write": true
    },
    "entries": {
      ".read": true,
      ".write": true
    }
  }
}
```

⚠️ **For production**, implement proper authentication. This is open access for team use.

## 🔄 Data Flow

1. **User logs in** → Stored in localStorage
2. **Fill form & submit** → Data sent to Firebase
3. **Firebase saves** → Returns confirmation
4. **UI updates** → Shows new entry in table
5. **Admin searches** → Retrieves data from Firebase
6. **Export Excel** → Downloads all Firebase data

## 🛠️ Customization

### Change Admin Passcode

Edit line 111 in `index.html`:

```javascript
const ADMIN_PASSCODE = "YOUR_NEW_CODE";
```

### Change Content Types

Edit line 112:

```javascript
const CONTENT_TYPES = ["Reel","Story","BTS","Full Shoot","Photoshoot","Other"];
```

### Modify Theme Colors

Edit `:root` CSS variables (lines 12-21):

```css
:root{
  --bg:#14131A;        /* Background */
  --accent:#E63946;    /* Accent color */
  --green:#5FBF7A;     /* Success color */
  /* ... */
}
```

## 📊 Admin Dashboard

- **Overall Stats** — Total shoots, delivered, in editing, brands
- **Member Search** — Enter name → See all their shoots with calculations
- **Export Excel** — Download all data in spreadsheet format
- **Shoots Per Member** — Bar chart visualization
- **All Logs Table** — Complete record with all fields

## 🎨 Mobile Responsive

- Works on desktop, tablet, mobile
- Touch-friendly buttons and forms
- Tables scroll horizontally on small screens
- Optimized for all viewport sizes

## 🐛 Troubleshooting

### Data Not Saving?
- Check Firebase config is correct
- Check Firebase Realtime Database is enabled
- Check browser console for errors (F12)
- Ensure database rules allow write

### Page Takes Long to Load?
- Firebase is loading in background
- First time might be slower
- Subsequent loads are cached

### Admin Login Not Working?
- Check exact passcode: `KABIRA2026`
- Case-sensitive
- Check console for errors

### Excel Export Empty?
- Click export from admin dashboard
- Make sure you have logged entries
- Check browser allows file downloads

## 📝 Usage Tips

1. **For Team Members:**
   - Log shoots as you complete them
   - Fill in all details for accurate tracking
   - Check your recent logs to see history

2. **For Admins:**
   - Use member search to check individual performance
   - Export monthly for records
   - Update passcode regularly

3. **Offline:**
   - App works offline if already loaded
   - Data syncs when back online
   - LocalStorage has backup

## 🚀 Deployment Checklist

- [ ] Firebase project created
- [ ] Realtime Database enabled
- [ ] Config added to index.html
- [ ] Code pushed to GitHub (or ready to deploy)
- [ ] Netlify site connected
- [ ] Test with sample data
- [ ] Share URL with team

## 📦 Files Included

- `index.html` — Complete app (single file)
- `README.md` — This file
- `.gitignore` — Git ignore patterns
- `netlify.toml` — Netlify config (optional)

## 🔗 Useful Links

- [Firebase Console](https://console.firebase.google.com/)
- [Netlify Dashboard](https://app.netlify.com/)
- [Firebase Docs](https://firebase.google.com/docs)
- [Netlify Docs](https://docs.netlify.com/)

## 💡 Support

- Check browser console (F12) for errors
- Verify Firebase config
- Test in private/incognito mode
- Clear browser cache if issues persist

## 📄 License

Free to use and modify for your team.

---

**Last Updated:** 2024
**Version:** 2.0 (Cloud + Netlify)
