# Smart Pricing Strategy Simulator for Startups
https://1drv.ms/x/c/d25b756fc27d4ee3/IQBOc50CdGJLSYw99L7D9QxHASZB4R_pr9wI8SKiU4GQ4k4?e=yRNEtk

> **Data disclaimer:** Every number in this repo is **SYNTHETIC DATA / ASSUMPTION / SIMULATION**. No real customer survey, competitor price, sales or revenue figures are used. Output is a **recommended price to test**, not a "perfect price".

## Project Overview
A pricing simulator that helps a startup founder compare price points and see the impact on demand, revenue, contribution margin, CAC, LTV:CAC, break-even and profit before launch.

## Dashboard
<img width="409" height="389" alt="P5 (S1) in outputs" src="https://github.com/user-attachments/assets/520f3946-7286-4bfd-b07b-b8361807a561" />


## Demo Video


https://github.com/user-attachments/assets/7a63c141-4299-4415-b162-4a5e40550805



## Business Problem
Find a price customers will pay while keeping healthy unit economics and sustainable growth.

## Startup Scenario (fictional)
**LearnLoop**: an AI-powered mock-test and doubt-solving subscription for Indian college and competitive-exam students. Monthly subscription; channels: Instagram/YouTube ads, campus ambassadors, referrals.

## Objectives
Compare cost-plus, competitor-based, value-based, penetration, premium, freemium, subscription and tiered pricing; quantify trade-offs; design a 30-day real-world validation plan.

## Methodology
1. Segment customers (Budget Student, Serious Aspirant, Working Upskiller) using synthetic WTP data (`customer-research/`).
2. Model demand: `conversion = base_conv x (price / ref_price)^-elasticity` (**elasticity 1.4 is an ASSUMPTION**; real elasticity needs experiment data).
3. Compute unit economics, break-even, discount break-even, sensitivity.
4. Score and compare scenarios; recommend a price range to test.

## Key formulas
- Contribution/unit = Price - Variable cost; CM% = CM / Price
- Break-even customers = (Fixed + Marketing) / CM per unit
- CAC = Marketing / New customers; LTV = CM per month x 1/(1 - retention); Payback = CAC / monthly CM
- Required extra volume after discount = CM_before / CM_after - 1

## Key Assumptions (editable in `pricing_model.py` or the app sidebar)
30,000 leads/month; 5% conversion at Rs 499; variable cost Rs 110 + 2% gateway; fixed Rs 2,00,000; marketing Rs 3,00,000; retention 85%/month.

## Results snapshot
See `docs/results.md` for full tables (scenarios, discount analysis, sensitivity).
- Revenue is highest at the lowest price, but **profit peaks in the Rs 399-499 zone**.
- Rs 999 earns the best margin % but too few customers to cover costs, so it **loses money** under these assumptions.
- A 20% discount needs ~35% more volume just to hold total contribution.
- Profit is most sensitive to **demand (leads/conversion)**, then variable cost and CAC, then price.

## Pricing Recommendation
**Recommended price to test:** Rs 399-499/month with Basic / Standard / Premium tiers and an annual plan, capped discounts (max 10-15%). Biggest risk: demand elasticity is unverified.

## Run the simulator
```bash
pip install -r requirements.txt
python build.py          # regenerates CSVs + docs/results.md
streamlit run app.py     # interactive dashboard
```

## Folder guide
| Folder | Upload here |
|---|---|
| customer-research | survey questions, personas, synthetic dataset |
| competitor-pricing | competitor table (with source, link, date checked for real prices) |
| cost-analysis | fixed / variable / CAC cost tables |
| pricing-strategies | strategy comparison, discount CSV |
| unit-economics | LTV, CAC, payback, break-even workings |
| scenario-analysis | scenario CSVs (conservative/base/optimistic) |
| sensitivity-analysis | sensitivity tables |
| dashboard | Excel / Power BI / Streamlit screenshots source |
| screenshots | dashboard images used in README and LinkedIn |
| presentation | 10-slide PPT / PDF |
| docs | report, results.md, validation plan |

## Limitations
Synthetic data; assumed elasticity; simplified linear demand curve; no seasonality, taxes (GST) or competitor reactions; management profit is not accounting profit.

## Tools Used
Python, pandas, NumPy, Streamlit, Excel/Google Sheets, (optional) Power BI.

## Future Scope
*Simulation improvements:* dynamic pricing, segment-specific pricing, K-Means segmentation.
*Real-world validation:* customer survey (Van Westendorp), A/B price test, real CAC/LTV, cohort and churn analysis.

## Conclusion
Pricing is a hypothesis to test. The simulator shows which assumptions matter most, so real research can focus on them.
