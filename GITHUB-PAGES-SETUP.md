# GitHub Pages Setup Instructions

## For Dan & Dale: Accessing the Dashboard Online

Once GitHub Pages is enabled, you'll be able to access the dashboard at:

**https://kowalcg.github.io/ChocolateOnJames/**

This will automatically redirect to the full dashboard where you can:
- View all project deliverables
- Access all folders and documents
- Navigate the complete project structure
- Everything works in your browser - no downloads needed!

---

## How to Enable GitHub Pages (One-Time Setup)

### Option 1: Via GitHub Website (Easiest)

1. Go to: https://github.com/kowalcg/ChocolateOnJames
2. Click on **Settings** (top right of the repository)
3. Scroll down to **Pages** in the left sidebar
4. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)`
5. Click **Save**
6. Wait 1-2 minutes for GitHub to build the site
7. Your dashboard will be live at: `https://kowalcg.github.io/ChocolateOnJames/`

### Option 2: Via Command Line

If you prefer command line, run:

```bash
cd "/Users/MacBook1/Library/CloudStorage/GoogleDrive-info@geartopdesign.com/Shared drives/Greg/1. Consulting/2. Chocolate on James"
git checkout -b gh-pages
git push origin gh-pages
```

Then in GitHub Settings > Pages, select the `gh-pages` branch.

---

## What This Does

- Makes the entire project accessible via web browser
- All links in the dashboard automatically work
- No need to download files or folders
- Can be accessed from any computer with internet
- Updates automatically when you push changes to GitHub

---

## Sharing the Link

Once enabled, share this URL with Dan & Dale:

**https://kowalcg.github.io/ChocolateOnJames/**

They can bookmark it and access it anytime, from anywhere!

---

## Troubleshooting

- **404 Error?** Wait 2-3 minutes after enabling - GitHub needs time to build
- **Links not working?** Make sure you're accessing via the GitHub Pages URL, not the raw GitHub file view
- **Still having issues?** Check GitHub Settings > Pages to ensure it's enabled and shows "Your site is live at..."

