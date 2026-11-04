# WOW Challenge – Week 41: Stripe Chart

##  Challenge Overview

This challenge explores how to create a Stripe Chart
using the native column chart in Power BI.

The objective is to visualise global temperature
anomalies from 1880 to 2025 using colour variations.

##  Dataset

Global Temperature Dataset

- Source: Workout Wednesday
- Period: 1880–2025
- Reference Period: 1951–1980

##  My Approach

1. Explored and understood the dataset.
2. Created DAX measures for stripe height and temperature anomaly.
3. Built a native column chart.
4. Applied conditional formatting using a blue-white-red gradient.
5. Designed the report with explanations and insights.

##  Dashboard Preview

![Stripe Chart](Screenshot/stripe_chart.png)

##  DAX Measures

### 1. Stripe Height

```dax
Stripe Height = 1
```

### 2. Temperature Anomaly

```dax
Temp Anomaly =
AVERAGE(GlobalTemp[Anomaly])
```

##  Visualisation Techniques

- **Native Column Chart:** Used a standard clustered column chart to create individual temperature stripes.
- **Constant Stripe Height:** Used a DAX measure to maintain equal heights across all years.
- **Conditional Formatting:** Applied a diverging colour gradient (Blue → White → Red) based on temperature anomalies.
- **Colour Interpretation:**
  - 🔵 Blue – Below average temperature.
  - ⚪ White – Near average temperature.
  - 🔴 Red – Above average temperature.
- **Visual Formatting:** Removed unnecessary chart elements to create a clean stripe chart.

##  Key Insights

- **1880–1930:** Predominantly blue stripes indicate temperatures generally below the reference-period average.
- **1940–1970:** A mixture of blue, white and light red stripes shows temperature fluctuations around the baseline.
- **1980–2025:** Red stripes become increasingly prominent, highlighting the long-term global warming trend.
- **Overall Observation:** Despite year-to-year variations, the transition from blue to red reveals a clear warming pattern over time.

##  Key Learnings

1. Learned how to transform a native Power BI column chart into a Stripe Chart.
2. Understood how DAX measures can control visual properties beyond traditional calculations.
3. Explored conditional formatting using a diverging colour scale.
4. Learned how colour can communicate trends without relying on traditional bar heights.
5. Understood how to present long-term trends through simple and effective data visualisation.

##  Tools & Technologies

- Power BI Desktop
- DAX (Data Analysis Expressions)
- Native Column Chart
- Conditional Formatting
- Excel Dataset



##  Challenge Reference

[Workout Wednesday – 2026 Week 41: Power BI Stripe Chart Using Native Column Chart](https://www.workout-wednesday.com/2026-week-41-power-bi-stripe-chart-using-native-column-chart/)

##  Acknowledgement

A big thank you to the **Workout Wednesday team** for designing these creative challenges and encouraging the Power BI community to experiment, explore different approaches, and continuously improve their data visualisation skills.

---

 **Learning Takeaway:** Sometimes, a simple change in how we visualise data can reveal a completely different story. Even global temperature trends can be communicated through colourful stripes!
