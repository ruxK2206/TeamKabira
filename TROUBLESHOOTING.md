# Troubleshooting Guide

Common issues and how to fix them.

---

## 🔴 Data Not Saving / Firebase Not Working

### Symptom:
- Form submission shows no message
- Data doesn't appear after refresh
- Console shows errors

### Cause:
Usually Firebase config is incorrect or missing

### Fix:
1. Open `index.html` in text editor
2. Find: `const firebaseConfig = {`
3. Check if config has your actual Firebase data
4. Verify `databaseURL` includes `.firebaseio.com`
5. Make sure all fields are filled (not blank)
6. Save file
7. Test again

### Verify Firebase:
1. Go to Firebase Console
2. Go to Realtime Database → Data tab
3. Do you see your data appearing there? 
   - YES ✅ → Firebase works, problem is elsewhere
   - NO ❌ → Firebase config is wrong

### Nuclear Option:
1. Delete Firebase project
2. Create brand new project
3. Copy fresh config
4. Paste to index.html
5. Try again

---

## 🔴 "Permission denied" Errors

### Symptom:
- Console error: "Permission denied"
- Data not saving to Firebase
- Red error messages in app

### Cause:
Database rules are too restrictive

### Fix:
1. Go to Firebase Console
2. Click Realtime Database
3. Go to Rules tab
4. Replace all text with this:

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

5. Click **Publish**
6. Wait 1-2 minutes
7. Try again
8. Check box to confirm changes were published

**Why this works:** Allows anyone with your database URL to read/write (fine for team use)

---

## 🔴 Admin Login Not Working

### Symptom:
- "Wrong passcode" message
- Can't access admin dashboard

### Causes & Fixes:

**1. Typo in passcode:**
- Passcode is: `KABIRA2026`
- Case-sensitive (all caps)
- No spaces
- Type exactly: K-A-B-I-R-A-2-0-2-6

**2. Changed passcode earlier:**
- Check `index.html` line 111
- See what you set it to
- Use that exact passcode

**3. Browser cache:**
- Hard refresh: Ctrl+Shift+R (or Cmd+Shift+R)
- Clear browser cache
- Try in private/incognito mode

---

## 🔴 Page Shows "Loading..." Forever

### Symptom:
- Page stuck on loading screen
- Shows spinner indefinitely
- Nothing loads

### Causes & Fixes:

**1. Firebase not loading:**
- Check internet connection
- Open browser console (F12)
- Look for Firebase errors
- Check if `databaseURL` is valid

**2. Slow internet:**
- Wait 30 seconds (Firebase can be slow)
- Try again
- Check internet speed

**3. Browser blocked Firebase:**
- Try private/incognito mode
- Disable browser extensions
- Try different browser

**4. Firebase config invalid:**
- Check config again
- Make sure databaseURL doesn't have typos
- Verify no extra spaces or characters

---

## 🔴 Data Disappeared After Refresh

### Symptom:
- Logged a shoot
- Refreshed page
- Data is gone

### Causes & Fixes:

**1. Firebase never saved it:**
- Check browser console (F12)
- Look for errors
- Go to Firebase Console → Data tab
- Is data there? 
   - YES ✅ → Data is in Firebase, check browser cache
   - NO ❌ → Firebase didn't save (permissions issue)

**2. Saved to localStorage only (offline):**
- Should sync to Firebase automatically
- Wait 30 seconds
- Check Firebase console

**3. Browser cleared data:**
- Don't clear browser cache for this site
- Check browser settings
- Make sure cookies/storage are enabled

### Verify:
1. Log a new shoot
2. Go to Firebase Console → Realtime Database
3. Do you see it in the Data tab?
   - YES ✅ → Data is saved, refresh page and check again
   - NO ❌ → Firebase not saving, check permissions

---

## 🔴 Excel Export Not Working

### Symptom:
- Click "Export to Excel"
- Nothing happens
- No file downloads

### Causes & Fixes:

**1. Browser blocked file download:**
- Check download permission popup
- Allow downloads for this site
- Try again

**2. No data to export:**
- Add some shoots first
- Need at least 1 entry
- Try exporting from admin dashboard

**3. XLSX library not loading:**
- Check console for errors
- Hard refresh: Ctrl+Shift+R
- Try different browser

**4. Filename issue:**
- File should download as: `Team-Kabira-Shoots-2024-01-15.xlsx`
- Check Downloads folder
- If still nothing, try different browser

### Workaround:
- Export from admin search results
- Select all (Ctrl+A)
- Copy table
- Paste into Excel manually

---

## 🔴 Member Search Not Working

### Symptom:
- Enter member name in search
- No results shown
- Stats don't appear

### Causes & Fixes:

**1. Typo in member name:**
- Check exact spelling
- Case-sensitive
- No extra spaces
- Must match exactly what they logged with

**2. Member has no data:**
- Member must have logged at least 1 shoot
- Check All Logs table
- Verify member name appears there

