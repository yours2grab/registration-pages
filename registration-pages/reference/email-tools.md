# Connecting the signup form

The registration page has its own pop-up form (first name + email). For Kit, Mailchimp and MailerLite it sends straight to their form link, and the page then moves the person on to the thank-you page by itself. You only need the form link: the `action="..."` link inside the tool's embed code.

Walk the person through it one click at a time. Ask them to paste the embed code into the chat, and pull the link out yourself.

## Kit
1. Go to Grow → Landing Pages & Forms → Create new → Form → Inline → pick any look → name it after the training → Save.
2. Click Publish → HTML → copy the code and paste it here.
3. Take the link that looks like `https://app.kit.com/forms/1234567/subscriptions` and put it in `EVENT.formAction`.
4. Confirmation email: in the form's Settings → Incentive, Kit sends a confirm email by default. Either write the confirmation there (subject from the settings, Zoom link inside), or turn off "Send incentive email" and send the confirmation with a Kit Automation (trigger: joins this form).
5. Optional: Settings → General → "Redirect to a URL" → the thank-you page link.

## Mailchimp
1. Audience → Signup forms → Embedded forms → Continue.
2. Copy the code and paste it here.
3. Take the link that looks like `https://NAME.usXX.list-manage.com/subscribe/post?u=...&id=...` and put it in `EVENT.formAction`.
4. Confirmation email: Audience → Signup forms → Form builder → "Final welcome email": write it with the Zoom link. If double opt-in is on, people must click the confirm email first; tell them that.

## MailerLite
1. Forms → Embedded forms → Create → name it → pick a group → Save.
2. On the form page click "Embed form" → HTML code → copy and paste it here.
3. Take the link that looks like `https://assets.mailerlite.com/jsonp/ACCOUNT_ID/forms/FORM_ID/subscribe` and put it in `EVENT.formAction`.
4. Confirmation email: Automations → New automation → trigger "When subscriber joins a group" (the group from step 1) → add an email with the Zoom link.

## Beehiiv
1. Grow → Subscribe Forms → New → name it. If there is a "redirect after subscribe" setting, put the thank-you page link there.
2. Copy the embed code (an `<iframe>`) and paste it here.
3. On the registration page, inside `<form class="box">`, keep the close button `×`, the `<h3>` and the date line, and replace the two inputs, the button and the error line with their iframe. Set the iframe to `width:100%;border:0`.
4. Under the iframe add: `<p style="margin-top:12px">Signed up? <a href="THANK-YOU-LINK">See your seat details</a></p>`.
5. Delete the `form.onsubmit=...` part of the script so it doesn't block their form.
6. Confirmation email: Beehiiv's welcome email (Settings → Emails → Welcome email) with the Zoom link.

## Substack
1. Their embed is: `<iframe src="https://NAME.substack.com/embed" width="100%" height="320" style="border:1px solid #EEE;background:white" frameborder="0" scrolling="no"></iframe>` (NAME = their Substack address).
2. Put it in the pop-up the same way as Beehiiv, steps 3 to 5.
3. Confirmation email: Substack sends its own welcome email (Settings → Emails → Welcome email). Put the Zoom link in it.

## Anything else (ActiveCampaign, Flodesk, ConvertKit-style tools, Systeme, etc.)
- If the embed code is a normal `<form action="...">` with fields: put the action link in `EVENT.formAction`. If the field names differ from `email`, `email_address`, `EMAIL`, `fields[email]`, `first_name`, `fields[first_name]`, `FNAME`, `fields[name]`, add theirs to the list in the `form.onsubmit` script.
- If it is a script or an iframe: put it in the pop-up the same way as Beehiiv.

## No email tool yet
Help them open a free Kit account at kit.com (free up to 10,000 subscribers), then follow the Kit steps above.

## Check it worked
The pop-up form can't see whether the email tool accepted the signup. So always test with a real email and check that the person shows up in the tool. If they don't: the form link is wrong (copy it again), or the tool needs a field it didn't get (look at the embed code's field names).
