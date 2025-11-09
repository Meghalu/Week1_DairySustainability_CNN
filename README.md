 Week1_DairySustainability_CNN
 Week 1: Data Preparation & Exploratory Data Analysis for CNN-Based Cow Behavior Classification in Dairy Farms

Project Overview
This Week 1 milestone preprocesses and analyzes the CBVD-5 dataset to prepare for CNN-based multi-label classification of cow behaviors (Stand, Lying down, Foraging, Drinking water, Rumination) in dairy farms. The goal is to assess environmental impacts, such as methane emissions (Rumination proxy: 1.2 kg/cow/day) and water use (Drinking water proxy: 50 L/episode), enabling 10-15% GHG reductions via monitoring.

Dataset
- **Source:** CBVD-5 (25,324 bounding box annotations, 3,199 images from dairy farm videos).
- **Structure:** CSV with metadata_id, file_list, flags, temporal_coordinates (empty), spatial_coordinates ([shape_id, x, y, width, height]), metadata (JSON-like behaviors).
- **Behaviors:** Multi-label (e.g., "0,4" = Stand + Rumination).

Methods
- **Parsing:** Regex for metadata (extract "1":"0,4" → [Stand, Rumination]) and eval for coordinates (box area = width * height, avg 43,154 px²).
- **Aggregation:** Groupby image_name with OR logic for multi-hot vectors (5 classes).
- **EDA:** Counter for distributions, combinations for co-occurrences, Matplotlib/Seaborn for visualizations (histograms, pies, bars).
- **Environmental Proxy:** Rumination count * 1.2 = 11,850 kg methane baseline; Drinking water 744 events * 50 L = 37,200 L water risk.

Results & Insights
- **Stats:** 3,199 unique images, avg 7.9 cows/image (max 24).
- **Distribution:** Stand 62.5%, Lying down 37.5%, Foraging 22.6%, Rumination 24.0%, Drinking water 2.9%.
- **Co-occurrences:** Stand + Rumination (4,500 instances, 82% images multi-label).
- **Sustainability:** Imbalance proxies high-impact rare behaviors; 15% GHG savings potential via alerts.

Files
- `Week1_CowBehavior_EDA.ipynb`: Full code for parsing, EDA, and label generation.
- `CBVD-5.csv`: Dataset.
- `cow_behavior_labels.csv`: Output (3,199 rows, multi-hot vectors).
- `labs.csv`: Additional labels for behaviors.

