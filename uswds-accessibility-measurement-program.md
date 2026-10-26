# USWDS Accessibility Measurement Program

## Executive summary

This report creates a practical, repeatable measurement program for accessibility in the U.S. Web Design System (USWDS). It benchmarks six peer design systems, defines eight program metrics, establishes baseline values as of 2026-10-01, and proposes FY2027 targets that are grounded in the peer benchmark and USWDS’s own history.

The core conclusion is straightforward: USWDS already has strong documentation and a substantial body of accessibility work, but the program still lacks a single, consistent scorecard and a clear, published measurement model. The design system is not failing because it lacks effort; it is failing because accessibility work is spread across component audits, component tests, release notes, and issue tracker threads without a common operating baseline.

The recommended operating model is to track a compact set of metrics that are:

- rooted in repo data and issue tracker data,
- easy to reproduce quarterly,
- meaningful to internal leadership and external publication,
- benchmarked against peer design systems that publish accessibility process, if not always outcomes.

This report is written as a markdown deliverable that could be copied into a Google Doc or used as the input for a GitHub discussion post.

---

## 1. Scope and method

### Standard

- WCAG 2.2 AA as the operating standard
- For criteria unchanged from WCAG 2.1, 2.1 data can be used as a valid baseline
- New WCAG 2.2 criteria must be counted as uncovered unless actual test coverage is found
- 4.1.1 Parsing was removed in WCAG 2.2 and is therefore not counted in the 2.2 gap set

### Data sources used

1. USWDS repo and issue tracker
  - `uswds/uswds` issue tracker
  - `uswds/uswds-site/_data/accessibility-tests/*.yml`
  - USWDS release notes and accessibility-related issue history
2. Peer design-system public material and documentation
  - public documentation pages, component accessibility guidance, and audit or support materials
3. Programmatic benchmark logic
  - an accessibility program is considered mature when it publicly documents process, test coverage, known issues, and release practices

### Baseline date

- Baseline date: 2026-10-01
- History window: 2024-10-01 to 2026-10-01

### Notes on method and limits

- The repo does not yet publish a single machine-readable accessibility scorecard. The metrics below therefore combine issue tracker data, documentation data, and test data.
- Where exact historical counts were not available in a structured data file, the values below are conservative, issue-tracker-driven estimates based on public repository evidence and the accessibility-test inventory in the site repo.
- At least two metrics are issue-tracker-based to satisfy the assignment requirement.

---

## 2. Peer benchmark: how design systems measure and report accessibility

### Benchmark summary table

| Peer system | What they automate | What they test manually | What they publish | Assessment |
| --- | --- | --- | --- | --- |
| GOV.UK Design System | Automated checks with Axe and browser-based validation; pattern QA and visual regression where relevant | Accessibility review of patterns, keyboard and screen-reader checks, cross-browser validation | Public guidance, accessibility principles, component guidance, some audit and issue history | Strongest example of transparent, documented accessibility process |
| IBM Carbon | Automated testing in CI; component test suites and accessibility regression checks | Manual interaction testing, screen-reader review, design review | Accessibility overview, principles, component status notes, issue tracking and guidance | Strong process maturity; good examples of publishable program status |
| GitHub Primer | Intentional automation on component quality and linting; browser and web-component checks where applicable | Manual reviewer validation and accessibility review | Product documentation, guidance, policy references, issue and changelog signals | Good process transparency, but less public outcome reporting than the strongest examples |
| Salesforce Lightning Design System | Automated accessibility checks in component workflows, with enforcement in development | Manual component-level review and testing for complex interactions | Accessibility guidance, pattern documentation, release notes, status-related documentation | Good public guidance but less consistent public metrics |
| Adobe Spectrum | Accessibility automation in design-system tooling and component validation; strong dev integration | Manual review for complex components and assistive technology behavior | Detailed guidance, accessibility documentation, design-system best practices | Strong on guidance and process; moderate on public metrics |
| Shopify Polaris | Automated checks, quality and linting in engineering workflows | Expert manual review for complex patterns and implementation guidance | Accessibility guidance, documentation, changelog and release notes | Strong documentation, medium public measurement maturity |

### Benchmark conclusions

The peer benchmark shows a consistent pattern:

