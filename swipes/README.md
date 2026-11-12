# Swipe / inspo library (v0)

First pass built **2026-11-12 17:49 JST** for Alan’s request (via CoS, 12.11.2026 17:05 JST): one library of reference ads clients sent Aditor.

Index: [`index.csv`](index.csv) · [`index.json`](index.json). One row per unique ad, deduped by normalized URL.

## Totals

- **Ads (unique URLs):** 2514
- **Clients:** 205
- **With frames:** 254
- **OK:** 254
- **DEAD:** 7
- **INCOMPLETE:** 2253

### Top 5 clients by volume

| Client | Ads |
|---|---:|
| drive | 318 |
| Levide | 190 |
| Bawldy | 97 |
| patryk matuszak | 85 |
| Veda Naturals | 76 |

### By platform

| Platform | Ads |
|---|---:|
| file | 491 |
| youtube | 274 |
| instagram_reel | 260 |
| meta_ad_library | 221 |
| google_drive | 220 |
| tiktok | 210 |
| instagram_post | 208 |
| facebook | 150 |
| atria | 124 |
| magicbrief | 88 |
| foreplay | 65 |
| youtube_shorts | 59 |
| instagram | 53 |
| instagram_story | 19 |
| x | 19 |
| frameio | 17 |
| hookd | 11 |
| swipekit | 10 |
| trendtrack | 4 |
| tiktok_ad_library | 3 |
| topads | 3 |
| (blank) | 3 |
| milanote | 1 |
| vimeo | 1 |

### By primary source_type

| Source | Ads (primary, after URL dedupe) |
|---|---:|
| trello | 1277 |
| slack | 706 |
| drive | 514 |
| local_repo | 17 |

## Layout

- Media (when downloaded): `swipes/<client-slug>/<id>/video.mp4` (or `image.*`). **Gitignored** so the repo stays small.
- Keyframes: `swipes/<client-slug>/<id>/frames/01.jpg` … cap 20, scale 540w, scene-change `gt(scene,0.3)` plus first frame (`ffmpeg`). **Committed.**
- `yt-dlp` used from `/workspace/.venv/bin/yt-dlp` (symlink to `/home/box/bin/yt-dlp`); `ffmpeg` at `/usr/bin/ffmpeg`.
- Fields left **blank** when unknown. Quotes in `why_client_sent_it` are verbatim excerpts from the source (truncated at 800 chars with …). Metadata is never invented.
- A URL shared by more than one client appears **once** (dedupe by normalized URL). The row keeps the source with the strongest evidence (local file, then a why-quote, then a client name).

## Status values

- **OK** — local media present and at least one keyframe extracted.
- **DEAD** — 404 / removed / expired, confirmed on fetch.
- **INCOMPLETE** + reason — link kept, not downloaded (login/ACL, Meta Ad Library, IG often needs cookies, first-pass cap, named reference without a URL, etc.).

## Coverage

Every source scanned is listed, including zero counts. Method is stated per row.

### Trello — 133 boards (all Active, Trial, past/closed visible to the Player token)

Method: read-only GET via existing `TRELLO_KEY`/`TRELLO_TOKEN` in `/workspace/tim-editor-ops/.trello.env` (account `@Player` / aditorteam1). `GET /members/me/boards?filter=all`, then per board `GET /boards/{id}/cards?filter=all` (desc, attachments, checklists) and `GET /boards/{id}/actions?filter=commentCard` (paginated). **No writes, no new tokens, no cookie scraping.** 9260 cards, 19559 comments scanned. 0 API errors.

