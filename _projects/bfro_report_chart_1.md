---
name: Assignment 5 – BFRO Bigfoot Reports
tools: [Python, Altair, HTML, vega-lite]
image: Week12/chart1_bfro_year_season.png
description: Two data visualizations of BFRO Bigfoot sighting reports using Python, Altair, vega-lite, and Jekyll.
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

# Assignment 5 – BFRO Bigfoot Reports

This project uses the **BFRO Bigfoot sightings dataset** and creates two visualizations using Python, pandas, Altair, and vega-lite. One chart shows yearly seasonal trends, and the other uses interactive filtering to explore seasonal patterns by U.S. state. Both charts were exported as HTML and embedded into this Jekyll webpage.

---

# The Visualizations

## **Plot 1 – Yearly Trend of BFRO Reports by Season**

Below is the first exported Altair chart, embedded directly into the page using an HTML `<iframe>`:

<vegachart
  schema-url="{{ site.baseurl }} '/assets/json/bfro_year_season.json'"
  style="width: 100%">
</vegachart>

### **Explanation**

The first visualization shows how reported Bigfoot sightings from the BFRO dataset change over time, broken down by season. Each point represents the number of reports recorded in a given year, and the connected lines help highlight trends from 1869 through 2018.  
The x-axis encodes the year as an ordinal value, the y-axis encodes the count of reports, and color encodes the season of the sighting (Winter, Spring, Summer, and Fall).  

A line mark with points was chosen so individual years remain readable while still emphasizing long-term trends.  
On the analysis side, the original `date` column was converted into a Pandas `datetime` type, a new `year` column was extracted, and rows with invalid dates were dropped to ensure accurate aggregations.

This plot makes it easy to see that reports are typically more common in the summer and fall, and that overall reporting levels increase in later decades compared to earlier years.

---

## **Plot 2 – Seasonal Distribution of BFRO Reports by State (Interactive)**

This second Altair chart uses a **dropdown selector** to filter the distribution of sightings by state:

<vegachart
  schema-url="{{ site.baseurl }} '/assets/json/bfro_season_state.json'"
  style="width: 100%">
</vegachart>

### **Explanation**

The second visualization focuses on the seasonal pattern of Bigfoot reports within a single state. It uses a bar chart where the x-axis encodes the season, the y-axis encodes the count of reports, and color reinforces the seasonal categories.

In the preprocessing stage, the `date` column was again converted into a datetime object, and the derived `year` and `season` fields were reused. Rows with missing states were removed to keep the dropdown clean.

For interactivity, an Altair **`selection_point`** parameter was bound to a dropdown menu of U.S. states. When the viewer selects a state, the chart automatically updates using `transform_filter()` to display the seasonal distribution for that specific location.

This interaction makes the visualization clearer and more useful, allowing users to compare patterns across states without needing overlapping bars or multiple facets.

---

# Search the Data & Methods

You can access the dataset and the analysis notebook used to generate these visualizations using the buttons below.

<div class="left">
{% include elements/button.html link="https://github.com/jsoto2003/jsoto2003.github.io/blob/main/Week12/bfro_reports_fall2022.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/jsoto2003/jsoto2003.github.io/blob/main/Week12/Assignment5.ipynb" text="The Analysis" %}
</div>

<br><br>

---

# Files Used

- **Dataset:** `bfro_reports_fall2022.csv`
- **Notebook:** `Assignment5.ipynb`
- **Exported Charts:**  
  - `chart1_bfro_year_season.html`  
  - `chart2_bfro_season_state.html`

This assignment integrates Python data processing, Altair chart creation, interactivity via vega-lite, and full deployment on a Jekyll website hosted through GitHub Pages.
