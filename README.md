# **AML-3203 — Assignment 3**

## **Network, Action, Search & Location Analytics Using YouTube Trending Videos**

### **Dataset:** YouTube Trending Videos (Kaggle)

Download link: https://www.kaggle.com/datasets/datasnaek/youtube-new

---

## **What to Submit**

### **1. Report**

Submit a written report in one of the following formats:

- **Markdown (`.md`) — recommended**
- PDF
- Word Document

### **2. Jupyter Notebook**

Submit a single notebook named:

```
A3_<lastname_firstname>.ipynb
```

Your notebook must run **top-to-bottom with no errors**.

---

# **Assignment Objective**

In this assignment, you will apply three major components of Social Media Analytics:

1. **Network Analytics**
2. **Action Analytics**
3. **Search & Location Analytics**

---

# **Task 1 — Network Analytics**

## Goal

Build and analyze a **Tag Co-occurrence Network** using YouTube trending video tags.

## Instructions

1. Download and load **one country dataset**, such as `USvideos.csv`.
2. Extract tags from each row.
   - Tags appear as:
     ```
     "tag1|tag2|tag3"
     ```
3. Build a **co-occurrence network**:
   - **Nodes** = tags
   - **Edges** = two tags appear together in the same video
4. Using NetworkX or any other suitable graph library, compute:
   - Number of nodes
   - Number of edges
   - Degree centrality
   - Top 10 most connected tags
5. Visualize one of the following:
   - Entire tag network (if small), or
   - Subgraph of top 20 most common tags

## Questions for Your Report

- Which tags are the most central and why?
- Which tags frequently co-occur together?
- Does the tag network appear **scale-free**, **random**, or **clustered**?
- What can content creators learn from tag co-occurrence patterns?

---

# **Task 2 — Action Analytics**

## Goal

Analyze user engagement based on likes, views, comments, and categories.

## Instructions

1. Create **at least three engagement KPIs**, such as:
   - **Like ratio**: `likes / views`
   - **Comment rate**: `comment_count / views`
   - **Dislike-to-like ratio**: `dislikes / likes`
2. Aggregate KPIs by **video category**.
   - Use `US_category_id.json` to map category IDs to names.
3. Generate at least **three visualizations**:
   - Average views per category
   - Distribution of like ratios
   - Top 10 most engaging categories

## Questions for Your Report

- Which categories generate the most engagement?
- Are high-view videos always high-engagement? Explain with data.
- What recommendations can you make to YouTube creators based on action metrics?

---

# **Task 3 — Search & Location Analytics**

## Goal

Analyze trending **keywords** and compare YouTube trends across countries.

Use two or more country datasets (e.g., US, GB, CA).

---

## **Part A — Keyword / Search Analytics**

### Instructions

1. Extract keywords from:
   - Video `title`
   - Video `tags`
2. Clean keywords:
   - Lowercase
   - Remove stopwords
   - Remove punctuation
3. Identify the **top 20 keywords** across trending videos.
4. Compare keyword usage across:
   - categories OR
   - countries

### Questions for Your Report

- What are the most common keywords in trending videos?
- Do some keywords appear more often in certain categories?
- What insights can advertisers or brands gain from keyword trends?

---

## **Part B — Location Analytics**

### Instructions

1. Load at least **two country files** (e.g., USvideos.csv & CAvideos.csv).
2. Compare:
   - Top trending categories per country
   - Average views per country
   - Top keywords per country
3. Produce at least **one visualization**, such as:
   - Side-by-side bar charts
   - Grouped bar charts

### Questions for Your Report

- Which country shows higher engagement levels?
- Do content preferences differ by country?
- What cultural or behavioral patterns appear across regions?

---

# **Report Structure**

Your report must follow the structure below:

1. **Title Page**
   - Assignment number
   - Your name
   - Your ID

2. **Business Question**
   - One clear question that ties the assignment together

3. **Success Metrics**
   - Define how success will be measured (e.g., coverage, clarity, insights)

4. **Methods Overview**
   - Briefly describe how each task was approached
   - Tools used (e.g., NetworkX, Pandas, Matplotlib)

5. **Results**
   - Include visualizations
   - Provide concise explanations

6. **Recommendations**
   - Explain how insights can help brands, creators, or marketers

7. **Limitations & Ethical Considerations**
   - Dataset bias
   - Location limitations
   - Privacy concerns

8. **References**

---

# **Rubric (100%)**

### **1. Problem Framing — 5%**

- Clear business question
- Defined success metrics

### **2. Task 1: Network Analytics — 25%**

- Correct tag network construction
- Centrality analysis
- Visualization quality
- Insightfulness

### **3. Task 2: Action Analytics — 25%**

- Correct KPI definitions
- Accurate computations
- Visualizations (min 3)
- Strong insights

### **4. Task 3: Search & Location Analytics — 25%**

- Keyword extraction
- Country/category comparisons
- Visualizations (min 1)
- Strong insights

### **5. Communication, Presentation & Notebook Quality — 20%**

- Clean and organized notebook
- Clear explanation in the report and presentation
- Labeled figures
- Reproducible workflow

---
