# Step-by-Step GitHub Pages Deployment Guide

Follow these steps in order to deploy your ComicVerse project to GitHub Pages.

## Prerequisites Checklist
- [ ] GitHub account created
- [ ] Git installed on your computer
- [ ] Node.js and npm installed

---

## Step 1: Update Repository Name (if needed)

**Important:** If your GitHub repository will have a different name than `COMIC_VERSE`, update the base path:

1. Open `vite.config.js`
2. On line 12, change `/COMIC_VERSE/` to match your repository name
   ```javascript
   base: process.env.GITHUB_PAGES === 'true' ? '/YOUR_REPO_NAME/' : '/',
   ```

**Example:** If your repo will be `my-comic-store`, change it to:
```javascript
base: process.env.GITHUB_PAGES === 'true' ? '/my-comic-store/' : '/',
```

---

## Step 2: Initialize Git Repository

Open terminal in your project directory and run:

```bash
cd /Users/rohitreddy/Downloads/COMIC_VERSE-main
git init
```

---

## Step 3: Add All Files to Git

```bash
git add .
```

---

## Step 4: Create Initial Commit

```bash
git commit -m "Initial commit: ComicVerse project setup"
```

---

## Step 5: Create GitHub Repository

1. Go to [GitHub.com](https://github.com) and sign in
2. Click the **"+"** icon in the top right corner
3. Select **"New repository"**
4. Fill in the details:
   - **Repository name:** `COMIC_VERSE` (or your preferred name)
   - **Description:** (optional) "Marvel & DC Comic Store"
   - **Visibility:** Choose Public or Private
   - **DO NOT** initialize with README, .gitignore, or license (we already have these)
5. Click **"Create repository"**

---

## Step 6: Connect Local Repository to GitHub

After creating the repo, GitHub will show you commands. Use these (replace `YOUR_USERNAME` with your GitHub username):

```bash
git remote add origin https://github.com/YOUR_USERNAME/COMIC_VERSE.git
git branch -M main
git push -u origin main
```

**Note:** If your repo name is different, replace `COMIC_VERSE` in the URL above.

---

## Step 7: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click on the **"Settings"** tab (top menu)
3. Scroll down to **"Pages"** in the left sidebar
4. Under **"Source"**, select **"GitHub Actions"** (NOT "Deploy from a branch")
5. The page will save automatically

---

## Step 8: Trigger Deployment

The deployment will automatically start when you:
- Push to the `main` branch (which you just did in Step 6)

OR manually trigger it:
1. Go to the **"Actions"** tab in your repository
2. You should see "Deploy to GitHub Pages" workflow
3. Click on it and then click **"Run workflow"** button (if needed)

---

## Step 9: Wait for Deployment

1. Go to the **"Actions"** tab
2. Click on the running workflow
3. Wait for it to complete (usually 1-2 minutes)
4. You'll see a green checkmark ✅ when it's done

---

## Step 10: Access Your Live Site

Once deployment is complete:

1. Go back to **Settings** → **Pages**
2. You'll see your site URL at the top: `https://YOUR_USERNAME.github.io/COMIC_VERSE/`
3. Click the link or copy it to your browser

**Your site is now live! 🎉**

---

## Troubleshooting

### Site shows 404 or blank page
- **Check:** Repository name in `vite.config.js` matches your GitHub repo name
- **Check:** GitHub Pages source is set to **"GitHub Actions"** (not "Deploy from a branch")
- **Wait:** It can take 1-2 minutes for the site to be available after deployment

### Build fails in Actions
- Go to **Actions** tab → Click on the failed workflow → Check the error logs
- Common issues:
  - Missing dependencies (should be fixed with our setup)
  - Repository name mismatch in vite.config.js

### Assets not loading
- Verify the base path in `vite.config.js` is correct
- Clear browser cache (Ctrl+Shift+R or Cmd+Shift+R)
- Check browser console for 404 errors

---

## Future Updates

To update your deployed site:
1. Make changes to your code
2. Commit and push:
   ```bash
   git add .
   git commit -m "Your update message"
   git push
   ```
3. The site will automatically redeploy via GitHub Actions

---

## Quick Command Reference

```bash
# Initialize git (if not done)
git init

# Add files
git add .

# Commit
git commit -m "Your message"

# Connect to GitHub (first time only)
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git
git branch -M main
git push -u origin main

# Future updates
git add .
git commit -m "Update message"
git push
```

---

**Need help?** Check the error messages in the GitHub Actions tab for specific issues.

