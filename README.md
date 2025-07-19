# Assignment_7
Streamlit Web Application to Predict the Annual Salary of a Software Developer in the Different Country of The World. 

# Software Developer Salary Prediction

A Streamlit web application that predicts software developer salaries based on survey data from the Stack Overflow Developer Survey 2020. It also provides exploratory data analysis (EDA) visualizations of salary distributions across countries and experience levels.

---

## Table of Contents

* [Overview](#overview)
* [Features](#features)
* [Installation](#installation)
* [Usage](#usage)
* [How It Works](#how-it-works)
* [Project Structure](#project-structure)
* [Screenshots](#screenshots)
* [Importance](#importance)
* [Dependencies](#dependencies)
* [License](#license)

---

## Overview

This project leverages machine learning to predict a software developer's annual salary (in USD) given their country, education level, and years of professional experience. The Streamlit interface allows users to either explore the dataset or input their details and get a salary estimate. It also converts the predicted USD salary into Indian Rupees (INR).

## Features

* **Prediction Page**: Input your country, education level, and years of experience to get a predicted salary in USD and INR.
* **Exploration Page**: Interactive visualizations powered by Matplotlib and Streamlit:

  * Pie chart showing the proportion of survey respondents by country.
  * Bar chart of mean salary by country.
  * Line chart of mean salary by years of experience.
* **Data Cleaning**: Handles rare categories by grouping them into "Other", filters out outliers, and cleans educational and experience fields.

---

## Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/username/salary-prediction-streamlit.git
   cd salary-prediction-streamlit
   ```
2. Create and activate a virtual environment:

   ```bash
   python -m venv venv
   source venv/bin/activate  # on Windows: venv\Scripts\activate
   ```
3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

---

## Usage

1. Run the Streamlit app:

   ```bash
   streamlit run app.py
   ```
2. In the browser, select **Predict** or **Explore** from the sidebar.

   * **Predict**: Fill in the dropdowns and slider, then click **Calculate Salary**.
   * **Explore**: View interactive charts of the dataset.

---

## How It Works

1. **Data Loading & Cleaning** (`explore.py`):

   * Loads `survey_results_public.csv`.
   * Filters for full-time developers and reasonable salary ranges (10k–250k USD).
   * Groups rare countries under "Other" using `shorten_categories`.
   * Cleans experience and education fields to numeric and simplified categories.
2. **Model Training (Offline)**:

   * A regression model is trained on the cleaned data.
   * Encoders and the trained model are saved to `saved_steps.pkl`.
3. **Prediction Page** (`prediction.py`):

   * Loads the pickled model, label encoder for country, and one-hot encoder for education.
   * Encodes user inputs and predicts salary with the regression model.
   * Converts USD to INR using a fixed exchange rate (83.00).
4. **Streamlit Integration** (`app.py`):

   * Sidebar to switch between pages.
   * Dynamic rendering of either exploration or prediction functionality.

---

## Project Structure

```
├── app.py              # Streamlit main launcher
├── explore.py          # EDA page: data loading & visualizations
├── prediction.py       # Prediction page: model loading & inference
├── saved_steps.pkl     # Pickled regression model and encoders
├── survey_results_public.csv  # Raw survey data
├── requirements.txt    # Python dependencies
└── README.md           # Project documentation (this file)
```

---

## Screenshots

**Prediction & Conversion in INR**

!\[Prediction Interface]\(Screenshot 2025-07-20 020015.png)

**Mean Salary Based on Experience**

!\[Salary vs Experience]\(Screenshot 2025-07-20 015929.png)

**Mean Salary Based on Country**

!\[Salary by Country]\(Screenshot 2025-07-20 015923.png)

**Data Proportion by Country**

!\[Survey Distribution]\(Screenshot 2025-07-20 015916.png)

---

## Importance

Predicting salaries helps:

* **Job Seekers** gauge their market worth.
* **Recruiters** set competitive salary ranges.
* **Data Scientists** practice end-to-end ML pipelines: data cleaning, modeling, and deployment.

The exploratory visualizations provide insights into how compensation varies globally and with experience.

---

## Dependencies

* Python 3.8+
* pandas
* NumPy
* scikit-learn
* Streamlit
* Matplotlib

Install via:

```bash
pip install pandas numpy scikit-learn streamlit matplotlib
```

---

## License

This project is released under the MIT License. See `LICENSE` for details.
