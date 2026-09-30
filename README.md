# FinanceAdvisor

**An AI-powered personal finance management and financial analytics web application built with Flask and Machine Learning.**

FinanceAdvisor helps users track their financial information, analyze spending patterns, predict future expenses, evaluate financial health, and plan savings goals through a centralized web interface.

---

## Overview

FinanceAdvisor is a full-stack web application that combines **Python, Flask, SQLite, SQLAlchemy, and Machine Learning** to provide personalized financial insights.

The system provides two primary machine learning capabilities:

* **Expense Prediction** — predicts the expected expense for the next month using regression.
* **Financial Health Classification** — classifies a user's financial condition as Healthy, Moderate, or Risky.

In addition, the application provides financial dashboards, goal planning, prediction history, profile management, and interactive visualizations.

> **Disclaimer:** FinanceAdvisor is an academic and educational project. Its predictions and financial insights are intended for demonstration purposes and should not be considered professional financial advice.

---

## Key Features

### Financial Dashboard

The dashboard provides a centralized view of the user's financial information, including:

* Monthly income
* Total expenses
* Savings
* Financial health
* Expense distribution
* Expense trends
* Financial insights
* Recent financial activity

### Expense Prediction

FinanceAdvisor predicts the user's expected expense for the following month based on financial and spending information.

The prediction model uses:

* Income
* Food expenses
* Shopping expenses
* Transport expenses
* Bills
* Entertainment expenses
* Other expenses
* Previous total expenses

**Model:** Random Forest Regressor

**Baseline:** Linear Regression

**Evaluation Metrics:**

* MAE
* MSE
* RMSE
* R² Score

### Financial Health Classification

The application evaluates the user's financial condition using:

* Income
* Total expenses
* Savings
* Debt
* Savings percentage

The system classifies the financial condition into:

* Healthy
* Moderate
* Risky

**Model:** Random Forest Classifier

**Baseline:** Logistic Regression

**Evaluation Metrics:**

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix

### Goal Planner

The Goal Planner helps users determine the monthly savings required to achieve a financial goal within a specified period.

The calculation is based on:

```text
Required Monthly Saving = Goal Amount / Target Months
```

It also evaluates whether the target is achievable based on the user's current monthly savings.

### Prediction History

The application maintains a history of:

* Expense predictions
* Financial health predictions
* Goal planning calculations

Users can access previous results and review their financial analysis.

### Profile Management

Users can manage:

* Personal information
* College
* Location
* Monthly income
* Currency
* Application theme
* Expense reminder preferences
* Goal notification preferences
* Email update preferences

### User Authentication

FinanceAdvisor provides:

* User registration
* Secure password hashing
* Login and logout
* Session-based authentication
* Protected application routes

---

## Technology Stack

| Category          | Technologies                 |
| ----------------- | ---------------------------- |
| Backend           | Python, Flask                |
| Frontend          | HTML5, CSS3, JavaScript      |
| UI Framework      | Bootstrap 5                  |
| Templates         | Jinja2                       |
| Charts            | Chart.js                     |
| Database          | SQLite                       |
| ORM               | Flask-SQLAlchemy, SQLAlchemy |
| Data Processing   | Pandas, NumPy                |
| Machine Learning  | Scikit-learn                 |
| Model Persistence | Joblib                       |
| Development       | Visual Studio Code, Git      |

---

## Machine Learning

FinanceAdvisor implements two machine learning pipelines.

### 1. Expense Prediction

This is a regression problem where the model predicts the expected expense for the following month.

```text
Financial Data
      |
      v
Data Preparation
      |
      v
Feature Selection
      |
      v
Train/Test Split
      |
      v
Random Forest Regressor
      |
      v
Model Evaluation
      |
      v
Saved Model
      |
      v
Next-Month Expense Prediction
```

### 2. Financial Health Classification

This is a classification problem where the model determines the user's financial health category.

```text
Financial Data
      |
      v
Data Preparation
      |
      v
Feature Selection
      |
      v
Train/Test Split
      |
      v
Random Forest Classifier
      |
      v
Model Evaluation
      |
      v
Saved Model
      |
      v
Financial Health Classification
```

---

## Project Architecture

