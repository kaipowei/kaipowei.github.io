---
name: update-portfolio
description: Add a finished project or piece of academic/career news to kaipowei.github.io (this repo). Use whenever Kaipo says he finished a project, got admitted/hired/published, or otherwise has portfolio-worthy news to add to the News or Projects section.
---

# Updating kaipowei.github.io

This is Kaipo Wei's personal site: a single `index.html` (About / News / Projects /
Experience / Skills / Contact) plus optional per-project write-ups under `projects/`.
Dark theme, `.entry` accordion components, no build step — just edit the HTML directly.

## Sources to check before writing anything

1. **This conversation** — what Kaipo just told you about the project or news.
2. **His memory system** (`claude-memory`, separate repo/tool) — check for relevant
   `project` or `user` memories about what he built and why, in case there's more
   context than what he typed in chat.
3. If the project has its own repo (e.g. a GitHub README), read that repo's README —
   it's usually the fullest description of what was built and why it was non-trivial.

Never invent technical details (dataset sizes, specific algorithms, metrics) that
aren't confirmed by one of the above. If a detail is missing, either ask Kaipo or
leave a `<p class="note">` saying the full write-up is coming — see the current
`projects/aicup.html` for that pattern. A fabricated technical claim on a job-hunting
site is worse than an honest gap.

## Adding a News entry

News rows live in `<section id="news">`, newest-first — but "newest" means nearest in
time to today, not strictly "already happened": upcoming plans (e.g. an admitted-but-
not-yet-started program) can sit above things that already happened, if they're
temporally closer. Match the granularity already used nearby (`Jul 2026`, `Spring 2026`,
`2025` — don't invent false precision like an exact day).

```html
<div class="news-row">
  <div class="d">Mon YYYY</div>
  <div>One sentence, plain, no hype adjectives.</div>
</div>
```

## Adding a Project entry

Entries live in `<section id="projects">`, inside `.entry` articles. Copy the
structure of an existing entry (e.g. the AI Quiz-Generation entry) rather than
reinventing it:

- `entry-head` → `h3` title + `span.meta` short tag (e.g. "LLM / cloud automation").
- `entry-summary` → one sentence, shown collapsed.
- `entry-detail-body` → 3-5 bullet points on what makes it non-trivial (not just a
  feature list), then one closing sentence on outcome/status.
- Only add `entry-links` (Code / Full write-up) if the link actually resolves —
  the site previously shipped with a `projects/lane-detection.html` link to a page
  that didn't exist, and `projects/` vs `project/` folder-name mismatch. Check the
  file exists before linking to it.
- Only one entry should have class `entry open` (the featured one) — don't add
  `open` to a new entry without removing it from whichever one currently has it,
  unless Kaipo asks for that.
- If the project's source is private, say so in the closing sentence instead of
  adding a Code link (see the AI Quiz-Generation entry for the phrasing pattern).

## Before pushing

This publishes to a live, public site. Always show Kaipo the diff and get an
explicit go-ahead before `git push` — don't push automatically just because the
skill ran.
