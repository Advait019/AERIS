# AERIS: Executive Overview & Methodology

## Executive Summary

The **Attrition Early-Warning & Officer Retention Intelligence System (AERIS)** is a data-driven solution designed to predict police officer attrition and enable proactive retention strategies. By leveraging machine learning and behavioral analytics, AERIS transforms reactive HR practices into strategic workforce management.

### The Challenge

Police departments face significant costs when officers leave:
- **Recruitment costs**: Advertising, screening, background checks
- **Training costs**: Academy, field training, specialized certifications
- **Knowledge loss**: Institutional knowledge, community relationships
- **Team impact**: Morale, overtime burden on remaining officers

Traditional approaches identify attrition risk too late (exit interviews) or too broadly (annual surveys). AERIS provides individual-level, proactive identification of at-risk officers.

### The Solution

AERIS uses a 5,001-officer dataset with 22 features to build predictive models that:
1. **Identify** officers at high risk of leaving before they make the decision
2. **Explain** which factors are driving their attrition risk
3. **Segment** officers into actionable personas for targeted interventions
4. **Quantify** the business impact and ROI of retention efforts

---

## Key Findings

### Top Attrition Drivers

Based on our multi-model analysis, the primary factors driving officer attrition are:

| Rank | Factor | Impact Direction | Actionability |
|------|--------|-----------------|---------------|
| 1 | Overtime Hours | More OT → Higher Risk | High - Policy change |
| 2 | Trauma Exposure | More Trauma → Higher Risk | High - Wellness support |
| 3 | Duty Satisfaction | Lower → Higher Risk | Medium - Culture/leadership |
| 4 | Work-Life Balance | Lower → Higher Risk | High - Scheduling changes |
| 5 | Night Shift Ratio | Higher → Higher Risk | Medium - Rotation policy |
| 6 | Years of Service | Newer → Higher Risk | Medium - Onboarding |
| 7 | Pay Band | Lower → Higher Risk | Low - Budget dependent |
| 8 | Critical Incidents | More → Higher Risk | High - Incident support |

### Comparison: Police vs. Corporate Attrition

| Factor | Corporate (IBM) Importance | Police (AERIS) Importance |
|--------|---------------------------|---------------------------|
| Overtime | High | Very High |
| Job Satisfaction | High | High |
| Trauma/Stress | Not measured | Critical |
| Distance from Home | Medium | Low |
| Work-Life Balance | High | Very High |
| Incident Exposure | Not applicable | High |

**Key Insight**: Police attrition has unique drivers (trauma, incidents) that generic HR analytics miss entirely.

---

## Methodology

### Data Pipeline

```
Raw Data (5,001 officers, 22 features)
    ↓
Feature Engineering
    - One-hot encoding for categorical variables
    - Standard scaling for numerical features
    - Stratified train/test split (80/20)
    ↓
Class Imbalance Handling
    - SMOTE oversampling (training only)
    - Class-weighted models
    - Balanced ensemble methods
    ↓
Multi-Model Training
    - Logistic Regression (interpretable baseline)
    - Random Forest (feature importance)
    - XGBoost (primary predictive model)
    - Balanced Random Forest (native imbalance handling)
    - EasyEnsemble (severe imbalance specialist)
    ↓
Threshold Optimization
    - Cost-benefit analysis
    - Police-specific cost parameters
    - Optimal threshold selection
    ↓
Persona Clustering
    - K-Means (hard clustering)
    - Gaussian Mixture Model (soft clustering)
    - Attrition rate by persona
    ↓
Output: Risk Scores + Personas
```

### Methodological Improvements

We implement several best practices that improve upon baseline approaches:

#### 1. Stratified Validation
- **Baseline**: Simple random split
- **AERIS**: Stratified split preserving class distribution
- **Improvement**: Ensures test set is representative

#### 2. Proper Scaling
- **Baseline**: Fit scaler on entire dataset
- **AERIS**: Fit on training data only, transform test
- **Improvement**: Prevents data leakage

#### 3. Class Imbalance Handling
- **Baseline**: Often ignored
- **AERIS**: SMOTE + class weights + PR-AUC evaluation
- **Improvement**: Better minority class (attrition) detection

#### 4. Threshold Optimization
- **Baseline**: Default 0.5 threshold
- **AERIS**: Cost-optimized based on:
  - Cost of missing at-risk officer: $15,000
  - Cost of unnecessary intervention: $500
- **Improvement**: Optimizes for business outcome, not accuracy

#### 5. Confidence Intervals
- **Baseline**: Single-point estimates
- **AERIS**: 5-fold CV with 95% confidence intervals
- **Improvement**: Honest uncertainty quantification

#### 6. Multi-Method Clustering
- **Baseline**: K-Means only
- **AERIS**: K-Means + GMM
- **Improvement**: Hard + probabilistic cluster assignment

---

## Officer Personas

### Persona Profiles

Based on clustering analysis, three distinct officer archetypes emerge:

