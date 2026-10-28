# S01E03 — what it shows

Source: the student's supplied kb-export-267efc5e.zip, exported 2026-10-04. Original export files are preserved byte for byte. This repo adds a signed review and a reproducible renderer; it does not change the product. The later engineering update reports the parser fixed and the hint won't fix because booking-v3 was retired.

- New page source: [src/routes/kb/incidents/4471-split/+page.svx](src/routes/kb/incidents/4471-split/+page.svx).
- Desk page, rendered from that source and the supplied components: [rendered/kb/incidents/4471-split/index.html](rendered/kb/incidents/4471-split/index.html). The whole rendered/ tree contains its CSS, JavaScript and linked KB pages.
- Reproducible report coverage: [evidence/report-assignments.json](evidence/report-assignments.json).
- Later closure evidence: [engineering update](evidence/engineering-update.md). Parser closes as completed; hint closes as not planned.
- GitHub issues in this repo are the two cause tickets. Their bodies give counts, all report IDs, evidence, reproduction steps and verification criteria. See [the issues](https://github.com/devilnest/mega-s01e03-what-it-shows/issues).

## View and reproduce

Use Node.js 24 and npm. Versions and integrity hashes are locked in package-lock.json.

~~~sh
npm ci --ignore-scripts
npm run audit
npm run build
npm run preview
~~~

Open http://localhost:4173/kb/incidents/4471-split/ to view the desk's page. Serving the whole rendered/ directory over HTTP also works. GitHub's file view displays HTML as source; the static assets are included so the page can be served locally with its interactive examples.

The snapshot assigns 379 unique reports to parser and 33 to hint, totaling 412. Fifteen overlapping export rows are not extra reports. Five parser-assigned reports have divergent symptoms and remain explicitly flagged for investigation; no third cause is asserted.

Computed counts, tenant classification, dedupe examples, stale-page notices, queue timeline and desk signature come from the source components and data at render/build time. Refresh the export and rebuild as the desk keeps working, then reconcile issue counts. A saved HTML snapshot cannot know later desk activity by itself.

The proposed cause-based intake rule leaves accepted decision 0001 intact. It requires desk review before adoption. The supplied product-scale statement is not treated as an affected-user count.

The course-issued signature is intentionally included only as required by the challenge's signed-page contract and its compiled rendering. Course logs, local authentication, dependency folders, private analysis and machine screenshots are outside this repo or ignored. No CI, deployment, or tracking automation is added.

## Validation

The build prerenders all five KB pages. Local headless Edge verification checked the derived counts and desk reference, the five dedupe cases and a live selector change, stale-policy warnings, no browser errors, and no document overflow at 390px.
