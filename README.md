# DA5401 – Assignment 6

**Name:** Anan Madhav T V  
**Roll Number:** MM22B013  

---

## 📂 Folder Structure  

├── DA5401_A6_MM22B013.ipynb           # Main Jupyter Notebook  
├── README.md                          # Documentation file                  
└── UCI_Credit_Credit.csv              # Dataset


---

## ⚙️ How to Run  
1. Open the notebook `DA5401_A6_MM22B013.ipynb` in **Jupyter Notebook** or **Google Colab**.  
2. Ensure the `UCI_Credit_Credit` file is present in the same directory.  

---

## 📝 Assignment Work

In this assignment, I tackled the problem of **handling missing data** by comparing different imputation techniques on the **UCI Credit Card Default Clients Dataset**. The goal was to see how each method affects the performance of a downstream classification task.

1.  **Data Preparation:** Loaded the dataset and artificially introduced **10% Missing At Random (MAR) values** into three numerical columns (`AGE`, `BILL_AMT1`, `BILL_AMT4`) to simulate a realistic data problem.
2.  **Imputation Strategies:** Implemented and compared four distinct strategies for handling the missing data:
    * **Strategy A (Median Imputation):** Filled all missing values with the median of their respective columns.
    * **Strategy B (Linear Regression Imputation):** Created a separate dataset with 10% MAR in a single column (`BILL_AMT1`) and used a linear regression model to predict and fill the missing values.
    * **Strategy C (Non-Linear KNN Imputation):** Used a K-Nearest Neighbors (KNN) imputer on the same single-column MAR dataset to fill the missing values.
    * **Strategy D (Listwise Deletion):** Simply removed all rows that contained any missing values from the multi-column MAR dataset.
3.  **Model Training:** Trained a **Logistic Regression classifier** on each of the four resulting datasets (A, B, C, and D).
4.  **Performance Comparison:** Evaluated each model's performance on its test set using a full classification report and generated a summary table to compare accuracy and F1-scores.

---

## ✅ Conclusion

-   **Listwise Deletion (Model D)** showed the highest F1-score (0.3780) but is **not recommended**. It achieved this by discarding a significant portion of the data, which introduces a high risk of bias and results in a model that cannot handle incomplete data in a real-world setting.
-   **Regression Imputation (Models B & C)** performed marginally better than the baseline but did not offer a significant improvement to justify their complexity in this specific case.
-   **Median Imputation (Model A)** provided strong baseline performance (F1-score of 0.3554), proving to be a robust and efficient strategy.

**Overall Recommendation:** For this scenario, **Median Imputation is the best strategy**. It's fast, simple, preserves the entire dataset to avoid bias, and performs on par with more complex regression-based methods. It offers the best balance of performance and practicality.
