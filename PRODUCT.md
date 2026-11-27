# PRODUCT: Registration Pages skill

Built 27 November 2026 (Bali). A Claude skill that lets anyone build a registration page and a thank-you page for a free live training, in the exact design of Virgil's free-training pages, and get both pages online. It needs no Vercel, no website and no code.

## What it is

- A folder (`registration-pages/`) that a person uploads to their own Claude as a skill.
- Inside: two page templates, the celebration picture, the instructions for Claude, and two step-by-step click guides (email tools and hosting).
- The person says "build my registration page". Claude asks 14 questions one at a time, fills both templates with their own words, connects the signup form to their email tool, and walks them through putting both pages online.

## Where the design comes from

The templates are copies of Virgil's live pages, with all his own text, reviews, photos, results and links replaced by `[square bracket]` spots:

- Registration page: virgilbrewster.com/free-training (source file `public/free-training/index.html` in the virgilbrewster.com deploy folder)
- Thank-you page: virgilbrewster.com/free-training/thank-you (source file `public/free-training/thank-you/index.html`)

The design, layout, colours, fonts, animations and code are unchanged. Fonts load from Google Fonts. Every image is inside the file, so each page is one self-contained file that works anywhere.

## Files

| File | What it is |
|---|---|
| `registration-pages/SKILL.md` | The instructions Claude follows (6 steps) |
| `registration-pages/templates/registration-page.html` | Sign-up page template (about 74 KB) |
| `registration-pages/templates/thank-you-page.html` | Thank-you page template, celebration animation built in (about 617 KB) |
| `registration-pages/assets/celebration.png` | The celebration sprite sheet (12 columns of 480 x 157 frames) |
| `registration-pages/reference/email-tools.md` | How to connect Kit, Mailchimp, MailerLite, Beehiiv, Substack, other tools, or no tool |
| `registration-pages/reference/hosting.md` | How to put the pages online: Netlify Drop (default), or WordPress, Squarespace, Wix, Framer, Kajabi |
| `registration-pages.zip` | The same folder zipped, ready to upload |

## How someone installs it

1. Download `registration-pages.zip` from this repo.
2. In Claude (claude.ai or the Claude app): Settings → Capabilities → make sure code execution / file creation is on → Skills → Upload skill → pick the zip.
3. In a new chat, type: "build my registration page".

## How it works, step by step

1. **Questions (14, one at a time):** training name and promise; date, time, time zone, length; who it is for; why they run it; the 3 things they cover plus the live extra; free bonus; their story in 4 lines plus photo; reviews and result screenshots; videos; Zoom link; their offer (points, price, checkout link, button text); sender name and confirmation subject line; email tool; website.
2. **Filling the templates:** Claude fills the one `EVENT` settings block at the top of each page (title, date, time zones, Zoom link, form link, thank-you link, sender, subject). The dates, times, countdown, "Live on..." lines and calendar buttons fill themselves from it. Then it fills every text spot with their words, puts in the videos, and removes any block they have nothing for. It never invents reviews, results, numbers or stories.
3. **Preview:** Claude gives them both pages to open and click through. It changes only what they ask.
4. **Signup form:** for Kit, Mailchimp and MailerLite, the page's own pop-up form sends name and email straight to their form link (it sends every field name those three tools use). For Beehiiv, Substack and others, their tool's embed code goes inside the same pop-up. The confirmation email is set up in their own tool.
5. **Online:** the default is Netlify Drop (free): two files named `index.html` and `thank-you.html` in one folder, dragged onto app.netlify.com/drop. Their website links to it. Pasting into a website builder is the second option. The thank-you page is too big for most code blocks, so it always goes on Netlify.
6. **Live test (6 checks on their phone):** page loads with dates and countdown, button opens the pop-up, signup lands on the thank-you page, the person shows up in the email tool and gets the confirmation email, Add to calendar is right, Work with me goes to their checkout.

Later: for a new date they change only the `EVENT` block in both files and upload again.

## Tests run on 27 November 2026

**Test 1 (16:37 to 16:44 Bali):** a helper followed the skill on Virgil's Mac with a made-up coach, "Maya Holt" (career coach, Kit, Squarespace). Both pages built. Date, times, countdown and calendar links were correct, with no JavaScript errors and no sideways scrolling on a phone. It found the problems listed under Known issues.

**Test 2, stranger test (16:50 to 17:02 Bali):** a completely fresh Claude with nothing of Virgil's (no CLAUDE.md, no memory, no connectors, no hooks, no settings). It had only the skill folder, and Virgil's agent played Maya, answering one message at a time. Results:
- It started the skill by itself on "build a registration page" and asked all 14 questions one at a time.
- It spotted that the test video, Zoom link, checkout link and Kit form number looked like samples and kept a "swap before you go live" list.
- The design came through identical to the template (one blank line of difference in the code), and no fill-in spots were left.
- Nothing was invented: Priya's job was left blank, "one-time offer" was taken out because Maya never said it, and blocks without content were removed.
- It said plainly which lines it had written itself (a headline built from her story, and one line about the session).
- It advised Netlify over Squarespace, fixed the "index (1)" download name problem with Mac and Windows steps, and checked both live pages loaded.
- When the signup didn't show in Kit, it explained why the confetti still plays and checked the two likely causes (wrong form number, unconfirmed subscriber).

Not tested yet: a real Kit account, a real Netlify account, and a real claude.ai account.

## Known issues (not fixed yet)

1. The sign-up pop-up's "Save my seat" button doesn't get the big pill button style, and the date line in the pop-up falls back to a plain font. The button style only applies inside `#os-sales`, and the pop-up sits outside it. The same is true on the live virgilbrewster.com/free-training page.
2. The skill doesn't ask for: brand name in the top bar, which other time zones to show, the Terms and Privacy links, the "how the session works" line and the "what happens on the day" line. Claude has to write or remove them.
3. With only a few reviews, the skill doesn't say which of the 4 review blocks to keep.
4. The training length is asked but only shows in the calendar invite, not on the pages.
5. YouTube embeds show an error in a local preview (they should play on the live https page).
6. The page can't see whether the email tool accepted a signup, so it always goes to the thank-you page.
7. The Kit confirmation email steps are unclear. Kit's default is a "confirm your subscription" email, so people stay unconfirmed until they click it. There are no reminder emails before the live.
8. If the person rushes ahead ("done the email") before Claude has shown them the confirmation email steps, Claude doesn't notice.
9. Netlify's menu names may have changed ("sites" became "projects" in 2025).
10. Squarespace code blocks need a Core plan or higher, and scripts only run on the published page.
11. Needs code execution on in the person's Claude. Without it Claude can't edit the files, and the thank-you page is too big to retype.
