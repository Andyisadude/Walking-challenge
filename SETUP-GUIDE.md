# 🏃 Tulsa Tech Walking Challenge — Setup Guide
### How to get your website live on the internet (beginner-friendly, free)

---

## What you'll need
- A computer with internet access
- About 30–45 minutes
- No coding experience required — just follow each step carefully

---

## PART 1 — Install the tools on your computer

### Step 1: Install Node.js
Node.js is the engine that runs your app locally so you can test it.

1. Go to **https://nodejs.org**
2. Click the big green **"LTS"** download button (the one that says "Recommended for most users")
3. Open the downloaded file and click through the installer (just keep clicking Next/Continue)
4. When it finishes, **restart your computer**

### Step 2: Verify Node installed correctly
1. On Windows: press the **Windows key**, type `cmd`, and open **Command Prompt**
   On Mac: press **Cmd + Space**, type `terminal`, open **Terminal**
2. Type this and press Enter:
   ```
   node --version
   ```
3. You should see something like `v20.11.0` — any number is fine. If you get an error, try restarting and repeating.

---

## PART 2 — Set up Firebase (your database)

Firebase is a free Google service that stores all the student submissions.

### Step 3: Create a Firebase account
1. Go to **https://console.firebase.google.com**
2. Sign in with a Google account (create one if needed)

### Step 4: Create a new project
1. Click **"Add project"** or **"Create a project"**
2. Name it something like `tulsa-tech-walking-challenge`
3. On the "Google Analytics" screen, you can turn it **off** — you don't need it
4. Click **"Create project"** and wait for it to finish
5. Click **"Continue"**

### Step 5: Create a Firestore database
1. In the left sidebar, click **"Build"** → **"Firestore Database"**
2. Click **"Create database"**
3. Choose **"Start in test mode"** ← important, choose this one
4. Select any location closest to Oklahoma (like `us-central1`)
5. Click **"Done"**

### Step 6: Get your Firebase config keys
1. Click the **gear icon** ⚙️ at the top left → **"Project settings"**
2. Scroll down to **"Your apps"**
3. Click the **`</>`** icon (Web app)
4. Give it a nickname like `walking-challenge-web`
5. Click **"Register app"**
6. You'll see a block of code that looks like this:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "your-project.firebaseapp.com",
  projectId: "your-project-id",
  storageBucket: "your-project.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

7. **Copy all of this** — you'll need it in the next part
8. Click **"Continue to console"**

---

## PART 3 — Set up the project files

### Step 7: Download the project folder
You should have received a folder called `walking-challenge` containing these files:
```
walking-challenge/
  index.html
  package.json
  vite.config.js
  src/
    main.jsx
    App.jsx
    firebase.js   ← you'll edit this one
```

Put this folder somewhere easy to find, like your **Desktop**.

### Step 8: Paste your Firebase config
1. Open the `src/firebase.js` file in any text editor
   (Right-click → Open with → Notepad on Windows, TextEdit on Mac)
2. You'll see placeholder text like `"PASTE_YOUR_API_KEY_HERE"`
3. Replace each placeholder with the matching value from your Firebase config
4. When done it should look something like:

```javascript
const firebaseConfig = {
  apiKey:            "AIzaSyXXXXXXXXXXXXXXXXX",
  authDomain:        "tulsa-tech-challenge.firebaseapp.com",
  projectId:         "tulsa-tech-challenge",
  storageBucket:     "tulsa-tech-challenge.appspot.com",
  messagingSenderId: "123456789012",
  appId:             "1:123456789012:web:abcdef123456",
};
```

5. **Save the file**

### Step 9: Install dependencies
1. Open Command Prompt (Windows) or Terminal (Mac)
2. Navigate to your project folder. If it's on your Desktop, type:
   - **Windows:** `cd Desktop\walking-challenge`
   - **Mac:** `cd Desktop/walking-challenge`
3. Press Enter, then type:
   ```
   npm install
   ```
4. Press Enter and wait — it will download the required packages (may take 1–2 minutes)

### Step 10: Test it locally
1. In the same Command Prompt / Terminal window, type:
   ```
   npm run dev
   ```
2. Press Enter. You'll see a message like:
   ```
   ➜  Local:   http://localhost:5173/
   ```
3. Open your web browser and go to **http://localhost:5173**
4. Your walking challenge website should load! Test it out — try submitting some steps.
5. When you're done testing, press **Ctrl + C** in the terminal to stop it.

---

## PART 4 — Put it on the internet with Vercel

Vercel hosts your website for free and gives it a real URL anyone can visit.

### Step 11: Create a GitHub account (if you don't have one)
1. Go to **https://github.com** and sign up for a free account

### Step 12: Upload your project to GitHub
1. Go to **https://github.com/new**
2. Name the repository `walking-challenge`
3. Keep it **Public**
4. Click **"Create repository"**
5. On the next page, look for the section that says **"…or upload an existing file"**
6. Click **"uploading an existing file"**
7. Drag your entire `walking-challenge` folder contents into the upload box
   (Select all files inside the folder — index.html, package.json, vite.config.js, and the src folder)
8. Click **"Commit changes"**

### Step 13: Deploy to Vercel
1. Go to **https://vercel.com** and click **"Sign Up"**
2. Choose **"Continue with GitHub"** and authorize it
3. Once logged in, click **"Add New Project"**
4. Find your `walking-challenge` repository and click **"Import"**
5. Vercel will auto-detect it's a Vite project — leave all settings as-is
6. Click **"Deploy"**
7. Wait about 1–2 minutes while it builds

### Step 14: Your website is live! 🎉
1. Vercel will show you a URL like `https://walking-challenge-abc123.vercel.app`
2. Click it — your website is now live on the internet!
3. Share this URL with students so they can start submitting steps

---

## PART 5 — Optional: Get a custom domain name

If you want a nicer URL like `tulsa-tech-steps.com` instead of the Vercel one:

1. Buy a domain at **https://namecheap.com** or **https://domains.google** (~$10–15/year)
2. In Vercel, go to your project → **Settings** → **Domains**
3. Add your domain and follow Vercel's instructions to connect it

---

## Troubleshooting

**"npm is not recognized" error**
→ Node.js didn't install correctly. Restart your computer and try again, or re-download from nodejs.org.

**Website loads but submissions don't save**
→ Your Firebase config values are wrong. Double-check that you copied them exactly from Firebase, with no extra spaces.

**"Permission denied" error in Firestore**
→ You may have chosen "production mode" instead of "test mode" when setting up Firestore. Go to Firebase Console → Firestore → Rules, and replace the contents with:
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```
Then click **Publish**.

**Vercel build fails**
→ Make sure all files were uploaded to GitHub including the `src` folder and all files inside it.

---

## Need help?
If you get stuck, take a screenshot of any error message and bring it to your IT department or contact someone with web development experience. The error message will tell them exactly what went wrong.
