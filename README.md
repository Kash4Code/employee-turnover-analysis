# Employee Turnover Analysis

## Business Question
Does employee turnover driven by workplace dissatisfaction increase with tenure, and if so, at which career stage is the retention risk highest?

## Dataset
- **Source:** [DETE exit survey](data/dete_survey.csv) and [TAFE exit survey](data/tafe_survey.csv) — Queensland, Australia public sector institutes
- **Size:** 1,500+ combined exit survey responses
- **Description:** Exit survey responses from two separate institutes, each using a different survey schema and column structure, requiring harmonization before joint analysis.

## Tools Used
- Python (pandas, NumPy) — schema unification, missing value handling, and dissatisfaction index construction
- Python (matplotlib, seaborn) — visualization
- Jupyter Notebook — analysis workflow

## Key Findings
1. **Dissatisfaction-driven resignation scales with tenure, peaking mid-to-late career** — Established staff (7-10 years) resign due to dissatisfaction at 52%, nearly double the rate of new hires under 3 years (30%).
2. **Each career stage has a distinct primary friction factor** — New hires cite career changes and relocation; Experienced staff (3-6 yrs) cite role progression and workload; Established staff (7-10 yrs) cite burnout and work-life balance; Veterans (11+ yrs) cite leadership style and lack of recognition.
3. **The highest-risk window is specifically 7-10 years, not "senior staff" broadly** — Veteran resignation dissatisfaction (49%) is elevated but slightly below the Established peak (52%), meaning retention intervention is most urgent just before the 10-year mark, not simply for the most tenured group overall.

   <img src="visuals/dissatisfaction_by_career_stage.png" width="600">

## Recommendations
- **Run structured stay interviews around years 5 and 7** to catch burnout signals before staff reach the high-risk 7-10 year resignation window.
- **Build targeted work-life balance and burnout-prevention programs** specifically for Established and Veteran staff, rather than applying generic retention programs uniformly across all tenure groups.
- **Follow up on exit interviews by department**, focused on culture and leadership feedback, to identify which specific teams are driving the dissatisfaction spike.

## Files
- `data/dete_survey.csv`, `data/tafe_survey.csv` — raw source survey datasets
- `notebooks/analysis.ipynb` — schema harmonization, dissatisfaction index construction, and segmentation analysis
- `visuals/dissatisfaction_by_service_cat.png` — resignation rate by career stage chart

## Methodology
DETE and TAFE tracked exits using entirely different survey formats, so the first step was harmonizing column names, categorical values, and missing-data conventions into a single unified schema. Nine separate dissatisfaction-related survey indicators (covering factors like workload, recognition, and work environment) were then combined into a single weighted dissatisfaction index, allowing responses from both institutes to be compared on the same scale.

Employees were segmented into four tenure-based career stages — New (<3 yrs), Experienced (3-6 yrs), Established (7-10 yrs), and Veteran (11+ yrs) — and the dissatisfaction-driven resignation rate was calculated within each group to isolate whether turnover was tenure-linked rather than uniform across the workforce.

**Limitations:** Exit surveys are self-selected and self-reported, meaning employees who leave without completing a survey (or who understate dissatisfaction to preserve references) are not captured, which likely means true dissatisfaction-driven turnover is underrepresented rather than overstated. The tenure boundaries (3, 6, and 10 years) are analytical groupings chosen for this study, not organizational definitions, so results should be read as directional trends rather than precise cutoffs.
