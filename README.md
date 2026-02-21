# Strategic Churn Mitigation: Aligning Product Marketing with Retention
**Role:** Product Marketing Data Analyst | **Tools:** Power BI, DAX, Dimensional Data Modeling

## 📌 Executive Summary
A SaaS company was experiencing significant revenue leakage due to customer churn (~22% overall). Standard assumptions pointed toward pricing friction, technical bugs, or poor customer support. 

Through a hypothesis-driven analysis of over 5 disparate data sources (CRM, Support, Usage Logs, Subscriptions), I systematically disproved these assumptions. The data revealed that churn is not a product or pricing failure, but a **Product Marketing mismatch**: the company is acquiring users through "Event" channels who expect a different feature set than the product currently offers. 

These users invest significant time in the app (averaging 3,000 seconds per session) but ultimately churn because the marketed value does not align with the product reality.

## 💡 Strategic Recommendations
1. **Immediate Pivot:** Pause high-cost "Event" marketing sponsorships until the Product-Market Fit for this specific cohort is redefined.
2. **Double-Down:** Reallocate acquisition budget toward "Partner" and "Organic" channels, which demonstrate significantly higher retention stability.
3. **Product Marketing Audit:** Conduct an immediate review of the messaging used at events to ensure alignment with the actual product feature roadmap.

---

## 🔍 The Investigation (Hypothesis-Driven Methodology)
To avoid building a "vanity dashboard," I utilized a Mutually Exclusive, Collectively Exhaustive (MECE) logic tree to isolate the root cause of churn, testing three main branches:

### 1. Pricing & Commercials ❌ (Disproved)
* **Hypothesis:** Higher-priced tiers drive higher churn due to cost sensitivity.
* **Finding:** Churn rates are statistically uniform across Enterprise (22.1%), Basic (22.0%), and Pro (21.9%) tiers. Exit surveys confirm "Pricing" is the *least* cited reason for leaving. 

![pricing_and_commercials](/images/pricing%20&%20commercial.png)

### 2. Product Reliability & Support ❌ (Disproved)
* **Hypothesis:** Technical bugs or slow support resolution drive customers away.
* **Finding:** Active accounts actually experience slightly more logged system errors (0.57) than churned accounts (0.54). Furthermore, support ticket resolution time and CSAT scores are identical across both cohorts. The product is stable.

![product reliability_and_support](/images/product%20reliability%20&%20support.png)

### 3. Engagement & Acquisition Match ✅ (Validated Root Cause)
* **Hypothesis:** Customers are "bouncing" because they don't use the product.
* **Finding (Disproved):** Session durations (~3,000 seconds) and login frequencies (~10 events) are identical between churned and active users. They are trying hard to use the product.

![Engagement_and_Acquisition Match](/images/Engagement%20&%20Acquisition%20Match.png)

* **The Breakthrough:** By isolating the primary exit reason ("Features") and segmenting by acquisition channel, I identified that the **"Event" referral source accounts for a disproportionate 25% of all churned accounts.** They are leaving because they were sold a feature set we do not prioritize.
---

## 📊 Executive Dashboard (Explanatory, Not Exploratory)
![Executive Slides](/images/Executive%20Slides.png)

**Design Philosophy:** Applied pre-attentive processing principles using a single highlight color to direct executive attention strictly to the root causes (Events & Features), removing all unnecessary visual clutter.

## 🛠 Technical Execution
![Star Schema](/images/Star%20Schema.png)
* **Data Modeling:** Built a robust Star Schema connecting `dim_accounts` to multiple fact tables (`fact_feature_usage`, `fact_subscriptions`, `fact_churn_events`, `fact_support_tickets`).
* **DAX Engineering:** Engineered dynamic measures using `DIVIDE()`, `CALCULATE()`, and standard aggregations to safely handle nulls and isolate specific cohorts without the need for calculated columns.
* **Workflow:** Adhered to the McKinsey 7-Step Problem Solving framework to ensure technical execution was strictly tied to business value.