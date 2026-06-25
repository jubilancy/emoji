# ✨ Emoji Gallery

An interactive image gallery with automatic GitHub Pages deployment. Add entries to `emojis.txt`, push to GitHub, and your site rebuilds automatically.

**Live site:** https://jubilancy.github.io/emoji/

---

## File Structure

```
emoji/
├── index.html              # Gallery website
├── emojis.txt              # Your image list
├── draft-emojis.txt        # Work-in-progress entries
├── .github/
│   └── workflows/
│       └── deploy.yml      # Auto-deploy workflow
└── README.md
```

---

## emojis.txt Format

One entry per line:

```
:name:|https://direct-url-to-image.gif
```

**Rules:**
- Format is exactly `name|url` — no spaces around the `|`
- Names should use `:colon_syntax:` with underscores instead of spaces
- URLs must be direct image links (opening in a browser should show the image itself, not a webpage)
- Supported formats: GIF, PNG, JPG, WebP, **SVG**
- Empty lines are ignored

**Valid examples:**
```
:videoims:|https://cdn.discordapp.com/emojis/123456789.gif
:hamham:|https://media.example.com/ham.gif
:donut:|https://i.imgur.com/donut.png
:my_icon:|https://example.com/icon.svg
```

**Invalid examples:**
```
:videoims: | https://...     ← spaces around pipe
:hamham: https://...         ← missing pipe
|https://...                 ← missing name
https://...                  ← missing name and pipe
```

---

## Features

| Feature | How to Use |
|---|---|
| **Search** | Type in the search box |
| **Preview** | Hover over any image |
| **Copy URL** | Click "Copy URL" in the hover preview |
| **Copy Name** | Click "Copy Name" in the hover preview |
| **Select** | Check the checkbox on an image |
| **Select All** | Click "Select All" button |
| **Download** | Select images, click "Download Selected" (saves as ZIP) |

---

## Adding Images

Edit `emojis.txt` and push:

```bash
# Add a line
echo ":new_emoji:|https://example.com/image.gif" >> emojis.txt

# Commit and push
git add emojis.txt
git commit -m "add new emoji"
git push
```

The GitHub Action will validate the file, build, and deploy — usually within ~30 seconds.

---

## Image Sources

**Discord** — Right-click an emoji → Copy Image Address
```
https://cdn.discordapp.com/emojis/EMOJI_ID.gif
https://cdn.discordapp.com/emojis/EMOJI_ID.png
```

**Tenor / Giphy** — Find GIF → Share → Copy Direct Link
```
https://media.tenor.com/...gif
https://media.giphy.com/.../giphy.gif
```

**Free image hosting** — upload and get a direct link
- [Imgur](https://imgur.com)
- [imgbb](https://imgbb.com)
- [Cloudinary](https://cloudinary.com) (free tier)

---

## Customization

**Colors** — edit CSS variables in `index.html` under `:root`:
```css
--primary: #1a1a2e;    /* main background */
--accent: #e94560;     /* highlight color */
--success: #00d4aa;    /* success color */
```

**Grid size** — find `.gallery` in `index.html`:
```css
grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
/* increase 100px to make cards bigger */
```

**Header text** — find in `index.html`:
```html
<h1>✨ Emoji Gallery</h1>
<p class="subtitle">Hover to preview • Click to copy • Select to download</p>
```

---

## Troubleshooting

**Image not loading**
- Open the URL directly in a browser — it should show the raw image, not a webpage
- Check for CORS restrictions on the host (Discord CDN links sometimes expire)

**Emoji not appearing in gallery**
- Make sure the line has a `|` separator
- Run `grep -v '|' emojis.txt` to find any malformed lines

**Site not updating after push**
- Check the Actions tab for workflow errors
- Hard refresh the page (Ctrl+F5 / Cmd+Shift+R)
- Trigger manually: Actions → Deploy Emoji Gallery → Run workflow

**Validation failed in CI**
- Every non-empty line must contain a `|`
- No lines with only spaces

---

## Setup Checklist (first time)

- [ ] Fork or clone this repo
- [ ] Add your entries to `emojis.txt`
- [ ] Go to Settings → Pages → set source to **GitHub Actions**
- [ ] Push to `main`
- [ ] Check the Actions tab — should go green
- [ ] Visit `https://YOUR-USERNAME.github.io/emoji/`
