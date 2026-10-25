# blog.meikelwis.com

A front-end-only blog. The page reads every post from **posts.json**, so publishing means editing that one file and uploading it.

## Files

| File | What it is |
| --- | --- |
| `index.html` | The blog itself (list, post pages, search, topics, dark mode). Upload once. |
| `posts.json` | Your blog settings and every post. The only file you update. |
| `images/` (optional) | Put post images here and reference them as `images/name.jpg`. |

## Hosting on blog.meikelwis.com

1. Point the `blog` subdomain at your host (same place as meikelwis.com, or any static host such as GitHub Pages, Netlify, Cloudflare Pages or cPanel).
2. Upload `index.html` and `posts.json` to the root folder of that subdomain.
3. Open `https://blog.meikelwis.com`.

Post links look like `https://blog.meikelwis.com/?p=welcome`, and topic links like `?tag=dbt`. They work on any static host, with no server rules needed.

## Publishing a post

Add an entry to the `posts` list in `posts.json`:

```json
{
  "slug": "my-first-dbt-tests",
  "title": "Writing dbt tests that catch real problems",
  "date": "2026-11-02",
  "summary": "One or two sentences for the post list.",
  "tags": ["dbt", "data quality"],
  "cover": "images/dbt-tests.jpg",
  "coverAlt": "Diagram of a dbt test run",
  "featured": false,
  "draft": false,
  "content": [
    "First paragraph.",
    "",
    "## A section heading",
    "",
    "More text in **Markdown**."
  ]
}
```

- `slug`, `title`, `date` and `content` are required; everything else is optional.
- `content` can be a list of lines (easiest to edit) or one string with `\n` line breaks.
- For long posts you can use `"contentFile": "posts/my-post.md"` instead of `content` and upload that Markdown file too.
- `draft: true` hides a post; `featured: true` pins it to the big card at the top.
- Reading time is calculated automatically; set `"readingTime": 8` to override it.
- Remember commas between posts, and a backslash before quotes inside text: `\"like this\"`.

Check the file at a JSON validator before uploading if you are unsure.

## Blog settings

The `blog` block at the top of `posts.json` sets the title, description, author, role and the portfolio, LinkedIn and email links used in the header, footer and author card.

## Previewing on your computer

Browsers don't let a page read `posts.json` when it is opened straight from a folder. Run a tiny local server instead:

```
cd blog
python3 -m http.server
```

then open http://localhost:8000.
