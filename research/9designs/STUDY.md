# 9designs.co design study

Reference site: https://www.9designs.co/ (London brand, web and growth studio).
Captured 2026-10-28 with Playwright and headless Chromium at 1440x900 (desktop) and 390x844 (phone). Cookie consent was denied before each capture.
Purpose: an internal reference for redesigning an independent executive advisory site. Screenshots and video are for internal reference only. None of the reference site's images, fonts, code or copy go into our site files.

Notation: "observed" is the default for everything below. Anything marked **(inferred)** is a reading of what was observed, not something measured.

## Summary

1. A Webflow site with all-black pages, near-white type, one hidden orange accent, and a very wide, heavy uppercase display face (Mammoth) mixed with its outline cut on alternate words.
2. The homepage is long: about 14,800 px on desktop and 21,600 px on phone, 21 H2 headings and about 4,250 words. It runs from situations, testimonials, case studies, outcomes and services through story, team and a closing call to action.
3. Motion is mostly small and custom-coded: fade-ups on entry, a section fade-out as you scroll past, an auto-drifting draggable testimonial strip, a scrolling quote ticker, a rotating quote, GSAP-drawn icon animations and a hover "glitch" on headings and nav links. There is no smooth-scroll library, pinning or preloader on the homepage.
4. Conversion runs through a single repeated button, "Let's talk about what comes next", that opens a Google Calendar booking page. No page visited has a form, and the contact page holds no form either.
5. Weight is the main technical weakness: about 20 MB transferred on the homepage after scrolling (19.5 MB of it images, several PNGs of 1.3 to 3.4 MB) and about 28 MB on the case study. A blocking Cookiebot dialog hides the whole page until the visitor answers it.

## Page map

| Page | URL | Purpose | Screens |
|---|---|---|---|
| Home | https://www.9designs.co/ | Positioning, proof, services, team, booking CTA | `screens/home-desktop.jpg`, `screens/home-phone.jpg`, `screens/home-hero-desktop.jpg`, `screens/home-hero-phone.jpg`, `screens/home-firstview-desktop.jpg`, `screens/home-firstview-phone.jpg`, `screens/home-scope-overlay-desktop.jpg`, `screens/home-scope-overlay-phone.jpg` |
| Work | https://www.9designs.co/work | Numbered list of 8 case studies, then a grid of other projects and a logo wall | `screens/work-desktop.jpg`, `screens/work-phone.jpg` |
| Case study | https://www.9designs.co/project/elite-home-staging | Long-form case study (about 3,700 words) with large images | `screens/case-study-desktop.jpg`, `screens/case-study-phone.jpg` |
| Contact | https://www.9designs.co/contact | What the first call covers, plus booking buttons | `screens/contact-desktop.jpg`, `screens/contact-phone.jpg` |
| AI guide | https://www.9designs.co/ai-guide | Long text page written for AI assistants and search (linked from the footer) | `screens/ai-guide-desktop.jpg`, `screens/ai-guide-phone.jpg` |

The main navigation has four links: `work`, `growth`, `about` and `contact`. Three of them are anchors on the homepage (`/#work`, `/#insights`, `/#about`). Only `contact` goes to its own page. The `/work` page is reached from "view more work" under the homepage case studies. The AI guide is a footer link.

Video: `video/home-scroll-desktop.webm` (30 s, 1024x640). It covers the consent dialog, the nav hover glitch, a card hover, a slow scroll to the footer and the "Explore the scope" overlay. The site has no menu to open (see Navigation), so the overlay is the closest thing to one.

## Homepage, section by section

Positions are from the top of the 1440 px desktop render. See `screens/home-desktop.jpg`.

