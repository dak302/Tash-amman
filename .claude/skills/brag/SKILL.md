---
name: brag
description: Make a short launch video for this project or a website, after asking the user many questions first. Use when the user types "/brag", or asks for a brag / launch / promo video. Asks the questions, then hands off to the brag-slim skill to build the video.
---

# /brag

A front door to `brag-slim`. Do NOT start building anything until the questions below are answered.

## 1. Ask first (always)

Ask in the user's language (they write Hebrew and French; match the language of their last message). Use the AskUserQuestion tool, up to 4 questions per call, in three rounds. Recommend an option when there is a sensible default and put it first with "(Recommended)". Skip a question only if the user already answered it in their message.

**Round 1 — what and for whom**
1. What is the video about? The whole site "לחיות את הת״ש" / one new feature (e.g. holidays page, documents, search, lone-soldier languages) / an external website URL.
2. Who will watch it? Soldiers / ת״ש staff and commanders / an evaluation or presentation / social media in general.
3. Language of on-screen text: Hebrew (Recommended) / French / English / Hebrew + subtitles.
4. Where will it be posted? WhatsApp / Instagram or TikTok (vertical) / a presentation or screen (landscape).

**Round 2 — look and feel**
1. Tone: polished (Recommended for an official guide) / default (punchy, clean) / app-store (feature cards) / deadpan / cinematic.
2. Format: landscape 16:9 / vertical 9:16 / square 1:1 (default from round 1, question 4).
3. Length: about 15s / about 20s (Recommended) / about 25s.
4. Music: calm / upbeat / no music.

**Round 3 — content**
1. Which 2–3 highlights to show (multiSelect): search, "בקצרה" summaries, checklist "מה כבר יש לך", bank documents, holidays calendar, redacted policy documents, lone-soldier languages, keva section.
2. Ending: show the site link / a short slogan / both.
3. Show the logo? yes / no.
4. Anything that must not appear (free text via "Other").

Then repeat back a 3–4 line summary of the answers and ask "להתחיל? / On commence ?". Wait for yes.

## 2. Security rules (this project only, always)

The site belongs to someone in the Intelligence Directorate and the video is meant to be shared:
- No personal names, signatures, phone numbers (mobile or otherwise), personal emails, unit names or numbers, internal system names or internal URLs.
- Do not show the redacted document pages unredacted, and do not zoom into blacked-out areas.
- Any checklist or saved state shown on screen uses neutral placeholder progress, never real user data.
- Keep `brag-output/` out of git (it is in `.gitignore`); never commit or push the video.

## 3. Hand off

Invoke the `brag-slim` skill with the answers as arguments, e.g.:
`/brag-slim --tone polished --format vertical --duration 20` plus a plain-language note with audience, language, highlights, ending, logo choice, exclusions and the security rules above.

Keep the user informed in one short line per stage (plan written, stills checked, render done). Be economical with tokens: check stills with automated checks where possible and look at only a few images.
