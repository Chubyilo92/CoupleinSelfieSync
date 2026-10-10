# CoupleIn: Selfie of the Day (replaces Mood Sync)

## The idea
Once a day each partner takes a selfie. The two photos combine into one shareable card: you on top, a white line, your partner below, with "CoupleIn · Day 658" on the line. A daily ritual that also works as free marketing, because every shared card carries the CoupleIn watermark.

## Decisions made
| Topic | Decision |
|---|---|
| Where it lives | Inside CoupleIn, not a separate app. CoupleIn has about 50 users (around 25 couples), the feature needs two people per account, and shared cards should drive traffic to CoupleIn. A spin-out can be considered later with real data. |
| Tab bar | Raised camera button in the centre **opens the camera directly**. It replaces the Mood tab, and Brownies sits to its left. Order: Calendar, Brownies, **Camera**, Resolve, Settings. Moments (today's card and history) opens after posting or from X. |
| Camera screen | Full screen. Tab bar hides. X at top-left closes back to Moments. Camera only, no gallery uploads (keeps it authentic). |
| Layout | Half-page camera on top, white line, partner's photo below. "CoupleIn · Day N" pill sits on the line. |
| Trigger | One gentle daily reminder at a time the couple picks (default evening). **No countdown** (adults, shifts, time zones; a timer adds guilt). Each person posts within their own local day (own midnight). |
| Nudge | When one partner posts, the other sees "Emma posted 12 min ago". |
| Reveal | Partner's photo is blurred and locked until you post yours. |
| Caption | Optional, max 60 characters. Shown on your own photo and on the shared card. |
| Mood Sync | Kept as a one-tap emoji on the selfie, using the app's existing 9 moods: Happy, Loved, Calm, Excited, Naughty, Tired, Anxious, Sad, Upset. Camera shows 6, scroll for the rest. |
| History | "Your moments" grid sits below today's card, newest first, 3 across. Each tile is a mini version of the shared card with its Day number on the white line. Tap a tile for the full card, caption, mood, Save and Share. |
| Missed days | The tile shows the person who posted, and for the person who missed, their **profile picture with an "M" badge** on a soft pink panel. Keeps the day in the history without an empty grey box. |
| Partner not linked | **Full flow still works.** You can post, add mood and caption, and earn points. Your partner's half shows an invite panel. Your selfies wait for them and unlock once they join. Nothing is blocked. |
| Points | A selfie earns **double a mood check**, plus a bonus when both partners post that day. |
| Retakes | You can retake or delete your selfie until your partner has seen it. After that it's locked in. |
| Milestone tiles (spec, not in mock) | Gold ring and star on the Day pill for round days (100, 200, 365, 500, 730, 1000, plus fun ones like 111 and 777). |

## First-time experience (decided)
A new user's first visit opens **straight on the camera**, with a short intro sheet on top. See `selfie-first-time-screens.png`.

**A. First open (intro sheet over a blurred camera)**
- A mini Day 1 card illustration: your selfie on top, a dashed invite placeholder below.
- Chip: "New · Moments"
- Title: **Your story, one selfie a day**
- Lead: "One photo each, every day. A year from now you'll have 365 days of you two: the ordinary, the silly, the ones you'd otherwise forget."
- Three steps:
  1. **Snap your selfie**: 10 seconds. Add a mood and a caption if you like.
  2. **Reveal together**: your partner's photo unlocks once you've both posted.
  3. **Earn double points**: 2× a mood check. Spend them on gestures from your partner's wishlist.
- Button: **Take my first selfie**
- Footer: "Only you two can ever see your photos."
- Shown once. After that, the camera opens directly.

**B. First selfie (partner not linked)**
- Coach banner on the camera: "**Take a selfie.** It'll be waiting for your partner once they join."
- Your partner's half is a soft pink invite panel: dashed avatar, "Your partner's half", "Invite them to see today's card", and an **Invite partner** button.
- Mood row and shutter work as normal.

**C. Posted solo**
- Your photo, with caption and mood, sits on top of the Day 1 card.
- Partner half: "Waiting for your partner. Your selfie is saved. It unlocks for them the moment they join."
- Sheet: **Day 1 saved**, a "2× pts" badge, and "Double points: 2× a mood check".
- Buttons: **Invite your partner** (primary) and **Go to Moments**.
- When the partner joins, every waiting selfie appears for them.

## Rules for missed days (decided)
- **One partner posts, the other doesn't:** the day closes at midnight. The tile shows the poster's photo and the missing partner's profile pic with an M. The poster's photo stays **blurred for the missing partner until they next post**. Their next selfie unlocks everything they missed at once: "3 moments from Emma waiting. Post to unlock."
- This doesn't affect the Day counter. Every photo is saved against its own date and Day number, nothing is back-dated, and you can't post into a past day.
- **Neither posts:** the tile shows both profile pics with an M. The streak gets **one free pass per week**. Extra streak saves can be bought with Brownie points.
- **Streak:** consecutive days where both partners posted (a photo or a mood-only post), with the weekly free pass applied automatically.
- **Mood-only posts:** you can post a mood with no selfie **up to 2 times a week**. That half of the card shows a large emoji on a soft panel, with the caption if added. It counts as posting for the streak and for unlocking.
- **Time zones:** each person's day ends at their own midnight. The shared day closes at the later of the two midnights.

## Downloads and Pro (decided)
- **Free:** view the whole history; save and share **today's card** and **milestone cards** (Day 100, 200, 365, 500, 730, 1000, 111, 777).
- **Pro (per couple):** download any other past card. Later Pro extras could include a monthly or yearly recap video and a printed photo book.
- Viewing history is never locked, so memories are never held hostage.

## Points (decided)
- A selfie earns **double the points of a mood check**, plus a bonus when both partners post that day. A mood-only post earns the normal mood-check points.
- Extra streak saves can be bought with points.

## Storage and privacy (recommended, confirm with Wajeeh)
- Private cloud storage (S3, Cloudflare R2 or Firebase Storage, whichever already holds profile pics). One folder per couple, nothing public.
- The app shows photos through short-lived private links.
- The server only returns your partner's photo after you've posted. Blurring on the phone alone isn't secure.
- Compress on the phone before upload (about 1080px JPEG, around 300 KB) and strip location data. Store a small thumbnail per photo for the history grid.
- The share card is built on the phone when Save is tapped, so it isn't stored.
- Cost: about 220 MB per couple per year. 1,000 couples is roughly $5 a month.
- **Leaving or deleting an account (decided): everything is deleted for both partners.** Recommended safeguard: warn both partners first and give 30 days to save their own photos (also covers the UK GDPR right to a copy of your data).
- Onboarding line: "Only you two can see these."

## Ideas for later
- Reactions: tap a heart or quick emoji on your partner's photo.
- Home-screen widget showing your partner's latest photo (Locket's growth driver).
- Monthly or yearly recap video (Pro).