| # | Section | What it shows | Layout | Interaction |
|---|---|---|---|---|
| 0 | Consent wall | Cookiebot dialog over a fully black page. Nothing of the site shows until the visitor picks Deny, Allow selection or Allow all (`screens/home-firstview-desktop.jpg`) | Centred modal, blue buttons (Cookiebot's own styling, not the site's) | Blocks the page |
| 1 | Header | Centred "9 DESIGNS" logo mark; four lowercase text links stacked vertically at top right; 1 px light rule below | 121 px tall, sticky, black | Hover glitch on links |
| 2 | Hero | "BRAND GROWTH FOR UNFINISHED BUSINESS" in four centred lines at 129 px, with "UNFINISHED" in the outline cut. A two-line strapline below mixes grey and white words ("Strategy-led brand growth studio for mid-market firms…") | Full width, centred, about 1 viewport tall. No image or video | A black gradient veil fixed under the header fades text as it scrolls up |
| 3 | "Big moves ask more of your brand" | Headline left, three short paragraphs right. Below it, a 3x2 grid of six situation cards (photo plus uppercase line, e.g. "You're navigating a merger or acquisition.") | 2-column intro, then a 3-column card grid with 28 px gaps; cards 430x344 (1.25:1) | Card hover: border brightens (50% to 85% opacity) and the photo scales to 1.04 |
| 4 | Testimonials | Strip of cards: name, role, 5 stars, quote, Trustpilot or LinkedIn link | Horizontal track wider than the screen, thin progress bar below | Drifts slowly on its own, pauses on interaction, can be dragged with the mouse (grab cursor). The cards repeat to make an endless loop |
| 5 | "The difference a stronger brand makes" | Two featured cases (Elite Home Staging, Jewel Toned Interiors): image on one side, then "What needed to change", "The brand's role", a boxed client quote and a text link on the other | 2 columns, alternating sides, 72 px gap | Image parallax (GSAP ScrollTrigger scrub, -6% to +2%); fade-up on entry |
| 6 | "The commercial outcomes we work towards" | Four numbered cards: "Make the new direction clear", "Strengthen the reputation…", "Win more of the right business", "Increase the firm's commercial value" | 4 columns, outlined boxes | Each card has a small GSAP animation of squares and bars (squares settle into a line, rising bars, etc.) |
| 7 | Quote ticker | Three rows of short client phrases in quotes, separated by dots | Full-bleed rows | Continuous horizontal scroll (CSS keyframe). The item nearest the centre scales up to 1.28x and brightens (JS loop) |
| 8 | "The work we deliver" | Process text and two photos on the left. On the right, a vertical timeline of three services: 01 Strategy, 02 Execution, 03 Support, each with an "Explore the scope" button | 2 columns; timeline with a large outline number column | A progress line fills as you scroll; items fade in. The button opens a full-screen scope overlay (below) |
| 9 | "Featured case studies" | Eight case cards: image, client name, one-line summary, sector tag. "view more work" link | 2-column grid of outlined cards, images 614x490 (1.25:1) | Fade-up on entry |
| 10 | "Our story" | Wide greyscale team photo with founder story text over it, plus three uppercase statements | Full-width image block, 1352x640 | Paragraphs and statements fade in with stepped delays |
| 11 | Rotating quote | One large uppercase client quote with stars and attribution | Centred | Crossfades to the next quote every 5.2 s |
| 12 | "Your direction and delivery team" | Five portrait cards: four named people with role and LinkedIn link, plus "+ Experts" | 5 columns, 16 px gap, portrait photos | None noted |
| 13 | Closing CTA | "What's your unfinished business?" (hero device repeated), two lines of text, white "Let's talk about what comes next →" button | Centred | Button fades up; on hover it turns transparent with a white outline and the arrow moves 5 px |
| 14 | "9 is not ten" | Brand slogan as a headline, short paragraph, Trustpilot badge, second booking button, large logo | Centred | None noted |
| 15 | Footer | "Site by 9 Designs, obviously." · Legal / AI guide · "2017–2026 © 9 Designs®" | One row, three items, rule above | None |

Also on every page: a fixed accessibility widget button (bottom right, Sienna) and a Cookiebot re-open icon (bottom left).

**Scope overlay** (`screens/home-scope-overlay-desktop.jpg`): a full-screen dialog over a blurred backdrop. It has the service name, about 60 uppercase deliverables in four to five columns, and Close buttons at top and bottom. It traps focus and closes on Escape. On phone it fills the whole screen and the groups become accordions (`screens/home-scope-overlay-phone.jpg`).

## Typography

Two families, both self-hosted on the Webflow CDN. Loaded faces: Switzer 400/600/700, Mammoth 400, Mammoth Outline 400.

