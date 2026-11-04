#  Workout Wednesday 2026 – Week 37 Challenge
## National Guacamole Day | The Great Guac Guide

##  About the Challenge

Happy National Guacamole Day! 🥑

This week's Workout Wednesday challenge combines two interesting things: **Power BI and Guacamole!**

The challenge is to build an **Icon Matrix** that explains what each ingredient brings to a guacamole dish.

Instead of displaying repetitive text such as *Yes, Maybe, and No*, we use icons to make the information easier to understand and visually appealing.

Imagine preparing a guacamole dish with ingredients like Avocado, Cilantro, Garlic, Jalapeño, Lime, Mango, Onion, and Tomato.

The goal is to identify whether each ingredient contributes to different characteristics:

- Chunky
- Classic
- Fruity
- Kid-Friendly
- Spicy

I decided to take this challenge a little further by experimenting with **two different approaches to achieve the same result**.

##  Challenge Objective

Create an Icon Matrix that communicates ingredient characteristics using visual indicators instead of repetitive text.

### Icon Legend

| Answer | Icon | Meaning |
|---|---|---|
| Yes | ✅ | Adds it |
| Maybe | ⚠️ | May add it |
| No | ❌ | Doesn't add it |

##  My Approach

I explored two different ways of building the same Icon Matrix in Power BI.

### 1. Using Native Power BI Features

For the first approach, I used Power BI's built-in conditional formatting.

**Steps:**

1. Imported the Guacamole dataset into Power BI Desktop.
2. Added a Matrix visual.
3. Placed `Ingredient` in Rows.
4. Placed `Characteristic` in Columns.
5. Placed `Answer` in Values.
6. Opened the Format visual pane and navigated to Cell elements.
7. Enabled Icons and configured conditional formatting rules for Yes, Maybe, and No.
8. Selected Icon only to display indicators without repeating text.
9. Adjusted formatting, alignment, spacing, and column widths.
10. Added an icon legend to improve readability.

**Key Learning:** Power BI's native conditional formatting makes it easy to convert categorical values into visual indicators without writing DAX.

### 2. Using a DAX Measure

For the second approach, I wanted to achieve the same result using DAX.

Instead of relying on native conditional formatting, I created a measure using `SELECTEDVALUE()` and `SWITCH()`.

**DAX Measure:**

```DAX
Guac Icon =
VAR _Answer =
    SELECTEDVALUE('Guacamole Data'[Answer])

RETURN
    SWITCH(
        _Answer,
        "Yes", UNICHAR(9989),
        "Maybe", UNICHAR(9888) & UNICHAR(65039),
        "No", UNICHAR(10060),
        BLANK()
    )
### How the DAX Measure Works

- `SELECTEDVALUE()` retrieves the answer applicable to the current Matrix cell.
- `SWITCH()` checks the answer and returns the corresponding icon.
- `UNICHAR()` converts Unicode character codes into symbols.
- `BLANK()` returns an empty result when no matching answer exists.

**Matrix Configuration:**

| Field | Placement |
|---|---|
| Ingredient | Rows |
| Characteristic | Columns |
| Guac Icon | Values |

**Key Learning:** DAX measures can dynamically return different results depending on the current filter context of a visual.

---

##  Dashboard Preview

### Guacamole Icon Matrix – Native Feature vs DAX

![Guacamole Icon Matrix - Workout Wednesday Week 37](Screenshots/icon_matrix.png)

**Left:** Native Power BI conditional formatting.

**Right:** DAX measure using `SELECTEDVALUE()`, `SWITCH()`, and `UNICHAR()`.

Both approaches produce the same analytical result using different techniques.

---

##  Key Learnings

This challenge helped me explore several useful Power BI concepts:

1. **Matrix Visual:** Understanding how rows, columns, and values work together to create a structured comparison.

2. **Conditional Formatting:** Using rules to dynamically display icons based on categorical values.

3. **DAX Measures:** Understanding how `SELECTEDVALUE()` retrieves the current value in a visual's filter context.

4. **SWITCH Function:** Applying conditional logic to return different outputs based on a given value.

5. **UNICHAR Function:** Converting Unicode character codes into visual symbols.

6. **Visual Storytelling:** Replacing repetitive text with meaningful icons to improve readability and reduce visual clutter.

7. **Multiple Approaches:** Learning that the same business requirement can be achieved using native Power BI features or DAX.

---

##  My Biggest Takeaway

Initially, I thought this was simply about replacing Yes, Maybe, and No with icons.

But I wanted to experiment further:

**Can I solve the same problem using two different approaches?**

That curiosity made this challenge more interesting.

The native approach helped me understand Power BI's built-in capabilities, while the DAX approach helped me understand how measures can dynamically return values based on filter context.

It reminded me that learning Power BI isn't just about completing a challenge. It's about experimenting, exploring alternatives, and discovering different ways to communicate information.

Sometimes, data storytelling can even begin with a bowl of guacamole! 🥑

---

##  Credits

A big thank you to **Laxmi Ponnusuran** for creating these creative and engaging Workout Wednesday challenges.

Challenges like these encourage me to think beyond the obvious solution, experiment with Power BI features, and continuously improve my data visualization skills.

---

##  Tools & Technologies

- Power BI Desktop
- DAX
- Matrix Visual
- Conditional Formatting
- Unicode Characters

## Challenge Details

| Detail | Information |
|---|---|
| Challenge | Workout Wednesday |
| Year | 2026 |
| Week | Week 37 |
| Theme | National Guacamole Day |
| Main Concept | Icon Matrix |
| Approaches | Native Feature & DAX Measure |
| Tool | Power BI Desktop |

---

**Happy Learning! **
