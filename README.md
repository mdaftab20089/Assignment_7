# Assignment_7: Software Developer Salary Prediction

![Streamlit Badge](https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)  
![Python Badge](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)  
![Machine Learning Badge](https://img.shields.io/badge/Machine_Learning-00C853?style=for-the-badge&logo=TensorFlow&logoColor=white)

**Streamlit Web Application to Predict the Annual Salary of a Software Developer Across Different Countries of the World**

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Project Structure](#project-structure)
- [Screenshots](#screenshots)
- [Importance](#importance)
- [Dependencies](#dependencies)
- [License](#license)
- [Contact](#contact)

---

## Overview

This project is a **Streamlit-based web application** designed to predict the annual salary (in USD) of software developers based on survey data from the Stack Overflow Developer Survey 2020. It incorporates machine learning techniques to estimate salaries based on factors such as country, education level, and years of professional experience. Additionally, the application provides an interactive exploration page with visualizations of salary distributions across countries and experience levels. Predicted salaries are also converted to Indian Rupees (INR) for local relevance.

---

## Features

- **Prediction Page**: Input your country, education level, and years of experience to receive a salary prediction in both USD and INR.
- **Exploration Page**: Interactive visualizations powered by Matplotlib and Streamlit, including:
  - Pie chart illustrating the proportion of survey respondents by country.
  - Bar chart displaying mean salary by country.
  - Line chart showing mean salary trends by years of experience.
- **Data Preprocessing**: Robust data cleaning, including grouping rare categories into "Other", filtering outliers, and standardizing education and experience fields.

---

## Installation

Follow these steps to set up the project locally:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/username/salary-prediction-streamlit.git
   cd salary-prediction-streamlit
   ```

2. **Set Up a Virtual Environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

---

## Usage

1. **Launch the Application**:
   ```bash
   streamlit run app.py
   ```

2. **Interact with the App**:
   - Use the sidebar to switch between **Predict** and **Explore** modes.
   - **Predict**: Enter your details (country, education, experience) and click **Calculate Salary**.
   - **Explore**: View and interact with the generated charts.

---

## How It Works

### 1. Data Loading & Cleaning (`explore.py`)
- Loads data from `survey_results_public.csv`.
- Filters for full-time developers with salaries between $10k and $250k USD.
- Groups rare countries under "Other" using `shorten_categories`.
- Converts experience and education fields into numeric and simplified categories.

### 2. Model Training (Offline)
- A regression model is trained on the cleaned dataset.
- Encoders and the trained model are saved to `saved_steps.pkl` for reuse.

### 3. Prediction Page (`prediction.py`)
- Loads the pickled model, label encoder for country, and one-hot encoder for education.
- Processes user inputs, predicts salary, and converts USD to INR using an exchange rate of 83.00.

### 4. Streamlit Integration (`app.py`)
- Provides a sidebar for page navigation.
- Dynamically renders prediction or exploration functionality based on user selection.

---

## Project Structure

| File/Directory         | Description                              |
|-------------------------|------------------------------------------|
| `app.py`               | Main Streamlit application launcher      |
| `explore.py`           | EDA page with data loading and visuals   |
| `prediction.py`        | Prediction page with model inference     |
| `saved_steps.pkl`      | Pickled regression model and encoders    |
| `survey_results_public.csv` | Raw survey data                   |
| `requirements.txt`     | List of Python dependencies             |
| `README.md`            | Project documentation (this file)        |

---

## Screenshots

### Prediction & Conversion in INR
![Prediction Interface](images/prediction_interface.png)

### Mean Salary Based on Experience
![Salary vs Experience](images/salary_vs_experience.png)

### Mean Salary Based on Country
![Salary by Country](images/salary_by_country.png)

### Data Proportion by Country
![Survey Distribution](images/survey_distribution.png)

---

## Importance

This application serves multiple stakeholders:
- **Job Seekers**: Gain insights into market salary expectations.
- **Recruiters**: Establish competitive salary benchmarks.
- **Data Scientists**: Practice a complete ML pipeline, from data preprocessing to deployment.

The exploratory visualizations offer valuable insights into global salary trends and experience-based compensation variations.

---

## Dependencies

- Python 3.8+
- `pandas`
- `numpy`
- `scikit-learn`
- `streamlit`
- `matplotlib`

Install all dependencies with:
```bash
pip install pandas numpy scikit-learn streamlit matplotlib
```

---

## License

This project is licensed under the **MIT License**. For more details, refer to the `LICENSE` file.

---

## Contact

For inquiries or collaboration, feel free to reach out:
- **Email**: aftabrahi20089@gmail.com