#### Persona 0: Burnout Risk
- **Profile**: High overtime, high trauma exposure, low satisfaction
- **Attrition Rate**: Highest among all personas
- **Size**: Significant minority of force
- **Recommended Interventions**:
  - Mandatory rest periods
  - Priority counseling access
  - Workload redistribution
  - Temporary assignment to lower-stress duties

#### Persona 1: Stable Veteran
- **Profile**: Long tenure, moderate hours, good work-life balance
- **Attrition Rate**: Lowest among all personas
- **Size**: Core of the department
- **Recommended Interventions**:
  - Recognition programs
  - Mentorship role assignments
  - Leadership development opportunities
  - Retention bonuses for key positions

#### Persona 2: New & Struggling
- **Profile**: Short tenure, variable hours, still adjusting
- **Attrition Rate**: Moderate, but high potential
- **Size**: Newer cohort of officers
- **Recommended Interventions**:
  - Enhanced onboarding support
  - Buddy/mentor pairing with veterans
  - Clear career path communication
  - Regular check-ins during first 2 years

### Persona-Based Intervention Matrix

| Intervention | Burnout Risk | Stable Veteran | New & Struggling |
|--------------|--------------|----------------|------------------|
| Overtime Caps | Primary | Not needed | Monitor |
| Counseling | Mandatory | Optional | Available |
| Mentorship | Receive | Provide | Receive |
| Career Planning | Recovery focus | Leadership track | Growth mapping |
| Recognition | Wellness achievements | Service milestones | Quick wins |

---

## Business Impact

### Cost Model

| Cost Category | Without AERIS | With AERIS |
|---------------|---------------|------------|
| Attrition costs | Full impact | Reduced by interventions |
| Intervention costs | None | Added cost |
| Net impact | High losses | Significant savings |

### ROI Calculation

The return on investment for AERIS implementation comes from:

1. **Direct Savings**
   - Prevented attrition × cost per attrition
   - Minus intervention costs

2. **Indirect Benefits**
   - Maintained team cohesion
   - Preserved institutional knowledge
   - Reduced overtime for remaining officers
   - Better community relationships

### Sensitivity Analysis

ROI remains positive across a range of assumptions:
- Intervention success rate: 30-50%
- Cost per attrition: $50,000-$100,000
- Cost per intervention: $1,000-$5,000

---

## Implementation Recommendations

### Phase 1: Immediate Actions (0-3 months)
1. Review Critical-risk officer list with HR leadership
2. Implement interventions for top 20 highest-risk officers
3. Establish tracking for intervention outcomes

### Phase 2: Systematic Integration (3-6 months)
1. Integrate AERIS scoring into regular HR reporting
2. Develop persona-specific intervention playbooks
3. Train supervisors on risk indicator recognition

### Phase 3: Continuous Improvement (6+ months)
1. Quarterly model retraining with new data
2. Threshold recalibration based on intervention outcomes
3. Feature expansion (new data sources)
4. Department-wide wellness culture initiatives

---

## Technical Specifications

### Model Performance Summary

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC | PR-AUC |
|-------|----------|-----------|--------|----|---------| -------|
| Logistic Regression | Baseline | Good | Varies | Moderate | Good | Moderate |
| Random Forest | High | Good | Good | Good | High | Good |
| XGBoost | Highest | Best | Best | Best | Highest | Best |
| Balanced RF | High | Good | Very Good | Good | High | Good |
| EasyEnsemble | High | Good | Very Good | Good | High | Good |

### Recommended Production Model
- **Primary**: XGBoost with optimized threshold
- **Backup**: Balanced Random Forest
- **Interpretability**: Logistic Regression coefficients for explanation

### Data Requirements
- Minimum update frequency: Quarterly
- Critical features: Overtime hours, trauma index, satisfaction surveys
- Data quality: No missing values in core features

---

## Comparison with Prior Art

### vs. IBM HR Analytics Benchmark

| Dimension | IBM HR Analysis | AERIS |
|-----------|-----------------|-------|
| Records | 1,470 | 5,001 (3.4x more) |
| Features | 13 | 22 (70% more) |
| Domain specificity | Generic corporate | Police-specific |
| Trauma indicators | None | 3 features |
| Threshold optimization | Not performed | Cost-based |
| Confidence intervals | Not reported | 95% CI provided |
| Business impact | Not quantified | ROI calculated |

### Key Innovations
1. **Police-specific features**: Trauma, incidents, night shifts
2. **Cost-optimized thresholds**: Based on actual department costs
3. **Dual clustering**: Hard + soft persona assignment
4. **Comprehensive validation**: K-fold CV with confidence intervals

---

## Conclusion

AERIS provides a significant advancement over traditional attrition management:

- **Proactive**: Identifies risk before departure decision
- **Individual**: Officer-level rather than department-level insights
- **Actionable**: Personas enable targeted interventions
- **Quantified**: Clear ROI for leadership buy-in
- **Reproducible**: Fixed seeds and documented methodology

By implementing AERIS, police departments can transform their approach to retention from reactive to strategic, ultimately protecting their most valuable asset: their officers.

---

*"AERIS - Protecting those who protect us, through data-driven retention."*
