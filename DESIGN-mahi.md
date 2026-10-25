# Design Procedures: Abdullah Al Mahi Portfolio

Live site: https://abdullahalmahi526.github.io
Repository: https://github.com/AbdullahAlMahi526/AbdullahAlMahi526.github.io (Mahi's own GitHub account)
Files: `index.html` (all HTML, CSS and JavaScript inline; fonts from Google Fonts), `portrait.webp`, `og.jpg` (1200×630 link preview), `README.md`

---

## 1. Brief

| Item | Decision |
| --- | --- |
| Owner | Abdullah Al Mahi, final-year B.Sc. EECE, MIST, Dhaka (graduating 2027), CGPA 3.92 |
| Requested by | Mehedi (friend), built from Mahi's `PORTFOLIO_DATA.md` |
| Owner's direction | Fixed palette (revised 19 Oct to five colours: `#3282B8`, `#2A2D64`, `#4A4E51`, `#333739`, `#1E2022`) with blue as the primary; style of a dark template reference (cut-out portrait in a coloured ring, kicker labels, solid + outline buttons, card grid with one filled highlight card) |
| Main audience | Graduate schools and supervisors, VLSI / semiconductor employers, research collaborators |
| Primary job | Show the ISVLSI compute-in-memory paper and the FormSense lead-author paper, then projects, industry attachments and leadership; make contact easy |

## 2. Concept

**"Silicon in blue."** A dark charcoal page with faint circuit traces and travelling pulses behind the hero. The reference template's portrait-in-ring hero is kept and given a die-grid disc and orbit. The memorable piece is a **playable SRAM compute-in-memory lab** based on his ISVLSI paper. Toolkit groups are drawn as IC packages with pins. Different from Mehedi's dusk-lab and Munawar's light-green engineering pad.

## 3. Design tokens

### Colour

Owner's five colours plus tints and shades derived from them (the list has no light colour, so text and highlights are light tints of the blue and grey).

| Token | Value | Source | Use |
| --- | --- | --- | --- |
| `--bg` | `#1E2022` | owner | Page background |
| `--s1` | `#333739` | owner | Cards, controls, stored-0 cells |
| `--s2` | `#4A4E51` | owner | Borders, wires, stored-0 outline, inactive dots |
| `--blue` | `#3282B8` | owner | **Primary**: ring disc, histogram bars, XNOR match, strokes, "Main drive" phase, hero introduction rule |
| `--indigo` | `#2A2D64` | owner | Gradient panels (degree card, contact band, figure backgrounds) |
| `--primary` | `#2C76A8` | shade of blue | Filled buttons, active tabs/filters, highlight card (white text passes 4.5:1) |
| `--sky` | `#7DB6DE` | tint of blue | Heading accents, kicker labels, stored-1 cells, curves, "Mahi" |
| `--ice` | `#BFDDF2` | tint of blue | Numbers, "Undergraduate Student", email, timing errors, Monte Carlo tail |
| `--deep` | `#1F2140` | shade of indigo | CIM lab background, mobile menu |
| grey | `#8F959A` | tint of `#4A4E51` | Secondary series: CMOS curve, "Initiation" phase, −1 outputs |
| Text | `#F2F5F8` / `#B3B9BF` | tints | Light ink and muted text |

### Typography

| Role | Typeface |
| --- | --- |
| Display | Archivo, width 96–118 %, weight 700–900 (name, section titles, numbers) |
| Text | Hanken Grotesk (400–700) |
| Readout | JetBrains Mono (kicker labels, chips, figure labels) |

## 4. Page structure

| Order | Section | Treatment |
| --- | --- | --- |
| 1 | Hero | Kicker pill ("Dhaka, Bangladesh · Class of 2027"), name ("Al" outlined, "Mahi" in sky blue), three-line introduction with a blue rule on the left ("Undergraduate Student" in ice blue; "Military Institute of Science and Technology"; "Department of Electrical, Electronic and Communication Engineering" in muted text), one-line intro, buttons, current roles; cut-out portrait breaking out of a blue die-grid disc with a rotating dashed orbit. **No text on or around the portrait** (stat badges removed at the owner's friend's request; the same figures are in the About counters). Portrait tilts with the cursor. Circuit traces fade behind the text column. |
| 2 | About | Statement with blue marker, three paragraphs, five counters (3.92, 4 papers, 2,000+, 5 projects, 3 roles), four focus cards; the hovered card fills blue like the reference's highlight card |
| 3 | CIM lab | Interactive SRAM compute-in-memory toy (section 5) |
| 4 | Research | Two IEEE papers, then two manuscripts; each a card with a code-drawn figure, venue/status chips, author list (Mahi underlined), key numbers, expandable details |
| 5 | Projects | Filter (All, VLSI & Memory, Embedded & Robotics, IoT & Wearables); VTOL wide card, SRAM butterfly curve, FormSense trace, 2-layer PCB, PIR lighting room; figures sit below the category chip and animate while on screen |
| 6 | Experience | Tabs: Industrial attachments (Neural Semiconductor, Walton) / Leadership (3 current roles with a pulsing "Now" dot, 2 earlier roles) |
| 7 | Education | Degree card with outlined "3.92", HSC and SSC 5.00, three honour cards |
| 8 | Toolkit | Seven "IC packages" (U1–U7) with tools as pins |
| 9 | Contact | Indigo gradient band, big ice-blue email (one line on desktop, breaks at "@" on phones), Copy email, five profile links, mailto form |

Navigation: fixed header that turns solid on scroll, section dot rail on the right (wide screens), full-screen menu on phones.

## 5. The CIM lab

