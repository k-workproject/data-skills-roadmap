# 🐍 Python Projects — Data Analyst Portfolio

รวมโปรเจกต์ฝึกฝนทักษะ Data Analyst ด้วย Python แบบ End-to-End ตั้งแต่ Data Cleaning, EDA, Feature Engineering จนถึง Modeling พร้อม Submit ขึ้น Kaggle Leaderboard จริงทุกโปรเจกต์

---

## 📂 รายการโปรเจกต์

| # | โปรเจกต์ | ประเภท | Best Model | Kaggle Score |
|---|---|---|---|---|
| 01 | [Titanic - Survival Prediction](./01-titanic_survival_prediction.ipynb) | Classification | SVM (Tuned) | 0.77990 (Accuracy) |
| 02 | [House Prices - Regression](./02-house_price_advance_regression.ipynb) | Regression | Lasso (Tuned) | 0.13599 (RMSE) |

---

## 🚢 01. Titanic - Survival Prediction

ทำนายการรอดชีวิตของผู้โดยสารเรือ Titanic

**🔗 Kaggle:** [Titanic - Machine Learning from Disaster](https://www.kaggle.com/competitions/titanic)

| หัวข้อ | รายละเอียด |
|---|---|
| Dataset | 891 แถว (train), 418 แถว (test) |
| Best Model | SVM (Tuned) — `C=0.1`, `gamma=0.1`, `kernel='poly'` |
| Validation F1-score | 0.7883 |
| Kaggle Accuracy | 0.77990 |

**ขั้นตอนหลัก:** Missing Value Imputation (Age, Embarked, Cabin→Deck) → Feature Engineering (Title, FamilySize, IsAlone) → EDA → ทดลอง 5 โมเดล → Hyperparameter Tuning ด้วย GridSearchCV

---

## 🏠 02. House Prices - Advanced Regression

ทำนายราคาขายบ้านจากคุณสมบัติกว่า 79 ฟีเจอร์

**🔗 Kaggle:** [House Prices - Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques)

| หัวข้อ | รายละเอียด |
|---|---|
| Dataset | 1,460 แถว (train), 1,459 แถว (test), 79 ฟีเจอร์ |
| Best Model | Lasso (Tuned) — `alpha=0.005` |
| Validation RMSE | 0.1222 (log scale) |
| Kaggle RMSE | 0.13599 (log scale) |

**ขั้นตอนหลัก:** แยก Missing Value เป็น "ไม่มีจริง" (เติม None/0) vs "ข้อมูลหาย" (เติม median/mode) → Outlier Removal (GrLivArea) → Feature Engineering (TotalSF, HouseAge, TotalBath) → Log Transform (SalePrice, LotArea) → ทดลอง 4 โมเดล → Hyperparameter Tuning

---

## 🧰 เครื่องมือที่ใช้ร่วมกันทุกโปรเจกต์

`Python` `Pandas` `NumPy` `Matplotlib` `Seaborn` `Scikit-learn` `Google Colab`

## 🔑 บทเรียนที่ได้จากทั้งสองโปรเจกต์

- Linear-based models (SVM, Lasso) มักทำผลงานดีกว่า Tree-based models เมื่อฟีเจอร์ส่วนใหญ่มีความสัมพันธ์กับ Target แบบเส้นตรง
- การทำ Feature Engineering ที่ดี (Title, Deck, TotalSF) มีผลต่อคุณภาพโมเดลมากกว่าความซับซ้อนของโมเดลที่เลือกใช้
- Cross-Validation score ไม่เท่ากับผลจริงบนข้อมูลใหม่เสมอไป ต้องทดสอบกับ Validation Set แยกต่างหากก่อนสรุปผลทุกครั้ง
- Missing Value ต้องตีความตามบริบทของข้อมูล ไม่ใช่เติมด้วยวิธีเดียวกันทุกครั้ง
