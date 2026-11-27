# Putting the pages online

## The default for everyone: Netlify Drop (free, no coding)

This works for everyone, with or without a website. Use it unless they really want the pages inside their website builder.

1. Give them the two finished files to download. Name them exactly:
   - `index.html` (the registration page)
   - `thank-you.html` (the thank-you page)
2. On their computer: make a new folder (for example `my-training`) and put both files in it.
3. Make a free account at netlify.com (sign up with Google is fine). Do this first: a drop without an account disappears after an hour.
4. Go to app.netlify.com/drop and drag the whole folder onto the page.
5. In a few seconds they get a live link like `https://random-name-123.netlify.app`.
   - Registration page: `https://random-name-123.netlify.app/`
   - Thank-you page: `https://random-name-123.netlify.app/thank-you.html`
6. Nicer name: Site configuration → Change site name → e.g. `jane-masterclass` → the link becomes `https://jane-masterclass.netlify.app`.
7. Put the thank-you link in `EVENT.thankYouUrl` on the registration page, give them the new `index.html`, and they upload again (below).

**Uploading a new version**: Site → Deploys → drag the folder (with both files) onto the "Need to update your site?" box.

**Their own domain (optional)**: Domain management → Add a domain → e.g. `training.janedoe.com` → Netlify shows one record to add at their domain company (GoDaddy, Namecheap, Squarespace Domains, etc.). Walk them through adding it. It can take up to a day to start working.

**Linking from their website**: add a button or menu link on their site to the Netlify registration link. That's all.

## Inside a website builder (only if they want it)

Some builders limit how much code one block can hold. The registration page (about 75 KB plus their photos) usually fits; the thank-you page holds the celebration picture and is about 620 KB, which is too big for most code blocks. So: **the thank-you page always goes on Netlify**, or put the celebration picture on their site first and use its link in `sprite.src` instead of the built-in one.

General steps: make a new blank page (no header or footer if the builder allows it), add a code block, paste the whole file in, publish, open the live page and check it.

- **WordPress**: Pages → Add New → choose a full-width or blank template if the theme has one → add a "Custom HTML" block → paste → Publish.
- **Squarespace**: add a blank page → add a Code block (needs a plan with code blocks) → paste → turn off "Display source" → Save.
- **Wix**: add a blank page → Add → Embed code → Embed HTML → "Code" → paste → stretch it to full width and make it tall enough.
- **Framer**: new page → insert an Embed → HTML → paste → set it to fill the page.
- **Kajabi**: new landing page → add a "Custom code" section → paste.
- **Webflow, Carrd, Showit**: their code blocks are too small or need a paid add-on. Use Netlify and link to it.

If the builder changes the look (fonts, spacing, the pop-up not opening), don't fight it: use Netlify and link to it from the site.