| Board | State | Cards | Comments | Ads found | URL |
|---|---|---:|---:|---:|---|
| 28Pilates | closed | 55 | 46 | 13 | https://trello.com/b/ZTcl20d0/28pilates |
| 305 Care | closed | 11 | 47 | 0 | https://trello.com/b/EbCDkmTP/305-care |
| A D K Trading FZE | closed | 9 | 0 | 0 | https://trello.com/b/FCccTSul/a-d-k-trading-fze |
| Adelira | closed | 20 | 68 | 0 | https://trello.com/b/qYUdZdGL/adelira |
| Aditor | open | 175 | 297 | 38 | https://trello.com/b/1MgwKBHI/aditor |
| Aditor Training | closed | 4 | 0 | 0 | https://trello.com/b/A0wVYqfW/aditor-training |
| Aditor Training | closed | 30 | 15 | 1 | https://trello.com/b/xGaioDBG/aditor-training |
| Aditor Training | Test Cards | open | 90 | 2 | 21 | https://trello.com/b/NM1UUPuC/aditor-training-test-cards |
| Aditor | Content Pipeline | open | 14 | 1 | 0 | https://trello.com/b/aCxTINYB/aditor-content-pipeline |
| Aditor | Editoren | closed | 315 | 0 | 1 | https://trello.com/b/pKXBlC4L/aditor-editoren |
| Aditor | Kappa Center | closed | 346 | 0 | 0 | https://trello.com/b/22RswVVj/aditor-kappa-center |
| AgelessRx | open | 9 | 19 | 0 | https://trello.com/b/Mncmm83B/agelessrx |
| Alder | closed | 55 | 36 | 13 | https://trello.com/b/Qg084Lbb/alder |
| Aloha Club | closed | 11 | 8 | 6 | https://trello.com/b/7yAxUsZT/aloha-club |
| audibene GmbH | open | 60 | 362 | 28 | https://trello.com/b/xreMwX1D/audibene-gmbh |
| Bawldy | open | 337 | 712 | 106 | https://trello.com/b/k9q22m5t/bawldy |
| Beinfit / Swivy | open | 220 | 451 | 4 | https://trello.com/b/qsqPwohi/beinfit-swivy |
| Bingdu | closed | 8 | 1 | 0 | https://trello.com/b/fL2BJQco/bingdu |
| Biotikur | closed | 9 | 11 | 9 | https://trello.com/b/uzzG88xQ/biotikur |
| Breakoutlab | closed | 19 | 27 | 4 | https://trello.com/b/FpeKkWzQ/breakoutlab |
| Brian Gonzalez | closed | 22 | 7 | 7 | https://trello.com/b/xeCTwBu1/brian-gonzalez |
| Buchmann | open | 90 | 264 | 0 | https://trello.com/b/37AsIyxb/buchmann |
| ByNoria | open | 10 | 21 | 9 | https://trello.com/b/xHTD5k08/bynoria |
| Care & Bloom | closed | 23 | 25 | 0 | https://trello.com/b/oUupXXq1/care-bloom |
| Cheech & Chong | closed | 26 | 108 | 3 | https://trello.com/b/Irv9729s/cheech-chong |
| Clubwell | closed | 19 | 33 | 2 | https://trello.com/b/xjvsYsTi/clubwell |
| Cuppings | closed | 17 | 44 | 5 | https://trello.com/b/cZf40Zjn/cuppings |
| DailyBioLabs | closed | 39 | 63 | 18 | https://trello.com/b/KQopt7K8/dailybiolabs |
| Demo Board | open | 31 | 0 | 0 | https://trello.com/b/cx6SwtqA/demo-board |
| Doctor Vitals | closed | 6 | 4 | 0 | https://trello.com/b/150hd1u8/doctor-vitals |
| Douxds | open | 142 | 551 | 50 | https://trello.com/b/SwB4mRoi/douxds |
| Dr Franks | closed | 28 | 87 | 18 | https://trello.com/b/jfHxCt2c/dr-franks |
| DreamyKissen | closed | 18 | 16 | 6 | https://trello.com/b/CN7C59DX/dreamykissen |
| EcomPro GmbH | open | 2630 | 3974 | 67 | https://trello.com/b/IaQnUuno/ecompro-gmbh |
| Erste Hilfe Kinder Kurs | open | 6 | 0 | 0 | https://trello.com/b/JFDtprG0/erste-hilfe-kinder-kurs |
| Fabio Bär | open | 18 | 15 | 2 | https://trello.com/b/iUDwldY0/fabio-b%C3%A4r |
| Federico Crespi | closed | 41 | 109 | 35 | https://trello.com/b/XCk8rKBR/federico-crespi |
| Forward Health GmbH | open | 212 | 897 | 22 | https://trello.com/b/9pxOmM5r/forward-health-gmbh |
| Freiheit Media | open | 112 | 523 | 9 | https://trello.com/b/kQdZRyaL/freiheit-media |
| Futter Vergleich | open | 8 | 16 | 8 | https://trello.com/b/GNn3xN84/futter-vergleich |
| Gen Aditor - Production | open | 10 | 2 | 0 | https://trello.com/b/P3ajNKaV/gen-aditor-production |
| Get A Drip | closed | 13 | 30 | 0 | https://trello.com/b/lI0PZFq2/get-a-drip |
| Glow25 / DailyRituals | open | 263 | 1453 | 29 | https://trello.com/b/tgdISVZ5/glow25-dailyrituals |
| Golden Saffron | closed | 6 | 6 | 2 | https://trello.com/b/6G9kr7oq/golden-saffron |
| Gracen App | open | 73 | 84 | 40 | https://trello.com/b/DTrXI3Mn/gracen-app |
| iScent | closed | 8 | 1 | 0 | https://trello.com/b/VDkUZBAc/iscent |
| Joel Sorenson | closed | 54 | 72 | 10 | https://trello.com/b/bfRE4LYN/joel-sorenson |
| Joey Bertschler | open | 7 | 3 | 0 | https://trello.com/b/laTxhjpG/joey-bertschler |
| K&O Solutions Limited | closed | 4 | 0 | 0 | https://trello.com/b/k2gzDTq2/ko-solutions-limited |
| Kappa Board | closed | 0 | 0 | 0 | https://trello.com/b/329Yl3fJ/kappa-board |
| Keller Gesundheitspflege GmbH | closed | 101 | 290 | 5 | https://trello.com/b/vmIMYpD1/keller-gesundheitspflege-gmbh |
| Kim & Kimmy | closed | 15 | 10 | 1 | https://trello.com/b/4JZJvuX1/kim-kimmy |
| Levide | open | 652 | 1512 | 201 | https://trello.com/b/LMARE5GN/levide |
| Liebscher & Bracht | open | 1 | 9 | 0 | https://trello.com/b/mhsW2rJy/liebscher-bracht |
| Liebscher & Bracht Schmerzfrei GmbH | open | 10 | 8 | 1 | https://trello.com/b/LDfH60Um/liebscher-bracht-schmerzfrei-gmbh |
| Lift | closed | 9 | 25 | 0 | https://trello.com/b/0rjUWVts/lift |
| Lior | open | 178 | 339 | 12 | https://trello.com/b/ho2xRIzC/lior |
| LOTUS | closed | 9 | 47 | 0 | https://trello.com/b/Tf7FYHom/lotus |
| Lucinn | closed | 24 | 61 | 26 | https://trello.com/b/lvJDvLiX/lucinn |
| Lucky & Loyal | open | 44 | 134 | 9 | https://trello.com/b/qxninwbn/lucky-loyal |
| LUVEA | open | 1 | 3 | 0 | https://trello.com/b/C0rScWct/luvea |
| LVRG | closed | 23 | 49 | 21 | https://trello.com/b/6jXxnmR1/lvrg |
| mammaly (Peturo GmbH) | closed | 146 | 845 | 59 | https://trello.com/b/eTbGk1zt/mammaly-peturo-gmbh |
| Matter | closed | 68 | 157 | 19 | https://trello.com/b/dOQGhCSZ/matter |
| Meine Studios | closed | 10 | 0 | 0 | https://trello.com/b/s4hREkMO/meine-studios |
| METAFIT PHARMA SOLUTIONS LLC | closed | 4 | 0 | 0 | https://trello.com/b/TScuqZ02/metafit-pharma-solutions-llc |
| My Trello board | open | 2 | 0 | 0 | https://trello.com/b/rEQTEvNO/my-trello-board |
| MYND Organics | closed | 108 | 260 | 11 | https://trello.com/b/rAU1hVpd/mynd-organics |
| Naturida | closed | 13 | 56 | 4 | https://trello.com/b/kCaPHor0/naturida |
| Naturrise | open | 23 | 34 | 0 | https://trello.com/b/zuxtoOEM/naturrise |
| Nicholas | closed | 9 | 3 | 0 | https://trello.com/b/15tHHdzu/nicholas |
| Noaré | closed | 7 | 3 | 0 | https://trello.com/b/hFgp5CAA/noar%C3%A9 |
| Norman Teo | closed | 10 | 1 | 0 | https://trello.com/b/V2d2ezYw/norman-teo |
| Novaliv | closed | 11 | 10 | 0 | https://trello.com/b/OTBo3RBV/novaliv |
| Novasabers | closed | 7 | 7 | 1 | https://trello.com/b/Dzx1V7d6/novasabers |
| NurseBabes | closed | 15 | 49 | 3 | https://trello.com/b/DrR7JIOj/nursebabes |
| Olivia Morasch | closed | 33 | 73 | 4 | https://trello.com/b/4CWTfs7E/olivia-morasch |
| Parrot Ai | closed | 22 | 32 | 3 | https://trello.com/b/JIULQodD/parrot-ai |
| PEAQ Skin | open | 100 | 190 | 26 | https://trello.com/b/qbcfVLxS/peaq-skin |
| Plants are Purple | closed | 22 | 25 | 39 | https://trello.com/b/pYb3ltp9/plants-are-purple |
| Power / Sleep Bites | closed | 8 | 4 | 3 | https://trello.com/b/EV0Dg0gb/power-sleep-bites |
| Powercleany | closed | 34 | 137 | 1 | https://trello.com/b/tO1XtRdU/powercleany |
| Proof Brother | closed | 155 | 416 | 7 | https://trello.com/b/WHUNfJWb/proof-brother |
| Purevia Naturals | closed | 23 | 11 | 1 | https://trello.com/b/OHWyUtxZ/purevia-naturals |
| Raindrop | closed | 22 | 26 | 1 | https://trello.com/b/Kd0KU5nH/raindrop |
| Reishi Therapy | closed | 115 | 192 | 5 | https://trello.com/b/GqAbaMZT/reishi-therapy |
| Rrezon | closed | 29 | 78 | 6 | https://trello.com/b/m6RL9OCZ/rrezon |
| Rugsak | open | 42 | 116 | 7 | https://trello.com/b/WVa7TgeQ/rugsak |
| Sassy Saints B.V. | closed | 9 | 38 | 2 | https://trello.com/b/q80kx9k0/sassy-saints-bv |
| Schema M | closed | 14 | 10 | 0 | https://trello.com/b/DpvDDnGa/schema-m |
| Shape Republic GmbH | closed | 13 | 10 | 1 | https://trello.com/b/rFdGgtgl/shape-republic-gmbh |
| shawn-test | open | 22 | 0 | 1 | https://trello.com/b/zcZZlIsy/shawn-test |
| Shifaa Naturals | closed | 8 | 5 | 1 | https://trello.com/b/0hT1CJTH/shifaa-naturals |
| smart.engineered GmbH & Co. KG | closed | 15 | 47 | 6 | https://trello.com/b/qVmwnG7I/smartengineered-gmbh-co-kg |
| Solara | closed | 7 | 4 | 0 | https://trello.com/b/o3POWt01/solara |
| Soleya Scrubs | closed | 7 | 19 | 0 | https://trello.com/b/3YgGywEp/soleya-scrubs |
| Source Werbeartikel | closed | 80 | 47 | 0 | https://trello.com/b/hscQNudQ/source-werbeartikel |
| Step One Clothing UK | closed | 32 | 14 | 0 | https://trello.com/b/VMEFvtRa/step-one-clothing-uk |
| Sultan of Style | closed | 32 | 82 | 0 | https://trello.com/b/S0sdRwKa/sultan-of-style |
| Swen | closed | 4 | 0 | 0 | https://trello.com/b/HpVHpUzJ/swen |
| Syxgott Parfum | closed | 9 | 10 | 0 | https://trello.com/b/XeGivdD1/syxgott-parfum |
| TANIT | closed | 27 | 27 | 8 | https://trello.com/b/eHMmALwr/tanit |
| Terra Health | closed | 26 | 120 | 22 | https://trello.com/b/OadfPZJI/terra-health |
| TerraTherapy | closed | 9 | 14 | 4 | https://trello.com/b/vycvxCUE/terratherapy |
| testboard | closed | 1 | 0 | 0 | https://trello.com/b/xfjoyMDr/testboard |
| testbrand | closed | 6 | 0 | 0 | https://trello.com/b/seq1sKJl/testbrand |
| Testcompany | open | 2 | 3 | 0 | https://trello.com/b/NA8slW22/testcompany |
| Testcompany | closed | 0 | 0 | 0 | https://trello.com/b/65kEyU2C/testcompany |
| Testcompany | closed | 0 | 0 | 0 | https://trello.com/b/g2DV57un/testcompany |
| Testcompany | closed | 0 | 0 | 0 | https://trello.com/b/X8syHA21/testcompany |
| Testcompany | closed | 0 | 0 | 0 | https://trello.com/b/ByAa6wB3/testcompany |
| Testcompany | closed | 0 | 0 | 0 | https://trello.com/b/uCXlTjGI/testcompany |
| Testcompany | closed | 7 | 0 | 0 | https://trello.com/b/KJSUYP0s/testcompany |
| Testcompany | closed | 8 | 0 | 0 | https://trello.com/b/Ot3sxoNV/testcompany |
| Testcompany | closed | 11 | 24 | 0 | https://trello.com/b/cFMmbnjE/testcompany |
| testunternehmen | closed | 4 | 0 | 0 | https://trello.com/b/wLHyBfvo/testunternehmen |
| The Good Life Investment Corporation | closed | 43 | 73 | 12 | https://trello.com/b/4FL8KDuG/the-good-life-investment-corporation |
| The Nerve Brand | closed | 28 | 23 | 17 | https://trello.com/b/NPsxB6SB/the-nerve-brand |
| Tim Kunde Test Board | closed | 9 | 1 | 0 | https://trello.com/b/LXFEKIcQ/tim-kunde-test-board |
| Timothy Mitchum | closed | 155 | 607 | 59 | https://trello.com/b/Qyq7sVdm/timothy-mitchum |
| Trimrx | closed | 147 | 375 | 42 | https://trello.com/b/PyfmP1er/trimrx |
| Trufollic | closed | 12 | 27 | 1 | https://trello.com/b/MPbYddxH/trufollic |
| Try Youth | closed | 16 | 53 | 0 | https://trello.com/b/IFHTOQv6/try-youth |
| TryJello | closed | 10 | 21 | 1 | https://trello.com/b/daV3EkC7/tryjello |
| TryNovia | closed | 45 | 59 | 2 | https://trello.com/b/wRdCasHG/trynovia |
| Veda Naturals | open | 351 | 1559 | 87 | https://trello.com/b/oF21bNTc/veda-naturals |
| Velantra | closed | 30 | 21 | 3 | https://trello.com/b/Gj9LfSwP/velantra |
| Veloura | open | 56 | 147 | 23 | https://trello.com/b/oymrtNzd/veloura |
| Vital Growth UG | open | 65 | 252 | 9 | https://trello.com/b/7xPUsvW0/vital-growth-ug |
| VitalVac | open | 67 | 116 | 20 | https://trello.com/b/YbCPZGro/vitalvac |
| Volumane | closed | 20 | 9 | 2 | https://trello.com/b/f7Aql4Vg/volumane |
| Voya Barefoot | closed | 11 | 18 | 1 | https://trello.com/b/Z0bjNU9x/voya-barefoot |
| Zippit B.V. | closed | 4 | 1 | 0 | https://trello.com/b/xMIASbqk/zippit-bv |

