# Testing Documentation — Moneesh's Portfolio

This document records testing performed throughout the development of the portfolio site, in line with criteria 5.1, 5.2, M.vi, and M.vii of the assessment grid. Entries are added at each development stage rather than retrospectively.

---

## Test Log

### Stage 2: Wireframes (design phase)

**Date:** [30/04/2026]

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

**Date:** [05/05/2026]

**What was tested:**
The complete HTML structure (header, hero, about, skills, projects, contact, footer) before any styling or framework integration.

**How it was tested:**
- Manually walked through the file in VS Code, checking each section uses semantic HTML5 tags appropriate to its content
- Verified heading hierarchy: one `<h1>` (page title in hero), `<h2>` for each section, `<h3>` for sub-headings (Quick Facts, project titles)
- Cross-checked every nav link `href` matches a corresponding `id` on a section
- Cross-checked every form `<label for="...">` matches an input `id`
- Confirmed every external link uses `target="_blank" rel="noopener noreferrer"` (criterion 2.5)
- Confirmed every `<img>` has descriptive `alt` text (criterion 1.2)
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


## Validator Tests

To be completed in later stages:
- [ ] HTML — official W3C validator (criterion 2.2)
- [ ] CSS — official Jigsaw validator (criterion 2.3)

## Browser Tests

To be completed once site is live:
- [ ] Chrome — desktop / tablet / mobile
- [ ] Firefox — desktop
- [ ] Safari — desktop / mobile
- [ ] Edge — desktop

## Lighthouse Audit

To be completed once site is deployed:
- [ ] Performance
- [ ] Accessibility
- [ ] Best Practices
- [ ] SEO

## Known Bugs

None at this stage.