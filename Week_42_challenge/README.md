# WOW Challenge – Week 42: Overlay Information With Bookmarks

##  Challenge Overview

This challenge explores how to use **Bookmarks, Buttons, and the Selection Pane** in Power BI to create interactive report experiences.

The objective is to switch between Team Standings and Driver Standings using bookmarks, highlight the fastest lap for each race, and provide additional information through an overlay.

The challenge demonstrates how bookmarks can improve dashboard navigation and user experience without creating multiple report pages.

##  Dataset

Formula 1 Standings Dataset

- Source: Workout Wednesday
- Challenge: 2026 Week 42
- Challenge by: Vivien Lee
- Main focus: Team Standings, Driver Standings, Fastest Lap, and Race Results.

##  My Approach

1. Explored and understood the racing dataset.
2. Created a measure to identify and highlight the fastest lap for each race.
3. Built a table visual displaying race results.
4. Added a Race slicer to filter the results.
5. Created two bump charts:
   - Team Standings
   - Driver Standings
6. Positioned both charts in the same location.
7. Used the Selection Pane to control chart visibility.
8. Created Team View and Driver View bookmarks.
9. Connected buttons to bookmarks to switch between the two charts.
10. Tested bookmark interactions to ensure the Race slicer selection was preserved.

##  Dashboard Preview

![WOW Week 42 - Overlay Information With Bookmarks](Screenshot/bookmark.png)

##  DAX Measures

### 1. Fastest Lap Per Race

```dax
Fastest Lap per Race =

VAR _CurrentRace =
    SELECTEDVALUE(Standings[Fastest Lap (minutes)])

VAR _FastestLapThisRace =
    CALCULATE(
        MIN(Standings[Fastest Lap (minutes)]),
        ALLEXCEPT(
            Standings,
            Standings[Race]
        )
    )

RETURN
    IF(
        _CurrentRace = _FastestLapThisRace,
        "#8D2E46",
        "#2D303A"
    )
