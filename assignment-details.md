

## Initial Assignment


I'd like you to build the measurement program for accessibility in the U.S. Web Design System (github.com/uswds/uswds). 

**Why this matters**

USWDS holds a high bar for accessibility, but we don't have a consistent way to measure it, compare it to peers, or track progress over time. We need a benchmark, a set of metrics with real baselines, and a scorecard we can report from every quarter.

**Standard**: WCAG 2.2 AA.

**Deliverables**:

1. **Peer benchmark**. How at least 4 peer design systems measure, test, and report accessibility. Suggested: GOV.UK Design System, IBM Carbon, GitHub Primer, Salesforce Lightning, Adobe Spectrum, and Shopify Polaris.For each one, cover what they automate, what they test manually, and what they publish.
2. **Metrics and baseline**. At least 6 accessibility metrics for USWDS.. For each metric, give a definition, the data source, the current value pulled from the repo and issue tracker, and a proposed FY2027 target. Examples: share of WCAG criteria covered by automated tests, open accessibility issues by severity, median time to fix, and releases with accessibility regressions.
3. **Scorecard template**. A one-page quarterly scorecard built from those metrics, filled in with the baseline values.

Put everything in a single report (Google Doc). Once I approve it, you'll have 2 business days to post the scorecard to uswds/uswds as a GitHub Discussion.

**What Fully Successful looks like**

- The benchmark covers at least 4 design systems.
- At least 6 metrics, each with a working definition, data source, real baseline value, and target.
- Each target is justified by the benchmark.
- It's delivered on time.

**What Outstanding looks like**

Everything above, plus:

- The benchmark covers at least 6 design systems.
- At least 8 metrics, each meeting the same quality bar as above.
- At least 2 practices from peer systems that USWDS should adopt, with an estimate of the effect of each.
- A scorecard that refreshes automatically from GitHub data.


Post Script - Project Goal: Being able to measure accessibility (and how we're increasing it over time) is critical, because we both need to 1) actually improve accessibility over time and 2) make sure we communicate externally so that people know we're improving accessibility over time.


## Followup Questions and Answers 1 


Question 1: When you write, re: Peer Benchmarks: "For each one, cover what they automate, what they test manually, and what they publish." what do you mean by "publish"?  My initial research indicates that they publish information about their accessibility strategies and workflows, but I have not yet found actual accessibility results or metrics.  In the context of that deliverable, can you clarify what information you're wanting to know about them publishing? 
Answer 1: I mean whatever each system makes public about accessibility: conformance statements, testing methods, per-component status, audit results, or metrics. If a system publishes its process but no results, say so. That's a useful finding.

Question 2: Though the assignment directs the use of WCAG 2.2 AA, my initial research suggests that there is significant overlap in the rules of 2.1 to 2.2.  It also suggests that the current accessibility test data available in the USWDS repository are based on 2.1.  When providing the metrics and baseline deliverables, will it be permitted to employ WCAG 2.1 AA data if the rules and methodologies at issue for the specific metrics are consistent between 2.1 and 2.2?  
Answer 2: Yes. Use 2.1 AA data for criteria that didn't change in 2.2. List the six A/AA criteria that are new in 2.2 and count them as not yet covered unless you find tests for them. Note that 4.1.1 Parsing was removed in 2.2.

Question 3: The Site Scanning program generates a substantial amount of accessibility scanning data of live websites that are employing USWDS.  Do you desire to keep the focus just on direct testing of the components and system in isolation, or would you be interested in factoring in real-world use and resulting accessibility results?  
Answer 3: Keep the core metrics on USWDS itself: the components, the repo, and the issue tracker. You may add one metric from Site Scanning if it's easy to pull.

Question 4: For the Metrics and Baseline deliverable, I believe I understand the requirements ("a definition, the data source, the current value..., and a... target"), but I'm confused by the ensuing examples ("share of WCAG criteria covered by automated tests, open accessibility issues by severity, median time to fix, and releases with accessibility regressions").  Each of those appear unrelated or in excess to the requirements.  Can you clarify what you are asking for in this deliverable beyond an explicit definition, citiation, current value, target value, and the correlation between the target value and a benchmark for each of the included metrics?
Answer 4: They're examples of metrics you could pick, not extra requirements. Each metric needs a definition, data source, current value, target, and a target justified by the benchmark. Nothing more.

Question 6: How preliminary are you comfortable with the completed assignment being?  The risks I've highlighted above make it likely that my final product will make a good start but not a good finish to the desired ends.  More v0.1 than 1.0.  Is this a concern for you?  If so, I would suggest that we schedule a meeting urgently at whatever time works for you because I want to both fully satisfy your expectations for me as an employee as well as help TTS succeed as best and efficiently as possible.  
Answer 6: The Fully Successful bar in my original email is the standard. I don't need a polished 1.0, but every metric needs a real baseline value and a target you can justify. If you can't get a value for a metric, choose a different metric.


## Further Direction 1


Benchmark. Add at least 4 peer design systems. For each, say what they automate, what they test manually, and what they publish.
Metrics. Axe-core rules are test checks, not program metrics. I need at least 6 metrics that show how accessible USWDS is overall, such as open accessibility issues or median time to fix. Each needs a definition, a data source, a current value, and an FY27 target.
Targets. Tie each one to what you find in the benchmark.
Scorecard. One page showing the baseline, current value, target, and trend over time for each metric. A single table of current counts doesn't show progress.


## Further Direction 2

1. Metrics. At least 6 distinct metrics.  At least 2 metrics must come from the uswds/uswds issue tracker. Explain any data you leave out, such as the "conditional" results and the 2 criteria missing from your metrics table.

2. Baselines and history. Use October 1, 2026, as the baseline date. For each metric, show quarterly values going back to October 1, 2024. You can get them from the issue tracker and from the git history of the test data. Show how you got each number so someone else can reproduce it.

3. Targets. Give a reason for each FY27 target. Where peers publish nothing useful, base the target on USWDS's own history and say so.

4. Benchmark. For each "Unknown," say what sources you checked.

5. Scorecard. One page with the baseline, quarterly history, current value, and FY27 target for each metric, plus a simple chart of at least one key metric over time.


## Important Notes

- The primary issue tracker relevant to this project is at https://github.com/uswds/uswds/issues
- There are some accessibility test results in this folder - https://github.com/uswds/uswds-site/tree/main/_data/accessibility-tests

