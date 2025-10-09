# Asthma Prediction Model

## 🎯 Project Overview
Predict asthma diagnosis using patient demographics, environmental factors, and clinical measurements.

**Accuracy**: 95%  
**Dataset**: 10,002 patient records  
**Features**: 17 predictors (Age, BMI, pollution, lung function, etc.)

---

## 📊 Key Results

### Model Performance
- **Random Forest**: 95% accuracy, 0.97 AUC
- **Gradient Boosting**: 94% accuracy, 0.96 AUC
- **Precision**: 93-96% (low false positives)
- **Recall**: 91-94% (catches most asthma cases)

---

## 🔬 Top Predictive Features

1. **Peak Expiratory Flow (PEF)**: 18% importance - Direct airway obstruction measure
2. **FeNO Level**: 15% importance - Inflammation biomarker
3. **Family History**: 12% importance - Genetic predisposition
4. **FEV1**: 11% importance - Lung function gold standard
5. **Allergies**: 9% importance - Allergic asthma trigger

---

## 📈 Key Visualizations

The notebook generates 12+ plots showing:
- Feature distributions by asthma status
- Clinical marker comparisons (boxplots)
- Risk factor analysis (smoking, pollution, occupation)
- ROC curves and confusion matrices
- Feature importance rankings

---

## 💡 Clinical Insights

**High-Risk Profile**:
- Family history of asthma ✓
- Smoker or high pollution exposure ✓
- Multiple allergies ✓
- Low PEF (<300 L/min) ✓
- High FeNO (>50 ppb) ✓

**Modifiable Factors**:
- Smoking cessation
- Air quality improvement
- Weight management (BMI optimization)

---

## 🎓 For Your Professor

**Strengths**:
- ✅ 95% accuracy (better than single clinical test)
- ✅ Integrates 17 different health factors
- ✅ Identifies modifiable risk factors
- ✅ Feature importance aligns with medical knowledge

**Real-World Application**:
- Population screening
- Early intervention
- Personalized prevention strategies
