# GitHub Pages Deployment Guide

This guide will help you deploy your Travel Explorer project to GitHub Pages.

## Prerequisites

1. A GitHub account
2. Git installed on your local machine
3. Node.js and npm installed

## Step-by-Step Deployment

### 1. Create a GitHub Repository

1. Go to [GitHub](https://github.com) and sign in
2. Click the "+" icon in the top right corner and select "New repository"
3. Name your repository `travel-explorer`
4. Make it public (required for free GitHub Pages)
5. Don't initialize with README, .gitignore, or license (we'll push our existing code)
6. Click "Create repository"

### 2. Update the Homepage URL

Before pushing to GitHub, update the homepage URL in `package.json`:

```json
"homepage": "https://YOUR_USERNAME.github.io/travel-explorer"
```

Replace `YOUR_USERNAME` with your actual GitHub username.

### 3. Initialize Git and Push to GitHub

Run these commands in your project directory:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Commit the changes
git commit -m "Initial commit"

# Add the remote repository (replace YOUR_USERNAME with your GitHub username)
git remote add origin https://github.com/YOUR_USERNAME/travel-explorer.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### 4. Enable GitHub Pages

1. Go to your repository on GitHub
2. Click on "Settings" tab
3. Scroll down to "Pages" section in the left sidebar
4. Under "Source", select "Deploy from a branch"
5. Choose "gh-pages" branch and "/ (root)" folder
6. Click "Save"

### 5. Install Dependencies and Deploy

Run these commands in your project directory:

```bash
# Install dependencies
npm install

# Deploy to GitHub Pages
npm run deploy
```

### 6. Automatic Deployment (Optional)

The GitHub Actions workflow (`.github/workflows/deploy.yml`) will automatically deploy your site whenever you push to the main branch.

To enable this:

1. Go to your repository settings
2. Click on "Actions" → "General"
3. Under "Workflow permissions", select "Read and write permissions"
4. Click "Save"

## Accessing Your Site

Your site will be available at: `https://YOUR_USERNAME.github.io/travel-explorer`

## Troubleshooting

### If the site doesn't load:
1. Check that the repository is public
2. Verify the homepage URL in package.json matches your GitHub username
3. Wait a few minutes for GitHub Pages to build and deploy
4. Check the "Actions" tab in your repository for any build errors

### If images don't load:
1. Make sure all image paths are relative
2. Check that the base path in `vite.config.js` is set correctly

### If routing doesn't work:
1. This is a known issue with single-page applications on GitHub Pages
2. Consider using HashRouter instead of BrowserRouter in your React app

## Manual Deployment

If you prefer manual deployment:

```bash
# Build the project
npm run build

# Deploy to GitHub Pages
npm run deploy
```

## Updating Your Site

To update your deployed site:

1. Make your changes
2. Commit and push to GitHub:
   ```bash
   git add .
   git commit -m "Update site"
   git push
   ```
3. If using automatic deployment, the site will update automatically
4. If using manual deployment, run `npm run deploy`

## Support

If you encounter any issues, check:
- GitHub Pages documentation: https://pages.github.com/
- GitHub Actions documentation: https://docs.github.com/en/actions
