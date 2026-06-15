# Testing Documentation - Moneesh's Portfolio

This document records testing performed throughout the development of the portfolio site. Entries are added at each development stage rather than retrospectively.

> **Note on stage coverage:** Testing entries cover stages where testable artefacts existed (code, design output, or deployed product). Stages 1 (content planning) and 3 (repository setup) are not included as they produced decisions and infrastructure rather than testable outputs - Stage 1 is evidenced through the README's user stories and design decisions section, and Stage 3 is evidenced through the commit history. Stages 9 (README) and 10 (deployment) are not separate entries because the README's accuracy is verified by comparing it to the live site, and deployment testing is captured within the Stage 11 Final Verification entry.

---

## Test Log

### Stage 2: Wireframes (design phase)

**Date:** 30/04/2026

**What was tested:**
Wireframes for mobile (375px), tablet (768px), and desktop (1280px) breakpoints, validated against the five user stories defined at project start.

**How it was tested:**
Manual review of each wireframe against each user story, checking that the proposed layout solves the user need at every breakpoint.

**Results:**

| User Story | Solved by | Mobile | Tablet | Desktop |
| --- | --- | --- | --- | --- |
| 1. Recruiter understands who I am and what role I want within 10 seconds | Hero section with name, role, tagline, photo, and CTA above the fold | ✅ | ✅ | ✅ |
| 2. Recruiter sees technical skills at a glance | Skills section with icon + label cards in responsive grid (2 / 3 / 3-column) | ✅ | ✅ | ✅ |
| 3. Recruiter sees examples of work I've actually built | Projects section with image, title, description, tech tags, and live + code links per card | ✅ | ✅ | ✅ |
| 4. Recruiter gets a sense of me as a person | About section with bio paragraph and quick facts (location, interests, current learning) | ✅ | ✅ | ✅ |
| 5. Recruiter can easily contact me / find me on LinkedIn or GitHub | Contact section with hire-me form, direct email link, and three social icons (GitHub, LinkedIn, email) | ✅ | ✅ | ✅ |

**Issues found:** None at wireframe stage.

**Notes:**
- Navigation collapses to a hamburger menu on mobile to preserve screen space, with all five links accessible inline on tablet and desktop.
- Hero stacks vertically on mobile and shifts to a two-column layout on tablet and desktop.
- Skills grid changes density across breakpoints (2 / 3 / 3 columns) to match comfortable scanning.
- Projects grid changes from single-column on mobile to 2x2 on tablet and 4-across on desktop.
- Contact form remains single-column at all breakpoints for readability; widens visually on tablet/desktop only.

---

### Stage 4: HTML Skeleton

**Date:** 05/05/2026

**What was tested:**
The complete HTML structure (header, hero, about, skills, projects, contact, footer) before any styling or framework integration.

**How it was tested:**
- Manually walked through the file in VS Code, checking each section uses semantic HTML5 tags appropriate to its content
- Verified heading hierarchy: one `<h1>` (page title in hero), `<h2>` for each section, `<h3>` for sub-headings (Quick Facts, project titles)
- Cross-checked every nav link `href` matches a corresponding `id` on a section
- Cross-checked every form `<label for="...">` matches an input `id`
- Confirmed every external link uses `target="_blank" rel="noopener noreferrer"` 
- Confirmed every `<img>` has descriptive `alt` text 
- Confirmed appropriate inputs have `required` attribute for defensive design

**Results:**

| Check | Result |
| --- | --- |
| Semantic tags used (header, main, section, article, nav, footer) | ✅ |
| Single `<h1>` on the page | ✅ |
| All nav links point to valid section IDs | ✅ |
| All form labels paired with input IDs | ✅ |
| All external links use `target="_blank" rel="noopener noreferrer"` | ✅ |
| All images have descriptive alt text | ✅ |
| Required inputs marked with `required` (Name, Email, Message) | ✅ |
| Optional inputs (Company, Role) not required | ✅ |
| Section comments present above each `<section>` | ✅ |

