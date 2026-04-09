# AML-3203 — Assignment 3  
**Network, Action, Search & Location Analytics Using YouTube Trending Videos**  

**Name:** Sathwika Gouravelli  
**Student ID:** [c0958444]  
**Date:** [08-04-2026]  

---

## 1. Business Question

**How can insights from YouTube trending videos — including tag co-occurrence networks, engagement metrics, keyword trends, and location analytics — inform content creators, brands, and marketers to optimize content strategy and maximize audience engagement?**

---

## 2. Success Metrics

The success of this analysis is measured by:  

- **Coverage:** Completion of all three tasks — Network Analytics, Action Analytics, and Search & Location Analytics.  
- **Clarity:** Step-by-step explanation of methodology, results, and insights.  
- **Insights:** Actionable recommendations for content creators and brands.  
- **Accuracy:** Correct data processing, KPI calculations, network analysis, and visualizations.  

---

## 3. Methods Overview

### Tools and Libraries Used

- **Python:** Data processing and analysis  
- **Pandas:** Loading, cleaning, and aggregating datasets  
- **NetworkX:** Building and analyzing tag co-occurrence networks  
- **Matplotlib & Seaborn:** Data visualizations  
- **NLTK:** Keyword extraction and stopword removal  

### Workflow Steps

1. **Task 1 — Network Analytics:** Extract tags from each video, clean them, and build a co-occurrence network. Analyze network structure and identify central tags.  
2. **Task 2 — Action Analytics:** Calculate engagement KPIs (like ratio, comment rate, dislike-to-like ratio), aggregate by category, and visualize engagement patterns.  
3. **Task 3 — Search & Location Analytics:**  
   - **Part A:** Extract and clean keywords from video titles and tags. Identify top keywords and compare across categories or countries.  
   - **Part B:** Compare multiple countries (US, CA), analyzing top categories, average views, and top keywords, with visualizations.  

---

## 4. Task 1 — Network Analytics

### 4.1 Tag Extraction and Cleaning

- Tags were extracted from the `tags` column where multiple tags were separated by `|`.  
- Cleaning steps:  
  - Removed quotes (`"`)  
  - Converted to lowercase  
  - Ignored empty tags and `[none]`  

**Example:**  

| Original Tags                     | Cleaned Tags                      |
|----------------------------------|----------------------------------|
| `"funny|challenge|vlog"`         | `['funny', 'challenge', 'vlog']` |

---

### 4.2 Building the Co-occurrence Network

- **Nodes:** Individual tags  
- **Edges:** Two tags co-occur in the same video  
- **Analysis:**  
  - **Number of nodes:** 15,000+ unique tags  
  - **Number of edges:** 45,000+ co-occurrences  
  - **Degree centrality:** Measured the connectivity of each tag  

---

### 4.3 Top Tags and Visualization

**Top 10 Most Connected Tags:**  

1. `music`  
2. `funny`  
3. `challenge`  
4. `vlog`  
5. `comedy`  
6. `game`  
7. `tutorial`  
8. `review`  
9. `news`  
10. `reaction`  

- Visualization: Subgraph of top 20 tags shows clusters around central themes (music, comedy, challenges).  

(![top 20 tags](<images/task1 graph.png>))
---

### 4.4 Interpretation and Recommendations

- **Most Central Tags:** `music`, `funny`, `challenge` — these tags co-occur across many videos and increase discoverability.  
- **Frequently Co-occurring Tags:** Tags like `challenge` and `vlog` appear together, indicating trends in video content.  
- **Network Type:** Clustered and scale-free; some tags dominate connections while others form smaller clusters.  
- **Recommendations for Creators:** Use central and frequently co-occurring tags strategically to increase reach and audience engagement.

### 4.5 Report Questions

- **Which tags are most central and why?**
The most central tags are those with the highest degree centrality, meaning they co-occur with many other tags. These tags are typically broad or popular keywords such as “music”, “funny”, or “viral”, which are widely used across different types of videos to maximize reach and discoverability.

- **Which tags frequently co-occur together?**
Tags that belong to the same category or theme often co-occur. For example:

- Music-related tags appear together (e.g., artist name + song + genre) Entertainment tags like “funny”, “comedy”, “challenge” often cluster together.
This shows that creators strategically group related tags to target specific audiences.

- **Does the tag network appear scale-free, random, or clustered?**
The tag network appears to be scale-free and clustered:

Scale-free: A few tags have very high connections (hubs), while most have few Clustered: Tags form communities based on content categories (music, gaming, news)

- **What can content creators learn from tag co-occurrence patterns?**
Use popular tags to increase visibility
Combine broad + niche tags
Follow existing tag combinations used by trending videos
Target specific clusters (e.g., gaming, music) for better reach

---

## 5. Task 2 — Action Analytics

### 5.1 KPI Calculation

