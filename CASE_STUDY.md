# Case study — Turning a severe slowdown into a verified fix

[← Back to showcase](README.md) · [Product walkthrough](PRODUCT_TOUR.md) · [Testing overview](TESTING.md)

**Discipline:** troubleshooting, controlled comparison, regression testing, software reliability  
**Context:** private Windows release testing of WatermarkPro  
**Outcome:** responsive operation restored while important user settings and original images were preserved during verification

## The problem

During physical Windows testing, a previously responsive desktop application became extremely slow. Startup and shutdown took approximately a minute, and routine interaction—including adding an image—also became unusually sluggish. The behavior appeared in both installed and portable builds.

The obvious explanation was not necessarily the correct one.

## Investigation: separate theories from observations

| Question | Test or observation | What it established |
| --- | --- | --- |
| Was antivirus activity causing the lag? | Observed system activity and relevant Windows security information during reproduction | No supporting evidence that the initial antivirus hypothesis explained the problem |
| Was the folder location responsible? | Compared behavior after moving the portable application outside a synchronized folder | The slowdown persisted |
| Was the application itself always slow? | Launched using fresh settings and repeated ordinary interactions | Startup, image selection, preview, navigation and shutdown became responsive |
| What differed between slow and responsive runs? | Compared persisted configuration states | The affected application state, rather than the executable alone, was the key variable |

These comparisons narrowed the investigation without requiring an unsafe change to Windows security protections.

## The measurable finding

The affected saved configuration had grown far beyond its expected size. The corrective work addressed growth in persisted application state and included handling previously affected settings.

| Check | Observed result |
| --- | --- |
| Affected configuration before repair | Approximately **1.5 GB** |
| Same preserved configuration after repair validation | Approximately **117 KB** |
| Additional repeated-batch check | An active settings file of approximately **37 KB** after five batches |
| Everyday behavior after validation | Responsive launch and interactions during the checked workflows |
| Preservation checks | Important preferences, templates and history remained available; selected originals were not changed during the test |

These figures describe **specific internal test cases**, not a universal performance benchmark.

## What I did

1. Reproduced the slowdown and recorded how it affected ordinary workflows.
2. Compared competing explanations rather than accepting the first plausible cause.
3. Used controlled tests with fresh and affected settings to narrow the problem.
4. Worked through the corrective process with AI-assisted development tools.
5. Ran validation using preserved affected configuration data and additional batches.
6. Checked for regressions in normal operation, saved settings, outputs, and source-file safety.

I do not present this as work performed in a professional IT support role or claim sole authorship of the underlying source-code change.

## Why it matters

This incident was an important example of diagnosing a system-level symptom through evidence rather than guesswork:

- **Reproduction** made the issue measurable.
- **Controlled comparison** identified the relevant variable.
- **Preservation testing** checked that a speed improvement did not sacrifice user data.
- **Regression checks** helped verify that ordinary workflows still functioned.

The same thinking carries over to desktop support, software QA, business systems troubleshooting, and release validation.

## What is intentionally omitted

The public case study does not include the affected settings files, internal paths, private logs, source code, implementation patches, complete test fixtures, release binaries, or build instructions. It is a **sanitized account of the troubleshooting approach and verified outcomes**.

For the broader test matrix, see [TESTING.md](TESTING.md).
