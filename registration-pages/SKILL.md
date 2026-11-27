---
name: registration-pages
description: Builds a registration page and a thank-you page for a free live training, webinar, workshop or masterclass from two proven templates. Fills them with the person's own words, connects the signup form to their email tool, and gets both pages online, even for someone with no website and no coding. Triggers on: registration page, sign-up page, signup page, webinar page, training page, workshop page, masterclass page, thank-you page, landing page for my live, build my registration page.
---

# Registration + Thank-you Pages

You build two pages from the files in `templates/`:

- `templates/registration-page.html`: the sign-up page
- `templates/thank-you-page.html`: the page people land on after signing up

**The design, layout, colours, fonts and code never change.** You only replace the `[square bracket]` spots with the person's own words, pictures and links. If you are not sure what goes in a spot, ask; never guess.

The person may know nothing about code or websites. Talk in plain words. Give them one thing to do at a time.

## Step 1. Ask, one question at a time

Ask these one by one. Wait for each answer before you ask the next. If they already told you something, don't ask it again.

1. What is your training called, and what do people walk away with? (one line)
2. Date, start time and your time zone? How long is it?
3. Who is it for?
4. Why are you running it? (one or two sentences, in their words)
5. The 3 things you cover, in order. Plus: the extra they get by coming live.
6. Do you give a free bonus to people who show up live? Its name, and a picture if you have one.
7. Your story in 4 short lines: where you started, what changed, your best result, what you help people do now. And a photo of you.
8. Reviews: paste them with the person's name, what they do, and their photo if you have it. Result screenshots too (sales, messages, wins).
9. A short invite video for the sign-up page, and a next-steps video for the thank-you page (YouTube, Loom or Vimeo link). Fine to skip.
10. Your Zoom (or other live) link.
11. Your offer for after the training: what they get (up to 5 points), the price, the checkout link, the button text.
12. Your name as it shows in the inbox, and the subject line of your confirmation email.
13. Which email tool do you use? (Kit, Mailchimp, MailerLite, Beehiiv, Substack, other, none)
14. Do you have a website? On what? (WordPress, Squarespace, Wix, Framer, Webflow, Kajabi, Carrd, Showit, none)

**Rules for what they give you**
- Never invent a review, a name, a result, a number, a quote or a story. Use their words exactly.
- If they have nothing for a block (no reviews, no bonus, no result screenshots, no talk reviews), take that whole `<section>` out. Never leave a placeholder or fake text.
- Fewer reviews than spots: use what they have and delete the spare cards. The moving review rows have the cards twice (the second copy sits in `scroll-dup` so the scroll loops): put the same reviews in both copies.
- Photos and screenshots they upload: put them in as `data:` images (base64) so the page works anywhere with no extra files. Keep each image under about 300 KB (shrink it first if needed).
- A finished page has zero `[` placeholders left. Search for `[` before you hand it over.

## Step 2. Fill both templates

**Settings first.** At the top of the main `<script>` in both files there is one `var EVENT={...}` block. Fill it the same in both files:

- `title`, `promise`: answer 1
- `startISO`: the start in ISO format with their offset, e.g. `2027-01-14T18:00:00+01:00`
- `dateLabel`: e.g. `Thursday 14 January`
- `durationMin`: minutes
- `zones`: the time zones to show, their own zone first, e.g. `[["Europe/Amsterdam","Amsterdam"],["America/New_York","New York"],["Europe/London","London"]]`
- `joinUrl`: their Zoom link
- `formAction`: see Step 4 (registration page only)
- `thankYouUrl`: the live link of the thank-you page (fill in after Step 5)
- `sender`, `subject`: answer 12

The headline, dates, times, countdown, "Live on..." lines and the Add to calendar buttons all fill themselves from this block. The countdown closes registration by itself when the training starts.

**Then the text spots.** Go top to bottom and replace every `[ ]` spot with their words: top bar (name and brand), the invite bar, the "for who" line, the headline and why, the 3 things, the bonus, the reviews, the story, the results, the offer pop-up on the thank-you page, and the Terms and Privacy links (if they have none, delete that line).

**Videos.** Replace the whole `<div class="vid-ph">...</div>` inside `<div class="vid">` with the embed:
- YouTube: `<iframe src="https://www.youtube.com/embed/VIDEO_ID" allowfullscreen></iframe>`
- Loom: `<iframe src="https://www.loom.com/embed/VIDEO_ID" allowfullscreen></iframe>`
- Vimeo: `<iframe src="https://player.vimeo.com/video/VIDEO_ID" allowfullscreen></iframe>`
No video: delete the whole `<div class="vid">` (and on the thank-you page also the "Watch this video" line above it).

**Celebration.** The thank-you page already has the celebration animation and confetti built in. Leave it. If they want their own picture there, it must be a sprite sheet in the same shape (12 columns of 480 x 157 frames); otherwise keep the built-in one.

**Title tag.** Fill `<title>` in both files.

## Step 3. Show the preview

Show both finished pages as a preview (an HTML artifact or file they can open). Tell them to click the buttons and check everything. Change only what they ask to change, and nothing else.

## Step 4. Connect the signup form

Open `reference/email-tools.md` and follow the part for their email tool.

- **Kit, Mailchimp, MailerLite**: you get their form link and put it in `EVENT.formAction`. The page's own pop-up form (name + email) sends straight to it, then sends the person to the thank-you page. The design stays the same.
- **Beehiiv, Substack, anything else**: swap the inside of the pop-up form for their tool's own embed code, as the guide shows, so it still opens from every button.
- **No email tool**: help them set up a free Kit account first (the guide has the steps), then connect as above.

Also set up the confirmation email in their tool with the subject line from answer 12 and the Zoom link inside.

## Step 5. Put both pages online

Open `reference/hosting.md` and follow the part for their situation. The default for everyone is **Netlify Drop** (free, no coding, works in a minute): the two pages go online as their own links, and they can link to them from any website, email or social post. If they want the pages on their own website, the guide has the steps per website builder.

When the thank-you page is live, put its link in `EVENT.thankYouUrl` on the registration page and upload the registration page again.

## Step 6. Test it together, end to end

Ask them to do this on the live link, on their phone:
1. Open the registration page. The headline, date, times and countdown show.
2. Click the button. The pop-up opens.
3. Sign up with their own email. They land on the thank-you page and the confetti goes off.
4. Their email tool shows them as a new subscriber, and the confirmation email arrives.
5. "Add to calendar" opens with the right date, time and Zoom link.
6. "Work with me" opens the offer and the button goes to their checkout.

Only call it done when all 6 work. If one fails, fix that one thing and test again.

## Later

When they come back ("new date", "change the headline", "make one for my next training"), work from the same two files. For a new date, change only the `EVENT` block in both files and upload again. Change only what they ask.
