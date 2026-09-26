# 🚢 Titanic - Survival Prediction

โปรเจกต์ทำนายการรอดชีวิตของผู้โดยสารเรือ Titanic โดยใช้ Machine Learning แบบ End-to-End ตั้งแต่ Data Cleaning, EDA, Feature Engineering จนถึง Modeling พร้อม Submit ขึ้น Kaggle Leaderboard จริง

**🔗 Kaggle Competition:** [Titanic - Machine Learning from Disaster](https://www.kaggle.com/competitions/titanic)  
**🏆 Kaggle Submission Score:** `0.77990` (Accuracy)

---

## 📋 สรุปโปรเจกต์

| หัวข้อ | รายละเอียด |
|---|---|
| Dataset | Titanic (Kaggle) — 891 แถว (train), 418 แถว (test) |
| Best Model | SVM (Tuned) — `C=0.1`, `gamma=0.1`, `kernel='poly'` |
| Validation F1-score | 0.7883 |
| Kaggle Accuracy | 0.77990 |

## 🛠️ ขั้นตอนการทำงาน

1. **Data Cleaning**
   - จัดการ Missing Value: `Age` (median แยกตาม Pclass+Sex), `Embarked` (mode), `Cabin` (ดึงเป็น `Deck` แทนการ drop)
   - เช็ค Duplicate row (ไม่พบ)
   - จัดการ Outlier ของ `Fare` ด้วย Log Transform

2. **Feature Engineering**
   - สร้าง `Title` จากคำนำหน้าใน `Name` (Mr, Miss, Mrs, Master, Rare)
   - สร้าง `FamilySize` และ `IsAlone` จาก `SibSp` + `Parch`
   - One-Hot Encoding สำหรับ `Sex`, `Embarked`, `Deck`, `Title`

3. **Exploratory Data Analysis (EDA)**
   - วิเคราะห์อัตรารอดชีวิตตาม Sex, Pclass, Age, Fare, Embarked, FamilySize
   - Correlation Heatmap เพื่อเช็ค Multicollinearity ก่อนเข้าโมเดล

4. **Modeling**
   - ทดลอง 5 โมเดล: Logistic Regression, Decision Tree, Random Forest, KNN, SVM
   - Hyperparameter Tuning ด้วย `GridSearchCV` + 5-Fold Cross-Validation
   - เลือก SVM (Tuned) เป็นโมเดลสุดท้าย

5. **Evaluation & Submission**
   - วัดผลด้วย Accuracy, Precision, Recall, F1-score
   - Predict บน test.csv และ Submit ขึ้น Kaggle Leaderboard

## 📊 ผลการทดลองโมเดล

| Model | F1-score (Validation) |
|---|---|
| **SVM (Tuned)** ⭐ | **0.7883** |
| SVM (Default) | 0.7727 |
| Logistic Regression | 0.7634 |
| Random Forest (Tuned) | 0.7344 |
| Random Forest (Default) | 0.7164 |
| KNN | 0.6923 |
| Decision Tree | 0.6715 |

## 🔑 Key Insights

- **เพศ** เป็นปัจจัยที่มีผลต่อการรอดชีวิตแรงที่สุด (หญิงรอด ~74% เทียบกับชาย ~19%)
- **ชั้นโดยสาร (Pclass)** และ **Fare** สะท้อนฐานะทางเศรษฐกิจ ซึ่งสัมพันธ์กับอัตรารอดชัดเจน
- **ขนาดครอบครัว** มีความสัมพันธ์แบบไม่เป็นเส้นตรง — ครอบครัวขนาด 2-4 คนรอดมากสุด
- ฟีเจอร์ที่ต้องดึงจาก raw data เอง (`Title`, `Deck`) ให้ signal ที่มีประโยชน์มากกว่าที่คาดไว้

## 🧰 เครื่องมือที่ใช้

`Python` `Pandas` `NumPy` `Matplotlib` `Seaborn` `Scikit-learn` `Google Colab`

## 📁 ไฟล์ในโฟลเดอร์นี้

- `titanic_survival_prediction.ipynb` — Notebook ฉบับเต็ม (Cleaning → EDA → Modeling → Submission)