```text
                         FinanceAdvisor
                              |
             +----------------+----------------+
             |                |                |
             v                v                v
         Frontend          Flask API        Database
      HTML/CSS/JS           Backend          SQLite
       Bootstrap               |
       Chart.js                |
             |                 |
             +--------+--------+
                      |
                      v
              Machine Learning
                      |
          +-----------+-----------+
          |                       |
          v                       v
   Expense Prediction     Financial Health
    Random Forest          Random Forest
     Regressor              Classifier
          |                       |
          v                       v
  Next-Month Expense      Health Classification
```

---

## Project Structure

```text
FinanceAdvisor/
│
├── app.py
├── config.py
├── models.py
├── ml_service.py
├── generate_dataset.py
├── train_models.py
├── requirements.txt
├── README.md
│
├── database/
│   └── finance.db
│
├── dataset/
│   ├── expense_data.csv
│   └── financial_health_data.csv
│
├── models/
│   ├── expense_regressor.pkl
│   ├── expense_regressor_meta.json
│   ├── financial_classifier.pkl
│   └── financial_classifier_meta.json
│
├── static/
│   ├── css/
│   │   └── style.css
│   │
│   ├── images/
│   │
│   └── js/
│       └── script.js
│
└── templates/
    ├── base.html
    ├── login.html
    ├── register.html
    ├── dashboard.html
    ├── expense_prediction.html
    ├── financial_status.html
    ├── goal_planner.html
    ├── history.html
    ├── profile.html
    ├── 404.html
    └── 500.html
```

---

## Application Modules

| Module             | Description                                              |
| ------------------ | -------------------------------------------------------- |
| Authentication     | User registration, login, logout, and session management |
| Dashboard          | Financial overview and personalized insights             |
| Expense Prediction | Predicts expected future expenses                        |
| Financial Status   | Classifies financial health                              |
| Goal Planner       | Calculates required monthly savings                      |
| History            | Stores and displays previous analyses                    |
| Profile            | Manages user information and preferences                 |
| Notifications      | Provides application notification information            |

---

## Database Design

FinanceAdvisor uses **SQLite** with **SQLAlchemy ORM**.

The main database entities are:

### User

Stores user account and preference information.

### FinancialRecord

Stores income, expenses, savings, and debt information.

### PredictionHistory

Stores previous prediction and analysis results.

### Goal

Stores financial goals, required savings, and goal status.

Relationship structure:

```text
User
 |
 +---- FinancialRecord
 |
 +---- PredictionHistory
 |
 +---- Goal
```

---

## Dataset

FinanceAdvisor uses two datasets for machine learning.

### Expense Dataset

```text
dataset/expense_data.csv
```

The dataset contains financial spending information used for expense prediction.

Key features include:

```text
income
food_expense
shopping_expense
transport_expense
bills
entertainment
other_expense
previous_total_expense
next_month_expense
```

Target:

```text
next_month_expense
```

### Financial Health Dataset

```text
dataset/financial_health_data.csv
```

Key features include:

```text
income
total_expense
savings
debt
savings_percentage
financial_status
```

Target:

```text
financial_status
```

Classes:

```text
Healthy
Moderate
Risky
```

---

## Installation

### Prerequisites

Make sure the following are installed:

* Python 3.10 or later
* Git
* A modern web browser

### 1. Clone the Repository

```bash
git clone <YOUR-GITHUB-REPOSITORY-URL>
cd FinanceAdvisor
```

### 2. Create a Virtual Environment

#### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

#### Linux/macOS

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Train the Machine Learning Models

The project includes a model training script.

Run:

```bash
python train_models.py
```

This process trains the regression and classification models and saves the resulting model files in the `models/` directory.

Generated model files include:

```text
models/
├── expense_regressor.pkl
├── expense_regressor_meta.json
├── financial_classifier.pkl
└── financial_classifier_meta.json
```

---

## Run the Application

Start the Flask application:

```bash
python app.py
```

The application will be available at:

```text
http://127.0.0.1:5000
```

Open the address in your browser.

---

## Application Routes

The application includes the following major routes:

