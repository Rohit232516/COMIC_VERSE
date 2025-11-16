# GitHub Pages Deployment Guide

This project is configured for automatic deployment to GitHub Pages using GitHub Actions.

## Prerequisites

1. A GitHub account
2. Your project pushed to a GitHub repository

## Step-by-Step Deployment

### 1. Update Repository Name in Vite Config (if needed)

If your GitHub repository name is **NOT** `COMIC_VERSE`, you need to update the base path in `vite.config.js`:

```javascript
base: process.env.GITHUB_PAGES === 'true' ? '/YOUR_REPO_NAME/' : '/',
```

Replace `YOUR_REPO_NAME` with your actual repository name.

**Example:** If your repo is `my-comic-store`, change it to:
```javascript
base: process.env.GITHUB_PAGES === 'true' ? '/my-comic-store/' : '/',
```

### 2. Push Code to GitHub

If you haven't already, initialize git and push your code:

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git push -u origin main
```

### 3. Enable GitHub Pages

1. Go to your repository on GitHub
2. Click on **Settings** tab
3. Scroll down to **Pages** in the left sidebar
4. Under **Source**, select **GitHub Actions** (not "Deploy from a branch")
5. Save the settings

### 4. Trigger Deployment

The deployment will automatically trigger when you:
- Push to the `main` or `master` branch
- Or manually trigger it from the **Actions** tab → **Deploy to GitHub Pages** → **Run workflow**

### 5. Access Your Site

Once deployed, your site will be available at:
```
https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/
```

**Example:** If your username is `johndoe` and repo is `COMIC_VERSE`:
```
https://johndoe.github.io/COMIC_VERSE/
```

## Manual Deployment (Alternative)

If you prefer to deploy manually:

```bash
# Build for GitHub Pages
npm run build:gh-pages

# The dist/ folder contains your built files
# You can deploy this folder using gh-pages package or manually
```

## Troubleshooting

### Site shows 404 or blank page
- Check that the base path in `vite.config.js` matches your repository name
- Ensure GitHub Pages is set to use **GitHub Actions** as the source
- Check the Actions tab for any build errors

### Assets not loading
- Verify the base path is correct (should start and end with `/`)
- Clear browser cache
- Check browser console for 404 errors

### Build fails in GitHub Actions
- Check that `package.json` has all required dependencies
- Verify Node.js version compatibility
- Check the Actions logs for specific error messages

## Notes

- The workflow automatically builds and deploys on every push to main/master
- The build uses the `build:gh-pages` script which sets the correct base path
- Your site will be publicly accessible once deployed

