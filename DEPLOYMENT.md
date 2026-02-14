# BetterOS Landing Page - Deployment Guide

## Quick Start with GitHub Pages + GitHub Actions

This site is configured to automatically deploy to GitHub Pages using GitHub Actions whenever you push to your main branch.

### Setup Instructions

1. **Create a GitHub Repository**
   - Go to [github.com/new](https://github.com/new)
   - Name it `betteros` (or any name)
   - Click "Create repository"

2. **Push Your Code**
   ```bash
   git init
   git add .
   git commit -m "Initial commit: BetterOS landing page"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/betteros.git
   git push -u origin main
   ```

3. **Enable GitHub Pages**
   - Go to your repository's **Settings**
   - Scroll to **Pages** section
   - Under "Source", select `Deploy from a branch`
   - Select branch: `gh-pages`
   - Click **Save**

4. **Configure Custom Domain (Optional)**
   - In the same **Pages** section
   - Under "Custom domain", enter `betteros.space`
   - Follow GitHub's nameserver instructions

5. **GitHub Actions Will Automatically Deploy**
   - The workflow in `.github/workflows/deploy.yml` runs automatically
   - Your site will be live at:
     - `https://YOUR_USERNAME.github.io/betteros` (if using default domain)
     - `https://betteros.space` (if using custom domain)

### How Client-Side Routing Works

This SPA (Single Page Application) uses client-side routing:

- `/` → Landing page
- `/manifesto` → Manifesto page
- `/pricing` → Pricing page  
- `/privacy` → Privacy page
- `/terms` → Terms & Conditions page

#### Routing Setup:
- `404.html` - Catches all non-existent routes and redirects to index.html
- `index.html` - Alpine.js detects the URL and shows the correct page
- No server configuration needed - all routing happens in the browser!

### What Gets Deployed

✅ `index.html` - Main application  
✅ `404.html` - Route handler for GitHub Pages  
✅ `public/icon.png` - Your logo  
✅ `.github/workflows/deploy.yml` - Automation  

### Automatic Deployments

Every time you push to `main`:
1. GitHub Actions triggers automatically
2. Files are uploaded to GitHub Pages
3. Site updates within 30 seconds
4. No manual steps needed!

### Common Issues & Fixes

**Q: 404 errors on direct navigation?**
- A: 404.html should handle this. Ensure it's in your root directory.

**Q: Theme doesn't persist?**
- A: Browser localStorage might be disabled. Check browser privacy settings.

**Q: Styles look different?**
- A: Clear your browser cache (Ctrl+Shift+Delete)

**Q: Custom domain shows 404?**
- A: Wait 5-10 minutes for DNS propagation and GitHub to update.

### Local Development

To test locally before deploying:

```bash
# Open index.html directly in browser (limited functionality)
# Or use a local server:

python3 -m http.server 8000
# Visit http://localhost:8000
```

### Troubleshooting

If deployment fails:
1. Check **Actions** tab in your repository
2. Click the failed workflow
3. See the error details
4. Fix the issue and push again

---

**Site is now production-ready!** 🚀