| Route                  | Purpose                    |
| ---------------------- | -------------------------- |
| `/`                    | Application entry point    |
| `/login`               | User login                 |
| `/register`            | User registration          |
| `/logout`              | User logout                |
| `/dashboard`           | Financial dashboard        |
| `/expense-prediction`  | Expense prediction page    |
| `/financial-status`    | Financial health page      |
| `/goal-planner`        | Goal planning page         |
| `/history`             | Prediction history         |
| `/history/<record_id>` | Individual history details |
| `/profile`             | User profile               |

Prediction and calculation endpoints include:

```text
/predict-expense
/predict-financial-status
/calculate-goal
```

---

## Configuration

Application configuration is managed through `config.py`.

The application supports environment variables for important configuration values:

```text
SECRET_KEY
DATABASE_URL
```

For production deployment, sensitive configuration values should be stored as environment variables rather than hard-coded in source code.

Example:

```bash
SECRET_KEY=your-secure-secret-key
DATABASE_URL=your-database-url
```

---

## Model Storage

The trained models are persisted using Joblib.

```text
expense_regressor.pkl
financial_classifier.pkl
```

Model metadata is stored separately:

```text
expense_regressor_meta.json
financial_classifier_meta.json
```

This allows the application to load trained models without retraining them every time the application starts.

---

## Security

The application implements basic security features including:

* Password hashing
* Session-based authentication
* Protected routes
* User-specific database records
* Input validation
* Environment-based configuration support

For production deployment, additional security measures should be considered, including:

* HTTPS
* CSRF protection
* Secure cookie configuration
* Production-grade secret management
* Database security
* Rate limiting
* Stronger authentication mechanisms

---

## Screenshots

Add screenshots of the application here after uploading them to your repository.

Example:

```markdown
## Screenshots

### Dashboard
![Dashboard](screenshots/dashboard.png)

### Expense Prediction
![Expense Prediction](screenshots/expense-prediction.png)

### Financial Status
![Financial Status](screenshots/financial-status.png)

### Goal Planner
![Goal Planner](screenshots/goal-planner.png)
```

Recommended repository structure:

```text
screenshots/
├── dashboard.png
├── expense-prediction.png
├── financial-status.png
└── goal-planner.png
```

---

## Limitations

* The machine learning models depend on the quality and characteristics of the available datasets.
* The current datasets are intended for project and demonstration purposes.
* Predictions may not accurately represent real-world financial outcomes.
* The application does not currently connect directly to bank or payment accounts.
* Goal planning is based on calculated savings requirements rather than machine learning.
* The system is not intended to replace professional financial advice.

---

## Future Enhancements

Potential improvements include:

1. Integration with real-time banking and transaction data.
2. Deployment using a cloud platform.
3. Mobile application development.
4. More advanced machine learning and deep learning models.
5. Automated transaction categorization.
6. Personalized long-term budgeting recommendations.
7. Advanced financial forecasting.
8. Automated financial reports and downloadable statements.
9. Investment planning and portfolio analysis.
10. Improved security and production-grade authentication.

---

## Requirements

The project dependencies are defined in `requirements.txt`.

```text
Flask>=3.0
Flask-SQLAlchemy>=3.1.1
SQLAlchemy>=2.0.30
pandas>=2.0
numpy>=1.24
scikit-learn>=1.3
joblib>=1.3
```

---

## Disclaimer

FinanceAdvisor is an academic and educational project developed to demonstrate the integration of web technologies, databases, data analysis, and machine learning for personal finance management.

The financial predictions and classifications generated by this application are for demonstration purposes only and should not be treated as professional financial advice.

---

## Author

**K. Hari Keerthana**
**M. Akshitha**
**M. Neeraja**

B.Tech in Artificial Intelligence and Machine Learning
Malla Reddy Engineering College for Women
India

---

## License

This project is intended for educational and academic purposes.

If you plan to distribute the project publicly, add an appropriate open-source license such as MIT License based on your intended usage.

---

## Getting Started

```bash
git clone <YOUR-GITHUB-REPOSITORY-URL>
cd FinanceAdvisor

python -m venv venv
venv\Scripts\activate

pip install -r requirements.txt

python train_models.py
python app.py
```

Open:

```text
http://127.0.0.1:5000
```

The application is then ready to use.
