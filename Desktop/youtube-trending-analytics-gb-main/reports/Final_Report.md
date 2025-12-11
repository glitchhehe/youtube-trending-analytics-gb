# 📊 YouTube Trending Video Analyzer + Channel Insights Toolkit (GB) Project Report

This report summarizes the objectives, methodology, and key findings of the "YouTube Trending Video Analyzer + Channel Insights Toolkit (GB)" Jupyter Notebook.

---

## 🚀 Project Overview

**Objective:** To clean, preprocess, analyze, and visualize data from trending YouTube videos in the United Kingdom (`GBvideos.csv`) to identify key trends, top-performing channels, and features associated with high performance.

**Dataset:** `GBvideos.csv` (YouTube Trending Videos - United Kingdom)

**Tools:** Python (Pandas, NumPy, Matplotlib)

---

## 🛠️ Methodology and Code Implementation

### 1. Data Cleaning and Preprocessing

The initial steps focused on preparing the raw dataset for accurate analysis:

* **Data Integrity:** Removed **duplicate rows** and entries where the video was **removed or errored** (`video_error_or_removed == True`).
* **Handling Missing Values:** Missing descriptions were filled, and placeholders (`\N`, `[none]`) in the `tags` column were standardized to `NaN` (Not a Number/Missing).
* **Type Conversion:** Core metrics (`views`, `likes`, `dislikes`, `comment_count`) were converted to **integers** after coercing non-numeric entries to zero.
* **Date/Time Parsing:** The `trending_date` (format `%y.%d.%m`) and `publish_time` strings were converted into usable **datetime objects** to enable time-based analysis.

### 2. Feature Engineering

Several key performance indicators (KPIs) and features were created to extract deeper insights:

* **Time Features:** Extracted **`publish_hour`** (0-23) and **`publish_day`** (e.g., Monday, Friday) from the `publish_time`.
* **Engagement Metrics:**
    * **`engagement`:** Calculated as the ratio of $(\text{likes} + \text{comment\_count}) / \text{views}$. This measures viewer interaction relative to viewership.
    * **`like_ratio`:** Calculated as $\frac{\text{likes}}{\text{likes} + \text{dislikes}}$ (measures audience approval).
* **Content Features:** Calculated **`title_length`** (in words) and **`description_length`** (in characters).
* **Speed to Trend:** Calculated **`days_to_trend`** by finding the difference in days between the `trending_date` and the `publish_date`.

---

## 📈 Key Findings and Visualizations

The analysis identified several patterns in the UK trending data:

### Channel Performance

* **Top Trending Channels:** The most frequently featured channels in the trending list are primarily **US-based late-night talk shows** and **major entertainment brands**.
    * Top 5: The Tonight Show Starring Jimmy Fallon (206), TheEllenShow (205), Jimmy Kimmel Live (204), Saturday Night Live (203), and WWE (202). * **Most Viewed Videos:** The highest-viewed videos generally reflect viral, mainstream media, and music content.

### Behavioral Insights

* **Views vs. Likes:** The scatter plot showed a **strong positive correlation** between the number of views and the number of likes (correlation coefficient $\approx 0.80$), indicating that as a video gains views, it typically gains likes proportionally. * **Engagement:** The average engagement rate across the dataset is approximately **3.8%** ($\approx 0.038$), with a small number of videos achieving significantly higher rates (max $\approx 0.33$).
* **Publishing Time:**
    * The **best average views** were achieved by videos published in the **early morning hours** (e.g., **5 AM** and **4 AM**), suggesting that videos released just before the UK workday often capture maximum attention early. 
### Content Themes

* **Top Tags:** The most common tags often reflect general themes or highly popular content creators, including terms like 'trailer', 'comedy', and specific creator names. 
---

## 📦 Advanced Insights Toolkit

The notebook includes a custom Python class, `YouTubeAnalyzer`, which encapsulates the analysis functions for reusability. Key functions include:

* `top_channels(n)` and `top_videos_by_views(n)`
* `most_engaging_videos(n)`: Identifies videos with the best **Engagement Rate**, which often highlights content that sparks a strong reaction, regardless of total views.
* `best_publish_hours(n)`: Analyzes which publish hours yield the highest *average* views.
* `channel_summary(channel)`: Provides comprehensive statistics for a single channel.

---

## ✅ Conclusion and Next Steps

The project successfully cleaned and transformed the raw trending data, providing a robust analysis of high-level trends. The key takeaway is the **strong influence of established entertainment brands** on the trending list and the potential advantage of **early morning publishing** for maximizing view velocity.

Would you like to see a deeper dive into the correlation between specific metrics (e.g., `like_ratio` vs. `engagement`), or a summary of a specific YouTube category?