## Flow
1. **Camera (centre button):** opens directly. On a new user's first visit, intro sheet first (see First-time experience).
2. **Moments:** today's card ("Emma posted · 12 min ago", locked photo, "Take today's selfie"), streak banner, then the history grid.
3. **Camera:** live selfie on top, Emma's blurred and locked below. Caption field on your photo, mood row, shutter. X to go back.
4. **Reveal:** both photos unblur, captions and mood chips show. Sheet with "Day N together", streak, **Save card** and **Share to Stories**. X closes back to Moments.
5. **Share card:** 1080 x 1920 PNG (see below).

## Share card spec
- 1080 x 1920 (9:16). Your selfie top, partner's bottom, 18px white line between.
- White pill on the line: heart + "CoupleIn · Day N" (N in brand pink).
- Mood chip (emoji + label) in the top-left of each photo.
- Caption pill bottom-left of each photo (dark translucent, white text).
- Watermark "♥ coupleinapp.com" bottom-right.
- File: `selfie-card-day-658.png`.

## Notifications (phase 2)
- Every day: the same gentle reminder at the couple's chosen time. Never skip or delay it to save attention for milestones.
- Milestone days: special wording ("Day 500 together. Take a selfie to mark it.") and a special card design (gold Day badge, confetti).
- Day before a milestone: heads-up ("Tomorrow is Day 365 together").
- Streak milestones: separate celebration at 7, 30 and 100 days in a row.
- Catch-up cards: once couples are at scale, give existing couples a card for the last milestone they passed.
- Keep milestone notifications rare so they stay special.

