# Flight Delay Prediction - Machine Learning Pipeline

## 📖 About This Repository

This repository contains a complete machine learning pipeline for predicting flight delays at the busiest US airports. The project uses historical flight data (2014-2018) from the Bureau of Transportation Statistics to build a predictive model that identifies whether a flight will be delayed by more than 15 minutes.

**Business Context:**  
This solution is designed for a travel booking website to inform customers about the likelihood of flight delays before they book their tickets.

---

## 📁 Repository Contents

- **`onpremises.ipynb`** - Main Jupyter notebook with the complete ML pipeline (data processing, EDA, modeling, evaluation)
- **`oncloud.ipynb`** - AWS SageMaker implementation for cloud-based deployment
- **`requirements.txt`** - Python package dependencies
- **`Final_Project_Data_Science_Pipeline.pdf`** - Project documentation and assignment details
- **`Flight_Delay_Prediction_Presentation.pptx`** - Presentation slides

---

## 🚀 How to Run This Code

### **Prerequisites**
- Python 3.8 or higher
- Jupyter Notebook or JupyterLab
- At least 4GB RAM available

### **Step 1: Clone the Repository**
```bash
git clone https://github.com/YOUR_USERNAME/flight-delay-prediction.git
cd flight-delay-prediction
```

### **Step 2: Install Dependencies**
```bash
pip install -r requirements.txt
```

The required packages include:
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- jupyter

### **Step 3: Download the Dataset**
**Important:** The data files are NOT included in this repository due to their large size.

1. Download the flight data ZIP files from the [BTS website](https://www.transtats.bts.gov/Fields.asp?gnoyr_VQ=FGJ) or the provided SharePoint link
2. Create a folder named `data/` in the project root directory
3. Place all the downloaded ZIP files (approximately 16 files) inside the `data/` folder

Your directory structure should look like:
```
flight-delay-prediction/
├── data/
│   ├── T_ONTIME_REPORTING_*.zip (16 ZIP files)
├── onpremises.ipynb
├── oncloud.ipynb
├── requirements.txt
└── README.md
```

### **Step 4: Run the Jupyter Notebook**
```bash
jupyter notebook onpremises.ipynb
```

Once Jupyter opens in your browser, run the cells sequentially from top to bottom using **Shift + Enter**.

---

## 📊 What to Expect When Running the Code

When you execute `onpremises.ipynb`, the following steps will be performed:

### **1. Data Preprocessing (Step 2)**
- **ZIP Extraction:** Extracts 16 ZIP files containing CSV data
- **CSV Combining:** Combines 17 individual CSV files into one dataset
- **Output:** Combined dataset with ~1 million flight records
- **Time:** 2-5 minutes depending on your system

### **2. Exploratory Data Analysis (Step 2)**
- **Data inspection:** View dataset shape, columns, and basic statistics
- **Missing values analysis:** Identify and handle null values
- **Airport filtering:** Focus on top 9 busiest US airports (ATL, ORD, DFW, DEN, CLT, LAX, IAH, PHX, SFO)
- **Visualizations:** Charts showing delay distributions, airport comparisons, seasonal patterns
- **Output:** Clean dataset with ~1.09 million rows

### **3. Baseline Model Training (Step 3)**
- **Feature preparation:** One-hot encoding of categorical variables (airports, airlines, day of week, month)
- **Train-test split:** 80% training, 20% testing
- **Model:** Logistic Regression with class balancing
- **Training time:** 1-2 minutes
- **Output:** Model performance metrics

**Expected Baseline Results:**
- Accuracy: ~59%
- Precision: ~27%
- Recall: ~62%
- F1-Score: ~37%
- ROC-AUC: ~0.64

### **4. Model Evaluation (Step 3)**
- **Confusion matrix:** Visual representation of predictions
- **Classification report:** Detailed precision, recall, F1 for each class
- **ROC curve:** Model discrimination ability
- **Feature importance:** Which features contribute most to predictions

### **5. Feature Engineering - Iteration II (Step 5)**
- **Holiday indicators:** Adds US federal holidays (2014-2018)
- **Weather data:** Merges historical weather data for each airport
- **Additional features:** Time-based patterns, airport congestion metrics
- **Output:** Enhanced dataset with additional predictive features

### **6. Improved Model Training (Step 6)**
- **Enhanced features:** Uses all engineered features
- **Model retraining:** Logistic Regression with improved feature set
- **Output:** Improved performance metrics

**Expected Improved Results:**
- Better precision (reduced false alarms)
- Higher recall (catch more actual delays)
- Improved F1-score and ROC-AUC

### **7. Model Comparison (Step 7)**
- **Side-by-side comparison:** Baseline vs Improved model
- **Visualizations:** Performance charts
- **Analysis:** Which features improved the model most

### **8. Files Generated**
After running the notebook, you'll find these new files:
- `combined_files.csv` - Combined flight dataset
- `combined_csv_v2.csv` - Tableau-ready visualization dataset
- Various charts and plots (saved as PNG files)

---

## 🎯 Project Goals

**Machine Learning Task:** Binary Classification (Delayed vs On-Time)

**Target Metrics:**
- Accuracy: > 85%
- Precision: > 70% (minimize false delay warnings)
- Recall: > 60% (catch most actual delays)
- F1-Score: > 65%

**Key Features Used:**
- Flight date and time
- Origin and destination airports
- Airline carrier
- Day of week and month
- Distance
- Weather conditions (improved model)
- Holiday indicators (improved model)

---

## 📈 Tableau Dashboard

An interactive dashboard visualizing flight delay patterns is available at:  
**[Tableau Public Link - To be added]**

The dashboard shows:
- Delay rates by airport
- Seasonal delay patterns
- Best/worst days to fly
- Top delayed routes
- Delay severity distribution

---

## 🔧 Troubleshooting

**Problem:** "FileNotFoundError: data folder not found"  
**Solution:** Create a `data/` folder and add the ZIP files as described in Step 3

**Problem:** "ModuleNotFoundError: No module named 'sklearn'"  
**Solution:** Run `pip install -r requirements.txt`

**Problem:** "Memory Error during data processing"  
**Solution:** Close other applications to free up RAM, or reduce the dataset size by processing fewer months

**Problem:** Code runs very slowly  
**Solution:** The first run extracts and processes large files. Subsequent runs are faster since data is already extracted.

---

## 👨‍💻 Author

Data Science Assignment - University of Canberra  
Flight Delay Prediction using Machine Learning

---

## 📄 License

Educational project for academic purposes.  
Dataset source: Bureau of Transportation Statistics (BTS), US Department of Transportation
