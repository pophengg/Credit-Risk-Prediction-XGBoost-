#  Credit Risk Default Prediction: A Production-Grade Machine Learning Approach

**Author:** [Poonyanuch Hengtamcharoen]  
**Background:** Finance professional transitioning into Data Science.  
**Tech Stack:** Python, Pandas, Scikit-Learn, Imbalanced-Learn (SMOTE), XGBoost, SHAP

･:･ ⌒♡*:･。 ⌒♥ ✧*:･ﾟ✧ ☆ﾟ.*･｡ﾟ *:･ﾟ★  ★｡･

## ｡･:･ﾟ☆ ｡ 1. Business Problem
สถาบันการเงินเผชิญกับความท้าทายในการบริหารจัดการหนี้เสีย (Non-Performing Loans - NPL) การปฏิเสธลูกค้าที่มีความเสี่ยงสูงได้อย่างแม่นยำตั้งแต่ขั้นตอนการพิจารณาสินเชื่อ จะช่วยลดความเสียหายจาก Credit Loss ได้อย่างมหาศาล โปรเจกต์นี้จึงมุ่งเน้นการสร้างโมเดล Machine Learning เพื่อพยากรณ์โอกาสที่ลูกค้าจะผิดนัดชำระหนี้ (Default/Charged Off) โดยให้ความสำคัญกับการอธิบายเหตุผลของโมเดล (Explainability) เพื่อให้สอดคล้องกับกฎระเบียบของหน่วยงานกำกับดูแล (Regulators)

## ★ ♫•*¨* 2. Dataset & Feature Engineering
ใช้ข้อมูล **Lending Club Loan Data** โดยได้ทำการดึงความรู้ทางด้านการเงิน (Financial Domain Knowledge) มาสร้างตัวแปรใหม่ (Feature Engineering) เพื่อให้โมเดลประเมินความสามารถในการชำระหนี้ได้ดีขึ้น:
* **Payment-to-Income (PTI) Ratio:** สัดส่วนค่างวดต่อเดือนเทียบกับรายได้ต่อเดือน
* **Loan-to-Income Ratio:** สัดส่วนวงเงินกู้รวมเทียบกับรายได้ทั้งปี

## •.¸¸♪ ♡* 3. Methodology & Advanced Techniques
* **Handling Imbalanced Data:** เนื่องจากสัดส่วนหนี้เสียในข้อมูลมีเพียง 20% จึงได้ใช้เทคนิค **SMOTE** (Synthetic Minority Over-sampling Technique) ในการปรับสมดุลข้อมูลชุด Train เพื่อป้องกันไม่ให้โมเดลเกิดความลำเอียง (Bias)
* **Modeling:** เลือกใช้ **XGBoost Classifier** ซึ่งเป็นอัลกอริทึมที่มีประสิทธิภาพสูงสำหรับ Tabular Data 
* **Evaluation:** ไม่ใช้ Accuracy เป็นเกณฑ์หลัก แต่เน้นวิเคราะห์ผ่าน **Confusion Matrix** และค่า **Recall** เนื่องจากในบริบทของการปล่อยสินเชื่อ ต้นทุนของการเกิด False Negative (ปล่อยกู้ให้ลูกค้าที่จะเบี้ยวหนี้) สูงกว่า False Positive (ปฏิเสธลูกค้าชั้นดี) อย่างมีนัยสำคัญ

## 。. *｡:ﾟ 4. Explainable AI (XAI) with SHAP Values
เพื่อหลีกเลี่ยงการใช้โมเดลกล่องดำ (Black-box Model) โปรเจกต์นี้ใช้ **SHAP Values** ในการอธิบายผลลัพธ์ของ XGBoost โดยพบว่าปัจจัยหลักที่ส่งผลต่อการเกิดหนี้เสีย (Feature Importance) คือ:
1. **Interest Rate (`int_rate`):** อัตราดอกเบี้ยที่สูงสะท้อนถึงความเสี่ยงที่ถูกประเมินไว้ตั้งแต่ต้น
2. **Payment-to-Income Ratio (`pti_ratio`):** ภาระค่างวดที่สูงเกินไปเมื่อเทียบกับรายได้เดือน
3. **Debt-to-Income (`dti`):** ภาระหนี้เดิมที่สูง ทำให้สภาพคล่องของลูกค้าน้อยลง

## ☆ ｡･:★ 5. Business Recommendations
* **Risk-Based Pricing:** ธนาคารสามารถนำความน่าจะเป็น (Probability of Default) จากโมเดลไปคำนวณอัตราดอกเบี้ยที่เหมาะสมกับความเสี่ยงของลูกค้าแต่ละรายได้
* **Policy Adjustment:** ควรเพิ่มความเข้มงวดในการตรวจสอบเอกสารรายได้ สำหรับกลุ่มลูกค้าที่มีค่า PTI Ratio สูงกว่าเกณฑ์ปกติที่โมเดลตรวจจับได้
