# AERIS: Attrition Early-Warning & Officer Retention Intelligence System

A comprehensive machine learning system for predicting police officer attrition and developing targeted retention strategies.

## Project Overview

AERIS addresses the critical challenge of predicting police officer attrition using advanced machine learning techniques. The system combines supervised classification with unsupervised clustering to create actionable officer personas and data-driven retention strategies tailored specifically for law enforcement contexts.

### Key Features

- **Multi-Model Classification Suite**: Logistic Regression, Random Forest, XGBoost, Balanced Random Forest, and EasyEnsemble
- **Class Imbalance Handling**: SMOTE oversampling and specialized ensemble methods
- **Cost-Optimized Thresholds**: Police-specific cost-benefit analysis for threshold tuning
- **Officer Persona Clustering**: K-Means and Gaussian Mixture Models for actionable segmentation
- **Comprehensive Validation**: Stratified K-Fold cross-validation with confidence intervals
- **Business Impact Quantification**: ROI calculations and annual savings projections

## Repository Structure

```
.
├── AERIS_master.ipynb                    # Main analysis notebook
├── realistic_police_attrition_dataset.csv # Source dataset (5,001 officers)
├── police_dataset_with_predictions.csv   # Output with risk scores (generated)
├── README.md                             # This file
├── overview.md                           # Executive summary and methodology
├── app.py                                # Streamlit application
└── attached_assets/                      # Reference materials
    ├── attrition_master (1)_*.ipynb      # Reference IBM HR analysis
    └── project_outline_*.py              # Original project outline
```

## Quick Start

### Prerequisites

- Python 3.11+
- Required packages (automatically installed):
  - pandas, numpy
  - scikit-learn
  - imbalanced-learn
  - xgboost
  - matplotlib, seaborn
  - scipy
  - streamlit

### Running the Analysis

**Option 1: Jupyter Notebook**
```bash
jupyter notebook AERIS_master.ipynb
```

**Option 2: Streamlit App**
```bash
streamlit run app.py --server.port 5000
```

## Dataset Description

The police attrition dataset contains 5,001 officer records with 22 features:

| Category | Features |
|----------|----------|
| Demographics | age, gender, marital_status |
| Career | rank, unit, years_of_service, base_pay_band |
| Workload | avg_weekly_hours, night_shift_ratio, overtime_hours_month |
| Stress Indicators | critical_incidents_last_year, trauma_exposure_index |
| Wellness | sick_days_last_year, mental_health_risk_flag |
| Satisfaction | duty_satisfaction, work_env_rating, work_life_balance |
| Career Events | promotion_last_3y, transfer_last_2y, posted_in_high_risk_area |
| Target | attrition (0/1) |

## Methodology Improvements

This project implements several methodological improvements over traditional HR analytics:

| Aspect | Traditional Approach | AERIS Approach |
|--------|---------------------|----------------|
| Validation | Single train/test split | Stratified K-Fold + confidence intervals |
| Class Imbalance | Often ignored | SMOTE + ensemble methods + PR-AUC |
| Threshold | Default 0.5 | Cost-optimized for police context |
| Feature Set | Generic HR metrics | Police-specific risk factors |
| Clustering | Simple K-Means | K-Means + Gaussian Mixture Model |
| Business Impact | Not quantified | ROI and savings calculated |

## Key Results

### Model Performance
- Best model achieves strong ROC-AUC and PR-AUC scores
- Threshold optimization reduces total cost significantly
- Cross-validation confirms model stability

### Top Attrition Drivers
1. Overtime hours and excessive workload
2. Trauma exposure index
3. Low duty satisfaction
4. Poor work-life balance
5. Night shift ratio

### Officer Personas
Three distinct officer archetypes identified:
- **Burnout Risk**: High stress, low satisfaction - requires immediate intervention
- **Stable Veteran**: Long tenure, balanced workload - potential mentors
- **New & Struggling**: Short tenure, adjusting - needs onboarding support

## Usage Notes

### For HR Analysts
1. Run the complete notebook to generate risk scores
2. Export `police_dataset_with_predictions.csv` for further analysis
3. Focus on Critical and High risk categories for immediate action

### For Department Leadership
1. Review the Business Impact section for ROI justification
2. Use persona profiles to design targeted interventions
3. Monitor the recommended metrics for ongoing assessment

### For Data Scientists
1. Model hyperparameters can be tuned in Section 5
2. Cost parameters in Section 7 should be calibrated to your department
3. Cross-validation settings in Section 10 ensure robust evaluation

## Outputs

The notebook generates:
- `police_dataset_with_predictions.csv`: Original data + risk scores and personas
- Visualization plots for all analysis sections
- Model performance comparisons
- Feature importance rankings
- Business impact projections

## Maintenance

### Recommended Practices
- **Quarterly Retraining**: Update models with new attrition data
- **Threshold Recalibration**: Adjust cost parameters as department needs change
- **Feature Monitoring**: Track if new features become available

### Data Quality Checks
- Verify no missing values before model training
- Ensure satisfaction surveys are collected before potential attrition events
- Validate that trauma exposure indices are up-to-date

## References

- IBM HR Analytics Employee Attrition Dataset (benchmark comparison)
- Scikit-learn documentation for model implementations
- Imbalanced-learn for SMOTE and ensemble methods

## License

This project is developed for internal police department use. Please consult your organization's data governance policies before deployment.

---

**AERIS - Protecting those who protect us, through data-driven retention.**
