# Board Games Analytics Dashboard

A Power BI dashboard designed to visualize and analyze board game data sourced from Kaggle.

* **Dataset Source:** [Kaggle - Board Games Dataset](https://www.kaggle.com/datasets/melissamonfared/board-games)

---

## Report Structure

The report is divided into three analytical pages:

### 1. Overview
* **Top Games:** Highlights the leading games ranked by popularity and average rating.
* **Rating Distribution:** Displays the overall spread and frequency of game ratings.
* **Type Distribution:** Visualizes the breakdown and share of games across different domains/types.

### 2. Rating Breakdown
* Deep-dive analysis examining relationships and correlations between key variables:
  * User rating scores vs. number of users scored.
  * Rating trends across years of publishing.
  * Rating patterns relative to game ownership numbers.

### 3. Recommendations
* An interactive recommendation engine equipped with multiple slicers.
* Dynamically filters and displays the **Top 10 Games** based on:
  * Highest rating
  * Ownership volume
  * Highest complexity
  * Lowest complexity

---

## Data Modeling & ETL Process

### Data Cleaning & Preparation
* Adjusted column data types across all fields.
* Removed empty and null values to ensure reporting integrity.
* Grouped continuous numeric metrics (user ratings and number of ratings) into **bins** to support distribution and correlation charts.

### Star Schema Architecture
The raw dataset was split into three distinct tables linked through a star schema:

1. **Board Games Table (Main / Fact):** Contains core game metrics, scores, ownership counts, complexity levels, and release metadata.
2. **Domains Table (Bridge / Dimension):** Stores game domains/types. Connected via a **$1:\text{Many}$ ($1:*$) relationship** to the Board Games table to accommodate games associated with multiple domains.
3. **Mechanics Table (Bridge / Dimension):** Stores gameplay mechanics. Connected via a **$1:\text{Many}$ ($1:*$) relationship** to the Board Games table to support games utilizing multiple mechanics.

---

## Interactivity & Features

* **Slicers:** Configured across pages to enable granular filtering by domain, mechanics, year, and metrics.
* **Custom Visual Interactions:** Visual interaction settings were modified to ensure slicers and charts cross-filter related visuals effectively without unintentional cross-highlighting issues.