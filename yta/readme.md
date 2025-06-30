Indian YouTube Trending Videos: A Data-Driven Exploration

Abstract
This study dissects the top-200 trending YouTube videos in India by harvesting live data from the YouTube Data API. Through rigorous cleaning, feature engineering, and exploratory data analysis (EDA), we illuminate the statistical signatures of viral content. Principal findings reveal (i) power-law engagement with heavy right skew, (ii) Music and Entertainment as dominant categories for both frequency and average engagement, (iii) a measurable preference for concise videos (< 10 min), and (iv) weak influence of tag count on viewership. All code is modular, reproducible, and configured for rapid re-runs with new API keys or regions.

Table of Contents
Dataset & Collection Protocol

Analytical Methodology

2.1 Pre-processing

2.2 Feature Engineering

2.3 Visual Analytics Pipeline

Results & Discussion

3.1 Engagement Distributions

3.2 Cross-Metric Correlations

3.3 Category-Level Insights

3.4 Duration Effects

3.5 Metadata Factors (Tags & Timing)

Key Take-aways

Project Structure & Reproducibility

Possible Extensions

References

1. Dataset & Collection Protocol
Source: YouTube Data API "mostPopular" endpoint

Scope: 200 videos, regionCode='IN', collected in a single snapshot

Fields: Video/Channel identifiers, title, description, publishedAt, statistics (views, likes, comments), content details (ISO-8601 duration), tags, and category IDs

Storage: Raw JSON to trending_videos.csv (UTF-8, ~2 MB)

Ethics & Quotas: Adheres to Google API TOS; ≤ 10,000 units per day

2. Analytical Methodology
2.1 Pre-processing
Convert publishedAt to datetime; parse durations via isodate

Numeric Rescaling:

Views & likes → Lakhs (100,000)

Comments → Thousands

Missing values: list-type fields (tags) default to empty lists; numeric NaNs coerced to zeros

2.2 Feature Engineering
Feature	Definition	Rationale
view_count_lakhs	views / 1e5	Culturally relevant magnitude
like_count_lakhs	likes / 1e5	—
comment_count_k	comments / 1e3	—
duration_seconds	ISO-8601 → seconds	Enables continuous analysis
duration_range	Bins: 0–5, 5–10, 10–20, 20–60, 60–120 min	Non-linear length effects
tag_count	len(tags)	Metadata richness
publish_hour	Local hour (0–23)	Circadian audience patterns
2.3 Visual Analytics Pipeline
The notebook renders ten core plots:

Histograms of views, likes, comments (lakhs/thousands)

Correlation heat-map (views ↔ likes ↔ comments)

Category bar-count (frequency)

Category engagement bars (mean views/likes/comments)

Duration-range engagement bars

Scatter: duration (s) vs views (lakhs)

Scatter: tag_count vs views

Scatter: publish_hour vs views (lakhs)

Publish-hour count plot (frequency)

Optional seaborn pair-plot of three engagement metrics

3. Results & Discussion
3.1 Engagement Distributions
The histograms are strongly right-skewed; about 80% of videos sit below 30 L views, yet a handful exceed 200 L. This conforms to a power-law popularity curve common on social platforms. Likes and comments echo the pattern, affirming that viral visibility concentrates engagement.

3.2 Cross-Metric Correlations
Pearson coefficients exceed 0.85 across views–likes–comments, underscoring coupled audience reactions—videos that attract eyeballs reliably garner proportional likes and discourse.

3.3 Category-Level Insights
Music and Entertainment account for nearly half the trending list and lead all categories in average views (≈ 55 L) and likes (≈ 3 L)

News & Politics trend less frequently and with lower median engagement, perhaps reflecting shorter shelf-life content

Category skew mirrors prior cross-country studies, strengthening external validity

3.4 Duration Effects
0–5 min videos outperform all other bins with ≈ 60 L mean views, suggesting snack-able content drives virality

Engagement declines monotonically beyond 10 min, aligning with viewer watch-time fatigue reported in platform white-papers

3.5 Metadata Factors
Tags: Scatterplots show diffuse clouds with a near-zero slope—tag proliferation alone does not predict views. Creators should focus on relevance, not sheer quantity.

Publish Hour: Trending uploads scatter across the clock; mild clustering at 12:00–15:00 IST hints at afternoon traction, but the effect lacks statistical heft. This corroborates anecdotal claims that content quality outweighs timing once a video lands on the trending list.

4. Key Take-aways
Virality is unequal—a minority of videos reap disproportionate engagement

Content vertical matters: Music and Entertainment dominate

Concise videos (< 10 min) maximize average views

Metadata quantity (tags) offers limited lift; strategic relevance is preferable

Upload timing is secondary; quality and audience fit prevail

5. Project Structure & Reproducibility
text
variousda-ds/
├── finalyt.ipynb          # Full analysis notebook
├── trending_videos.csv    # Raw API pull (example snapshot)
├── imgs/                  # Auto-saved PNGs from notebook
├── README.md              # *You are here*
└── requirements.txt       # pandas, seaborn, matplotlib, google-api-python-client, isodate
Quick Start
One-click Re-run:

Add your YouTube API key in the config cell

Execute all cells (Runtime → Run all)

Plots regenerate and CSV refreshes

Environment: Python 3.10; tested on Google Colab & local Jupyter Lab

Dependencies
text
pandas>=1.3.0
matplotlib>=3.5.0
seaborn>=0.11.0
google-api-python-client>=2.0.0
isodate>=0.6.0

License
This project is open source and available under the MIT License.

Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
