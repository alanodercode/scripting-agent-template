# Creative Strategist System — Template

A clean, stripped-down version of the creative strategist system. Copy this folder to start a new agency setup, then fill in brand-specific context using the onboarding questionnaire below.

---

## What's In This Template

```
template/
├── README.md                         ← This file (setup + onboarding questions)
├── _SYSTEM_CONTEXT.md                ← Generic system prompt (fill in agency name + brands)
├── frameworks/
│   ├── writing-guide.md              ← Universal style rules (spoken word, hooks, CTAs)
│   ├── universal-patterns.md         ← Empty — fill in as you learn what works/fails
│   ├── 100k-day-ad-framework.md      ← Belief-first ad structure (universal)
│   └── templates/
│       ├── brand-template.md         ← Copy for each new brand
│       └── script-template.md        ← Copy for each new script
├── swipes/
│   ├── README.md                     ← How to break down winning ads
│   └── _template.md                  ← Copy for each new swipe
└── brands/                           ← One folder per brand (start empty)
```

What's been stripped vs. the live system:
- All client/brand folders (`brands/*`) — empty here, fill per onboarding
- Agency-specific delivery SOPs (e.g. Trello board IDs, list names)
- The "Active Brands" table in `_SYSTEM_CONTEXT.md` — placeholder
- Brand-specific examples baked into `universal-patterns.md`

---

## Setup — Step by Step

1. **Copy the folder.** Duplicate `template/` to a new repo (or to the root of an empty repo) and rename it however you want.
2. **Run the onboarding questionnaire** below with the agency owner. Don't skip — guesses become wrong scripts.
3. **Fill `_SYSTEM_CONTEXT.md`** with the agency name, language defaults, and the active brands table.
4. **Create one `brands/[brand]/brand.md` per brand** using `frameworks/templates/brand-template.md`. Don't write a script before the brand file exists.
5. **Add any agency-specific SOPs** to `frameworks/` (delivery board, naming conventions, approval flow). Keep them short and explicit.
6. **Test on one brand, one script.** Read it out loud. Have the owner approve. Then scale.

---

## Onboarding Questionnaire

Ask the agency owner ALL of these before cultivating any brand. The answers determine how the entire system gets configured.

### 1. Agency & Portfolio
- What's the agency name and primary positioning?
- How many brands/clients are active right now?
- For each brand: name, category, market (US/UK/DE/etc.), language, weekly script volume.
- Are any brands grouped under a sub-agency or umbrella client? (If yes, capture the parent + cadence rules.)
- Which brands are compliance-sensitive (health, finance, medical, GLP-1, supplements)?

### 2. Voice & Style Defaults
- Any global voice rules across all brands? (e.g. no em dashes, contractions required, no ALL CAPS)
- Forbidden words or phrases at the agency level? (e.g. "revolutionary," "miracle," "guaranteed")
- Preferred humanifiers / filler words per language? (English vs German vs other)
- Tone defaults: conversational, authoritative, peer-to-peer, founder-led?

### 3. Output Format (per script)
- What sections does a delivered script contain? (Hooks, visual notes, body, on-screen text, CTA, compliance line)
- How many hooks per script as the standard? (5? 10?)
- Are angle labels included or stripped before delivery?
- Is format/length/funnel-stage included on the top line?
- Visual direction: bullet points or plain paragraph?

### 4. Workflow & Delivery
- Where do final scripts get delivered? (Trello / Asana / Notion / Google Doc / Slack / ClickUp)
- What's the column/list structure? (Pipeline → Next Up → Approved, etc.)
- Who reviews and approves? Can the AI move cards forward, or only draft?
- Naming convention for cards/files? (Numbered sequentially per brand? Per agency? Date format?)
- Turnaround expectation: how fast from brief to delivered?

### 5. Compliance Per Brand
- For each compliance-sensitive brand: forbidden claims, required disclaimers, on-screen text rules, regulator (FTC, MHRA, ASA, FDA, etc.).
- Are there pre-approved phrases or "safe language" lists?
- Who signs off on compliance — the agency or the client?

### 6. Frameworks & SOPs
- Default ad framework? ($100k/day, PAS, AIDA, custom belief-first?)
- Any brand-specific SOPs that override defaults?
- Are there proven hook formulas or CTA templates the agency reuses?

### 7. Proof & Research
- Where do brand bibles, winning ads, and transcripts live?
- What proof sources can be cited per brand? (Studies, reviews, press, founder credentials)
- Are there review repositories (Trustpilot, Amazon, internal) the AI can pull pain/desire language from?

### 8. Markets & Languages
- Which languages need native scripts (not translation)?
- Region-specific rules (UK ASA wording, German "Werbung" labeling, US FTC endorsement guides)?
- Currency, units, spelling defaults per market?

### 9. Swipes & Inspiration
- Does the agency keep a swipe file? Where?
- Any specific competitors or adjacent brands the AI should monitor?
- Preferred ad libraries (Meta Ad Library, TikTok Creative Center, Foreplay, etc.)?

### 10. What "Done" Looks Like
- What does an approved script look like? (Get one example per brand if possible.)
- What's been rejected and why? (Failure cases reveal the real bar.)
- What's the conversion target or success metric (CPA, ROAS, hook rate)?

---

## After Onboarding — First-Week Checklist

- [ ] `_SYSTEM_CONTEXT.md` filled in: agency name, active brands table, delivery format
- [ ] One `brand.md` per brand, completed using the template
- [ ] Agency-specific SOPs added to `frameworks/` (delivery, compliance, naming)
- [ ] At least 3 swipes broken down in `swipes/` to seed pattern recognition
- [ ] First test script approved by the owner before scaling volume

---

## Maintenance

- `universal-patterns.md` — update as you learn what consistently works/fails across brands. This is the agency's compounding intelligence.
- `brands/[brand]/patterns.md` — update per brand when a hook style, format, or angle proves out.
- `swipes/` — add a new breakdown any time a competitor ad makes you stop scrolling. Extract the mechanism, don't copy the words.