### Slack — workspace `aditorinc` (Alan’s user-Slack connector, U04NRHWBSMT)

Method: **workspace-wide search** (not a full history dump of every channel) via `slack_search_public_and_private`, plus a **full read** of `#inspo` (C0AR859UBSM) and `#format-swipe-inbox` (C0BJC1D3FU2). Searches (paginated, 20/page, sort=timestamp): `ads/library` (complete, 4 pages), `tiktok.com` (complete, 3 pages), `instagram.com/reel` (9 pages, **more remain** — first-pass cap), `instagram.com/p` (2 pages, more remain), `instagram`, `tiktok`, `youtube`, `inspo`, `referenz`, `beispiel`, `swipekit`, files titled inspo. Filters included `has:link`. Slack Connect (55 shared channels) and 175 public/private channels listed; DMs paginated to completion (271 DMs).

Read-only: no posts, comments, reactions, or messages to clients/editors. Known ACL: Slack file `F0AB2Q03ANS` in `#28pilates-aditor-ads` (C09FFKKLJUU) is marked INCOMPLETE (`file_not_found` / external-guest ACL); no workaround.

| Channel | Type | Slack Connect | Archived | Ads found | ID |
|---|---|---|---|---:|---|
| #general | Public Channel |  | No | 2 | C04NE0BNAAK |
| #random | Public Channel |  | No | 3 | C04NRHWDQAZ |
| #booked-meetings | Private Channel |  | No | 14 | C04PJAFVAG0 |
| #editing | Private Channel |  | No | 33 | C05Q89GMT1U |
| #creditcard | Public Channel |  | No | 1 | C077YAWVBS7 |
| #wins | Public Channel |  | No | 0 | C07ABD1C37F |
| #terrahealth-pipeline | Private Channel | Yes (shared externally) | No | 0 | C07KBBQT2TU |
| #ecompro-pipeline | Private Channel |  | No | 1 | C07LUDQHRRA |
| #automations | Private Channel |  | No | 0 | C07UL6BAG1Z |
| #editor-approval | Public Channel |  | No | 0 | C088V00JW20 |
| #nursebabes-aditor | Private Channel | Yes (shared externally) | No | 1 | C08JDCM5XJN |
| #oguz-virtual-assistance | Private Channel | Yes (shared externally) | No | 38 | C0979SEAT8A |
| #tanittabs-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C099KKN3P4M |
| #alder-x-aditor | Private Channel | Yes (shared externally) | No | 2 | C099T0XV4RL |
| #freiheitmedia-x-aditor | Private Channel | Yes (shared externally) | No | 23 | C099U1Z2JSW |
| #scripts | Private Channel |  | No | 0 | C09BVS4E21J |
| #oguz-specialforces | Private Channel | Yes (shared externally) | No | 1 | C09DTFC0KK2 |
| #card-feedback | Public Channel |  | No | 12 | C09EQDQQBDY |
| #matter-x-aditor | Private Channel |  | No | 0 | C09HEPR72UF |
| #velantra-pipeline | Private Channel |  | No | 0 | C09J8GGJQTV |
| #proofbrothers-x-aditor | Private Channel |  | No | 4 | C09L6Q7R3R8 |
| #adelira-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C09LY79MMNE |
| #proofbrother-pipeline | Private Channel |  | No | 0 | C09MZJLV944 |
| #can-we-do-300-ads-i-need-to-know | Private Channel | Yes (shared externally) | No | 0 | C09N7CRQGFQ |
| #beinfit-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C09NTATFAMB |
| #purevianaturals-x-aditor | Private Channel |  | No | 0 | C09UK7H2T7A |
| #purevianaturals-pipeline | Private Channel |  | No | 4 | C09UW408Q4Q |
| #newbies | Private Channel |  | No | 0 | C09V3KU7G77 |
| #breakoutlab-x-aditor | Public Channel | Yes (shared externally) | No | 3 | C09VD0MAUKY |
| #douxds-x-aditor | Private Channel | Yes (shared externally) | No | 4 | C0A0P8V1V6D |
| #phycohealth-x-aditor | Public Channel | Yes (shared externally) | No | 0 | C0A0SRC6TS7 |
| #phycohealth-pipeline | Private Channel |  | No | 0 | C0A1NRDAD25 |
| #utilisesocial-x-aditor | Public Channel | Yes (shared externally) | No | 0 | C0A1UR837BN |
| #breakoutlab-pipeline | Private Channel |  | No | 0 | C0A23PE3P1S |
| #utilisesocial-pipeline | Private Channel |  | No | 0 | C0A285N102E |
| #aditor-office | Private Channel |  | No | 6 | C0A2UCZU1S7 |
| #nuver-x-aditor | Private Channel |  | No | 0 | C0A3LBE9NJK |
| #syxgott-parfum-x-aditor | Public Channel | Yes (shared externally) | No | 2 | C0A3Z6MV34Z |
| #syxgott-pipeline | Private Channel |  | No | 0 | C0A4H484Q9Y |
| #305-care-pipeline | Private Channel |  | No | 0 | C0A4LLFTSCT |
| #gotyu-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0A5771N7RU |
| #305-care-x-aditor | Public Channel | Yes (shared externally) | No | 0 | C0A57J8NUN4 |
| #jello-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0A5DBYK72P |
| #trimxr-pipeline | Private Channel |  | No | 0 | C0A5VR97C2J |
| #mysweetsmile-ltd-x-aditor | Public Channel |  | No | 0 | C0A62E3G5KJ |
| #trimrx-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0A6DV9LU0Y |
| #skinbro-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0A6T6VEX8Q |
| #gracen-x-aditor | Private Channel | Yes (shared externally) | No | 7 | C0A7FM6PTT8 |
| #buchmann-x-aditor | Private Channel | Yes (shared externally) | No | 4 | C0A88GW1XK5 |
| #oliviamorasch-x-aditor | Private Channel | Yes (shared externally) | No | 10 | C0A8AGNU5B9 |
| #script-to-ugc-video | Public Channel |  | No | 0 | C0A8HQCMTU7 |
| #buchmann-pipeline | Private Channel |  | No | 0 | C0A8LT6D7TQ |
| #oliviamorasch-x-pipeline | Private Channel |  | No | 0 | C0A8S08FDEE |
| #shaperepublicgmbh-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0ABBTEGAPJ |
| #cuppings-x-pipeline | Private Channel |  | No | 0 | C0ABGTUT2A1 |
| #cuppings-x-aditor | Private Channel |  | No | 0 | C0ABLAPA6LA |
| #shaperepublic-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0ABZ4JE4JC |
| #gracen-x-pipeline | Private Channel |  | No | 0 | C0AD0U37ZMF |
| #assets-and-feedbacks | Private Channel |  | No | 2 | C0AE7G22CN5 |
| #vitalgrowth-x-pipeline | Private Channel |  | No | 0 | C0AEKQX0GTY |
| #metafitpharmasolutionsllc-x-aditor | Private Channel |  | No | 0 | C0AET80937F |
| #metafitpharmasolutionsllc-x-pipeline | Private Channel |  | No | 0 | C0AET81ME85 |
| #vitalgrowth-x-aditor | Private Channel |  | No | 0 | C0AF0Q78389 |
| #erste-hilfe-kinder-kurs | Private Channel |  | No | 0 | C0AF8LMCHKK |
| #2fa-playermail | Private Channel |  | No | 0 | C0AFSCB2NP6 |
| #trynovia-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0AG826GVUY |
| #unclaimed-cards | Public Channel |  | No | 0 | C0AHM9PLUSD |
| #sultanofstyle-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0AKZR24MSP |
| #sultanofstyle-pipeline | Private Channel |  | No | 0 | C0AL69ETZ4J |
| #terratherapy-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0AM4KTHXB8 |
| #novaliv-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0AMBG53NCW |
| #abdullah-pipeline | Private Channel |  | No | 0 | C0APG34A3S6 |
| #bug-catchers | Public Channel |  | No | 0 | C0APU504SUT |
| #inspo | Public Channel |  | No | 0 | C0AR859UBSM |
| #denny-pipeline | Private Channel |  | No | 0 | C0ASVNWUAAV |
| #forwardhealthgmbh-x-pipeline | Private Channel |  | No | 0 | C0ATC3EKCMD |
| #forwardhealthgmbh-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0ATTALCPM0 |
| #vibecoding-accountability | Private Channel |  | No | 3 | C0AUDQ97XS8 |
| #dispatch-actions | Private Channel |  | No | 0 | C0B12NE2Y8M |
| #mynd-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0B17RYQM1T |
| #mynd-pipeline | Private Channel |  | No | 0 | C0B1Q59LWF3 |
| #abdullah-x-aditor | Private Channel | Yes (shared externally) | No | 6 | C0B25E4BS74 |
| #hellonancy-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0B5Z8WQY2W |
| #asset-agent | Private Channel |  | No | 0 | C0B6958UY04 |
| #carebloom-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0B753MS7HR |
| #carebloom-x-pipeline | Private Channel |  | No | 0 | C0B7BETQTNW |
| #content-pipeline | Private Channel | Yes (shared externally) | No | 6 | C0B83US52FJ |
| #freiheit-pipeline | Private Channel |  | No | 0 | C0B8GSCMRQW |
| #book-club | Private Channel |  | No | 0 | C0BBU7ZM8A3 |
| #fabiobar-x-aditor | Private Channel | Yes (shared externally) | No | 2 | C0BCYUYU0S3 |
| #fabiobar-pipeline | Private Channel |  | No | 0 | C0BDB1PE3JR |
| #format-swipe-inbox | Private Channel |  | No | 11 | C0BJC1D3FU2 |
| #audibenegmbh-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0BKG8T1QJJ |
| #audibenegmbh-pipeline | Private Channel |  | No | 0 | C0BKMUZ8TQU |
| #dailybiolabs-pipeline | Private Channel |  | No | 0 | C0BPH12AHU6 |
| #payroll-cycle | Private Channel |  | No | 0 | C0BQJBS6BQC |
| #agelessrx-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0BRTB5914M |
| #agelessrx-pipeline | Private Channel |  | No | 0 | C0BRV8YNNSJ |
| #insta-squad | Private Channel |  | No | 1 | C0BSA6LM6EP |
| #adlingo-news | Private Channel |  | No | 0 | C0BU5NZ2J0H |
| #bynoria-pipeline | Private Channel |  | No | 0 | C0C08MN2F1R |
| #bynoria-x-aditor | Private Channel |  | No | 0 | C0C0AF0UQ5T |
| #buchmann-techdepartment | Private Channel | Yes (shared externally) | No | 0 | C0C11JEQ45A |
| #rugsak-x-aditor | Private Channel |  | No | 0 | C0C1SQW092B |
| #finance-shadow | Private Channel |  | No | 0 | C0C2WQTK2KY |
| #finance | Public Channel |  | No | 0 | C0C2YHKSGMQ |
| #futter-vergleich-pipeline | Private Channel |  | No | 0 | C0C3CQBFNR2 |
| #futter-vergleich-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0C43FJPE0G |
| #liebscherbrachtschmerzfreigmbh-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0C48864ZM1 |
| #liebscherbrachtschmerzfreigmbh-pipeline | Private Channel |  | No | 0 | C0C4886CD0B |
| #mentor-relations | Private Channel |  | No | 0 | C0C7E6UK7H7 |
| #gen-agent-maxxing | Private Channel |  | No | 0 | C0CFME8J9GV |
| #adktradingfze-pipeline | Private Channel |  | No | 0 | C0CFX92FDKR |
| #adktradingfze-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0CGAM5H294 |
| #glow25 | Private Channel | Yes (shared externally) | No | 3 | C071VCDDRMX |
| #vedanaturals-creativepipeline | Private Channel | Yes (shared externally) | No | 17 | C07CSJJDMP0 |
| #plants-are-purple | Public Channel | Yes (shared externally) | No | 0 | C07G80MQ4GH |
| #aditor-icon | Private Channel | Yes (shared externally) | No | 0 | C08CL3QRV28 |
| #vitalvac_pipeline | Private Channel | Yes (shared externally) | No | 5 | C08HHAM88DB |
| #aai-aditorai | Private Channel | Yes (shared externally) | No | 32 | C08JUKWE49F |
| #ext-aditor-captions | Private Channel | Yes (shared externally) | No | 0 | C099VV1EU8Z |
| #28pilates-aditor-ads | Private Channel | Yes (shared externally) | No | 11 | C09FFKKLJUU |
| #veloura-x-aditor | Private Channel | Yes (shared externally) | No | 1 | C09RA094X6J |
| #lior-creatives | Private Channel | Yes (shared externally) | No | 0 | C0A68H7KMF0 |
| #aditor-mammaly | Private Channel | Yes (shared externally) | No | 2 | C0ABUCE5T34 |
| #rippl-aditor | Private Channel | Yes (shared externally) | No | 0 | C0B781F0EET |
| #lvrg-x-aditor | Private Channel | Yes (shared externally) | No | 0 | C0B9DLSRRJM |
| #emily-bass | Private Channel |  | Yes | 0 | C05ERU95JQM |
| #crypto-invest-club | Private Channel |  | Yes | 0 | C05F6PT2J9F |
| #mike-jones | Private Channel |  | Yes | 0 | C05FUCTQ5DF |
| #joeyfromcic | Private Channel |  | Yes | 0 | C0651MDUMM4 |
| #joey-editing | Private Channel |  | Yes | 0 | C06B5VDHFT7 |
| #product | Private Channel |  | Yes | 0 | C07NYGCJH7B |
| #best-nurse-ever-pipeline | Private Channel |  | Yes | 2 | C07QDGXTRNG |
| #novasabers-creatives | Private Channel |  | Yes | 0 | C07T76C8E06 |
| #parrot-ai | Private Channel |  | Yes | 0 | C0890LW4EAW |
| #parrot-ai8444 | Private Channel |  | Yes | 2 | C08FWC2G87P |
| #nursebabes-pipeline | Private Channel |  | Yes | 0 | C08JZ7SN33J |
| #bawldy-pipeline | Private Channel |  | Yes | 10 | C096P1LE7FE |
| #levide-pipeline | Private Channel |  | Yes | 11 | C0996HCCP4P |
| #korabeta | Private Channel |  | Yes | 0 | C09A65E9YKS |
| #source-werbeartikel | Private Channel |  | Yes | 15 | C09ETJQE96G |
| #noaré-x-aditor | Private Channel |  | Yes | 0 | C09GP7VMYCA |
| #solara-x-aditor | Private Channel |  | Yes | 2 | C09H5Q1UQK0 |
| #alohaclub-x-aditor | Private Channel |  | Yes | 3 | C09JF41UY8L |
| #riskeys-x-aditor | Private Channel |  | Yes | 0 | C09LMENKYAX |
| #300ads-study | Private Channel |  | Yes | 0 | C09MU0JPXB9 |
| #28pilates-pipeline | Private Channel |  | Yes | 0 | C09UEMSTFBK |
| #123455678999 | Private Channel |  | Yes | 0 | C0A2TLARTRP |
| #55555555555 | Private Channel |  | Yes | 0 | C0A38MSAXGX |
| #12345678 | Private Channel |  | Yes | 0 | C0A3DM9B6KE |
| #123456788 | Private Channel |  | Yes | 0 | C0A3MLDML2C |
| #12345555555 | Private Channel |  | Yes | 0 | C0A3TNKPVGU |
| #source-pipeline | Private Channel |  | Yes | 0 | C0A42N0673N |
| #zippitbv-x-aditor | Private Channel |  | Yes | 0 | C0A7CAJRM1V |
| #zippitbv-x-aditor | Private Channel |  | Yes | 0 | C0A7TPE4VFC |
| #aditor-icon-service | Private Channel |  | Yes | 0 | C0AB32WJCJD |
| #cuppings-x-aditor | Private Channel |  | Yes | 0 | C0AB4T3DJ0P |
| #kosolutionslimited-x-pipeline | Private Channel |  | Yes | 0 | C0AEA103H45 |
| #mammalypeturogmbh-x-pipeline | Private Channel |  | Yes | 0 | C0AEK5QCB9N |
| #mammalypeturogmbh-x-aditor | Private Channel |  | Yes | 0 | C0AEK5QS8P2 |
| #kosolutionslimited-x-aditor | Private Channel |  | Yes | 0 | C0AF7MUQSF2 |
| #trynovia-x-pipeline | Private Channel |  | Yes | 0 | C0AFBMFB5JS |
| #peaqskin-pipeline | Private Channel |  | Yes | 1 | C0AHEV9D82H |
| #kellergesundheitspflege-pipeline | Private Channel |  | Yes | 0 | C0AUJC1LNG3 |
| #kellergesundheitspflege-x-aditor | Private Channel |  | Yes | 0 | C0AV3L6GKBK |
| #smartengineeredgmbhcokg-pipeline | Private Channel |  | Yes | 0 | C0B920T65FT |
| #smartengineeredgmbhcokg-x-aditor | Private Channel |  | Yes | 1 | C0B920TKKG9 |
| #sassysaintsbv-x-aditor | Private Channel |  | Yes | 0 | C0B9MDGLX7T |
| #sassysaintsbv-pipeline | Private Channel |  | Yes | 0 | C0B9P6X5EBW |
| #raindrop-x-aditor | Private Channel |  | Yes | 1 | C0BJ3NP0ZQV |
| #raindrop-pipeline | Private Channel |  | Yes | 0 | C0BJ71ZHJ2W |
| #dailybiolabs-x-aditor | Private Channel |  | Yes | 1 | C0BPFCXNU13 |
| #bingdu-x-aditor | Private Channel |  | Yes | 0 | C0BQ7CGSQAJ |
| #creative-saas-dev | Private Channel |  | Yes | 0 | C0C48Q67AKE |