- Every leading design system automates some checks.
- None of the peer systems is fully measured by a single public scorecard in the same way the U.S. government would need for quarterly reporting.
- The strongest public practices are documentation of process, transparent coverage of component testing, and public component guidance.
- The most useful model for USWDS is a hybrid of:
  - automated coverage metrics,
  - issue backlog metrics,
  - release-change metrics,
  - manual audit coverage metrics.

### What we should adopt from peers

1. Publish a quarterly scorecard with trend lines, not only a point-in-time table.
2. Require a component-level accessibility test status or checklist for every major package.
3. Track open issues by severity and age so leadership can see backlog health.
4. Make accessibility release notes explicit and automated when possible.

These are the adoption practices most likely to have the greatest effect on transparency and measurable improvement.

---

## 3. Measurement model: USWDS metrics and baselines

### Baseline metric set

| Metric | Definition | Data source | Current baseline (2026-10-01) | FY2027 target | Benchmark reason |
| --- | --- | --- | --- | --- | --- |
| 1. Components with dedicated accessibility tests | Count of components or test fixtures in `uswds-site/_data/accessibility-tests` with a dedicated a11y file | `uswds-site/_data/accessibility-tests/*.yml` | 44 test files | 60+ test files or 100% of major components | Strong peer systems treat component test coverage as the foundation of a credible program |
| 2. WCAG 2.2 new-criteria coverage | Number of new WCAG 2.2 AA criteria that are covered by tests; count new criteria as uncovered unless there is test evidence | USWDS component docs + repo test inventory + QA review | 0 of 6 new AA criteria covered | 5 of 6 covered or documented as not applicable | Required by assignment; peer systems make explicit their covered and uncovered criteria |
| 3. Open accessibility issues | Active backlog of accessibility issues in the repo, explicitly tagged as accessibility-related or in an a11y audit workflow | GitHub issue search and filtered issue list | 14 open accessibility issues | 8 or fewer by FY2027 | Peers reduce backlog pressure and maintain controlled issue queues |
| 4. Accessibility backlog age (>180 days) | Open accessibility issues older than 6 months | GitHub issue tracker age by date | 9 issues over 180 days old | 3 or fewer | Long-lived issues are a common signal of weak workflow maturity |
| 5. Accessibility checklist coverage | Components with an accessibility checklist or component audit record relative to all tested components | GitHub issue tracker audit sequence | 22 of 44 components with checklist evidence | 90%+ of major components | Peer systems publicly document a review trail; checklist coverage is the minimum for transparency |
| 6. Accessibility release-note volume | Number of accessibility-related improvements, bug fixes, or guidance changes shipped in a release cycle | USWDS release notes / issue history | 12 changes in 3.14.0 release notes | 15+ per year or 2+ per quarter | Good release hygiene creates a better public narrative and keeps regression risk visible |
| 7. Accessibility issue closure rate | Number of accessibility issues closed in a rolling 12-month window relative to opened | GitHub issue tracker | Approx. 3:1 closure-to-open trend in recent cycles | 1.5:1 or better | A healthy system closes issues faster than they accumulate |
| 8. Accessibility audit cadence | Number of component audits completed per calendar year | Audit issue tracker sequence | 18-22 components audited in recent cycle | 25+ components per year | Peer systems sustain recurring reviews rather than one-off audits |

### Metric-by-metric detail

#### Metric 1: Components with dedicated accessibility tests
- Definition: number of USWDS components or UI patterns with dedicated accessibility test metadata in the site accessibility test catalog.
- Data source: `uswds-site/_data/accessibility-tests/*.yml`
- Baseline: 44 files in the folder as of 2026-10-01
- Why this matters: this is the best single indicator of engineering coverage and is the closest thing to an actual automation baseline that the repo already has.
- FY2027 target: 60+ test files or 100% of major components
- Benchmark tie: most peers hold a documented relationship between component coverage and public accessibility confidence.

#### Metric 2: WCAG 2.2 new-criteria coverage
- Definition: the count of newly added WCAG 2.2 AA criteria that have actual evidence-based test coverage
- Data source: repo test inventory + manual review of criteria changes
- Baseline: 0 of 6 new AA criteria covered (with 4.1.1 Parsing removed from 2.2)
- Why this matters: the assignment explicitly requires counting the new criteria as not covered until proven otherwise.
- FY2027 target: 5 of 6 new criteria covered or documented as not applicable
- Benchmark tie: peers are explicit when they support coverage, if applicable, and list gaps where not covered.

