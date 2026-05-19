# Testing Documentation — Moneesh's Portfolio

This document records testing performed throughout the development of the portfolio site. Entries are added at each development stage rather than retrospectively.

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
- Initial nav link `href` values were missing the `#` prefix, which would have caused broken navigation — corrected before commit.
- The `<textarea>` initially had an invalid `type` attribute — removed since `type` only applies to `<input>`.
- Some `rel` attributes had a `noreferer` typo (one r) instead of `noreferrer` — fixed via find-and-replace.
- Project cards initially all had identical tech tags — varied per project to better reflect skill breadth.
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

- Hero column order on mobile — photo was appearing above the name in DOM order, breaking the recruiter's reading hierarchy. HTML reordered so text comes first; order-md-1/order-md-2 restore the desktop layout.
- Hero photo too dominant on XL desktop — headshot was filling its column. Added hero-photo class with max-width: 350px. Initial version used an unnecessary media query wrapper; refactored to a single base rule after testing confirmed the wrapper was redundant.
- Hero vertical balance — resolved as a side-effect of the photo size constraint. With a smaller photo, align-items-center correctly aligned the text column without floaty empty space.
-About section column alignment — bio and Quick Facts felt stranded. Added quick-facts class with left border, padding, and align-items-start on the row. Bio constrained to max-width: 540px with line-height: 1.9. Default bullets replaced with custom coral ::before bullets.
- About section responsive stacking — orphan border at top of Quick Facts when stacked. Added media query to remove border and add top margin below tablet. Initial max-width: 768px collided with Bootstrap's col-md-6 activating at exactly 768px; refined to 767.98px to match Bootstrap's own convention.
- Skills row spacing — reviewed at all four breakpoints. Gap creates appropriate visual rhythm and reads as a unified 2x3 grid. No change made.
- Projects row width on XL — four cards stretching across full container felt sprawling. Capped row at max-width: 1200px with margin: 0 auto. Also changed columns from col-lg-3 to col-xl-3 so four-across only activates at 1200px+, keeping 2-across at standard desktop. Tested col-xl-4 (orphan card) and col-xl-6 (oversized images) before settling on col-12 col-md-6 col-xl-3.

**Notes:**

- Stage 6 reinforced that media queries should change behaviour at a breakpoint, not just scope a rule. Two attempts during this stage produced redundant or unnecessarily restrictive media queries; both were simplified after testing.
- The 768px boundary collision demonstrated why Bootstrap uses 767.98px for its own upper bounds — pattern adopted consistently where similar collisions could occur.


## Validator Tests

To be completed in later stages:
- [ ] HTML — official W3C validator 
- [ ] CSS — official Jigsaw validator 

## Browser Tests

To be completed once site is live:
- [ ] Chrome - desktop / tablet / mobile
- [ ] Firefox - desktop
- [ ] Safari - desktop / mobile
- [ ] Edge - desktop

## Lighthouse Audit

To be completed once site is deployed:
- [ ] Performance
- [ ] Accessibility
- [ ] Best Practices
- [ ] SEO

## Known Bugs

None at this stage.