# Olympic Speedskating Medal Prediction
## Overview
This project develops a probabilistic medal prediction system for the 1000m Speed Skating event at the 2026 Milano Cortina Winter Olympics, with a specific focus on U.S. athletes. Using historical international competition data from 2016 through early 2026, the analysis combines machine learning classification, regression modeling, and Monte Carlo simulation to estimate medal probabilities for Olympic qualifiers.

The analysis focuses on three primary objectives:
- Predicting whether an athlete will medal using machine learning classification models
- Forecasting projected Olympic finish times using regression modeling
- Simulating medal outcomes through Monte Carlo simulations

---
## Data Sources
### 1. Historical Competition Results
Competition data and split times were consolidated from a provided Excel workbook. This has not been included in the repository for privacy purposes.

Variables included:
- Athlete name
- Country
- Race time
- 200m split time
- Age
- Competition date
- Medal outcome
- Race classification

---
### 2. Olympic Qualification Filtering
To reflect realistic Olympic qualification standards, the dataset was filtered using ISU eligibility criteria.

Exclusions included:
- Athletes outside qualifying age ranges
- DSQ, DNF, DNS, and B-group results
- Performances outside Olympic qualifying standards

Only athletes achieving qualifying times between August 1, 2025, and January 18, 2026, were retained.

---
## Methods
### Baseline Model
An introductory logistic regression model was created using:
- 200m split time
- Athlete age
- Senior race count

Baseline performance:
- Men's ROC AUC: 0.85
- Women's ROC AUC: 0.84

This model established an initial benchmark before additional feature engineering.

---
### Feature Engineering
Derived features included:
- Average medal outcome
- Recent performance z-score
- Senior elite race count
- Weighted recent race performance
- Historical race consistency
- Competition experience

Sample weights were also applied to:
- More recent races
- Higher-level elite competitions

The primary challenge was balancing predictive power while avoiding overfitting from features too closely tied to final race times.

---
### Classification Models
Three classification models were trained and compared for medal prediction:

#### 1. Logistic Regression
Purpose:
- Establish interpretable medal probability predictions
- Capture linear relationships between engineered features and outcomes

---
#### 2. Neural Network
Purpose:
- Capture nonlinear interactions between athlete performance variables
- Compare deep learning performance against simpler models

---
#### 3. XGBoost Classification
Purpose:
- Evaluate boosted-tree performance on elite competition data
- Test whether nonlinear feature interactions improved medal prediction

---
### Finish Time Prediction
Although logistic regression performed best for classification, XGBoost regression was selected for finish time forecasting due to its stronger predictive capability for continuous outcomes.

Validation approach:
- Randomized 80/20 training-testing split
- Predicted finish times evaluated against held-out race results

Performance:
- Predictions averaged within approximately 0.3–0.4 seconds of actual race times

---
### Monte Carlo Simulation
Simulation details:
- 10,000 simulations
- Athlete-specific:
  - Predicted finish time (μ)
  - Historical race variability (σ)

Purpose:
- Estimate probabilities of:
  - Winning gold
  - Winning any medal
  - Final placement distribution

---
## Key Findings
### Men's 1000m
- American Jordan Stolz emerged as the clear favorite
- Medal probability: 46.7%
- Gold medal probability: 22.96%

### Women's 1000m
- Brittany Bowe was projected as the top American medal contender
- Medal probability: 8.82%

### Additional Findings:
- Relationships between variables and medal outcomes appeared more linear than anticipated
- "Average Medal Outcome" and "Recent Performance (Z-Score)" were among the strongest predictive features

---
## Coaching Implications
- Emphasize recent elite-level racing opportunities
- Track athlete consistency across major competitions
- Use recent performance trends to guide Olympic preparation

---
## Limitations
- Small elite-level sample size
- Olympic competition outcomes influenced by:
  - Lane assignments
  - Pacing strategy
  - Race-day conditions
  - Tactical decisions
- Historical results may not fully capture current athlete form

---
## Future Additions
- Compare projected results to actual 2026 Olympic outcomes
- Incorporate lane assignment effects
- Model pacing strategy and split consistency
- Expand framework to additional Olympic distances
- Include more advanced race-specific contextual variables

---
## Repository Files
- Main analysis HTML
- Final report document
- Tableau workbook with visualizations

---
## Conclusion
This project establishes a machine learning framework for Olympic medal forecasting in speedskating. By combining feature engineering, classification modeling, regression forecasting, and Monte Carlo simulation, the analysis provides probabilistic insight into Olympic performance outcomes while highlighting the importance of recent elite-level competition and athlete consistency.