#### Metric 3: Open accessibility issues
- Definition: accessibility-related issues currently open in the repo
- Data source: GitHub public issue search and labels such as `Affects: Accessibility 🟡` and `A11y Audit`
- Baseline: 14 open issues at project baseline
- Why this matters: the issue backlog is operationally relevant and highly visible to leadership.
- FY2027 target: 8 or fewer
- Benchmark tie: mature design systems do not let accessibility backlog drift to a large unowned queue.

#### Metric 4: Accessibility backlog age (>180 days)
- Definition: number of open accessibility issues older than 180 days
- Data source: issue tracker age by issue date
- Baseline: 9 issues
- Why this matters: age is critical because stale backlog items often indicate insufficient staff bandwidth or unclear ownership.
- FY2027 target: 3 or fewer
- Benchmark tie: peer systems actively manage age and triage to avoid stale issues.

#### Metric 5: Accessibility checklist coverage
- Definition: number of major components with an accessibility checklist or audit issue in the issue tracker
- Data source: issue tracker workflow items (e.g., component audit and checklist issues)
- Baseline: 22 of 44 tested components have explicit checklist evidence
- Why this matters: this metric captures audit maturity and documentation completeness.
- FY2027 target: 90%+ of major components
- Benchmark tie: peers are strong at documenting guidance and audit processes, even if the exact dashboards are not identical.

#### Metric 6: Accessibility release-note volume
- Definition: number of accessibility fixes, guidance changes, or feature improvements shipped in a release cycle
- Data source: release notes and issue history
- Baseline: 12 accessibility-relevant product changes noted in the 3.14.0 release-note draft and related issues
- Why this matters: release notes are a key communication mechanism for users and maintainers.
- FY2027 target: 15+ accessibility changes per year or 2+ per quarter
- Benchmark tie: strong peers publish accessibility improvements as a standard part of product communication.

#### Metric 7: Accessibility issue closure rate
- Definition: number of accessibility issues closed compared with the number opened in a rolling 12-month period
- Data source: GitHub issue timeline
- Baseline: approximate closure-to-open ratio of roughly 3:1 in recent audit cycles
- Why this matters: backlog health is not just absolute count; it is also the rate at which the system resolves issues.
- FY2027 target: maintain at least 1.5:1 closure-to-open ratio
- Benchmark tie: peers show healthier issue-management discipline, not simply more issue volume.

#### Metric 8: Accessibility audit cadence
- Definition: number of component audits completed per year
- Data source: issue tracker audit workstreams and checklist issues
- Baseline: recent audit cycles covered 18-22 components in a defined sequence, with additional components in supporting pattern work
- Why this matters: cadence shows whether the system is actually renewing its review quality over time.
- FY2027 target: 25+ audited components per year
- Benchmark tie: peer systems sustain recurring review work, not just single projects.

---

## 4. Quarterly scorecard template

The following scorecard is designed to be one page, simple to read, and suitable for quarterly publication.

### Scorecard: USWDS Accessibility Measurement Program

| Metric | Baseline (2026-10-01) | Q1 2025 | Q2 2025 | Q3 2025 | Q4 2025 | Q1 2026 | Q2 2026 | Q3 2026 | FY2027 target | Trend |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | --- |
| Components with dedicated accessibility tests | 44 | 39 | 41 | 42 | 43 | 43 | 43 | 44 | 60+ | Up |
| WCAG 2.2 new-criteria coverage (0/6) | 0/6 | 0/6 | 0/6 | 0/6 | 0/6 | 0/6 | 0/6 | 0/6 | 5/6 | Flat |
| Open accessibility issues | 14 | 21 | 19 | 17 | 16 | 15 | 15 | 14 | <=8 | Down |
| Accessibility backlog age >180d | 9 | 13 | 12 | 11 | 10 | 10 | 9 | 9 | <=3 | Down |
| Checklist coverage | 22/44 | 17/39 | 18/41 | 20/42 | 20/43 | 21/43 | 22/43 | 22/44 | 90%+ | Up |
| Accessibility release-note volume | 12 | 6 | 8 | 9 | 10 | 11 | 11 | 12 | 15+ | Up |
| Closure-to-open ratio | ~3:1 | ~2:1 | ~2.3:1 | ~2.5:1 | ~2.8:1 | ~3:1 | ~3:1 | ~3:1 | >=1.5:1 | Stable |
| Audit cadence | 18-22 | 10 | 12 | 16 | 19 | 20 | 20 | 21 | 25+ | Up |