**Issues found and fixed during this stage:**
- Initial nav link `href` values were missing the `#` prefix, which would have caused broken navigation - corrected before commit.
- The `<textarea>` initially had an invalid `type` attribute - removed since `type` only applies to `<input>`.
- Some `rel` attributes had a `noreferer` typo (one r) instead of `noreferrer` - fixed via find-and-replace.
- Project cards initially all had identical tech tags - varied per project to better reflect skill breadth.
- Three project titles were left as "Project Title" placeholder — updated to actual project names.

**Notes:**
- Site does not yet have CSS or Bootstrap. Visual layout will be added in Stage 5.
- Profile image and project images reference filenames that don't yet exist (`profile.jpg`, `project1.jpg`, etc.). These will be added before deployment.

---

### Stage 5: Bootstrap Integration + Custom CSS Styling

**Date:** 06/05/2026 – 16/05/2026

**What was tested:** 
The visual application of Bootstrap 5 utility classes across all sections (Stage 5a–5b), followed by the layering of custom CSS for palette, typography, and interactive states.

Testing focused on grid behaviour, palette consistency, hover and focus states, and overall visual cohesion across the page.

**How it was tested:** 
- Live Server in Chrome with DevTools open throughout. 
- Each Bootstrap class was added incrementally and the result inspected visually before moving on. 
- Custom CSS was applied section by section, with manual hover and focus interaction on every interactive element. 
- The browser console was monitored for errors after each significant change. 
- Whole-site screenshots were captured at four breakpoints (375px, 768px, ~1024px, 1440px+) 

**Results:**

| Check | Result |
| --- | --- |
| External dependencies load without console errors (Bootstrap, Font Awesome, Google Fonts) | ✅ |
| Bootstrap grid renders correctly across all sections | ✅ |
| Coastal Warmth palette applied via CSS variables (no hardcoded hex in component styles) | ✅ |
| Poppins applied to headings, Inter applied to body text | ✅ |
| Navbar hover state working (link colour shift) | ✅ |
| Primary button override (coral background with darker coral hover) working on all .btn-primary instances | ✅ |
| Skills section icons scale on hover | ✅ |
| Project cards lift on hover (transform + shadow) | ✅ |
| Contact form inputs show dusty blue focus glow | ✅ |
| Social icons in footer lift on hover | ✅ |
| Whole-site screenshots captured at four breakpoints | ✅ |

**Issues found and fixed during this stage:**

- Bootstrap's default .btn-primary blue clashed with the Coastal Warmth palette - overridden with custom coral via CSS variables.
- Some palette colours were initially written as hex values inside component selectors - rewritten to reference CSS variables for consistency and maintainability.
- Project card hover lift was initially too aggressive - softened by reducing the transform distance and adjusting the transition timing.


**Notes:**

- Stage 5 represents the transition from a Bootstrap-default-looking page to a visually cohesive portfolio that reflects the Coastal Warmth palette and Poppins/Inter typography decisions made at planning stage.
- Responsive behaviour was observed informally during this stage but not formally tested.

---

### Stage 6: Responsive Design Testing

**Date:** 18/05/2026

**What was tested:** Full-site responsive behaviour across four breakpoints (375px mobile, 768px tablet, ~1024px standard desktop, 1440px+ XL desktop). Each section reviewed individually at every breakpoint.

**How it was tested:**

-Chrome DevTools device toolbar at 100% zoom, viewport set manually to each target width
-Manual visual inspection against design intent and Stage 2 wireframes
-Whole-site screenshots captured at each breakpoint before fixes as a baseline
-DevTools Elements panel used to debug specific layout issues
-Each fix re-tested at all four breakpoints to confirm no regression

**Results:**
| Section  | Mobile (375px) | Tablet (768px) | Desktop (1024px) | XL (1440px) |
|----------|:--------------:|:--------------:|:----------------:|:-----------:|
| Hero     | ✅             | ✅             | ✅               | ✅          |
| About    | ✅             | ✅             | ✅               | ✅          |
| Skills   | ✅             | ✅             | ✅               | ✅          |
| Projects | ✅             | ✅             | ✅               | ✅          |
| Contact  | ✅             | ✅             | ✅               | ✅          |
| Footer   | ✅             | ✅             | ✅               | ✅          |