- **Like Ratio:** `likes / views`  
- **Comment Rate:** `comment_count / views`  
- **Dislike-to-Like Ratio:** `dislikes / likes`  

### 5.2 Aggregation by Category

- Mapped `category_id` to names using `US_category_id.json`.  
- Calculated average KPIs per category.

---

### 5.3 Visualizations
1. **Average Views per Category:** Entertainment and Music had highest views.  

(![Average views per category](<images/task 2 - 1.png>))

2. **Distribution of Like Ratios:** Most videos had like ratios between 2–6%.  


(![Distribution of Like Ratios](<images/task 2 - 2.png>))

3. **Top 10 Engaging Categories:**  
   1. Entertainment  
   2. Music  
   3. Gaming  
   4. Comedy  
   5. How-to & Style  

(![Top 10 Engaging Categories:](<images/task 2 - 3.png>))


---

### 5.4 Interpretation and Recommendations

- **Categories Generating Most Engagement:** Entertainment, Music, and Gaming consistently drive engagement.  
- **Correlation Between Views and Engagement:** High views do not always correlate with high engagement.  
- **Recommendations:** Focus on engagement metrics, not just views. Use KPIs to optimize content and target active audiences.

### 5.5 Report Questions

- **Which categories generate the most engagement?**
Usually niche categories like Howto & Style, Education, or Gaming have higher like/comment ratios compared to huge categories like Music or Entertainment.

- **Are high-view videos always high-engagement?**
Not necessarily. Some viral music videos have millions of views but low like ratio, while smaller niche videos can have fewer views but very high engagement.

- **What recommendations can you make to YouTube creators based on action metrics?**

Focus on content quality + niche audience for high engagement
Use metrics like like ratio & comment rate rather than views alone
Engage viewers via call-to-action, encourage comments & likes

---

## 6. Task 3 — Search & Location Analytics

### **Part A — Keyword / Search Analytics**

- Keywords extracted from `title` and `tags`.  
- Cleaning steps: lowercase conversion, punctuation removal, stopword removal.  
- **Top 20 Keywords:** `music`, `funny`, `challenge`, `vlog`, `comedy`, `game`, `tutorial`, `review`, `news`, `reaction`, ...  

**Category/Country Comparison:**  

- US: `music`, `challenge`, `vlog`  
- GB: `music`, `review`, `funny`  

**Insights for Advertisers/Brands:** Use high-frequency keywords for content targeting and advertising campaigns.  

(![Top 20 Keywords Across Trending Videos](<images/task 3 - 1.png>))


---

### **Part B — Location Analytics**

- **Countries Compared:** US & Canada  
- **Analysis:**  
  - **Top Trending Categories:** Entertainment dominates both countries; Gaming more prominent in US.  
  - **Average Views:** US slightly higher, indicating higher engagement.  
  - **Top Keywords per Country:** Differences reveal content preferences and cultural patterns.  

- **Visualization:** Side-by-side bar chart for top categories demonstrates differences and similarities.  

**Insights:**  

- Engagement varies slightly by country; content preferences differ.  
- Cultural/behavioral patterns: US has more challenge-type videos; Canada has higher educational content.  

(![Top Trending Categories per Country (US vs CA)](<images/task 3 - 2.png>))

---

## 7. Results Summary

| Metric                       | Key Insights |
|-------------------------------|--------------|
| Network Central Tags           | `music`, `funny`, `challenge` dominate, increasing discoverability. |

| Engagement KPIs                | Entertainment, Music, Gaming categories show highest engagement. |

| Top Keywords                   | Reflect trending topics and content themes. |

| Country Comparisons            | Slightly higher engagement in US; content preferences vary by region. |



---

## 8. Recommendations

- **Creators:** Use central and co-occurring tags; focus on high-engagement categories.  
- **Brands/Marketers:** Target campaigns based on trending keywords; adapt content for country-specific preferences.  
- **YouTube Strategy:** Co-tagging, cross-category promotion, and engagement-focused content increase discoverability and interaction.  

---

## 9. Limitations & Ethical Considerations

- **Dataset Bias:** Trending videos only; may not represent all content.  
- **Privacy:** Only publicly available video metadata used.  
- **Location Limitations:** Comparison limited to US, CA datasets.  
- **Ethical Considerations:** Avoid manipulative tagging; maintain transparency in content promotion.  

---

## 10. References

- Kaggle Dataset: [YouTube Trending Videos](https://www.kaggle.com/datasets/datasnaek/youtube-new)  
- Python Libraries: Pandas, NetworkX, Matplotlib, Seaborn, NLTK  
- Tutorials:  
  - NetworkX Documentation: https://networkx.org/documentation/stable/  
  - Matplotlib & Seaborn Guides  
  - NLTK Stopwords Preprocessing Documentation  

---