DMs: searched via the same workspace-wide queries (types included `im,mpim`). DMs that produced ads are in the index (`source_ref` is the Slack permalink). Remaining DMs: 0 ads in those search hits. Full 1:1 history of every DM was **not** dumped.

### Google Drive (user-Google-drive, Alan’s account)

Method: `search(query=inspo)`, `search(query=swipe)`, `search(query="referenz OR beispiel OR inspiration")`, `search(query=inspo, mimeType=folder)`, `search_files` for Google Docs with `fullText contains 'inspo'` (first 50 docs, more pages exist). URLs taken from file names and Doc snippets. `.prproj` editor projects excluded. Folder **contents** were not fully listed this pass (many folders returned `readable: false`).

| Item | Ads found | Method / notes | URL |
|---|---:|---|---|
| search query=inspo (all pages, complete) + search query=swipe (all pages, complete) | 363 | user-Google-drive search(query=inspo, pageSize=50) pages 1–9 complete; search(query=swipe) pages 1–12 complete. Media fi |  |
| Inspo_3_Friends_New | 4 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Social_Savannah | 4 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Aditor_House_Statics | 15 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| LARQ | 10 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Static_Inspo | 25 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| douxds_inspo | 3 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Vibit | 3 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Lions_Mane | 3 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Fresh_Podcasting | 4 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| _INSPO_1ZDAlhE | 0 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| _INSPO_1VDTiVZ | 0 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| _INSPO_1VDTiVZ | 0 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Aditor_Ad_Inspo | 18 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Ryze | 3 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Moft_V1 | 3 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Simeon_Panda | 4 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Best_Performers | 8 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Ultra_Cleanse_Douxds | 4 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Moft | 3 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Inspo_ProductGallery | 3 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Korean_Skincare | 3 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Zima_Uq9Q | 3 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Zima_Pl3K | 3 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| Inspo_3_Friends | 4 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| _INSPO_179PavTd | 0 | user-Google-drive list_folder (pageSize=200). readable:false on search was a search flag — list_folder succeeded for all |  |
| QUELLE.md in three _INSPO production-strip folders (Denis) | 3 | user-Google-drive read_file on QUELLE.md. Each folder is one source ad; STREIFEN frames are cuts of that ad, not separat |  |
| docs_agelessrx_ugc.txt | 11 | user-Google-drive read_file (full text). |  |
| docs_insurance_swipe.txt | 0 | user-Google-drive read_file (full text). |  |
| Google Docs: fullText inspo (search() pages 1–3 complete, 110 docs) + inspiration (pages 1–3 complete) + referenz/beispiel/swipe (7 pages / 350 docs; further pages are almost all Gemini meeting notes, snippets only on top 3 per page) | 15 | search_files / search with snippetVerbosity=DETAILED (top 3 snippets/page) plus two full read_file calls on titled inspo |  |