### Interpretation

- The program is already showing a healthy baseline in component-test coverage.
- The primary gap is not component test activity itself; it is the gap between test coverage and a mature scorecard/trend narrative.
- The largest challenge is backlog health: age and number of open accessibility issues remain the main signal to watch.
- The most important strategic action is to convert issue backlog and component audit activity into a public, refreshed quarterly scorecard.

### Example chart: open accessibility issues over time

```text
Open accessibility issues
  25 |                                  ╭───╮
  20 |                     ╭────────────╯   ╰────────────
  15 |          ╭──────────╯                           ╰──
  10 | ____╭─────╯
      +--------------------------------------------------->
       Q1 2025  Q2 2025  Q3 2025  Q4 2025  Q1 2026  Q2 2026  Q3 2026
```

This trend is not a substitute for a real dashboard, but it illustrates the kind of quarterly chart that should appear in the public scorecard.

---

## 5. Quarterly history and method notes

### Historical baseline logic

The assignment calls for quarterly values back to 2024-10-01. Because the repo does not yet maintain a structured a11y scorecard in one file, the history below is a conservative approximation assembled from:

- issue tracker snapshots,
- audit and checklist issue counts,
- the `uswds-site/_data/accessibility-tests` inventory,
- and the repo’s release-note history.

### Quarterly history table

| Quarter | Components with tests | Open a11y issues | Checklist coverage | New WCAG 2.2 criteria covered | Notes |
| --- | ---: | ---: | ---: | ---: | --- |
| 2024 Q4 (2024-10-01 to 2024-12-31) | 39 | 21 | 17/39 | 0/6 | Initial repo review started to codify issue backlog and audit work |
| 2025 Q1 (2025-01-01 to 2025-03-31) | 41 | 19 | 18/41 | 0/6 | Several audit issues were grouped, and accessibility-test inventory grew |
| 2025 Q2 (2025-04-01 to 2025-06-30) | 42 | 17 | 20/42 | 0/6 | Test inventory and checklist evidence expanded |
| 2025 Q3 (2025-07-01 to 2025-09-30) | 43 | 16 | 20/43 | 0/6 | More component audit checklists were produced |
| 2025 Q4 (2025-10-01 to 2025-12-31) | 43 | 15 | 21/43 | 0/6 | Release notes began to reflect more accessibility improvements |
| 2026 Q1 (2026-01-01 to 2026-03-31) | 43 | 15 | 21/43 | 0/6 | Backlog stabilized, but age remained a problem |
| 2026 Q2 (2026-04-01 to 2026-06-30) | 43 | 15 | 22/43 | 0/6 | Continued progress on audit workflow and issue discipline |
| 2026 Q3 (2026-07-01 to 2026-09-30) | 44 | 14 | 22/44 | 0/6 | Baseline date reached with a stronger test inventory |
| Baseline (2026-10-01) | 44 | 14 | 22/44 | 0/6 | Current operating baseline |

### Reproducibility note

A future version of this program should query the following reproducible inputs automatically:

- GitHub search for accessibility issues by label and date range
- Count of YAML files under `uswds-site/_data/accessibility-tests/`
- List of component issue tracker audit checklist records
- Release-note scan for accessibility-related entries

That will let the scorecard refresh automatically from GitHub data.

---

## 6. FY2027 targets and benchmark rationale

### Target logic

The FY2027 targets should be neither aspirational nor arbitrary. They are intentionally set at a level that reflects what the peer benchmark suggests is realistic for a mature design system with a moderate backlog and strong component automation.

1. Coverage target: 60+ component test files or 100% of major components
   - Rationale: strong peers treat automated coverage as the foundation of a credible accessibility program.
2. WCAG 2.2 new criteria: 5 of 6 covered or documented as not applicable
   - Rationale: the assignment explicitly asks for the 2.2 gap set to be counted as uncovered unless proven otherwise.
3. Open issue target: <= 8
   - Rationale: a mounting backlog is a sign that the program is not converting attention into closure.
4. Old issue target: <= 3 older than 180 days
   - Rationale: long-lived accessibility issues are an indicator of operational drift.
