# 🎨 Emoji Gallery - Complete Setup Guide

## Overview
This is a stunning, interactive emoji/GIF gallery with automatic GitHub Pages deployment. Update your emojis, push to GitHub, and your site automatically rebuilds!

## Files Included

1. **index.html** - The interactive gallery website
2. **emojis.txt** - Your emoji configuration file
3. **deploy.yml** - GitHub Actions workflow (goes in `.github/workflows/`)

## Quick Setup

### Step 1: Create a GitHub Repository
```bash
# Create a new public repository on GitHub (e.g., "emoji-gallery")
# Clone it locally
git clone https://github.com/YOUR-USERNAME/emoji-gallery.git
cd emoji-gallery
```

### Step 2: Add Files
Copy these files to your repository:
- `index.html` → root directory
- `emojis.txt` → root directory
- `deploy.yml` → `.github/workflows/` directory

Create the workflows directory if it doesn't exist:
```bash
mkdir -p .github/workflows
```

### Step 3: Configure Your Emojis

Edit `emojis.txt` with the format:
```
:emoji_name:|https://direct-url-to-image.gif
:another:|https://cdn.example.com/image.gif
```

**Important Notes:**
- Each line: `name|url`
- Names should start with `:` and use emoji syntax (e.g., `:videoims:`)
- URLs must be direct links to the media file
- URLs can be from Discord, Giphy, Tenor, or any image CDN
- Supported formats: GIF, PNG, JPG, WebP

### Step 4: Push to GitHub
```bash
git add .
git commit -m "Initial emoji gallery setup"
git push origin main
```

### Step 5: Enable GitHub Pages

1. Go to your repository on GitHub
2. Settings → Pages
3. Source: Deploy from a branch
4. Branch: `main` (or whatever your default branch is)
5. Folder: `/ (root)`
6. Click Save

The workflow will trigger automatically and deploy your site!

## Updating Emojis

Every time you update `emojis.txt` and push:

```bash
# Edit emojis.txt with new emojis
nano emojis.txt  # or use your editor

# Commit and push
git add emojis.txt
git commit -m "Add new emojis"
git push origin main
```

The GitHub Action automatically:
✅ Validates the file format  
✅ Builds the site  
✅ Deploys to GitHub Pages  
✅ All in ~30 seconds!

## Emoji Sources

### Finding Direct URLs

**Discord Emojis:**
- Right-click emoji → Copy Image Address
- URL format: `https://cdn.discordapp.com/emojis/EMOJI_ID.gif`

**Tenor/Giphy:**
- Find GIF → Share → Copy direct link (ends in .gif)
- Often works as: `https://media.tenor.com/...`

**Custom Hosting:**
- Upload to any image CDN (Imgur, imgbb, Cloudinary, etc.)
- Get the direct link ending in `.gif` or `.png`

### Example Emojis
```
:heart:|https://cdn.discordapp.com/emojis/1234567890123456789.gif
:tada:|https://media.giphy.com/media/g9GWusSxFjnK8/giphy.gif
:fire:|https://media.tenor.com/images/fire123.gif
:smile:|https://i.imgur.com/smile.png
```

## Features

### User Features
- 🔍 **Search** - Filter emojis by name
- 👆 **Hover Preview** - Large preview in corner with URL
- 📋 **Copy URLs** - Click to copy direct link
- 📝 **Copy Names** - Copy emoji name syntax
- ☑️ **Multi-Select** - Check boxes to select multiple
- 📥 **Batch Download** - Download selected emojis as ZIP
- 📱 **Responsive** - Works on mobile and desktop
- 🎨 **Dark Theme** - Beautiful gradient UI

### Technical Features
- ✅ Automatic validation of emojis.txt
- ✅ Responsive grid layout
- ✅ Smooth animations and transitions
- ✅ No build step required
- ✅ Static hosting (free on GitHub Pages)
- ✅ Fast loading with minimal dependencies

## File Format Reference

### emojis.txt

```
:name:|URL
:another_name:|URL
:third:|URL
```

**Rules:**
- One emoji per line
- Exact format: `name|url`
- No spaces around `|`
- Empty lines are skipped
- URLs must be valid and direct (not redirects)

### Valid Examples
```
:videoims:|https://cdn.discordapp.com/emojis/123456789.gif
:hamham:|https://media.example.com/ham.gif
:donut:|https://i.imgur.com/donut.png
```

### Invalid Examples ❌
```
:videoims: | https://... (spaces around |)
:hamham: https://... (missing |)
|https://... (missing name)
https://... (missing name|)
```

## Troubleshooting

### Images not loading?
- Check the URL is direct (copy link address, not just the page)
- Ensure it ends in `.gif`, `.png`, `.jpg`, etc.
- Try opening the URL in a new tab

### GitHub Pages not updating?
- Check Actions tab for workflow status
- Ensure branch is set to `main` in Pages settings
- Try triggering manually: Actions → Deploy Emoji Gallery → Run workflow

### File validation fails?
- Check for missing `|` separators
- Ensure format is exactly: `name|url`
- No trailing spaces after URL
- No empty lines with spaces (use completely empty lines)

### Emojis.txt format error
Run this to find the problematic line:
```bash
grep -v '|' emojis.txt
```

This shows lines without the pipe character.

## Customization

### Change Gallery Theme
Edit the CSS variables in `index.html` under `:root`:
```css
--primary: #1a1a2e;           /* Main background */
--accent: #e94560;             /* Highlight color */
--success: #00d4aa;           /* Success color */
```

### Change Grid Size
In `index.html`, find `.gallery` CSS:
```css
grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
/* minmax(100px, ...) controls emoji card size */
```

### Add Custom Header Text
Find in `index.html`:
```html
<h1>✨ Emoji Gallery</h1>
<p class="subtitle">Hover to preview • Click to copy • Select to download</p>
```

## Deployment Status

Your gallery will be available at:
```
https://YOUR-USERNAME.github.io/emoji-gallery/
```

Replace `YOUR-USERNAME` with your GitHub username.

## Tips & Best Practices

1. **Test URLs first** - Copy URL in browser before adding
2. **Use descriptive names** - `:cool_fire:` better than `:emoji1:`
3. **Organize categories** - Use prefixes: `:pfp_cute:`, `:pfp_cool:`
4. **Keep URLs stable** - Use permanent CDN links, avoid temporary links
5. **Batch updates** - Add multiple emojis before pushing

## Advanced: Custom Domain

To use a custom domain instead of `username.github.io/emoji-gallery`:

1. Buy a domain (Namecheap, GoDaddy, etc.)
2. Go to repo Settings → Pages
3. Enter your domain in "Custom domain"
4. Follow the DNS setup instructions
5. GitHub will handle the HTTPS certificate automatically

## License & Attribution

This emoji gallery is yours to use freely! Share it, remix it, customize it.

---

**Questions?** Check the GitHub Issues on the template repository or refer to:
- GitHub Pages docs: https://pages.github.com/
- GitHub Actions docs: https://docs.github.com/actions