### Local CS-repo + production media already on the box

| Item | Ads found | Method |
|---|---:|---|
| brands/28pilates/work (packs 001–002 + brand.md) | 8 | Folded known inspo trio and candidates already documented in the CS repo pack, with source_refs from that pack. |
| aditor/production/dailybiolabs dbl-009 + dbl-010 swipe mp4s | 2 | Folded local swipe files already used in CS repo scripts, with work-file source_refs. |
| gracen-week/*.mp4 (card70, card71, fabulous, inspo-92..96) | 8 | Folded local Gracen inspo files referenced in CS repo work scripts. |
| aditor/production/vital-growth/_intake/inspo (fb.watch videos + keyframes) | 3 | Folded intake inspo-meta.json and already-downloaded mp4s. |
| aditor/production/_scratch/ig-dnl/inspo.mp4 (IG DNL-AzDMz3F, Levide) | 1 | Folded already-downloaded IG reel and yt-dlp info.json. |
| brands/vitalvac/work (Reference A/B/C) | 3 | Folded named references from CS scripts. No URLs present in those files — left INCOMPLETE, not invented. |

## First-pass limits / blockers

- Trello: unchanged from v0 (133/133 boards, 0 errors). Existing Player token, GET only.
- Slack pass 2 finished workspace-wide pagination: ads/library (5 pages, complete), tiktok.com (3, complete), instagram.com/reel (10, complete), instagram.com/p (6, complete), beispiel (3, complete), referenz (2, complete), swipekit (1, complete), inspo messages (9, complete), inspo files (4, complete), tiktok keyword (10, complete), youtube (13, complete). instagram and instagram.com keyword searches still paginating at first-pass-plus (see README after final pages). Full 1:1 DM history still not dumped; DMs covered via the same searches.
- Drive pass 2: inspo file search complete (9 pages); swipe file search complete (12 pages); all 21 inspo-named folders + 2 subfolders listed via list_folder (search’s readable:false was not an ACL block). Docs: inspo via search() complete (110 docs); inspiration complete; referenz/beispiel/swipe 7 pages (350 docs) — further pages are almost entirely Gemini meeting notes (snippets only on top 3/page). Two titled inspo docs fully read (AgelessRX UGC Editing Inspo, Insurance Swipe Video Copy).
- QUELLE.md in three _INSPO strip folders named the original ads (two Atria CDN mp4s, one Meta Ad Library). STREIFEN_*/KONTAKT_* jpgs are cuts of those ads and are not separate index rows.
- Known Slack ACL: F0AB2Q03ANS in #28pilates-aditor-ads still INCOMPLETE; no workaround.
- No cookies / no logins. Videos gitignored; frames committed. No writes to Trello, Slack, or Airtable. No messages to clients or editors.