## Design system (match the existing app)
- Font: Inter (400 to 800).
- Brand pink `#FF6B9D`. Button gradient `#FF7098` to `#FFB055`. Banner gradient `#FF6C9C` to `#FDB051`.
- Text `#212121`, grey `#9E9E9E`, light grey `#BDBDBD`. Page grey `#F8F8F8`.
- Soft pink `#FDF2F8` (chips, missed panel). Featured card border `#F9A8D4`. Screen header gradient `#FDF3F9` to white.
- Points pill: bg `#FEFCE8`, text `#A16207`, star `#EAB307`. Streak banner: bg `#FFF7ED`, flame `#F97316`.
- Icons: Lucide, stroke 2. Buttons: pill, 44px (in cards) or 48px (full width). Cards: radius 24. Tab bar 57px, white, 1px top border.
- Screens: `screens/1-moments.png`, `2-camera.png`, `3-reveal.png` (1290 x 2796). Overview: `selfie-of-the-day-screens.png`.

## Data (suggested)
- One record per person per day: couple_id, local_date, day_number, user_id, type (photo or mood-only), photo_path, thumb_path, caption (60 max), mood, posted_at, seen_by_partner_at.
- A photo unlocks for the partner once the partner has any post dated on or after it.
- Retakes are allowed while seen_by_partner_at is empty.

## Launch and measurement
- At 50 users a two-week slice test won't say anything reliable. Ship to everyone, then message the active couples and ask whether they post and why.
- Test the format on your own socials first: post the split card (own photos or a friendly couple's) and link to the app.
- Numbers to watch: share of couples where **both** post each day, 7-day return rate, cards saved or shared per week, new installs that mention it. If both-post is under about 30%, fix the format before scaling.
- Growth feature first: the partner invite and the share flow matter most. Make inviting a partner a one-minute job.

## Risks
- One partner skips for long stretches. Covered: the day closes at midnight, and waiting photos unlock on their next post.
- A camera takes more effort than a tap, so completion will be lower than Mood Sync. Expect a spike and then a drop unless the habit sticks.
- Some people won't want to show their face daily. Keep a skip option and the mood emoji as the light version.
- Most public shares will happen at milestones, not daily. Milestone cards need extra design care.

## Open questions
- **Day counter:** days together (from the couple's start date) or days on CoupleIn? The screenshots say "Together 2y 4m", which doesn't match Day 658.
- **Missed days:** show who skipped (as mocked) or give couples a setting to hide it?
- **Existing Mood data:** suggestion is to carry current Mood streaks over and keep old mood entries visible as history.
- **Points numbers:** the both-posted bonus and the price of a streak save. A selfie is 2× a mood check.

## About the mock
- Mock photos are the couple selfie you supplied, cut at the white line into him and her and reframed for each screen. History tiles reuse the same two photos with different crops and light, since there is only one photo per person. Profile pictures on missed-day tiles are cropped from the same photos. Swap in real daily selfies when building.
- Placeholder numbers: 41 streak, 240 points, "Emma posted 12 min ago".

## Before you build: checklist
**Decide (3 items)**
- Day counter: days together or days on CoupleIn.
- Points numbers: the both-posted bonus and the price of a streak save.
- Carry existing Mood streaks over (suggested: yes).

**States the design doesn't show yet** (first open, first selfie and posted-solo are now designed)
- Day 1 or empty history for new couples.
- Waiting-photos unlock ("3 moments from Emma waiting").
- Mood-only half, and the counter for the 2 left this week.
- Upload failed or offline: save locally, retry, never lose the photo.
- Camera permission denied: explain why and link to Settings.

**Technical**
- Push notifications at each person's chosen local time, plus the "Emma posted" push (FCM and APNs).
- Front camera: don't mirror the saved photo, and test on several Android phones.
- Share to Instagram Stories needs a Meta app ID. TikTok has its own share kit. Plain "Save to Photos" works everywhere.
- Server check that a partner's photo is only returned after you've posted.
- Analytics events (PostHog): selfie_posted, mood_only_posted, both_posted, card_saved, card_shared, photos_unlocked, streak_saved.

**App Store / Play Store and legal**
- Camera and photo-library permission wording (iOS asks for a reason string).
- Update the App Store privacy label and Play data-safety form: photos are now collected.
- Update the privacy policy: what's stored, where, for how long, and deletion for both partners on leaving.
- In-app account deletion (Apple requires it) with the 30-day warning to save photos.
- An "unlink partner" option in Settings, for safety if a relationship ends badly.

**Testing**
- Two test accounts as a couple on different phones, including one set to another time zone.
- Run through: both post, one posts, neither posts, mood-only, retake, unlock after days away, Pro download, delete account.
