# Geo-Localisation Coursework (Web Science H)

**Course:** COMPSCI4077 – Web Science (H)  
**Weight:** 20% of Final Mark  
**Score:** 100%  
**Author:** Davit Muradyan  
**Date:** February 2025  

---

## Overview

This project implements a full geo-localisation and newsworthiness analysis pipeline on real Twitter data collected from London.  

The objectives were to:  
1. Organise tweets into 1km x 1km grids and analyse spatial distribution.  
2. Develop and apply a newsworthiness scoring algorithm.  
3. Explore how filtering by newsworthiness affects geo-localisation.  
4. Identify limitations and potential biases in the data.  

---

## Tasks and Approach

### 1. Grid-Based Geo-Organisation

- Processed around **13,000 geo-tagged tweets** from London.  
- Used **Haversine distance** to map tweets into 1km x 1km grids.  
- Computed detailed statistics: total tweets, active grid cells, and distribution measures (mean, median, standard deviation).  
- Produced **heatmaps and histograms** visualising tweet density.  

**Key Findings:**  
- Total tweets processed: **13,192**  
- Active grid cells: **203 / 2832**  
- Most active cell: **4,298 tweets**  
- Mean tweets per grid: **≈65**  
- Highest activity concentrated in **central London**.  

---

### 2. Newsworthiness Scoring Algorithm

- Developed a **likelihood-ratio-based model** using high-quality, low-quality, and background tweet datasets.  
- Each tweet was scored as:  
  \[
  \text{score} = \log_2\left(\frac{1 + \sum S_{HQ}}{1 + \sum S_{LQ}}\right)
  \]
- Implemented tokenisation via **spaCy** for robust linguistic processing.  
- Explored the effect of removing **stopwords** and varying **threshold values** (default = 2.0).  

**Results**

| Category       | % Newsworthy | Avg Score | Min  | Max  |
|----------------|---------------|-----------|------|------|
| High-quality   | 79.49%        | 1.49      | -4.21| 8.23 |
| Low-quality    | 19.78%        | -4.73     | -11.96 | 6.63 |
| Background     | 36.58%        | 0.34      | -8.42 | 6.68 |

The algorithm effectively distinguished meaningful content from low-quality noise.

---

### 3. Applying Newsworthiness to Geo Data

Tweets below the threshold were filtered out and reanalysed spatially.  
This improved the clarity of geographic insights by removing irrelevant data.  

| Metric | Before | After |
|--------|---------|--------|
| Tweets processed | 13,192 | 2,071 |
| Active grid cells | 203 | 143 |
| Max tweets per cell | 4,298 | 269 |
| Mean tweets per cell | 64.99 | 14.48 |

**Observation:**  
After filtering, activity became more focused on key hotspots — showing that integrating textual quality with spatial data increases localisation accuracy.

---

### 4. Discussion and Insights

**Geo-localisation challenges:**  
- Some tweets lacked precise coordinates and relied on bounding boxes.  
- Certain cells were dominated by repetitive or event-driven tweets.  
- Data skewed toward central London, reducing suburban representation.  

**Improvement ideas:**  
- Use user metadata (follower count, posting frequency) for weighting.  
- Apply temporal segmentation for event dynamics.  
- Consider clustering algorithms for non-grid-based localisation.  

---

## 🛠️ Tools and Libraries

- Python  
- pandas, numpy, json, math  
- matplotlib, seaborn  
- spaCy (for NLP and lemmatisation)  
- Haversine distance calculations for grid mapping  

---

## Key Results Summary

- **13,192 tweets processed**  
- **203 active grid cells** before filtering  
- **2,071 tweets remaining** after applying newsworthiness threshold  
- **Improved clarity** in heatmap and histogram visualisations  
- Strong **differentiation between tweet quality levels**  

---

## Coursework Specification

The coursework specification defined four core tasks:  
1. Grid-based spatial organisation of tweet data  
2. Newsworthiness scoring implementation and analysis  
3. Geo-localisation with filtered data  
4. Open-ended discussion of data and methodological issues  

If the coursework brief cannot be shared publicly, simply note:  
> The official specification is omitted for copyright reasons but described above.

---

## Requirements

Minimal dependencies for this project:

pandas
numpy
matplotlib
seaborn
spacy

Run the following to install all dependencies:

```bash
pip install -r requirements.txt
```
## Conclusion

This coursework demonstrated how spatial and textual data analysis can complement each other.
By applying a probabilistic newsworthiness model, noisy tweets were filtered out, improving spatial accuracy and interpretability.

The project was marked 100%, reflecting excellence in both technical implementation and critical interpretation.