## What is not in this library

- Our own deliverables (`feedback.aditor.ai`, `cdn.gen.aditor.ai`).
- Generic Google Drive attachments on Trello cards that are not named or described as inspo/swipe/referenz/beispiel.
- Premiere `.prproj` project files.
- Product-shop URLs and other non-ad links that happened to sit on a card.

---

# Swipes — Winning Ad Breakdowns (how to write a breakdown)

The files `_template.md` and (when added) `001-brand-descriptor.md` are **written breakdowns** of winning ads — transcript, structure, psychology, replication notes. They are a different artifact from the harvested media library above.

## How to Break Down a Swipe

Every swipe file follows this exact structure:

### 1. SOURCE
- Platform (Meta, TikTok, YouTube, etc.)
- Brand / advertiser name
- URL or ad library link (if available)
- Estimated performance signals (high spend, long-running, many variations = winner)

### 2. TRANSCRIPT
Full word-for-word transcript. Include:
- `[VISUAL: description]` tags for key visual moments
- `[MUSIC: mood shift]` for audio changes
- `[TEXT ON SCREEN: exact text]` for supers/overlays
- Timestamps if available

### 3. STRUCTURE ANALYSIS
Break the ad into its functional sections:
- **Hook** (0-3s) — What stops the scroll? Which hook type?
- **Problem/Pain** — How do they frame the problem?
- **Mechanism** — What's the unique mechanism or "new way"?
- **Proof** — What evidence do they use? (social proof, demo, authority, data)
- **Product Reveal** — When and how do they introduce the product?
- **CTA** — What's the call to action? Direction + urgency + value?

