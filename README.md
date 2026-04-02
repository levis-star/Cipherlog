# CipherLog — Personal Cybersecurity Blog

A modern, responsive personal cybersecurity blog website built with vanilla HTML, CSS, and JavaScript.
No build tools, no dependencies, no server required.

---

## Quick Start

```bash
# Option 1: Just open the file
open index.html

# Option 2: Serve locally (recommended to avoid any CORS edge cases)
python3 -m http.server 8080
# Then visit http://localhost:8080
```

That's it. The entire site is a single `index.html` file.

---

## Features

| Feature | Status |
|---|---|
| Home page with hero, stats, latest posts | ✅ |
| Blog listing with search & category filter | ✅ |
| Full post view with markdown rendering | ✅ |
| New post creation (persisted to localStorage) | ✅ |
| Key takeaways section on posts | ✅ |
| Achievements timeline + badge grid | ✅ |
| About Me with skills & interests | ✅ |
| Feedback form with localStorage persistence | ✅ |
| Community feedback display | ✅ |
| Dark / Light mode toggle (persisted) | ✅ |
| Responsive (mobile, tablet, desktop) | ✅ |
| Animated terminal hero, cursor blink | ✅ |
| SEO meta tags | ✅ |

---

## Pages

### Home (`/`)
- Hero section with terminal code aesthetic
- Stats bar (posts written, certs, CTF solves, categories)
- Latest 3 blog posts with "View All" link

### Blog (`/blog`)
- Full post grid
- Live search by title, excerpt, and tags
- Category filter buttons (Network Security, Cryptography, Malware Analysis, CTF, Forensics, Web Security)

### Post View
- Full article rendering
- Key Takeaways highlight box
- Tag list
- Back to blog navigation

### New Post (Admin)
- Title, category, content, key takeaways, tags fields
- Live preview button
- Publishes to localStorage and appears in blog immediately

### Achievements
- Timeline of certifications and milestones
- Badge/certification card grid

### About Me
- Personal bio
- Interest tags
- Skill bars with tools (Wireshark, Metasploit, Burp Suite, etc.)
- Social links (GitHub, LinkedIn)

### Feedback
- Submission form (name, email optional, message)
- Stored in localStorage
- Community messages displayed below form

---

## Customization

All personal data is in the JavaScript section at the bottom of `index.html`.

### Change your name/bio
Search for `Alex Chen` and update:
- Hero section HTML
- About page HTML
- Footer HTML

### Edit achievements
Find `DEFAULT_ACHIEVEMENTS` array and modify objects:
```js
{
  id: 'ach-1',
  title: 'Your Certification Name',
  org: 'Issuing Organization',
  description: 'Brief description...',
  date: '2025-01-15',   // YYYY-MM-DD
  icon: '🏆'
}
```

### Edit badges
Find `DEFAULT_BADGES` array:
```js
{ icon: '🛡️', name: 'Badge Name', sub: 'Subtitle or date' }
```

### Add seed blog posts
Modify `DEFAULT_POSTS` array. Each post:
```js
{
  id: 'post-unique-id',
  title: 'Post Title',
  category: 'Network Security',   // Must match a filter category
  date: '2025-01-01',
  excerpt: 'Short description shown in listings...',
  content: `Full markdown-style content...`,
  takeaways: ['Takeaway 1', 'Takeaway 2'],
  tags: ['tag1', 'tag2'],
  readTime: '7 min read'
}
```

### Change colors/theme
Edit CSS custom properties at the top of the `<style>` block:
```css
:root {
  --accent: #00ff88;     /* Primary green accent */
  --accent2: #00c4ff;    /* Blue secondary */
  --accent3: #ff6b35;    /* Orange tertiary */
}
```

### Social links
Find `href="https://github.com"` and `href="https://linkedin.com"` and replace with your actual URLs.

---

## Content Format (New Posts)

The post editor supports basic markdown-like formatting:

| Syntax | Output |
|---|---|
| `## Heading` | `<h2>` |
| `### Sub-heading` | `<h3>` |
| `**bold text**` | Bold |
| `` `inline code` `` | Inline code |
| ` ```code block``` ` | Code block |
| `> quote text` | Blockquote |

---

## Data Persistence

All user-created data is stored in browser `localStorage`:

| Key | Contents |
|---|---|
| `cipherlog_posts` | Array of blog posts (includes your new posts) |
| `cipherlog_feedback` | Array of feedback submissions |
| `cipherlog_theme` | `"dark"` or `"light"` preference |

Note: localStorage is browser/device specific. To back up posts, use the browser DevTools console:
```js
// Export posts
JSON.stringify(JSON.parse(localStorage.getItem('cipherlog_posts')), null, 2)

// Reset to defaults
localStorage.removeItem('cipherlog_posts')
```

---

## Future Enhancements (Backend)

To add a real backend:

### Node.js + Express + MongoDB
```
backend/
  server.js         Express REST API
  routes/posts.js   GET/POST/PUT/DELETE /api/posts
  routes/feedback.js
  models/Post.js    Mongoose schema
  .env              MongoDB URI, JWT secret
```

### Firebase (Serverless)
- Firestore for posts and feedback
- Firebase Auth for admin login
- Firebase Hosting for deployment

### Key API endpoints to build:
- `GET /api/posts` — list all posts
- `POST /api/posts` — create post (auth required)
- `GET /api/posts/:id` — single post
- `POST /api/feedback` — submit feedback
- `GET /api/feedback` — list feedback (auth required)

---

## Deployment

**GitHub Pages**: Push to a repo, enable Pages from the `main` branch root.

**Netlify**: Drag and drop the `index.html` file.

**Vercel**: `vercel deploy` from the directory.

---

## Tech Stack

- **HTML5** — Semantic structure
- **CSS3** — Custom properties, grid, flexbox, animations, dark/light mode
- **Vanilla JS** — No frameworks, no build step
- **Google Fonts** — IBM Plex Mono + Syne
- **localStorage** — Client-side persistence

---

## License

MIT — use freely for personal and commercial projects.
