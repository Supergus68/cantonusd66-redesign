# Canton Union School District #66 — Website Redesign

Modern, parent-focused website redesign for **Canton Union School District #66** (Fulton County, Illinois).

- **Live Demo Site**: [https://cantonusd66.pages.dev](https://cantonusd66.pages.dev)
- **Official Legacy Site Reference**: [www.cantonusd.org](https://www.cantonusd.org)
- **District Office**: 20 West Walnut Street, Canton, IL 61520 · (309) 647-9411

---

## 🎯 Redesign Goals & Key Fixes

1. **Eliminated Menu Clutter & Deep Nesting**:
   - Replaced Weebly's 4-to-5 level deep flyout menus with clear, role-based navigation.
   - Removed dozens of duplicate links across nested subpages.
2. **Prioritized Parent & Student Daily Essentials**:
   - High-visibility quick access cards right beneath the hero for:
     - 🎓 **Skyward Family Access** (Grades, attendance, schedules)
     - 🍎 **Whitsons Food Service Menus** (Daily cafeteria menus via FD MealPlanner)
     - 📅 **District 2026–27 Master Calendar** (Holidays, early outs, institute days)
     - 📝 **Student Registration & Residency Verification**
3. **Interactive Board of Education Policy Search**:
   - Built-in instant client-side search engine covering IASB PRESS policy sections.
   - Quick filters for **Section 7 (Students)**, **Section 6 (Instruction & Tech)**, **Section 4 (Operations & Safety)**, **Section 2 (School Board Governance)**, and **Section 8 (Community)**.
   - Includes full policies, plain-English parent takeaways, and direct links to official IASB documents.
4. **Dedicated School Showcase for All 5 Schools**:
   - **Canton High School (CHS)** — Grades 9–12 · Home of the Little Giants
   - **Ingersoll Middle School (IMS)** — Grades 5–8 · 1:1 Chromebooks
   - **Eastview Elementary School** — Grades K–4
   - **Lincoln Elementary School** — Grades K–4
   - **Westview Elementary School** — Grades K–4
   - Each school has its own dedicated page matching the main portal's clean design with direct staff contacts, daily lunch menus, handbooks, and bell schedules.
5. **Authentic Little Giants Colors & Mobile Responsiveness**:
   - Official Canton Purple (`#6A0DAD`) and Vegas Gold (`#C5B358`).
   - Accessible WCAG AA contrast, fast load times, and responsive layout.

---

## 👩‍🏫 Keeping the Teacher / Staff Directory Up to Date

The searchable "Find a Teacher / Staff" box on the home page and on every school page is powered by a single file:

```
src/data/teachers.js
```

Each person is one row, for example:

```js
{ "name": "Jane Doe", "school": "Lincoln Elementary School", "position": "3rd Grade", "subject": "", "email": "jane.doe@cusd66.org" },
```

- **Add a new teacher or staff member:** copy an existing row, change the name, `school`, `position`, `subject`, and `email`, and save the file.
- **Remove someone who retired or left:** delete their entire row (including the trailing comma) and save the file.
- **Change a role or email:** edit just that value in their row.

Important:
- `school` must exactly match one of the names in `src/data/schools.js`, e.g. `Canton High School`, `Ingersoll Middle School`, `Eastview Elementary School`, `Lincoln Elementary School`, or `Westview Elementary School`.
- Email addresses are encoded automatically when the site builds, so they never appear as plain text in the page source. Supply the real address in the file; it will be protected on the live site.
- If you leave `email` empty (`"email": ""`), the search result shows a "Call school" button instead of an email button.

After saving changes, rebuild and deploy the site (`npm run build`, then publish the `dist` folder). The update appears on the home page and all school pages at once.

---

## 🛠️ Tech Stack

- **Framework**: [Astro](https://astro.build) (zero JS by default, instant client components where needed)
- **Hosting**: Cloudflare Pages
- **Styling**: Vanilla Modern CSS Design System (Custom properties, grid, flexbox)
- **Version Control**: Git / GitHub
