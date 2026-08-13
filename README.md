# Personal website

One-page academic site. A single hand-written `index.html` — no build step, no
framework. What's in this folder is byte-for-byte what visitors see.

## Before publishing

Search `index.html` for `<mark>` — every highlighted `[bracketed]` bit is a
placeholder to replace (university, job-market line, working-paper titles).
Delete the `<mark>` wrapper once the real text is in; nothing highlighted
should survive to the live site.

Then drop the real files into `files/`:

- `files/cv.pdf` — your CV (the `CV` link points here)
- `files/jmp.pdf` — the JMP draft (the paper title links here)
- `files/photo.jpg` — portrait; fills the framed photo slot left of the bio
  automatically (until then the frame shows your initials). The frame is
  square, so a square crop shows uncropped.

Optional links (Google Scholar, GitHub) are in the HTML as comments — fill in
the URL and uncomment.

## Publishing on GitHub Pages

1. Create a **public** repo on GitHub named exactly `<your-username>.github.io`.
2. From this folder:
   ```bash
   git init
   git add .
   git commit -m "Initial site"
   git remote add origin git@github.com:<your-username>/<your-username>.github.io.git
   git push -u origin main
   ```
3. Wait a minute; the site is live at `https://<your-username>.github.io`.

Every later update is just: edit → commit → push. The live site refreshes
about a minute after each push. Updating your CV means overwriting
`files/cv.pdf` and pushing.

## Custom domain (optional)

1. Buy a domain at any registrar (Namecheap, Cloudflare, Porkbun; ~$10–15/yr).
2. On GitHub: repo → Settings → Pages → "Custom domain" → enter your domain
   (e.g. `nanwang.com`) and save. GitHub adds a `CNAME` file to the repo —
   keep it; deleting it disconnects the domain.
3. At your registrar's DNS settings:
   - For the apex domain (`nanwang.com`): four **A records** pointing to
     GitHub Pages: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`,
     `185.199.111.153`.
   - For `www.nanwang.com`: one **CNAME record** pointing to
     `<your-username>.github.io`.
4. Wait for DNS to propagate (minutes to a few hours), then back in
   Settings → Pages tick **Enforce HTTPS** once it becomes clickable.

After this the site serves at your domain and the `github.io` address
redirects to it. Nothing about the workflow changes — still edit → commit →
push.

## Adding a paper

Copy an `<article class="paper">…</article>` block inside `index.html` and
edit its title, coauthor line, status line, and links. The abstract lives in a
`<details>` block (see the JMP entry) — copy that too if you want one.

## Design notes

- Serif is the system Charter/Georgia stack; no webfonts, so the page loads
  instantly and works offline.
- Colors are CSS variables at the top of the `<style>` block (`--accent` is
  the link navy). Light and dark mode both follow the visitor's OS setting.
- Keep the page one column and under ~45rem wide; that constraint is the
  design.
