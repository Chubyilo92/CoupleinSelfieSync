# Final Plan: Founder Plan (Sync)

Oct 10, 2026

## 1. Decisions and what was cut

Sync is the hero feature and the growth engine: one pose a day, both partners send, a 3-2-1 reveal, and a card worth sharing. The developer has a separate spec (Final Plan: Developer Spec). This page is yours: marketing, money, risks and what only you can decide.

**Locked**

- One thing a day, every day. A new pose unlocks at 3AM once both have sent the current one.
- Pricing: weekly £5.99, monthly £9.99, yearly £49.99.
- Only Sync is free. Calendar, Brownies and Resolve are Pro, shown as locked placeholders with promise lines ("We are a priority.", "Speak their language!", "8 of 10 couples resolve in 5 minutes.").
- Photos stay on the phone. Free users can open the last 14 days. A short-lived relay delivers photos between phones and deletes them.
- First selfie is a hard gate: nobody sees any other screen until it is sent.
- Week 1 video after the 7th completed pair, promised on the first reveal.
- "Who did it better?" is the post button. The countdown only says "Reveal" then 3-2-1.

**Cut from the MVP**

- Saturday global challenge (too many bugs for a non-core feature). It returns as a social challenge only, see section 2.
- History grid, streaks, mood emoji, mood-only posts, missed-day tiles.
- "Who did it better" voting and scoreboard. Good idea for later.
- "Couple of the week" and any public in-app feed.

## 2. Marketing and viral launch plan

Two growth loops: your absurd videos bring in the first couples, then every shared card and every partner invite brings in the next.

**Your content (from the filming sheet).** Each location (road, roof, bathtub, fridge) is filmed as two rival POVs: "My wife is too competitive" and "My husband made me do this". Add a screen recording of the 3-2-1 reveal and a "5 poses that made us laugh" carousel. Cadence: POV videos 1 a day, screen recordings 2 to 3 a week, carousels 2 a week. Show the countdown in real time, never sped up.

**The Trojan horse.** The absurd poses are the marketing. Stunts such as the road and the roof are fine as your own filmed content with a spotter, as the sheet requires. Keep them out of the in-app pose list: Apple and Google review the app, and a pose that sends people onto a road is the one thing that could get it pulled. Safe-but-absurd poses (floor, fridge, dry bathtub, chair) give the same effect.

**Moves to make**

1. **End every video with the pose name and "Do it with your partner, link in bottom."** Reply to the best stitches and duets with your own.
2. **Saturday as a social hashtag challenge** (no app build). One fixed day, one pose, one hashtag. Anyone does it with their normal daily selfie.
3. **Seed 5 to 10 couple creators from one niche** with overlapping audiences, all posting the same pose within a few hours with the same hashtag and format, so one audience sees it several times. Twenty creators with separate audiences would not look busy.
4. **A landing page per shared card.** Anyone tapping a shared card lands on "Do this pose with someone" with a one-tap store link, not the generic home page.
5. **Write each pose notification as a dare**, for example "Pose 4: kiss while pretending to be asleep."
6. **Make the first 7 poses the funniest and most filmable.** They feed the Week 1 video and most free users will not pass 14.
7. **Put the paywall where people are attached:** the Week 1 video ("Remove the watermark"), plus the locked tabs and the day 10 to 13 photo-lock warning.
8. **Invite as a curiosity gap.** The invite carries the blurred locked card and the compliment, and says they took a selfie just for the partner.

**Later:** a real "Who did it better?" vote with a scoreboard, and a stake on it (the loser does the dishes).

**Numbers to watch:** share of couples where both partners send each day, partner joined within 48 hours of the invite (this is your second install per user), installs per share, 7-day return, Week 1 video shared. If both-send is under about 30%, fix the format before spending more on reach.

## 3. Economics: pricing, relay cost, what to measure

| Plan | Price |
| --- | --- |
| Weekly | £5.99 |
| Monthly | £9.99 |
| Yearly | £49.99 |

**Relay storage cost** (photos wait in an encrypted temporary store until both partners have sent, then are deleted once both have downloaded, or after 30 days). At 100,000 photos a day, roughly: Cloudflare R2 about $17 a month, Amazon S3 about $95 a month. These are approximations; R2 is the cheaper option.

**Numbers to watch:**

- Share of new users who send the first selfie (the hard gate).
- Share of couples where both partners complete a day.
- Couples reaching the Week 1 video (7th completed pair).
- Paywall views at the Week 1 video, and conversion from there.
- Weekly vs monthly vs yearly split.

## 4. Risks

- **14-day lock frustration:** older photos are stored on the phone but locked on Free. Some users may feel punished. The Week 1 video is the soft paywall to test this.
- **Camera effort drop-off:** one pose a day only works if sending feels easy. Watch day 2 to day 7 retention.
- **Privacy promise:** the relay means photos briefly leave the phone. The copy must say this honestly (encrypted, deleted after both download).
- **Unverified claim:** "8 of 10 couples resolve in 5 minutes" is not backed by data yet. Verify before it goes live.
- **Gendered placeholders:** the women/men versions may draw criticism as generalisations. "Prefer not to say" gets a neutral version.

## 5. Open questions and your to-do list

**Open questions (decide with the developer):**

- Does the Missions tab hold Sync? (assumed yes, it is the only free tab)
- Is Pro per person or per couple?
- Hard gate: first selfie only, or every day?
- What do points buy, and is there a daily cap? (25 points per photo for now)
- Week 1 video trigger: after the 7th completed pair; partial video on day 10 if slow.

**Your to-do list:**

- Verify the 8 of 10 claim and the invented Resolve timings (1:30 / 1:00 / 1:00 / 1:30).
- Rebuild the 365-pose sheet with no dates, Pose 1 = lie flat on back.
- Approve the first 14 poses.
- Still to design: countdown screen, invite fork, pricing page, Week 1 video promise and ready screens.
- Hand the Developer Spec to your developer.
