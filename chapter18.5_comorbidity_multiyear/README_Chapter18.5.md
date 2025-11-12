# Chapter 18.5: Multi-Year Comorbidity Analysis

## Overview
This chapter provides comprehensive multi-year analysis of comorbidity patterns between **Ischemic Heart Disease (IHD)** and **Ischemic Stroke (IS)** using GBD 2021 data.

## Key Analyses

### 1. Cross-Classification Heatmap
- **File**: `01_cross_classification_heatmap.png` (231 KB)
- **Description**: Shows distribution of countries by IHD and IS incidence levels
- **Insight**: Reveals co-occurrence patterns and quadrant clustering

### 2. Temporal Correlation Dot Plot
- **File**: `02_temporal_correlation_dotplot.png` (748 KB)
- **Description**: Evolution of IHD-IS correlation from 1990-2021
- **Insight**: Temporal trends and regional clustering
- **Correlation**: Consistent pattern (ρ = 0.971), IHD-dominant (ρ = 0.386), IS-dominant (ρ = 0.363)

### 3. Custom Regional Analysis
- **File**: `03_comorbidity_heatmap_custom_regions.png` (1.0 MB)
- **Description**: Comorbidity patterns by development level (Developed, Emerging, LDC, Other)
- **Insight**: Regional disparities in disease burden
- **Coverage**: 55 countries across 4 regional categories

### 4. Country Similarity Network
- **File**: `04_country_simplified_network.png` (177 KB)
- **Description**: Simplified network analysis showing countries with similar disease burden patterns
- **Insight**: Country distribution by IHD vs IS burden (top 50 countries)

### 5. Machine Learning Prediction
- **Files**: `05_feature_importance.png` (74 KB), `06_alternative_importance.png` (70 KB)
- **Description**: Random Forest model predicting comorbidity severity
- **Insight**: Key predictive factors for severe comorbidity
- **Model Performance**: 500 trees trained, OOB Error rate available

### 6. Temporal Evolution Heatmap
- **File**: `07_temporal_evolution_heatmap.png` (108 KB)
- **Description**: Severity score evolution by region over time (1990-2019)
- **Insight**: Regional trends and pattern changes

### 7. Correlation Evolution
- **File**: `08_correlation_evolution.png` (119 KB)
- **Description**: Spearman correlation coefficient between IHD and IS over time
- **Insight**: Strengthening or weakening of disease relationship

### 8. Country Rankings
- **File**: `09_country_rankings.png` (357 KB)
- **Description**: Top 50 countries by IHD and IS burden
- **Insight**: Disease burden distribution globally

## Data Files

### Processed Data
- `IHD_IS_comorbidity_data.csv` (2.0 MB): Merged IHD and IS data with quartile classifications (24,480 rows)
- `temporal_evolution_summary.csv` (5.9 KB): Average severity by year and region
- `correlation_evolution.csv` (837 B): Correlation coefficients by year
- `country_rankings.csv` (2.9 KB): Country rankings by disease burden

### Machine Learning
- `model_metrics.csv` (54 B): Random Forest model performance metrics
- `summary_statistics.csv` (183 B): Overall analysis summary

### Network Analysis
- `network_top50_burden/`: Network analysis directory

## Summary Statistics

| Metric | Value |
|--------|-------|
| Total Observations | 24,480 |
| Countries | 204 |
| Years Range | 1990-2019 |
| Average IHD | 54,081.32 |
| Average IS | 13,231.92 |
| Max IHD | 6,894,608 |
| Max IS | 2,606,352 |
| Overall Correlation | 0.423 |
| High Comorbidity Countries | 2,809 |

## Key Findings

1. **Temporal Trends**: Correlation between IHD and IS shows moderate overall correlation (0.423) with distinct regional patterns
2. **Regional Disparities**: 55 countries across 4 development levels show varying comorbidity patterns
3. **High-Risk Countries**: 2,809 country-year observations show high comorbidity (both diseases high)
4. **Predictive Factors**: Machine learning identifies key features for comorbidity severity prediction

## Technical Details

- **Data Source**: IHME-GBD_2021_DATA-999a6534-1.csv (15MB)
- **Coverage**: 204 countries, 1990-2019 (30 years)
- **Measures**: Incidence rates per 100,000 population
- **Age Groups**: All ages, Both sexes
- **Disease Classification**: Quartile-based (Low, Lower-middle, Upper-middle, High)

## Visualization Quality
- All plots saved as high-resolution PNG (300 DPI)
- Color palettes optimized for publication
- Professional formatting with titles, subtitles, and captions

## Analysis Methods

### Cross-Classification Analysis
Countries are classified into quartiles based on disease burden for both IHD and IS. This creates a 4x4 matrix showing co-occurrence patterns.

### Temporal Correlation Analysis
Spearman correlation coefficients calculated by region type and year to track evolving disease relationships.

### Regional Classification
Custom regions based on development level:
- **Developed Countries**: High-income nations (17 countries)
- **Emerging Economies**: Middle-income nations (15 countries)
- **Least Developed Countries**: Low-income nations (15 countries)
- **Other Developing Countries**: Remaining countries (8 countries)

### Machine Learning
Random Forest regression model with 500 trees to predict comorbidity severity score based on:
- Disease burden levels
- Temporal trends
- Regional patterns

### Severity Score Calculation
```
Score 4: High IHD + High IS
Score 3: High IHD or High IS (with other at Lower-middle or above)
Score 2: Upper-middle or Lower-middle levels
Score 1: Low levels
```

## Usage

```r
# Load processed data
library(data.table)
data <- fread("IHD_IS_comorbidity_data.csv")

# View summary statistics
summary_stats <- fread("summary_statistics.csv")
print(summary_stats)

# Analyze temporal trends
temporal_data <- fread("temporal_evolution_summary.csv")
print(head(temporal_data))

# Country rankings
rankings <- fread("country_rankings.csv")
print(head(rankings, 20))
```

## File Sizes

**Visualizations (9 files, 2.8 MB total)**:
- PNG files: 231 KB - 1.0 MB each
- High-resolution 300 DPI for publication

**Data Files (6 files, 2.1 MB total)**:
- CSV files: 54 B - 2.9 KB each
- Main dataset: 2.0 MB

## Generated On
2025-11-12 00:50:35

GlobalBurdenR v3.0.0 | Chapter 18.5
