# 🎃 WOW Challenge – Week 46: One Bar, Two Stories – The Total and the Trend

##  Challenge Overview

This week's Workout Wednesday challenge explores how Power BI Data Labels can communicate more than just the total value.

The objective was to visualise pumpkin sales across seven seasons (2019–2025) and display both the sales total and Year-over-Year (YoY) change.

Instead of presenting only sales figures, this challenge focuses on combining totals and trends to communicate business performance more effectively.

---

##  Dataset

**Dataset:** Harvest Hollow Farm – Pumpkin Sales

The dataset contains pumpkin sales information across seven seasons, from 2019 to 2025.

The dataset was used to analyse:

- Annual pumpkin sales
- Previous year's sales
- Year-over-Year growth
- Sales growth and decline patterns

---

##  Challenge Objectives

- Calculate total pumpkin sales.
- Calculate previous-year sales.
- Calculate Year-over-Year growth percentage.
- Create dynamic YoY labels.
- Apply conditional colours to growth and decline indicators.
- Visualise sales performance across seasons.
- Experiment with an alternative Butterfly-style visualisation.

---

##  DAX Measures

### 1. Total Pumpkin Sales

```dax
Total Pumpkin sales =
SUM(Harvest[Pumpkins Sold])
```

### 2. Pumpkins Previous Year (PY)

```dax
Pumpkins PY =
VAR yr = SELECTEDVALUE(Harvest[Year])
RETURN
    CALCULATE(
        [Total Pumpkin sales],
        REMOVEFILTERS(Harvest[Year]),
        Harvest[Year] = yr - 1
    )
```

### 3. Pumpkins YoY %

```dax
Pumpkins YoY % =
IF(
    NOT ISBLANK([Pumpkins PY]),
    DIVIDE(
        [Total Pumpkin sales] - [Pumpkins PY],
        [Pumpkins PY]
    )
)
```

### 4. Pumpkins YoY Label

```dax
Pumpkins YoY Label =
VAR chg = [Pumpkins YoY %]
RETURN
    SWITCH(
        TRUE(),
        ISBLANK(chg), "first season",
        ABS(chg) < 0.01, "▬ steady",
        chg > 0.25, "▲ " & FORMAT(chg, "0%"),
        chg > 0, "▲ " & FORMAT(chg, "0%"),
        "▼ " & FORMAT(ABS(chg), "0%")
    )
```

### 5. Pumpkins YoY Color

```dax
Pumpkins YoY Color =
VAR chg = [Pumpkins YoY %]
RETURN
    SWITCH(
        TRUE(),
        ISBLANK(chg) || ABS(chg) < 0.01, "#8B7355",
        chg > 0, "#556B2F",
        "#A52A2A"
    )
```

---

##  Visualisation Approach

### Original Challenge

The original challenge focused on using the Data Labels feature in Power BI's native bar and column charts.

The Data Labels functionality includes:

- **Value:** Displays the primary value.
- **Title:** Adds an optional title.
- **Detail:** Displays additional information alongside or below the primary value.
- **Layout:** Controls whether labels are displayed in single-line or multi-line format.

The objective was to display annual sales along with YoY growth indicators.

---

##  Alternative Visualisation – Butterfly Chart

Instead of limiting myself to the original visualisation, I experimented with an alternative butterfly-style layout using a Power BI Table visual and conditional formatting with Data Bars.

### Visual Structure

- Previous/current sales comparison using Data Bars.
- Year positioned in the centre.
- YoY growth labels.
- Growth and decline indicators.

This approach allowed me to explore how the same dataset could be presented differently while retaining the key business information.

---

##  Business Insights

The pumpkin sales data revealed interesting year-over-year performance patterns.

| Year | Pumpkin Sales | YoY Growth |
|------|--------------:|-----------:|
| 2019 | 12,400 | First Season |
| 2020 | 9,800 | ▼ 21% |
| 2021 | 13,900 | ▲ 42% |
| 2022 | 15,200 | ▲ 9% |
| 2023 | 16,800 | ▲ 11% |
| 2024 | 16,600 | ▼ 1% |
| 2025 | 19,300 | ▲ 16% |

### Key Observations

- **2020:** Sales declined by 21% compared with the previous season.
- **2021:** Sales recovered strongly, growing by 42%.
- **2022:** Sales continued to increase by 9%.
- **2023:** Sales grew by another 11%.
- **2024:** Sales experienced a slight decline of 1%.
- **2025:** Sales bounced back with 16% growth, reaching the highest sales level across the seven seasons.

---

##  Key Learnings

- Data labels can communicate additional business context beyond the primary value.
- YoY analysis helps identify growth, decline and performance patterns.
- DAX measures can dynamically calculate previous-year values and growth percentages.
- Conditional formatting makes positive and negative performance easier to interpret.
- The same dataset can tell different stories when presented using different visualisation techniques.
- Experimenting with alternative layouts helps improve visualisation skills and creativity.

---

##  Final Output

The final report combines annual pumpkin sales, previous-year comparisons and YoY growth indicators in a butterfly-style layout.

The objective was to make sales comparisons easier to interpret while keeping the visual simple and focused.

---

##  My Takeaway

Sometimes, a small dataset can reveal so many insights.

The real value is not always in the volume of data, but in how we analyse, visualise and communicate it.

One dataset. Seven seasons. Multiple insights. Different visualisation possibilities.

**Explore the data. Find the story. Communicate the insight!**

---

##  Credits

Thanks to the Workout Wednesday community for this week's challenge and the opportunity to learn, experiment and explore new ways to visualise data.

Special thanks to **Santhanalakshmi Ponnurasan** for creating this challenge.

#PowerBI #WorkoutWednesday #WOWChallenge #DataAnalytics #DataVisualization #DAX #BusinessIntelligence