- **8 × 8 SRAM array** (SVG). Each cell stores a binary weight; the top row holds ±1 inputs. Click any cell or input to flip it (keyboard: Enter/Space).
- **Compute XNOR**: a pulse runs down the bitlines, each row lights its matches (blue), popcount bars fill and the output sign (±1) appears. Auto-run every 2.2 s while on screen.
- **Monte Carlo histogram**: 1,200 delay samples (stratified normal quantiles, so counts are exact). Samples past the clock edge are ice blue; tail ÷ 1,200 = XNOR error probability. Each XNOR flips with that probability; an error cell turns dark with an ice-blue ×.
- **Process variation slider**: σ of delay, 4–20 % (default 12 %).
- **Unmitigated / Mitigated**: clock edge set so that at σ = 12 % the tail is 114/1,200 (p = 0.095) or 3/1,200 (p = 0.0025), the paper's two values.
- **Accuracy curve**: `acc = 10 + 79.7·exp(−k·p^a)`, fitted through the paper's two points (0.0025 → 89.34 %, 0.095 → 58.27 %). Readouts: error probability, accuracy, errors in last run, energy (3.17 pJ × 64 ops per run). A row of the last 20 "test digits" turns ice blue when misclassified, sampled at the current accuracy.
- A note under the lab says it is an illustrative model built on the paper's reported figures.

## 6. Content sources and rules

- All facts come from `PORTFOLIO_DATA.md` and the owner's friend's instructions. Plain first-person sentences, numbers with units.
- Department name uses MIST's official wording, "Electrical, Electronic and Communication Engineering".
- Public contact: email and profile links only. Phone number and home address are deliberately left out (owner's friend chose this).
- Paper status: both IEEE papers listed by venue as peer-reviewed conference papers; no DOI or "published" claim, because neither was indexed online on 19 Oct 2026. PCF-SPR: "Under journal review". VTOL paper: "In preparation".
- Co-author names (Munawar, Mehedi) are not linked to their sites (decided).
- Profile links are text buttons, not brand logos.

## 7. Photo, preview and CV slots

- `portrait.webp`: background removed with rembg (isnet model) from the supplied photo, 720 × 720.
- `og.jpg`: 1200 × 630 link-preview card (name, the same three-line introduction, portrait on the blue disc), referenced by absolute URL in `og:image` with `twitter:card`; canonical URL set.
- Upload `VTOL.jpg` (or `VTOL.jpeg`) next to `index.html` and it replaces the drawn VTOL on the project card.
- Upload `cv.pdf` next to `index.html` and "Download CV" buttons appear in the hero and contact sections.

## 8. Quality rules and testing

- Responsive from 360 px phones to wide desktops; tested at 1536×730, 1440×900, 1100×800, 820×1180, 390×844 and 360×780 with no sideways scrolling.
- `prefers-reduced-motion` stops all animation and auto-run; the lab still computes on click.
- Figure animations and the lab run only while on screen; canvases capped at 2× pixel ratio and redrawn when fonts load.
- Visible focus outlines, labelled controls, ARIA tabs with arrow-key support, Escape closes the menu.
- Test procedure: `node --check` on the script; headless Chromium screenshots at the sizes above (fonts served locally via Fontsource); interaction script (flip cell and input, mitigated/unmitigated, σ 4/12/20, auto-run toggle, filter, tabs, reduced-motion phone run); live check after publishing.

## 9. Publishing and updating

GitHub Pages from the `main` branch, root folder, in Mahi's account `AbdullahAlMahi526`. To update: open the repository, **Add file → Upload files**, drop the new `index.html` (or `VTOL.jpg`, `cv.pdf`), commit, wait 1–10 minutes, hard-refresh.

## 10. Change log

| Date | Change |
| --- | --- |
| 19 Oct 2026 | Built and published: violet palette, portrait-in-ring hero with orbit badges, CIM lab, papers, projects, experience tabs, IC-package toolkit, contact |
| 19 Oct 2026 | Palette changed to five colours with blue primary; hero badges moved off the face (desktop repositioned, phones/tablets grid below portrait); shorter badge labels; lab error cells made clearly visible; project figures moved below their category chip; traces faded behind hero text; email fits one line on desktop; added `og.jpg` link preview and canonical URL |
| 19 Oct 2026 | Hero role line ("VLSI and hardware-aware AI researcher") replaced with the three-line introduction (student, MIST, EECE department); kicker pill changed to "Dhaka, Bangladesh · Class of 2027" to avoid repeating MIST; `og.jpg` updated to match |
| 19 Oct 2026 | Removed the four stat badges from the portrait; the portrait now stands alone in its ring at every size |
| 19 Oct 2026 | Removed unpublished VTOL drone paper; updated paper counter from 4 to 3; uploaded and committed VTOL.jpg to repository root |
| 25 Oct 2026 | Bespoke UI/UX redesign & engineering refactor: upgraded typography to Plus Jakarta Sans & JetBrains Mono; implemented exact tri-accent palette (Electric Blue #4895EF, Deep Tech Purple #7209B7, Vibrant Magenta/Pink #F50BBE) over #1E2022; refactored hero with confident asymmetrical layout and dual-accent CTAs; built interactive "See More" slide-out drawer system for all research papers and projects with dedicated fields for DOIs/papers, LinkedIn announcements, and GitHub repositories; preserved full interactive CIM Lab and SVG circuit animations; added subtle glassmorphism and ambient border glow micro-interactions. |

## 11. Open items

- CV (`cv.pdf`)
- DOIs / links for the ISVLSI and iCACCESS papers once they are online