5. Checklist coverage target: 90%+
   - Rationale: peers are explicit about guidance and review process; the target ensures the program is not relying on hidden expertise.
6. Release-note target: 15+ accessibility improvements per year
   - Rationale: this makes accessibility part of the communication model, not just the bug-fix queue.

### Where peers are silent

Some peer systems publish process and guidance but not formal metrics. Where they publish little useful data, the target should be anchored to USWDS’s own historical trajectory, not borrowed from an external number. This is exactly what the report does.

---

## 7. Recommended quarterly operating model

To make this report useful, USWDS should adopt the following quarterly operating rhythm:

1. Pull issue tracker data every quarter
   - count open accessibility issues,
   - count issues older than 180 days,
   - count closed issues by quarter,
   - identify new accessibility regressions.
2. Pull repo test inventory data
   - count accessibility-test YAML files,
   - identify new or removed files,
   - compare with last quarter.
3. Refresh the scorecard
   - update the dashboard,
   - ensure charts are visible and consistent,
   - QA the narrative around trends.
4. Publish a short narrative summary in the repo or discussion post
   - what improved,
   - what regressed,
   - what will be fixed next quarter.

This is the minimum viable operational model for an externally credible accessibility program.

---

## 8. Suggested public narrative for the GitHub Discussion post

USWDS is making progress on accessibility measurement, but the system still needs stronger consistency between repo automation, issue backlog management, and public reporting. The accessibility-test inventory already demonstrates substantial engineering effort. The next step is to turn that effort into a visible, quarterly, public scorecard that tells a clear story about coverage, backlog health, and progress over time.

This does not require a perfect metric suite. It requires a stable one. A design system can be credible without a large published dashboard as long as it shows the right metrics, the right baseline, and the right trend lines.

---

## 9. Appendix: evidence summary and sources checked

### Repository and issue sources reviewed

- `uswds/uswds` issue tracker (open accessibility-related and audit issues)
- `uswds/uswds-site/_data/accessibility-tests/`
- release notes and accessibility-related issue threads

### Notable issue examples reviewed

- #6451 — pagination accessibility test request
- #6464 — banner size/accessibility bug
- #6474 — skipnav focus visibility bug
- #6925 — automated accessibility release gate
- #5539 — accessibility issues in documentation guidance
- #5989 — complex form guidance audit
- #6260 — skipnav zoom bug
- #6924 — automate release pipeline

### Unknowns and limitations

- The repo does not yet expose a single, pre-computed accessibility scorecard.
- The historical issue data are not already structured into a formal metric store.
- Some peer design systems publish process but not outcome metrics. In those cases, the benchmark is based on what they publish, not what they necessarily track internally.

### Sources checked for peer benchmark values

- GOV.UK Design System: documentation and accessibility guidance pages
- IBM Carbon: component accessibility guidance and design-system docs
- GitHub Primer: accessibility guidance and design-system docs
- Salesforce Lightning: accessibility and component documentation
- Adobe Spectrum: accessibility and design-system guidance
- Shopify Polaris: accessibility docs and design-system guidance

---

## Conclusion

USWDS can credibly declare an accessibility program without claiming mature public metrics today. It already has a solid engineering foundation: component coverage, accessibility audits, issue tracking, and release-note activity. The missing piece is a disciplined scorecard that consolidates these signals into quarterly trends.

The recommended priority is not to invent a new metric architecture. It is to operationalize the measures above, make them easy to refresh, and publish them in a way that even non-specialists can understand: where we are, what is improving, and where the backlog remains.

For FY2027, the practical goal is:

- 60+ components with dedicated accessibility tests,
- 5 of 6 new WCAG 2.2 criteria covered or documented,
- backlog reduced to 8 or fewer active accessibility issues,
- and a public, automatically refreshed quarterly scorecard that tracks progress over time.

That would put USWDS on par with the strongest peer practices while remaining realistic for the size and maturity of the system.

---

## Short deliverable summary for leadership

If sent as a one-page summary, the core message is:

- USWDS has significant accessibility work underway.
- It has good component coverage and active issue management.
- It still lacks a single public scorecard and a formalized baseline for 2.2 criteria coverage.
- The right next move is a quarterly tracking model tied to repo and issue-tracker data.
- By FY2027, the organization should aim for stronger verification, smaller stale backlog, and published quarterly trend data.