| Role | Family | Desktop size / line-height | Phone size | Weight | Tracking | Case |
|---|---|---|---|---|---|---|
| H1 (hero) | Mammoth | 129 / 116 px (0.9) | 40 px | 400 | -0.03em (-3.87 px) | Upper |
| H2 (section) | Mammoth | 86 / 77 px (0.9) | 36 px | 400 | -0.03em | Upper |
| H3 (cards) | Mammoth, Arial Black fallback | 26 / 27 px | 20 px | 700 (synthetic, inferred: only weight 400 is loaded) | +0.01em | Upper |
| Big quote | Mammoth | clamp(22px, 3.2vw, 46px), lh 1.08 | 22 px | 700 | +0.01em | Upper |
| Body | Switzer | 16 / 20.8 px (1.3) | 16 px | 600–700 | ~-0.01em | Sentence |
| Small labels, links | Switzer | 11–13 px | same | 500–700 | +0.1 to +0.14em | Upper |
| Nav links | Switzer | 15 / 20 px | 15 px | 400 | normal | Lower |
| Buttons | Switzer | 13 px (12 px on small screens) | 12 px | 650 | +0.12em | Upper |

Patterns:
- Every heading uses the solid-plus-outline device: one or two words in Mammoth Outline ("UNFINISHED", "MORE", "BRAND", "DELIVER", "CASE STUDIES", "STORY", "TEAM").
- All display type is uppercase. Line-height runs under 1, so lines nearly touch.
- Body text is unusually heavy. The most common body style is Switzer 16 px weight 700 in grey (#878787), so long paragraphs read as bold grey on black.
- Mid-sentence emphasis switches individual words between grey and white (hero strapline, "Our story").

## Colour

The site is in effect monochrome. Values come from `:root` CSS variables and computed styles.

| Token (site's name) | Hex | Use |
|---|---|---|
| `--ink` | #000000 | Page background on every page |
| `--paper` | #f2f2f2 | Headings, card borders, button fill |
| (none) | #ffffff | Nav links, some text, button text on hover |
| `--body` | #b2b2b2 | Lighter body text, scope list items |
| `--mute` | #878787 | Most body copy (the most frequent text colour on the homepage) |
| `--hair` | #2e2e2e | Divider lines |
| (borders) | #ffffff at 10–12%, #f2f2f2 at 50% | Card outlines, rules |
| deleted variable "accent" | #f03c0a | Only in the hover glitch shadow on headings and nav links |

There are no coloured backgrounds, gradients (apart from the black header veil) or tinted panels. Colour comes only from the photographs and client work.

## Layout and grid

- Full-width pages with no max-width container. The content edge sits 44 px from the viewport on desktop (the header uses 21.6 px) and 20 px on phone. At 1440 px the content width is 1352 px.
- Grids observed: 3 columns with 28 px gaps (situation cards); 2 columns with 72 px gaps (featured cases, alternating); 4 columns with 20 px gaps (outcome cards); 5 columns with 16 px gaps (team); 130 px + fluid with 36 px gaps (timeline rows); a 2/3 + 1/3 Webflow layout grid.
- Text blocks are capped at 520–640 px wide.
- Section spacing: 144 px top padding on desktop and 160 px on phone (more on phone than on desktop), with bottom padding 0. The space comes from the next section's top padding.
- Boxes are square-cornered everywhere (border-radius 0), with 1 px light outlines on black. No shadows.

## Imagery

- Situation cards: stock and stock-style photos (three are loaded from images.unsplash.com) at 1.25:1, `object-fit: cover`.
- Case cards: client work mockups (phones in hands, a branded truck, print, website screens) at 1.25:1, inside outlined cards.
- Story: one wide team photo, greyscale via CSS `filter: grayscale(1)`, about 2.1:1, with text over it.
- Team: colour portraits of mixed styles on plain backgrounds (inferred: not one consistent shoot).
- Case study page: very large full-width images (wrapped vehicle, workshops, wireframes, full-page website captures).
- Images are not full-bleed. They sit inside the 44 px page margins. All `<img>` use `loading="lazy"`.
- Hover: photo scale 1.04 plus a brighter border on situation cards. No colour or filter change on hover.
- On `/work`, several "Strategy, brand & digital work" thumbnails showed a WordPress logo with "Generating Preview" text (`screens/work-desktop.jpg`, lower half). These look like unfinished link-preview images.

## Motion and interaction

GSAP 3.12.5 and ScrollTrigger come from cdnjs. Webflow Interactions (IX2) are also active, with 24 `data-w-id` elements on the homepage. Most effects are hand-written inline scripts using IntersectionObserver and requestAnimationFrame. Nearly all of them are switched off under `prefers-reduced-motion: reduce`.

| Effect | Where | Trigger | Implementation |
|---|---|---|---|
| Consent wall | First load, all pages | Page load | Cookiebot, blocking |
| Header veil | Below the header | Always (fixed) | Fixed 252 px black-to-clear gradient. Content fades out as it passes under the header |
| Section fade-out | Every `<section>` | Scroll: opacity drops as the section's bottom passes 70% of the viewport | Custom JS |
| Fade-up reveals | Featured cases, CTA, story, timeline | Entering the viewport | IntersectionObserver plus CSS transitions, staggered delays |
| Image parallax | Featured case images | Scroll (scrub) | GSAP ScrollTrigger (2 triggers on the homepage) |
| Hover glitch | All H1–H6 and nav links | Hover or keyboard focus | CSS pseudo-elements with orange (#f03c0a) and grey offset shadows and clipped keyframes. A script adds the `glitch-9d` class to every heading |
| Testimonial strip | Homepage testimonials | Auto-drift; drag | Custom JS, duplicated cards for a loop, progress bar |
| Quote ticker | Homepage, under the outcomes | Continuous | CSS `translateX(-50%)` loop plus JS centre-scaling |
| Rotating quote | Homepage | Timer, 5.2 s | Custom JS crossfade |
| Outcome icons | Four outcome cards | Inferred: entering the viewport or hover (timelines are created paused) | GSAP timelines of small squares and bars |
| Timeline progress | "The work we deliver" | Scroll | Custom JS `scaleY` on a line |
| Scope overlay | "Explore the scope" buttons | Click | Custom modal with focus trap and Escape to close |
| Button hover | Primary buttons | Hover | Fill becomes outline, arrow moves 5 px |
| Page loader | Contact page | Page load | Webflow `page-load` element with four `load-bar` bars (on phone these overflow the page width, 461 px against 390 px) |

Not present: Lenis, Locomotive, Barba (page transitions), Swiper, Splide, SplitText or SplitType, a custom cursor, pinned or sticky scroll sections, or a homepage preloader. The only cursor change is grab/grabbing on the testimonial strip.

## Navigation

- Header is `position: sticky; top: 0`, solid black with a 1 px light bottom rule. It does **not** hide on scroll; its position and transform were unchanged after scrolling down and back up.
- No burger and no full-screen menu at any width. The four links stay as a stacked text list at top right on desktop and phone.
- Header height is 121 px on desktop and 136 px on phone, so on a 844 px phone screen it takes about 16% of the height, permanently.
- Three of the four nav links jump to homepage anchors, so from an inner page "growth" and "about" send you back to the homepage.
- The case study has no previous/next links. It ends with a "More projects" grid of all eight cases, including the one you are reading, then the footer.

## Conversion

- One action: book a call through a Google Calendar appointment page (an external Google URL). The button text is "Let's talk about what comes next →" on the homepage (2), the contact page (3) and the work page (in the closing "9 is not ten" block). The case study page has no booking button: it ends with the "More projects" grid and the footer, so the only route to contact from there is the `contact` nav link.
- `/contact` explains what the first conversation covers (four numbered points) and repeats the booking button. It has no form and no email, phone or WhatsApp links. A phone number and email appear only in the schema.org data. A click tracker for `tel:`, `mailto:` and WhatsApp links exists, but no such links were seen on the visited pages.
- Secondary proof sits next to the CTAs: Trustpilot badge, star ratings, client-named quotes linking to individual Trustpilot reviews.
- No pop-ups, exit-intent prompts, newsletter sign-up or lead magnet were observed.

## Mobile behaviour differences

- Everything collapses to one column. The situation grid is a single 350 px column, featured cases and outcome cards stack, and the team cards stack. The homepage grows from about 14,800 px to 21,600 px.
- Display type scales down sharply (H1 129 to 40 px, H2 86 to 36 px). The outline words stay, and their thin strokes get faint at that size (`screens/home-hero-phone.jpg`).
- Section top padding increases on phone (160 px against 144 px), which adds to the length.
- The sticky header stays 136 px tall with the logo and four stacked links (no burger).
- The scope overlay becomes full screen with accordion groups.
- Horizontal overflow: on `/work` one heading measures 397 px, and on `/contact` the loader bars measure 461 px, against a 390 px viewport. The full-page phone captures for those pages came out wider than 390 px.
- The testimonial strip still auto-drifts on phone. The drag code is written for the mouse; touch behaviour was not tested **(inferred: touch probably falls back to native horizontal scroll)**.

## Tech stack

| Layer | Observed |
|---|---|
| Builder | Webflow (`<meta name="generator" content="Webflow">`, `data-wf-site`, `w-` classes, `cdn.prod.website-files.com`, webflow.js chunks) |
| JS | jQuery 3.5.1 (Webflow default), GSAP 3.12.5 + ScrollTrigger (cdnjs), several custom inline scripts (about 35 KB) |
| CSS | Webflow stylesheet plus about 50 KB of inline custom CSS |
| Fonts | Switzer, Mammoth, Mammoth Outline (self-hosted on the Webflow CDN, about 150 KB) |
| Consent | Cookiebot (blocking dialog) |
| Analytics | Google Analytics 4 (gtag), Microsoft Clarity (session recording; it also called c.bing.com) |
| Accessibility | Sienna accessibility widget (jsDelivr) |
| Booking | Google Calendar appointment schedules |
| Structured data | schema.org Organization with slogan, email, phone, LinkedIn profiles |

Performance (single run each, headless Chromium, no throttling, so treat as rough):

| Page | Requests (after full scroll) | Transferred before scroll | Transferred after scroll | LCP (ms) | LCP element |
|---|---|---|---|---|---|
| Home desktop | 71 | 10.5 MB | 20.3 MB | 1,320 | hero strapline text |
| Work desktop | 116 | 9.5 MB | 13.9 MB | 1,180 | heading |
| Case study desktop | 61 | 1.4 MB | 27.7 MB | 1,124 | first image (751 KB PNG) |
| Contact desktop | 42 | 1.1 MB | 1.1 MB | 1,276 | photo |
| AI guide desktop | 41 | 0.7 MB | 0.9 MB | 972 | heading |

Images are about 96% of the homepage weight. Many are full-size PNGs: 3.4 MB, 2.3 MB, 2.3 MB, 2.1 MB, 1.9 MB and 1.3 MB on the homepage, and nine images between 0.7 and 3.3 MB on the case study. The real first view is the consent dialog, so LCP as measured reflects text behind the dialog (inferred: a real visitor sees the hero only after answering the dialog).

## How a sceptical executive audience would react

This section is judgement **(inferred)**. It ties back to what was observed above.

| Observed | Likely reaction from senior executives | Takeaway for an advisory site |
|---|---|---|
| Wide, heavy uppercase headlines at 86–129 px on every section, with outline words | Reads as an agency showing its craft. Loud, and the outline words are hard to read on phone | Use one large, calm statement at most. Keep sentence case and normal tracking for reading text |
| 21 H2s and about 4,250 words on one page | Too long to scan before a first call. The point gets lost | Keep the homepage to a few sections with one claim each. Put depth on inner pages |
| Black background with bold grey body text | Fine for a portfolio, tiring for reading long copy. Contrast of #878787 on black is about 5.8:1 (calculated), which passes AA but is not comfortable for long text | Dark tones can carry authority, but body copy needs more contrast and normal weight |
| Hover glitch, tickers, auto-drifting strips, rotating quotes | Motion for its own sake. Moving testimonials and tickers look like volume, not judgement | Keep motion to quiet fades. No auto-moving content |
| Blocking cookie dialog before any content | First impression is friction | Use a non-blocking consent bar, or avoid cookies that need consent |
| One CTA, booking straight into a calendar | Clear and low effort. Some executives prefer a short note or an email address first | Offer booking and a plain email address side by side |
| Named client quotes with Trustpilot links, named team with LinkedIn | Credible: real names and checkable sources | Use named, checkable proof, but fewer items |
| Stock photos for the situation cards | Generic. Weakens the claim of specific expertise | Use no imagery or only real, specific imagery |
| Situation framing ("You're navigating a merger…") | Relevant: it meets the reader at their problem | Worth adapting: lead with the situations the firm is called into |
| 20–28 MB pages, multi-MB PNGs | Slow on hotel Wi-Fi or mobile data. Signals carelessness to a technical buyer | Keep pages light (well under 1 MB), use compressed images, few scripts |
| Sticky 136 px header and no burger on phone | Takes screen space on every scroll | Short header on phone. Consider letting it hide on scroll |
| "Site by 9 Designs, obviously." and the "9 is not ten" slogan | Playful agency voice | Advisory voice should be plain and direct |
