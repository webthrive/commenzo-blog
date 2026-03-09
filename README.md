# Commenzo Blog

Static HTML blog for `commenzo.com/blog`. Deployed via Cloudflare Pages from this repo.

## Structure

```
/blog
  index.html              ← Blog listing page (update when adding posts)
  _redirects              ← Cloudflare routing rules
  /assets
    blog.css              ← Shared stylesheet — edit to update styles globally
    header.html           ← Shared nav — edit once to update sitewide
    footer.html           ← Shared footer — edit once to update sitewide
  /posts
    post-slug.html        ← Individual post files
```

---

## Adding a New Post

### 1. Ask Claude to generate the post

Provide Claude with:
- **Topic / title**
- **Commenzo sentiment data** (keyword, post count, % positive/neutral/negative)
- **Source post URLs** (optional, for citation)
- **Target audience** (marketer, founder, consultant, etc.)

Claude will produce a complete `posts/your-slug.html` file ready to drop in.

### 2. Add the file

Copy the generated `.html` file into `/posts/`.

### 3. Update the index

In `index.html`:
- Replace the **Featured Post** block (`post-featured`) with the new post
- Add a new `post-card` in the grid for the new post
- Move the old featured post down into the grid if keeping it visible

### 4. Push to GitHub

```bash
git add .
git commit -m "Add post: your-post-title"
git push
```

Cloudflare Pages auto-deploys. Live in ~30 seconds.

---

## Updating the Nav or Footer

Edit `/assets/header.html` or `/assets/footer.html` — changes apply to every page on next deploy.

---

## Post File Template

When asking Claude for a new post, reference this structure:

```
Title:
Slug: (e.g. reddit-vs-linkedin-sentiment-gap)
Tag: (e.g. Marketing Intelligence / Sentiment Analysis / Platform Intelligence)
Date: (e.g. March 2026)
Read time: (e.g. 5 min read)
Excerpt: (1-2 sentences for the index card)
Sentiment data: keyword / post count / % positive / % neutral / % negative
Body: [topic brief or paste Commenzo output]
```

---

## Design System

- **Navy:** `#09222E`
- **Green:** `#89D99D`
- **Font:** `ui-sans-serif, system-ui`
- Sentiment box: use `.sentiment-box` component for embedded Commenzo data
- Post CTA: always ends with `.post-cta-strip` → free trial CTA