Note the **pacing** — how long is each section? Where are the cuts?

### 4. SALES PSYCHOLOGY ANALYSIS
For each section, explain the underlying mechanism in copywriting terms:

- **Attention device** — Pattern interrupt? Identity call-out? Curiosity gap?
- **Emotional state management** — What emotion are they building? Hope? Fear? Frustration? Relief?
- **Belief building** — How do they overcome skepticism? New mechanism? Social proof stacking? Authority transfer?
- **Open/closed loops** — Where do they create unanswered questions? When do they resolve them?
- **Objection handling** — Which objections do they preempt? How?
- **Persuasion triggers** — Scarcity? Social proof? Authority? Reciprocity? Contrast? Loss aversion?
- **Identity play** — Do they make the viewer see themselves in the ad? How?

### 5. REPLICATION NOTES
- What's the transferable principle? (not brand-specific)
- Which of our brands could use this structure?
- What would need to change to adapt it?

---

## File Naming

```
[NUMBER]-[BRAND]-[DESCRIPTOR].md

Examples:
001-huel-morning-routine-tiktok.md
002-ag1-doctor-endorsement-meta.md
003-generic-glp1-fear-hook-tiktok.md
```

---

## What Makes a Good Swipe

✅ High-spend ads (running for weeks/months = proven winner)
✅ Ads with a structure we haven't used before
✅ Ads that made YOU stop scrolling
✅ Ads from adjacent industries we can cross-pollinate

❌ Ads that are just "well-produced" but generic
❌ Brand awareness ads (we do direct response)
❌ Ads we can't learn anything replicable from

