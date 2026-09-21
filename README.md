# Comparative Analysis of Sequential Models for Mobile Network Traffic Forecasting

**Student:** Francis Mutabazi  
**Course:** Machine Learning Techniques I – African Leadership University  
**Assignment:** Formative 1 – September 2026

---

## Research Question

> How do different sequential models compare for one-step-ahead mobile network traffic forecasting, and how does their performance vary across geographical areas with different traffic characteristics?

---

## Project Overview

This repository contains the complete solution for the Formative Assignment 1 on sequential models for mobile network traffic forecasting.

We compare three sequential architectures taught in class:

- **SimpleRNN**
- **LSTM**
- **GRU**

on the Telecom Italia Big Data Challenge dataset (Milan, Nov 2013 – Jan 2014). The goal is one-step-ahead forecasting of Internet traffic for the three busiest geographical squares during the week 16–22 December 2013.

The work follows a systematic experimental process with clear justification for every design decision.

---

## Repository Structure
```bash
├── README.md
├── notebook/
│   └── MLTech1_Formative1.ipynb          # Complete Colab notebook
└── requirements.txt
```

## Dataset

- **Source:** Telecom Italia Big Data Challenge – Milan  
- **Period:** 1 November 2013 – 1 January 2014 (62 days)  
- **Resolution:** 10-minute intervals  
- **Squares used:** Top-3 busiest (5161, 5059, 5259) + reference squares 4159 & 4556  
- **Target variable:** Internet traffic only  

The dataset is **not** included in this repository due to size (~20 GB).  
It must be downloaded from Harvard Dataverse and placed in Google Drive as described in the notebook.

---

## How to Run the Notebook

1. Open the notebook in **Google Colab**.
2. Mount your Google Drive (the dataset must already be uploaded as 8 zip files).
3. Run all cells sequentially from top to bottom.
4. The notebook will:
   - Extract and process the full dataset in a memory-efficient way
   - Perform exploratory data analysis
   - Run four controlled experiments
   - Generate all required plots and metrics tables
   - Produce the final comparative results

**Expected runtime** (Colab free tier): approximately 45–90 minutes depending on the runtime.

---

## Experimental Process

| Experiment | Description                              | Key Outcome                          |
|------------|------------------------------------------|--------------------------------------|
| 1          | log1p + MSE                              | Models collapsed to near-zero        |
| 2          | log1p + 48-hour history                  | Still flat predictions               |
| 3          | Original scale + time-of-day features    | First non-flat forecasts             |
| 4 (Final)  | Original scale + time features + weighted MSE | Clear daily cycles + realistic peaks |

**Final chosen configuration:** Experiment 4  
**Best model:** LSTM (lowest RMSE on two of the three squares)

---

## Key Results (Experiment 4)

| Model     | Square 5059 | Square 5161 | Square 5259 |
|-----------|-------------|-------------|-------------|
| SimpleRNN | 580.0       | 494.1       | 768.1       |
| **LSTM**  | **500.5**   | **401.6**   | **651.8**   |
| GRU       | 505.6       | 524.2       | 806.5       |

*(RMSE values)*

---

## Requirements
```bash
tensorflow
pandas
numpy
matplotlib
seaborn
scikit-learn
statsmodels
psutil
```

(Or simply run the notebook in Google Colab – all libraries are installed automatically.)

---

## Video Demo

> **YouTube link:**  
> https://youtu.be/vfRVARsZ854  

---

## Author

**Francis Mutabazi**  
African Leadership University  
Machine Learning Techniques I – 2026