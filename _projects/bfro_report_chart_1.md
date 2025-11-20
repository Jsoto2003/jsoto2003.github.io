---
layout: post
title: "Assignment 5 - BFRO Bigfoot Reports"
---

<p>
  <a class="btn" href="https://github.com/jsoto2003/jsoto2003.github.io/blob/main/Week12/bfro_reports_fall2022.csv">Dataset</a>
  <a class="btn" href="https://github.com/jsoto2003/jsoto2003.github.io/blob/main/Week12/Assignment5.ipynb">Data and Chart Analysis</a>
</p>

<h2>Plot 1: Yearly trend of BFRO reports by season</h2>

<iframe
  src="{{ '/Week12/chart1_bfro_year_season.html' | relative_url }}"
  width="100%"
  height="420"
  style="border:none;"
></iframe>

<p>
  The first visualization shows how reported Bigfoot sightings from the BFRO dataset change over time, broken down by season. Each point represents the number of reports recorded in a given year, and the connected lines help highlight trends from 1869 through 2018. The x-axis encodes the year as an ordinal value, the y-axis encodes the count of reports, and color encodes the season of the sighting (Winter, Spring, Summer, and Fall). I used a line mark with points so individual years remain readable while still emphasizing the overall trajectory of the data. On the analysis side, I converted the original date column into a Pandas datetime type, extracted a new year column, and dropped rows with missing dates so the aggregation by year would be correct. This plot makes it easy to see that reports are generally more common in the summer and fall than in the winter, and that reported sightings tend to increase in later decades compared to the early part of the time series.
</p>

<h2>Plot 2: Seasonal distribution of BFRO reports by state (interactive)</h2>

<iframe
  src="{{ '/Week12/chart2_bfro_season_state.html' | relative_url }}"
  width="100%"
  height="380"
  style="border:none;"
></iframe>

<p>
  The second visualization focuses on the seasonal pattern of Bigfoot reports within a single state at a time. It uses a bar chart where the x-axis encodes the season of the report, the y-axis encodes the count of reports, and color also represents season to reinforce the categorical grouping. To build this chart, I again converted the original date column into a datetime object and reused the year and season fields, but here the data are aggregated by both state and season. I filtered out rows without a state to keep the dropdown options clean. This chart is powered by an Altair <code>selection_point</code> parameter that is bound to a dropdown list of states. When a user chooses a state from the dropdown, the chart automatically filters to show the distribution of reports across seasons in that specific location. This interaction helps make the seasonal patterns easier to compare across states without cluttering the view with dozens of overlapping bars or facets.
</p>

<p>
  For interactivity, I chose a dropdown widget that lets the user choose a state and see its seasonal breakdown. The <code>selection_point</code> parameter is bound to a select input so the current state value can be used as a filter in the chart via <code>transform_filter()</code>. This makes the visualization more readable than a static version, because the user can quickly flip through different states to compare their seasonal distributions instead of trying to interpret a single dense figure that shows all states at once.
</p>
