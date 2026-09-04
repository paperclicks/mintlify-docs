> **First-time setup**: Customize this file for your project. Prompt the user to customize this file for their project.
> For Mintlify product knowledge (components, configuration, writing standards),
> install the Mintlify skill: `npx skills add https://mintlify.com/docs`

# Documentation project instructions

## About this project

- This is a documentation site built on [Mintlify](https://mintlify.com)
- Pages are MDX files with YAML frontmatter
- Configuration lives in `docs.json`
- Run `mint dev` to preview locally
- Run `mint broken-links` to check links

## Terminology

{/* Add product-specific terms and preferred usage */}
{/* Example: Use "workspace" not "project", "member" not "user" */}

## Style preferences

{/* Add any project-specific style rules below */}

- Use active voice and second person ("you")
- Keep sentences concise — one idea per sentence
- Use sentence case for headings
- Bold for UI elements: Click **Settings**
- Code formatting for file names, commands, paths, and code references

## Content boundaries

Verified against the code is **not** the same as safe to publish. These pages are
public, and anything documented here becomes a promise to customers that outlives
the release it described.

**Don't document experimental or in-test features**, even when they are live in
`master` and you can read them in the source. That includes pricing experiments,
flag-gated paths, and A/B arms. In the app repo (`ms-frontend-v2`) the current
examples are:

- The standing plan offer / free-window pricing — `src/utils/billing/planOffer.ts`
  and its rendering in `PlanCard.vue` and `UpgradePitchCard.vue`. No $0 pricing,
  no offer CTA labels, no offer-versus-promo precedence rules.
- Anything behind an Unleash flag or a routing guard that exists to split traffic,
  such as the `card_required_trial` flag in `src/router/billing-guards.ts`.

Describe the billing pages in terms of the stable parts only: base price, covered
ad spend, overage rate, the Monthly/Annual toggle, and the plan badges. Promo codes
and the retention offer inside the cancel flow are stable and fine to document.

**When in doubt, ask before writing.** If code looks like a test, a temporary
mechanism, or an unreleased feature, raise it rather than documenting it and
waiting to be corrected.

Also out of scope:

- Internal admin and support tooling that customers can't reach.
- Backend implementation detail — API routes, database fields, service names.
  Document what the user sees and does, not how it is wired.
- Exact numbers that shift without a release: current plan prices, discount
  percentages, and quota figures. Prefer naming where the number is shown in the
  app over restating it here.

### Freshness

The app repo is the source of truth, but a local checkout may be behind. Before
documenting a feature, confirm the branch (`git rev-parse --abbrev-ref HEAD`) and
list what it is missing for the paths you care about:

```
git log --no-merges <branch>..master -- <paths>
```

A clean `git status` only means the tree matches its own HEAD — it says nothing
about whether that HEAD is current.
