# Project Summary — A/B Testing Analysis: Furniture E-commerce UX Experiments

## Objective
Evaluate the impact of four UX interventions on purchase funnel conversion 
and promotional engagement across 800K+ sessions during peak season 
(November 2020 – January 2021).

## What Was Tested
| Test | Feature |
|---|---|
| Test 1 | Simplified Checkout Flow — progress bar, auto-fill for shipping and payment |
| Test 2 | Promotional Banner Repositioning — sidebar → sticky bottom bar |
| Test 3 | Personalized Promotion Targeting — browsing history based recommendations |
| Test 4 | Mandatory Registration Before Checkout |

## Method
- Unit of analysis: session (`ga_session_id`)
- Statistical test: two-sided proportions z-test (α = 0.05)
- 8 metrics tracked: 5 funnel + 3 promotion

## Results & Decisions

| Test | Decision | Key Metric | Change | p-value |
|---|---|---|---|---|
| Test 1 |  Roll out | add_payment_info/session | +12.54% | < 0.001 |
| Test 2 |  Investigate | add_to_cart ↑ / view_promotion ↓ | mixed | < 0.001 / 0.004 |
| Test 3 |  Reject | begin_checkout/session | -3.35% | 0.012 |
| Test 4 |  Reject | new_accounts/session | -3.36% | 0.018 |

## Business Recommendations
- **Roll out Test 1** — simplified checkout meaningfully reduces friction 
at payment and shipping steps. Investigate post-payment drop-off before 
scaling.
- **Segment Test 2** — sticky banner drives add-to-cart but reduces 
promotion visibility. Run device/channel breakdown to find winning segments.
- **Revise Test 3** — personalization algorithm shows negative effects 
across funnel and cart. Review recommendation logic before retesting.
- **Abandon Test 4** — mandatory registration wall actively harms both 
conversion and acquisition. Consider optional registration with incentive instead.

## Limitations
- Peak-season data only — results may differ in off-peak periods
- Session-level analysis — user-level (new vs. returning) segmentation 
not performed
