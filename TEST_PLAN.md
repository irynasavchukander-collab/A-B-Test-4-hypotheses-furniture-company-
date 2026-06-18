 # Test Plan

## Experiment Design
- **Randomization unit:** ga_session_id
- **Traffic split:** 50/50 (control vs. variant)
- **Test duration:** 2020-11-01 – 2021-01-27 (~12 weeks)
- **Significance level:** α = 0.05
- **Test type:** two-sided (we test for both positive and negative effects)

## Sample Size
800,996 total sessions across 4 tests.
Each test ran on an independent user segment — no overlap between tests.

## Guardrail Metrics
orders/session was monitored as a guardrail — 
no test should be rolled out if it significantly harms final conversion.

## Known Limitations
- Tests ran simultaneously during peak season
- No pre-experiment AA test documented
- User-level (new vs. returning) split not available
