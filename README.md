# Time Series Analysis and Forecasting

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![ARIMA](https://img.shields.io/badge/Model-ARIMA-orange)
![Time Series](https://img.shields.io/badge/Analysis-Time%20Series-purple)

A comprehensive time series analysis and forecasting project using ARIMA models to predict property prices with bootstrapping techniques for improved model stability.

## 📊 Project Overview

This project implements a robust time series forecasting system using ARIMA (Autoregressive Integrated Moving Average) models to predict property prices. The implementation includes exploratory data analysis, model selection, performance evaluation, and bootstrapping for enhanced prediction stability.

## 🎯 Key Features

- **Exploratory Data Analysis (EDA)** with comprehensive visualizations
- **ARIMA Model Selection** using auto_arima for optimal parameter tuning
- **Time Series Decomposition** to identify trends and seasonality
- **Bootstrapping Techniques** for improved model stability
- **Performance Metrics** including RMSE and MAPE
- **Interactive Visualizations** of forecasts and model performance

## 📁 Project Structure

```
Time-Series-Analysis-and-Forecasting/
├── 📓 time_series_analysis.ipynb    # Main analysis notebook
├── 📊 raw_sales.csv                 # Dataset (29,581 property sales records)
├── 📈 visualizations/               # Generated plots and charts
├── 📋 requirements.txt              # Python dependencies
└── 📄 README.md                     # Project documentation
```

## 🛠️ Installation & Setup

### Prerequisites
- Python 3.8 or higher
- pip package manager

### Step 1: Clone the Repository
```bash
git clone https://github.com/VincentOracle/Time-Series-Analysis-and-Forecasting.git
cd Time-Series-Analysis-and-Forecasting
```

### Step 2: Create Virtual Environment (Recommended)
```bash
python -m venv ts_env
source ts_env/bin/activate  # On Windows: ts_env\Scripts\activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Required Packages
```python
pandas>=1.3.0
numpy>=1.21.0
matplotlib>=3.4.0
seaborn>=0.11.0
statsmodels>=0.13.0
pmdarima>=2.0.0
scikit-learn>=1.0.0
jupyter>=1.0.0
```

## 📈 Dataset Description

**File:** `raw_sales.csv`
- **Records:** 29,581 property sales
- **Features:**
  - `datesold`: Date of property sale
  - `postcode`: Location postal code
  - `price`: Sale price
  - `propertyType`: Type of property
  - `bedrooms`: Number of bedrooms

## 🔬 Methodology

### 1. Exploratory Data Analysis (EDA)
- Time series visualization
- Trend and seasonality identification
- Statistical summary analysis
- Missing value detection

### 2. Time Series Decomposition
- **Additive Model**: Trend + Seasonality + Residuals
- Component analysis for underlying patterns
- Seasonal pattern identification

### 3. ARIMA Model Implementation
```python
from pmdarima import auto_arima

# Automatic parameter selection
model = auto_arima(train_data, 
                   seasonal=True,
                   m=12,  # Monthly seasonality
                   trace=True,
                   error_action='ignore',
                   suppress_warnings=True)
```

### 4. Model Training & Evaluation
- **Train-Test Split**: 80% training, 20% testing
- **Performance Metrics**:
  - Root Mean Squared Error (RMSE)
  - Mean Absolute Percentage Error (MAPE)

### 5. Bootstrapping for Stability
```python
# Multiple model training on bootstrapped samples
bootstrap_predictions = []
for _ in range(num_bootstraps):
    sample = resample(train_data)
    model.fit(sample)
    pred = model.predict(n_periods=len(test_data))
    bootstrap_predictions.append(pred)
```

## 📊 Implementation Details

### Model Selection Process
The optimal ARIMA model was selected using `auto_arima` which identified:
- **ARIMA Order**: (3,1,1)
- **Components**: 
  - 3 autoregressive terms
  - 1 degree of differencing
  - 1 moving average term
- **Selection Criterion**: Akaike Information Criterion (AIC)

### Key Implementation Steps

1. **Data Preprocessing**
   - Date parsing and indexing
   - Missing value handling
   - Data normalization

2. **Trend Analysis**
   - Visual trend identification
   - Statistical trend tests
   - Seasonal decomposition

3. **Model Optimization**
   - Parameter grid search
   - Cross-validation
   - Model diagnostics

4. **Forecast Generation**
   - Training period: First 80% of data
   - Testing period: Remaining 20%
   - Confidence interval calculation

## 📈 Results & Performance

### Model Evaluation Metrics
- **RMSE**: 18,602.766
- **MAPE**: 22.325%

### Key Findings
1. **Strong Upward Trend**: Consistent price appreciation over time
2. **Yearly Seasonality**: Regular seasonal patterns observed
3. **Autocorrelation**: Strong correlation with 1-3 month lags
4. **Model Performance**: Good predictive accuracy with room for optimization

### Visualizations Generated
- Time series plots with trends
- Seasonal decomposition charts
- Autocorrelation function (ACF) plots
- Forecast vs actual comparisons
- Residual analysis plots

## 🚀 Usage

### Running the Analysis

1. **Start Jupyter Notebook**
```bash
jupyter notebook time_series_analysis.ipynb
```

2. **Execute Cells Sequentially**
   - Data loading and inspection
   - Exploratory data analysis
   - Model training and evaluation
   - Forecast generation

### Customizing the Analysis

```python
# Modify model parameters
custom_model = auto_arima(data,
                         start_p=0, start_q=0,
                         max_p=5, max_q=5,
                         seasonal=True,
                         m=12,
                         stepwise=True,
                         suppress_warnings=True)
```

## 🔍 Technical Insights

### ARIMA Model Components
- **AR (Autoregressive)**: Uses dependent relationship between observations
- **I (Integrated)**: Differencing to make time series stationary
- **MA (Moving Average)**: Dependency between observation and residual errors

### Bootstrapping Benefits
- Improved model stability
- Reduced overfitting
- Better generalization
- Confidence interval estimation

### Performance Interpretation
- **RMSE**: Lower values indicate better accuracy
- **MAPE**: Percentage error for relative performance assessment
- **AIC**: Model selection criterion balancing fit and complexity

## 📚 Academic References

This implementation is based on established time series methodologies:

1. **Bisgaard, S., & Kulahci, M. (2011)** - *Time series analysis and forecasting by example*
2. **Yaffee, R. A., & McGee, M. (2000)** - *Introduction to time series analysis*
3. **Parzen, E. (1982)** - ARARMA models for time series analysis
4. **Navarro-Esbrı, J. et al. (2002)** - Time series analysis techniques
5. **Geurts, M. (1977)** - Time series analysis and control
6. **Fildes, R., & Makridakis, S. (1995)** - Empirical accuracy studies

## 🛠️ Advanced Features

### Model Diagnostics
- Residual analysis
- Normality tests
- Heteroscedasticity checks
- Model stability verification

### Extended Capabilities
- Multiple seasonal patterns
- Exogenous variable incorporation
- Rolling forecast validation
- Model comparison frameworks

## 📈 Business Applications

### Real Estate
- Property price forecasting
- Investment timing optimization
- Market trend analysis
- Risk assessment

### General Applications
- Sales forecasting
- Demand prediction
- Financial market analysis
- Resource planning

## 🔮 Future Enhancements

### Planned Improvements
1. **Advanced Models**: SARIMA, Prophet, LSTM networks
2. **Feature Engineering**: Additional economic indicators
3. **Ensemble Methods**: Combined forecasting approaches
4. **Real-time Updates**: Dynamic model retraining
5. **Dashboard**: Interactive visualization interface

### Research Directions
- Multivariate time series analysis
- Transfer learning applications
- Uncertainty quantification
- Causal impact analysis

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for:

- Bug fixes
- Performance improvements
- Additional features
- Documentation enhancements
- Dataset expansions

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 👨‍💻 Author

**Were Vincent Ouma**  
*Computer Science Student*

- 📧 Email: [oumawere20021@gmail.com](mailto:oumawere20021@gmail.com)
- 📱 Phone: +254 768653509
- 🏫 Institution: Kenyatta University
- 🎓 School: Pure and Applied Sciences  
- 📚 Department: Computing and Information Science
- 💻 Faculty: Computer Science

### Academic Affiliation
**Kenyatta University**  
School of Pure and Applied Sciences  
Department of Computing and Information Science  
Faculty of Computer Science

## 🙏 Acknowledgments

- Kenyatta University Faculty for guidance
- Open source community for libraries and tools
- Data providers for the property sales dataset
- Researchers in time series analysis field

---

**Note**: This project is for educational and research purposes. Always validate models with domain expertise before making real-world decisions.

*Last Updated: May 2024*  
*Project Status: Completed Development*
