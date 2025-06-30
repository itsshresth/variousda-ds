# Indian YouTube Trending Videos: A Data-Driven Exploration

> "What makes a video go viral in India? Let's decode the trends, categories, and patterns behind the magic."

---

## Abstract

This project analyzes the Top 200 trending YouTube videos in India, retrieved live via the YouTube Data API. We perform structured pre-processing, insightful feature engineering, and visual analytics to uncover:

- Power-law distribution in engagement
- Music & Entertainment as the most viral categories
- Concise content (< 10 min) winning the attention war
- Tag count not significantly influencing viewership

Everything is modular, reproducible, and ready for plug-and-play reruns.

---

## Table of Contents

1. [Dataset & Collection Protocol](#1-dataset--collection-protocol)
2. [Analytical Methodology](#2-analytical-methodology)
    - 2.1 [Pre-processing](#21-pre-processing)
    - 2.2 [Feature Engineering](#22-feature-engineering)
    - 2.3 [Visual Analytics Pipeline](#23-visual-analytics-pipeline)
3. [Results & Discussion](#3-results--discussion)
4. [Key Takeaways](#4-key-takeaways)
5. [Project Structure & Reproducibility](#5-project-structure--reproducibility)
6. [Dependencies](#dependencies)
7. [License](#license)
8. [Contributing](#contributing)

---

## 1. Dataset & Collection Protocol

| Parameter        | Details |
|------------------|---------|
| Source           | YouTube Data API (`mostPopular` endpoint) |
| Region           | `IN` (India) |
| Sample Size      | 200 videos |
| Fields           | ID, Title, Description, Category, Stats, Tags, Duration, PublishedAt |
| Storage          | `trending_videos.csv` (~2 MB, UTF-8) |
| Quota Use        | ≤ 10,000 units/day, compliant with API TOS |

---

## 2. Analytical Methodology

### 2.1 Pre-processing

- Convert `publishedAt` to datetime format
- Parse ISO-8601 video durations to seconds
- Rescale:
    - `views`, `likes` → Lakhs
    - `comments` → Thousands
- Handle missing values:
    - Tags → empty lists
    - Numeric NaNs → zeroes

### 2.2 Feature Engineering

| Feature               | Definition                         | Purpose |
|-----------------------|-------------------------------------|---------|
| `view_count_lakhs`    | Views ÷ 1e5                         | Cultural relevance |
| `like_count_lakhs`    | Likes ÷ 1e5                         | — |
| `comment_count_k`     | Comments ÷ 1e3                      | — |
| `duration_seconds`    | Parsed video duration               | Continuous metric |
| `duration_range`      | Binned (0–5, 5–10, 10–20, etc.)     | Non-linear effects |
| `tag_count`           | Length of tag list                 | Metadata richness |
| `publish_hour`        | Local hour (0–23)                  | Circadian behavior |

### 2.3 Visual Analytics Pipeline

- Histograms: Views, Likes, Comments
- Correlation heatmap: Engagement metrics
- Category frequency and average engagement bar plots
- Duration vs Engagement bar chart
- Scatterplots:
    - Duration vs Views
    - Tag Count vs Views
    - Publish Hour vs Views
- Publish Hour frequency plot
- Optional Seaborn pairplot

---

## 3. Results & Discussion

### 3.1 Engagement Distributions
- Strong right skew
- 80% of videos have fewer than 30 lakh views, while a few exceed 200 lakh
- Confirms power-law distribution in virality

### 3.2 Cross-Metric Correlations
- Pearson coefficients > 0.85 between views, likes, and comments
- Indicates high correlation across engagement metrics

### 3.3 Category-Level Insights
| Category        | Avg Views (Lakhs) | Highlights |
|------------------|--------------------|------------|
| Music            | ~55L               | Most dominant category |
| Entertainment    | ~52L               | High engagement |
| News             | ~18L               | Short shelf-life content |

### 3.4 Duration Effects
| Duration Bin (min) | Avg Views (Lakhs) |
|---------------------|--------------------|
| 0–5                | ~60                |
| 5–10               | ~45                |
| 10–20              | ~30                |

Shorter videos receive higher average view counts.

### 3.5 Metadata Factors
- Tags: Very low correlation with viewership
- Publish Hour: Slight clustering around 12–15 IST, but no significant predictive value

---

## 4. Key Takeaways

- Viral engagement follows a power-law distribution
- Music and Entertainment dominate trending content
- Videos under 10 minutes achieve higher average views
- Tag quantity offers limited value; relevance is more important
- Upload timing has minimal impact compared to content quality

---

## 5. Project Structure & Reproducibility

```
variousda-ds/
├── finalyt.ipynb          # Full analysis notebook
├── trending_videos.csv    # Raw snapshot data
├── README.md              
```

### Quick Start

1. Insert your API key in the notebook configuration
2. Run all cells: Runtime → Run All
3. Automatically downloads and visualizes updated data

Compatible with Google Colab and local Jupyter environments

---

## Dependencies

```txt
pandas>=1.3.0
matplotlib>=3.5.0
seaborn>=0.11.0
google-api-python-client>=2.0.0
isodate>=0.6.0
```

---

## License

This project is licensed under the MIT License.

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss the proposed modifications.

---

Built and maintained with a commitment to research-driven analytics.

