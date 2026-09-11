# GitHub Profile README Dashboard Redesign

## Goal

Transform `README.md` from a long, text-heavy profile into a modern, clean, analytics-led GitHub profile dashboard for **Md Nazmul Hasan Nihal**. The README should quickly communicate technical focus, show public GitHub activity, and make representative work easy to scan without sacrificing accessibility or factual accuracy.

## Current State

- The profile README is 264 lines and already includes badges, project tables, local technology icons, GitHub stats, top-language output, social links, and repository administration content.
- The repository contains `README.md` plus a substantial `img/` icon library; no application runtime or build pipeline is present.
- The existing technology section is visually dense, while the most important signal—current GitHub activity and project impact—is buried near the bottom.
- GitHub profile READMEs support Markdown and a limited subset of HTML, but not custom CSS or JavaScript. The redesign must therefore use responsive HTML tables, image sizing, SVG/PNG cards, and Markdown structure.

## Design Decisions

### Visual direction

Use the selected **dark analytics dashboard** direction:

- Charcoal/near-black card surfaces, white and muted-gray text, and restrained blue/cyan accents.
- Compact KPI cards and clear section dividers instead of a large icon wall.
- Consistent card widths, spacing, and alignment; no decorative elements that compete with technical content.
- Keep all surrounding text readable in both GitHub light and dark themes. Dynamic cards should use a dark/transparent theme with visible borders where needed.

### Information architecture

Reorder the profile into this sequence:

1. **Hero:** avatar, name, role, one-sentence value proposition, and 3–5 high-signal badges.
2. **Live GitHub dashboard:** repository stats, top languages, contribution streak, and contribution graph in a responsive 2×2 layout.
3. **Technical focus:** three concise capability cards for Data Science & Machine Learning, Data Engineering, and Full-Stack Delivery.
4. **Featured work:** four primary project cards with problem, stack, and outcome/impact, followed by a compact “More repositories” link group for the remaining projects.
5. **Technical toolkit:** grouped, curated technology chips using the existing `img/` assets; retain only the tools that support the profile narrative.
6. **Delivery approach:** a short four-step pipeline such as **Ingest → Model → Deploy → Communicate**, showing end-to-end proficiency.
7. **Connect:** a compact row of verified social/profile links.
8. **Repository notes:** collapse or remove installation, usage, contribution, and repository-contents material from the profile-facing view; preserve it only if needed in a separate repository document.

### Dynamic elements

Use public, read-only endpoints and label them as live/public GitHub data:

- GitHub stats: `https://github-readme-stats.vercel.app/api?username=NazmulHasanNihal&show_icons=true&hide_border=true&theme=transparent&count_private=true`
- Top languages chart: `https://github-readme-stats.vercel.app/api/top-langs/?username=NazmulHasanNihal&hide_border=true&layout=donut&theme=transparent&langs_count=8`
- Contribution streak: `https://streak-stats.demolab.com/?user=NazmulHasanNihal&hide_border=true&theme=transparent`
- Contribution graph: `https://ghchart.rshah.org/NazmulHasanNihal`
- Optional repository badges for featured projects: GitHub stars, forks, language, and last-commit badges from `img.shields.io`, using the exact repository names.

Do not invent stars, contribution totals, employment details, availability, certifications, or project outcomes. If a third-party endpoint is unavailable, omit that card or provide a static, clearly labeled fallback rather than leaving a broken image.

## Implementation Tasks

1. Replace the current header with a compact centered hero and a small set of consistent custom badges.
2. Add the live GitHub dashboard near the top using a responsive HTML table; constrain image widths so cards do not overflow on mobile.
3. Rewrite the overview as three outcome-focused capability cards, retaining the existing factual tool coverage but removing repetitive prose.
4. Rebuild the project section around four flagship repositories, then retain the remaining three as a concise secondary list. Add only verified repository badges and links.
5. Curate the technology section into four grouped rows and reuse the existing local SVG assets. Add meaningful `alt` text and consistent dimensions.
6. Add a short delivery-pipeline strip and a compact connect row.
7. Remove or collapse repository administration sections that do not help a profile visitor, while preserving accurate project and social links.
8. Keep the file dependency-free: no scripts, custom CSS, credentials, private data, or generated analytics files.

## Acceptance Criteria

- The first viewport communicates who Nihal is, his three focus areas, and at least one live GitHub activity signal.
- The README has a clear visual hierarchy and is substantially easier to scan than the current version.
- All project, social, stats, chart, and badge links resolve to the intended public destinations.
- Dynamic images include useful alt text, bounded widths, and a graceful fallback if a service is unavailable.
- The layout remains readable on desktop and narrow/mobile GitHub views.
- The technology section is curated rather than exhaustive and does not duplicate the project tables.
- No secrets, credentials, private data, or unsupported claims are added.
- The result uses only GitHub-compatible Markdown and HTML.

## Risks and Mitigations

- **Third-party service availability:** stats and graph providers may rate-limit or change endpoints. Validate every URL and keep the number of external images limited.
- **GitHub theme differences:** dark card images can look different in light mode. Use high-contrast text, subtle borders, and test both themes.
- **Image overload:** too many dynamic images slow rendering. Prioritize four dashboard visuals and a small number of project badges.
- **Stale metrics:** live cards can lag behind GitHub. Describe them as public/live indicators, not real-time guarantees.
- **Asset path errors:** GitHub rendering is case-sensitive. Verify every local `img/` filename exactly as referenced.
- **HTML sanitization:** avoid unsupported styles and scripts; use simple tables, `<div align="center">`, links, and images only.

## Validation Plan

1. Preview the revised README in a GitHub-compatible Markdown renderer.
2. Open the rendered profile in both GitHub light and dark modes.
3. Check the layout at desktop width and a narrow/mobile width.
4. Request every dynamic image URL and confirm it returns a valid image.
5. Verify every project, social, and repository badge link.
6. Confirm all local icon paths and alt text.
7. Review the final copy for unsupported claims, duplication, spelling, and accessibility.
8. Compare the revised README against the original to ensure no important project or contact link was lost.

## Out of Scope

- Building a custom analytics backend or GitHub API integration.
- Adding JavaScript, custom CSS, animations that GitHub does not support, or private metrics.
- Changing project repositories or creating new application code.
- Adding unverified personal, employment, certification, or availability claims.
