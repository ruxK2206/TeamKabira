# Firebase Setup Guide — Step by Step

This guide walks you through setting up Firebase Realtime Database for your Team Kabira tracker.

## Step 1: Create Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click **"Create a project"** (or **"Add project"**)
3. Enter project name: `team-kabira` (or any name)
4. Accept terms and click **"Continue"**
5. Disable Google Analytics (for simplicity)
6. Click **"Create project"**
7. Wait for setup to complete (1-2 minutes)

## Step 2: Enable Realtime Database

1. In Firebase Console, go to **"Build"** → **"Realtime Database"**
2. Click **"Create Database"**
3. Select region: **"us-central1"** (or closest to you)
4. Start in **"Production mode"**
5. Click **"Create"**
6. Database is now live! You'll get a URL like: `project-name.firebaseio.com`

## Step 3: Set Database Rules

1. Click your database name
2. Go to **"Rules"** tab
3. Replace the default rules with:

```json
{
  "rules": {
    "members": {
      ".read": true,
      ".write": true,
      ".indexOn": ["$key"]
    },
    "entries": {
      ".read": true,
      ".write": true,
      ".indexOn": ["date", "member", "status"]
    }
  }
}
```

4. Click **"Publish"**

## Step 4: Get Your Firebase Config

1. In Firebase Console, click the **gear icon** (settings) at top left
2. Click **"Project settings"**
3. Go to **"General"** tab
4. Scroll down to find **"Your apps"** section
5. Click on **"Web"** app (or create if doesn't exist)
6. You'll see a config object like:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSyDxxxxxxxxxxxxxxxxxxx",
  authDomain: "team-kabira.firebaseapp.com",
  databaseURL: "https://team-kabira-xxxx.firebaseio.com",
  projectId: "team-kabira-xxxx",
  storageBucket: "team-kabira-xxxx.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:xxxxxxxxxxxxx"
};
```

7. **Copy this entire config**

## Step 5: Add Config to index.html

1. Open `index.html` in a text editor
2. Find line 113 (search for `firebaseConfig`)
3. Replace the entire config object with your copied config
4. **Save the file**

Example:
```javascript
const firebaseConfig = {
  apiKey: "AIzaSyDxxxxxxxxxxxxxxxxxxx",
  authDomain: "team-kabira.firebaseapp.com",
  databaseURL: "https://team-kabira-xxxx.firebaseio.com",
  projectId: "team-kabira-xxxx",
  storageBucket: "team-kabira-xxxx.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:xxxxxxxxxxxxx"
};
```

## Step 6: Test Firebase Connection

1. Open `index.html` in your browser
2. Open browser console (F12 → Console tab)
3. Try logging in and adding a shoot
4. Go back to Firebase Console → **"Realtime Database"** → **"Data"** tab
5. You should see your data appear in real-time!

If you see:
```
members: {
  0: "Your Name"
}
entries: {
  xxxxxxx: { brand: "Nike", ... }
}
```

✅ **Your Firebase is working!**

## Step 7: Verify Read/Write Access

Test that data is persisting:

1. Log a shoot with details
2. **Refresh the page** (Ctrl+R or Cmd+R)
3. Your data should still be there
4. Try the admin dashboard
5. Search for a member name
6. Export to Excel

All should work smoothly!

## Firebase Realtime Database Pricing

- **Free Tier (Spark):**
  - 100 concurrent connections
  - 1 GB storage
  - 10 GB/month data transfer
  - **Perfect for team of 5-10 people**

- **Paid Tier (Blaze):** Pay as you grow

Your small team will easily stay within free limits!

## Troubleshooting Firebase

### "Permission denied" errors

- Check database rules are correctly set
- Make sure `.write: true` is enabled
- Try again after 1-2 minutes (rules might take time to apply)

### Data not appearing in Firebase Console

- Check browser console (F12) for errors
- Ensure config is correct
- Try submitting a form again
- Refresh Firebase Console

### Firebase config shows as blank

- Make sure you copied the entire config
- Check for special characters
- No `const` keyword in the config object (remove if present)
- Just the object with `{}`

### Getting 403 errors

- Most likely database rules issue
- Go back to Rules tab
- Copy-paste the rules exactly as shown above
- Click Publish
- Wait 2 minutes
- Try again

### App loads but no data syncs

- Check browser console for JavaScript errors
- Verify databaseURL includes full path with `.firebaseio.com`
- Make sure projectId matches config

## Security Notes

- These rules allow **anyone with your database URL to read/write**
- Good for **internal team use**
- For **public app**, implement authentication (email/password)
- Consider adding `.indexOn` rules for faster queries

## Monitoring Firebase Usage

1. Go to Firebase Console
2. Click **"Realtime Database"**
3. Go to **"Usage"** tab
4. See read/write operations, storage used
5. Set up alerts for unusual activity (Settings → Billing)

## Scaling to Production

If you grow beyond free tier:

1. Consider **Firestore** (different pricing model)
2. Implement **user authentication**
3. Add **data validation rules**
4. Enable **backup and restore**
5. Monitor with **Google Cloud Console**

For now, enjoy your free, unlimited team tracker! 🚀

---

**Questions?** Check Firebase Docs: https://firebase.google.com/docs/database