**3. Incorrect member name:**
- Look at the "Shoots Per Member" bar chart
- Click on exact name from there
- Copy and paste into search

---

## 🔴 Mobile App Not Working

### Symptom:
- Page won't load on phone
- Forms don't work on mobile
- Data not syncing on mobile

### Causes & Fixes:

**1. Mobile browser issue:**
- Try different browser (Chrome, Firefox)
- Clear browser cache on phone
- Restart phone

**2. Responsive design issue:**
- Hold phone in portrait mode
- Check if readable
- Try landscape mode

**3. Slow internet on mobile:**
- Wait for page to fully load
- Check WiFi connection
- Try cellular data

**4. Mobile cache issue:**
- Log out (switch members)
- Log back in
- Hard refresh: Pull to refresh page

### Test Mobile:
- Go to your Netlify URL on phone
- Sign in
- Log a shoot
- Refresh page
- Data should persist

---

## 🔴 Netlify Deployment Issues

### Symptom:
- Can't deploy to Netlify
- "File not found" after deploy
- 404 errors on Netlify

### Causes & Fixes:

**1. Wrong file uploaded:**
- Make sure `index.html` is at root level
- Not in a folder
- Exactly named `index.html`

**2. Netlify can't find index.html:**
- Check you have `netlify.toml` file
- It has redirect rules
- Upload both files together

**3. Deploy but Firebase not working:**
- Check Firebase config is in index.html
- Hard refresh on Netlify URL: Ctrl+Shift+R
- Wait 5 minutes for CDN cache

**4. Drag & drop didn't work:**
- Try GitHub method instead
- Click "Add new site" in Netlify
- Connect GitHub repo
- Netlify auto-deploys

---

## 🔴 Firebase Quota Exceeded

### Symptom:
- Lots of "429" errors
- "Too many requests" message
- Firebase operations slow down

### Causes:
- Free tier has limits
- Too many concurrent users
- Inefficient queries

### Fix:
- Check Firebase → Usage tab
- If over limits, upgrade to Blaze plan
- OR reduce concurrent users
- OR optimize database queries

**For small team:** You won't hit this!

---

## 🔴 "CORS" or "Mixed Content" Errors

### Symptom:
- Console shows CORS errors
- Mixed content warnings
- API calls fail

### Causes:
- Rare with Firebase + Netlify
- Usually browser security

### Fix:
1. Hard refresh: Ctrl+Shift+R
2. Try different browser
3. Try incognito mode
4. Clear browser cache

---

## 🔴 Can't Change Admin Passcode

### Symptom:
- Want to change passcode
- Don't know how
- Code doesn't work after change

### Fix:
1. Open `index.html` in text editor
2. Find line ~111: `const ADMIN_PASSCODE = "KABIRA2026";`
3. Replace `"KABIRA2026"` with your new code
4. Example: `const ADMIN_PASSCODE = "MyPass123";`
5. Save file
6. Redeploy to Netlify
7. New passcode works

### New passcode rules:
- Can be anything
- Case-sensitive
- No spaces (optional but easier)
- At least 6 characters (for security)

---

## ✅ Common Non-Issues (You're Fine)

These aren't problems, they're normal:

**"Firebase loading slowly on first load"** ✅
- Normal, Firebase initializes
- Subsequent loads are instant

**"Page goes blank for 2 seconds"** ✅
- Data loading from Firebase
- Expected behavior

**"Admin passcode case-sensitive"** ✅
- By design
- Makes it more secure

**"Data takes 5 seconds to sync"** ✅
- Firebase network speed
- Totally normal
- Usually instant

---

## 🔧 Debug Mode

### How to check what's happening:

**1. Open Browser Console:**
- Press F12
- Click "Console" tab

**2. Look for errors:**
- Red text = errors
- Yellow text = warnings

**3. Check Firebase logs:**
- Go to Firebase Console
- Click Realtime Database
- Look at Rules → Logs tab

**4. Test Firebase directly:**
```javascript
// In browser console, type:
firebase.database().ref('test').set({hello: 'world'})
// Should see "true" or no error
```

---

## 🆘 Still Stuck?

1. **Check console first:** F12 → Console tab
2. **Read error message carefully**
3. **Verify Firebase config is correct**
4. **Test in private/incognito mode**
5. **Try different browser**
6. **Clear browser cache**
7. **Restart computer**

---

## 📞 Getting Help

### Provide this info:
- What were you doing?
- What happened?
- What should have happened?
- What does console say? (F12)
- Browser & OS you're using
- Netlify URL or local testing?

---

## 💡 Prevention Tips

- ✅ Save Firebase config somewhere safe
- ✅ Export data monthly
- ✅ Test after any changes
- ✅ Use browser console regularly (F12)
- ✅ Keep documentation updated
- ✅ Test on mobile regularly

---

**Still having issues?** Check the README.md or FIREBASE_SETUP.md for more details.

Happy tracking! 🚀