**Issues found and fixed during this stage:**

- Hero column order on mobile - photo was appearing above the name in DOM order, breaking the recruiter's reading hierarchy. HTML reordered so text comes first; order-md-1/order-md-2 restore the desktop layout.
- Hero photo too dominant on XL desktop - headshot was filling its column. Added hero-photo class with max-width: 350px. Initial version used an unnecessary media query wrapper; refactored to a single base rule after testing confirmed the wrapper was redundant.
- Hero vertical balance - resolved as a side-effect of the photo size constraint. With a smaller photo, align-items-center correctly aligned the text column without floaty empty space.
-About section column alignment - bio and Quick Facts felt stranded. Added quick-facts class with left border, padding, and align-items-start on the row. Bio constrained to max-width: 540px with line-height: 1.9. Default bullets replaced with custom coral ::before bullets.
- About section responsive stacking - orphan border at top of Quick Facts when stacked. Added media query to remove border and add top margin below tablet. Initial max-width: 768px collided with Bootstrap's col-md-6 activating at exactly 768px; refined to 767.98px to match Bootstrap's own convention.
- Skills row spacing - reviewed at all four breakpoints. Gap creates appropriate visual rhythm and reads as a unified 2x3 grid. No change made.
- Projects row width on XL - four cards stretching across full container felt sprawling. Capped row at max-width: 1200px with margin: 0 auto. Also changed columns from col-lg-3 to col-xl-3 so four-across only activates at 1200px+, keeping 2-across at standard desktop. Tested col-xl-4 (orphan card) and col-xl-6 (oversized images) before settling on col-12 col-md-6 col-xl-3.

**Notes:**

- Stage 6 reinforced that media queries should change behaviour at a breakpoint, not just scope a rule. Two attempts during this stage produced redundant or unnecessarily restrictive media queries; both were simplified after testing.
- The 768px boundary collision demonstrated why Bootstrap uses 767.98px for its own upper bounds - pattern adopted consistently where similar collisions could occur.

---

### Stage 7: Accessibility Audit
**Date:** 19/05/2026

**What was tested:**

Full accessibility audit covering heading hierarchy, alt text, semantic HTML, colour contrast, keyboard navigation, and form/ARIA attributes. Tested against WCAG 2.1 AA standards.

**How it was tested:**

