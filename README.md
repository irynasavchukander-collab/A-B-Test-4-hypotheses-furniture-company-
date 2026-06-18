
# A/B Testing Analysis — Furniture E-commerce UX Experiments

## Overview
This project evaluates the impact of four independent UX experiments 
conducted on a global furniture e-commerce platform during peak season 
(November 2020 – January 2021). Using SQL/BigQuery for data extraction 
and Python for statistical analysis, the project measures how checkout 
redesign, promotional banner changes, personalization, and registration 
gates affect 8 key funnel and promotion metrics.

## Business Context
The product team identified two friction points:
- High drop-off during the checkout process (payment and shipping steps)
- Low engagement with promotional content (banner views and selections)

Four UX interventions were tested simultaneously across 800K+ sessions.

## Tools & Technologies
- **SQL / Google BigQuery** — multi-table CTE-based data extraction
- **Python (pandas, numpy, scipy, statsmodels)** — data processing and 
proportions z-test
- **Matplotlib / Seaborn** — heatmap and bar chart visualizations
- **Tableau** — results dashboard and distribution calculator

## Dataset
800,996 rows × 9 columns. Date range: 2020-11-01 – 2021-01-27.  
Source: public e-commerce training dataset (`data-analytics-mate.DA`).  
Unit of analysis: session (`ga_session_id`). No missing values.

## Experiments & Hypotheses

| Test | Feature Tested | H₁ |
|---|---|---|
| Test 1 | Simplified Checkout Flow (progress bar, auto-fill) | Increases begin_checkout, add_shipping_info, add_payment_info |
| Test 2 | Promotional Banner Repositioning (sidebar - sticky bar) | Increases add_to_cart and view_promotion |
| Test 3 | Personalized Promotion Targeting (browsing history based) | Increases view_promotion, select_promotion, add_to_cart |
| Test 4 | Mandatory Registration Before Checkout | Increases new_accounts without harming begin_checkout |

## Metrics Analyzed

### Funnel Metrics
| Metric | Interpretation |
|---|---|
| `begin_checkout/session` | Share of sessions that initiated checkout |
| `add_shipping_info/session` | Share of sessions that entered shipping details |
| `add_payment_info/session` | Share of sessions that entered payment info |
| `orders/session` | Share of sessions with a completed purchase |
| `new_accounts/session` | Share of sessions resulting in new registrations |

### Promotion Metrics
| Metric | Interpretation |
|---|---|
| `view_promotion/session` | Share of sessions where promotions were viewed |
| `select_promotion/session` | Share of sessions where promotions were clicked |
| `add_to_cart/session` | Share of sessions with add-to-cart actions |

## Key Results

![Metric Change Heatmap](images/metric_change_heatmap.png)
*Heatmap of relative metric changes (test vs. control) across all four tests. Green = positive, red = negative. Test 1 shows the most consistent positive effect across funnel metrics.*

**Test 1 — ✅ Roll out | H₁ Confirmed**  
Simplified checkout increased payment conversion by +12.54% (p < 0.001), 
shipping info by +6.56% (p = 0.009), and checkout starts by +6.66% (p = 0.003). 
No effect on final orders — post-payment drop-off warrants further investigation.

![Test 1 Conversion Rate Control vs Test](images/test1_conversion_bar.png)
*Conversion rates for control vs. test group across all 8 metrics in Test 1. Payment and shipping steps show the strongest lift.*

**Test 2 — ⚠️ Investigate | Mixed signals**  
Sticky banner increased add_to_cart by +9.75% (p < 0.001) but reduced 
promotion views by -1.36% (p = 0.004). The banner acts as a CTA rather 
than a discovery surface — requires segmentation before rollout.

**Test 3 — ❌ Reject | H₁ Refuted**  
Personalized promotions caused a decline across funnel and promo metrics: 
begin_checkout -3.35% (p = 0.012), add_to_cart -3.06% (p < 0.001), 
view_promotion -1.06% (p = 0.017). Personalization algorithm needs revision.

**Test 4 — ❌ Reject | H₁ Refuted**  
Mandatory registration gate backfired: new_accounts fell by -3.36% 
(p = 0.018) and begin_checkout by -2.35% (p = 0.046). Users abandoned 
sessions when faced with a forced registration wall.

## Final Decision Table

| Test | Decision | Key Reason |
|---|---|---|
| Test 1 | ✅ Roll out | Significant positive funnel improvement |
| Test 2 | ⚠️ Investigate | Mixed signals — CTA up, visibility down |
| Test 3 | ❌ Reject | Negative effect on funnel and cart |
| Test 4 | ❌ Reject | Registration gate harms both acquisition and conversion |

## Limitations
Results reflect peak-season behavior (Nov–Jan) and may not generalize 
to off-peak periods. Funnel metrics are measured at session level; 
user-level analysis (new vs. returning) was not performed and may 
reveal additional segmentation effects.

## Dashboards
- [A/B Test Results Dashboard](https://public.tableau.com/app/profile/iryna.savchuk/viz/ABportfolio1/Dashboard1?publish=yes)
- [Distribution Calculator](https://public.tableau.com/app/profile/iryna.savchuk/viz/ABdestributionportfolio2/Calculators?publish=yes)

## Files
- `AB_portfolio_furniture_ecommerce.ipynb` — full notebook
- `images/` — visualizations used in this README

## Author
Iryna Savchuk
