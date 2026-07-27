# Portfolio — Setup Guide

Your site is a single static file: `index.html` (HTML, CSS, and JS all in one place, zero dependencies, zero build step). That makes it trivial to preview, edit, and deploy.

## 1. Add your photo

Drop a photo into the same folder as `index.html` and name it exactly:

```
profile.jpg
```

That's it — the circle in the hero section already points to `profile.jpg` and will pick it up automatically. If the file isn't found, it quietly falls back to showing your initials, so the site never breaks.

- Use a square-ish photo (roughly 400×400px or larger) for the best crop.
- If you'd rather use a `.png` file, open `index.html`, find this line near the top of `<body>`:
  ```html
  <img src="profile.jpg" alt="Gurkirat Singh Lohat" id="avatarImg">
  ```
  and change `profile.jpg` to `profile.png` (or whatever filename you used).

## 2. Colors

Everything is driven by three CSS variables at the top of the `<style>` block:

```css
:root{
  --white: #ffffff;
  --black: #0a0a0a;
  --yellow: #ffcc00;
}
```

Change any of these and the whole site updates. The page also has `color-scheme: light only` set, so it will **not** switch to a dark theme based on the visitor's system settings.

## 3. Editing content

Everything is plain HTML — search for the text you want to change and edit it directly:

- **Hero** — name, tagline, role line (`#home` section)
- **About** — your bio paragraphs and the "Currently" card (`#about` section)
- **Hackathons** — add more entries by copying the `.hackathon-card` block (`#hackathons` section)
- **Projects** — each project is a `.project-card` block (`#projects` section). Once you have live demos or repo links, wrap the card in an `<a href="...">` tag, or add a "View project" link inside `.project-body`.
- **Contact info** — email, location, status (`#contact` section)

## 4. GitHub & LeetCode stats

The Stats section embeds live images from public stats APIs — no backend needed, they regenerate on every page load:

- GitHub overview + top languages: [github-readme-stats](https://github.com/anuraghazra/github-readme-stats)
- GitHub streak: [github-readme-streak-stats](https://github.com/DenverCoder1/github-readme-streak-stats)
- LeetCode card: [leetcard.jacoblin.cool](https://github.com/JacobLinCool/LeetCode-Card)

If your GitHub or LeetCode usernames ever change, just update the `username=` (GitHub) or path segment (`/gurkiratsingh79`) in each image URL inside the `#stats` section.

These free APIs occasionally have brief downtime — if a card doesn't load, refresh in a minute or two.

## 5. Contact form

The form currently validates input and shows a confirmation message, but it isn't wired to send email yet (a static site has no backend). The easiest fix, free for personal use:

1. Go to [formspree.io](https://formspree.io) and create a free account.
2. Create a new form, copy the endpoint it gives you (looks like `https://formspree.io/f/xxxxxxx`).
3. In `index.html`, find:
   ```html
   <form id="contactForm" novalidate>
   ```
   and change it to:
   ```html
   <form id="contactForm" action="https://formspree.io/f/xxxxxxx" method="POST">
   ```
4. Remove the `e.preventDefault();` line inside the `<script>` block's submit handler (or just delete the whole JS validation block) so the form submits normally to Formspree.

## 6. Deploying to Vercel

1. Push this folder to a GitHub repository (create one on github.com, then):
   ```bash
   git init
   git add .
   git commit -m "My portfolio"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
2. Go to [vercel.com](https://vercel.com), sign in with GitHub, and click **Add New → Project**.
3. Import the repository you just pushed.
4. Framework Preset: choose **Other** (it's a plain static site — no build command needed, no output directory to set).
5. Click **Deploy**. You'll get a live URL like `your-repo.vercel.app` within a minute.
6. (Optional) Add a custom domain under Project → Settings → Domains.

Every time you push a change to `main`, Vercel redeploys automatically.

## 7. Adding case studies later

When you're ready to write full case studies for GitGrade, Heart Disease Predictor, or LeetCode Suggestions, the simplest approach:

- Create separate files like `project-gitgrade.html` (copy the `<head>`/header/footer structure from `index.html` for consistency).
- Replace the `soon` class on the relevant `.project-cta` span with a real link, e.g.:
  ```html
  <a href="project-gitgrade.html" class="project-cta">Case study →</a>
  ```

## File checklist before deploying

- [ ] `profile.jpg` added
- [ ] Colors reviewed
- [ ] Bio/skills double-checked
- [ ] Contact form wired to Formspree (or removed if you don't need it yet)
- [ ] GitHub/LeetCode usernames confirmed correct in the Stats section