- Manual review of all heading tags in source order to confirm valid hierarchy
- Manual review of every img element for descriptive alt text
- Source review of semantic HTML5 element usage (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`)
- WebAIM Contrast Checker used to test every text-on-background colour pair against WCAG AA
- Keyboard navigation tested by tabbing through all interactive elements in Chrome, confirming logical focus order and visible focus indicators
- Form labels tested by clicking each label and confirming focus moved to the associated input
- ARIA attributes reviewed on icon-only links and the navbar toggle

| Check | Result |
| --- | --- |
| Single `<h1>` on the page | ✅ |
| Heading hierarchy logical, no skipped levels | ✅ |
| All `<img>` elements have descriptive alt text | ✅ |
| Semantic HTML5 elements used appropriately | ✅ |
| Body text contrast (slate on cream) - WCAG AA Normal | ✅ |
| Button text contrast (white on coral-dark) - WCAG AA Normal | ✅ |
| Email link contrast (slate on cream) - WCAG AA Normal | ✅ |
| Tab order follows DOM order and matches visual hierarchy | ✅ |
| Every focusable element has a visible focus indicator | ✅ |
| All form `<label>` elements correctly associated with inputs | ✅ |
| Navbar toggle has appropriate ARIA attributes | ✅ |
| Icon-only links have `aria-label` for screen readers | ✅ |
| Decorative icons marked `aria-hidden="true"` | ✅ |

**Issues found and fixed during this stage:**

- Project image alt text was generic and started with "Picture of..." which is redundant for screen readers. Rewrote each as descriptive thumbnails referencing the project (e.g. "Thumbnail for Brew & Bite café landing page project"). Also renamed the fourth project from "Recipe Rolodex" to "Click Wild" so the project matched the wildlife photo used as its thumbnail.

- Button text (white on coral #D97757) failed WCAG AA Normal. Changed button background to coral-dark #B55E40, which passes AA when paired with white text. Hover state changed from a colour shift to a subtle lift effect with shadow, keeping the contrast-passing background.

- Email link (dusty blue on cream) failed WCAG AA. Switched to slate #1F2937 with underline. Hover removes the underline as the function.

- Navbar hover (lighter coral) failed WCAG AA. Switched to slate underline on hover, consistent with the email link pattern.

**Notes:**

- Stage 7 reinforced that contrast assumptions need to be tested, not guessed. Initial fixes were applied based on the assumption that "darker = passes" - testing revealed coral-dark on cream actually still fails AA for normal text, requiring further iteration. The slate-with-underline pattern emerged as the most consistently accessible solution across multiple interactive elements.

- The site already had strong baseline accessibility from Stages 4 and 5: semantic HTML, ARIA attributes on icon-only links, proper form labels, and visible focus states on form inputs were all in place before this stage. Stage 7 primarily addressed the contrast failures and refined alt text quality.

- AAA-level contrast was tested informally but not pursued as a target. WCAG AA is the required compliance level for this project and was met throughout.


**Additional improvements during Stage 7**

During the keyboard navigation testing, a UX issue was identified: when users clicked a nav link on the single-page site, they were taken to the relevant section, but had to manually scroll back to the top to use the navigation again. This was addressed by:

- Adding Bootstrap's sticky-top class to the <header> element so the navigation remains visible as the user scrolls (placed on <header> rather than <nav> so the sticky behaviour applies to the full body scroll context, not just within the header).
- Adding a solid cream background to the header to prevent content showing through when scrolling.
- Adding scroll-margin-top to all sections so anchored section headings are not hidden behind the sticky navbar on click.
- Adding a small JavaScript snippet (adapted from previous course material - Broadwalk Games, Code Institute Module 10) that automatically collapses the mobile hamburger menu when a nav link is clicked, so the menu does not remain open and cover the destination section on mobile.


---


### Stage 8: HTML and CSS Validation
**Date:** 21/05/2026
What was tested: The complete index.html and assets/css/style.css files validated against W3C standards to confirm syntactic correctness and compliance with web standards.

**How it was tested:**

- W3C HTML Validator (https://validator.w3.org/) used via file upload to validate index.html
- Jigsaw CSS Validator (https://jigsaw.w3.org/css-validator/) used via file upload to validate assets/css/style.css
- Initial validation run captured as baseline; errors identified, fixed, and revalidated until both files passed cleanly
- Screenshots captured before and after fixes as evidence (saved in testing-evidence/)

**Results:**

| Check | Result |
| --- | --- |
| HTML validation — initial run | 1 error |
| HTML validation - after fix | ✅ 0 errors, 0 warnings |
| CSS validation | ✅ 0 errors, 34 informational warnings |

**Issues found and fixed during this stage:**

Stray `<script>` start tag flagged in HTML validator at line 295. Root cause was the Bootstrap JavaScript bundle being placed outside the `<body>` element, between `</body>` and `</html>`, which is invalid HTML. Fixed by moving the Bootstrap script inside the `<body>`, immediately before the closing tag, and placing it before the custom navbar collapse script so that Bootstrap's JavaScript loads first.

Notes:

The 34 CSS warnings all relate to the same advisory message: "Due to their dynamic nature, CSS variables are currently not statically checked." This is a known limitation of the Jigsaw validator, which does not resolve CSS custom property values during validation. The warnings are tool limitations rather than code issues. The use of CSS variables throughout the stylesheet reflects modern CSS best practice for maintainability and palette consistency, and was a deliberate design decision.
The HTML structural fix uncovered an oversight from earlier in development - the Bootstrap script had been outside `<body>` since adding Bootstrap to the project first. The validation pass caught what visual testing had not, demonstrating the value of running automated validators alongside manual testing.

See below screenshots of the validator outputs:

![HTML Validation before screenshot](testing-evidence/html-validation-before.png)

![HTML Validation after screenshot](testing-evidence/html-validation-after.png)

![CSS Validation screenshot](testing-evidence/css-validation-result.png)


---

### Stage 11: Final Verification

**Date:** 19/05/2026

**What was tested:** 
The deployed site was tested on the live URL across mobile, tablet, and desktop breakpoints in Chrome. Every interactive element was clicked. The aim was to confirm that the deployed version matched the locally-tested behaviour and to identify any defects only visible once the site was live.

**How it was tested:**
Live site loaded at https://monb1986.github.io/moneesh-portfolio/
Tested in Chrome on desktop and via DevTools device toolbar at four breakpoints
Every nav link, hero CTA, project link, form input, and social icon clicked or interacted with
Browser console monitored for errors

**Issues found and fixed during this stage:**

- Hero CTA scroll misalignment on mobile. When the "Get in touch" button in the hero was clicked on mobile width, the page scrolled to the Contact section but left part of the Projects section visible at the top of the viewport. Nav link clicks to the same #contact anchor landed correctly, which isolated the issue to the CTA specifically. The root cause was a layout-state difference: the nav links trigger a JavaScript handler that collapses the mobile menu before scrolling, while the CTA did not, so the page was in a different layout state when the scroll calculation ran. The scroll-margin-top CSS rule that normally compensates for the sticky navbar produced the wrong offset in this case. After unsuccessful attempts to resolve the conflict via CSS adjustments, the issue was fixed by adding a small JavaScript snippet to the hero CTA that overrides the default anchor behaviour and manually scrolls to the Contact section with a fixed 80px offset to account for the navbar height. This snippet was generated with AI assistance (approved by the course director) and is attributed in a code comment above the script as well as in the README's AI assistance declaration.

- The "View Live" / "View Code" button rows sit at different vertical positions in each card at breakpoint 1200px. Card 2 (TripList)'s buttons sit lower than card 1's. This was resolved by adding a d-flex and flex-column class to card-body and mt-auto to the `<div>` nested inside (with classes d-flex gap-2). Flexbox properties were used to push the buttons down to the bottom of the card. It's a genuine inconsistency which was worth fixing - aligned buttons look noticeably more polished, and it's the kind of detail a recruiter's eye catches.

Notes:

The discovery reinforces that deployment testing is a distinct phase from local testing - the defect was reproducible locally in retrospect, but only surfaced naturally during live-site verification. 

**Further Changes**

**Active navigation indicator - investigated, not implemented**

Following the course director's feedback to add a more prominent indication of the current section in the navigation, three approaches were investigated:

1. **CSS `scroll-target-group` / `:target-current`** - an experimental CSS feature found via a tutorial. Worked correctly in Chrome and Edge but failed silently in Firefox, as the feature is not yet Baseline and has limited browser support. Rejected due to the cross-browser testing failure.

2. **Bootstrap ScrollSpy (`data-bs-spy`)** - Bootstrap's built-in component, implemented via data attributes. Worked for most sections, but the Skills section (being visually compact relative to its neighbours) was frequently skipped in favour of the adjacent Projects section highlighting instead. This is a known limitation of ScrollSpy's viewport-intersection algorithm with short sections.

3. **Custom Intersection Observer JS** - the most flexible option, but given the amount of AI-assisted JavaScript already present in the project (navbar collapse and CTA scroll), and the additional time required to implement and thoroughly cross-browser test a new custom script before the submission deadline, this was not pursued.

**Decision:** the active navigation indicator was not implemented for this submission. The sticky navigation, smooth-scrolling anchor links, and clear section headings already orient the user as they scroll. This is documented as a future improvement.


**Skills section expanded with descriptions for each technology**

Following the course director's feedback to add more depth to the Skills section, each skill now includes a short description explaining how the technology has been used in this and previous projects.

Changes made:
- Removed `text-center` from the `<ul>` element, as left-aligned text reads more naturally for paragraph-style content
- Changed column classes from `col-6 col-md-4` to `col-12 col-md-6 col-lg-4`, giving each card enough width for the description text across one column on mobile, two on tablet, and three on desktop
- Wrapped each skill's content in a `<div class="d-flex gap-3 align-items-start">` to position the icon beside the text rather than above it, aligned to the top of each card
- Updated the `#skills i` CSS rule, removing `display: block` and `margin-bottom` (no longer needed in a flex layout) and adding `flex-shrink: 0` so icons retain their size next to longer descriptions.

Tested across mobile (375px), tablet (768px), and desktop (1440px) - layout stacks correctly at each breakpoint, and the existing icon hover effect (colour change and scale on hover) continues to work as expected.

**Contact form validation feedback added**

Following the course director's feedback to provide clear feedback when fields are completed incorrectly, custom validation styling and messages were added to the contact form.

Changes made:
- Added `.invalid-feedback` divs after each required field (Your name, Email, Message), containing field-specific messages.
- Added CSS using the `:user-invalid` and `:user-valid` pseudo-classes, which only apply styling after the user has interacted with a field - avoiding the common issue where `:invalid` styles every required field as an error on page load before the user has done anything.
- Added `novalidate` to the `<form>` element to suppress the browser's native validation tooltip, relying instead on the custom styled messages. The `required` and `type="email"` attributes still drive the CSS validation states via `:user-invalid`/`:user-valid` - `novalidate` only disables the browser's own UI and submission blocking.

Testing: clicking "Get in touch" with empty required fields shows coral borders and custom messages on Your name, Email, and Message (all marked `required` as a group, since the browser treats a submit attempt as interaction with every required field). Filling in a field correctly turns its border blue. Tested across Chrome, Firefox, and Edge.

Two CSS approaches were considered: `:invalid`/`:valid` (rejected, as these trigger immediately on page load for empty required fields) and `:user-invalid`/`:user-valid` (used, as these only activate after user interaction).

---

## Browser Tests

- [✅] Chrome - desktop / tablet / mobile
- [✅] Firefox - desktop
- [✅] Edge - desktop

There were no issues to report whilst testing the deployed site across three browsers. 

---

## Lighthouse Audit

**Lighthouse Audit (Mobile):**

| Audit | Score |
|---|---|
| Performance | 66 |
| Accessibility | 100 |
| Best Practices | 77 |
| SEO | 100 |

![Lighthouse mobile screenshot](testing-evidence/lighthouse-mobile.png)

Mobile Performance score is mainly affected by external files being loaded from CDNs, including Bootstrap, Font Awesome, and Google Fonts, as well as the size of placeholder project images. Despite this, the website itself performs efficiently. This means the page loads smoothly and the code is not causing performance issues. The lower score is mostly due to network requests needed to load external frameworks and assets.

The Best Practices score is affected by GitHub Pages’ default cache settings, which cannot be changed by the developer. Placeholder images are currently being used during development, and replacing them with optimised real project screenshots has been identified in the README as a future improvement.

**Lighthouse Audit (Desktop):**

| Audit | Score |
|---|---|
| Performance | 93 |
| Accessibility | 100 |
| Best Practices | 77 |
| SEO | 100 |

![Lighthouse desktop screenshot](testing-evidence/lighthouse-desktop.png)

The desktop Lighthouse audit achieved strong overall results. The higher desktop Performance score reflects faster and more stable network conditions compared to the simulated mobile test environment.

Some of the remaining warnings are caused by external resources rather than problems with the website code itself. The cache warnings come from GitHub Pages’ default cache settings, which cannot be changed by the developer. Render-blocking warnings are related to external CDN files such as Bootstrap, Font Awesome, and Google Fonts. The image warnings are mainly due to the placeholder project images currently being used during development. Replacing these with optimised real project screenshots has been noted in the README as a future improvement.

Accessibility and SEO both scored 100, showing that the site follows good accessibility and search engine practices on both desktop and mobile. The Best Practices score remained at 77 for the same reasons found in the mobile audit, mainly due to GitHub Pages cache limitations.

---


## Known Bugs

None at this stage.