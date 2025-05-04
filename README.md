# Housing Price Exploratory Data Analysis

**Repository:** [https://github.com/Naeem1144/Exploratory-Data-Analysis/](https://github.com/Naeem1144/Exploratory-Data-Analysis/)

## Overview

This project performs an Exploratory Data Analysis (EDA) on the `Housing.csv` dataset, which is included in this repository. The primary goal is to understand the dataset's structure, identify key features influencing housing prices, analyze distributions, check for correlations, and prepare the data for potential future modeling tasks. The analysis utilizes various Python libraries for data manipulation, visualization (including interactive plots), and preprocessing.

## Dataset

The analysis uses the `Housing.csv` dataset.

**Features:**

*   `price`: The selling price of the house. (Target Variable)
*   `area`: The total area of the property in square feet.
*   `bedrooms`: Number of bedrooms.
*   `bathrooms`: Number of bathrooms.
*   `stories`: Number of stories (floors).
*   `mainroad`: Whether the house is connected to the main road (yes/no).
*   `guestroom`: Whether the house has a guest room (yes/no).
*   `basement`: Whether the house has a basement (yes/no).
*   `hotwaterheating`: Whether the house has hot water heating (yes/no).
*   `airconditioning`: Whether the house has air conditioning (yes/no).
*   `parking`: Number of parking spots.
*   `prefarea`: Whether the house is located in a preferred area (yes/no).
*   `furnishingstatus`: Furnishing status of the house (furnished/semi-furnished/unfurnished).

## Objectives

*   Load and inspect the housing dataset.
*   Check for and handle missing values and duplicates.
*   Analyze the distribution of individual features (Univariate Analysis).
*   Identify and address skewness in numerical features.
*   Visualize relationships between different features, particularly with the target variable `price` (Bivariate/Multivariate Analysis).
*   Gain insights into factors that might affect housing prices.
*   Perform basic data preprocessing like encoding categorical variables.

## Tools and Libraries Used

*   **Python:** Core programming language.
*   **Pandas:** Data manipulation and analysis.
*   **NumPy:** Numerical operations.
*   **Matplotlib:** Static data visualization.
*   **Seaborn:** Statistical data visualization (built on Matplotlib).
*   **Plotly Express:** Interactive data visualization.
*   **Scikit-learn:** Data preprocessing (`PowerTransformer`, `get_dummies`).
*   **Jupyter Notebook:** Interactive development environment.

## Exploratory Data Analysis Steps (Performed in the Notebook)

1.  **Data Loading & Initial Inspection:**
    *   Loaded `Housing.csv` into a Pandas DataFrame.
    *   Examined the first few rows (`.head()`) and the overall shape (`.shape`).
2.  **Data Cleaning:**
    *   Checked for missing values (`.isna().sum()`). **Result:** No missing values found.
    *   Checked for duplicate rows (`.duplicated().sum()`). **Result:** No duplicate rows found.
3.  **Data Preprocessing:**
    *   Set display options for float formatting.
    *   Encoded binary categorical features (`guestroom`, `basement`, `hotwaterheating`, `airconditioning`, `prefarea`) into numerical format (0/1) using `pd.get_dummies`.
4.  **Univariate Analysis:**
    *   Analyzed the distribution of numerical features (`price`, `area`, `bedrooms`, `bathrooms`, `stories`, `parking`) using Kernel Density Estimation (KDE) plots (`sns.kdeplot`).
    *   Calculated skewness for numerical features (`.skew()`).
    *   Applied `PowerTransformer` to reduce skewness in `price` and `area` and visualized the distributions before and after transformation.
5.  **Bivariate/Multivariate Analysis:**
    *   Used joint plots (`sns.jointplot`) with KDE to visualize the relationship and distribution between:
        *   `price` and `area` (colored by `furnishingstatus`)
        *   `price` and `bedrooms` (colored by `stories`)
    *   Created an interactive scatter plot (`px.scatter`) to visualize the relationship between `price` and `area`, with points colored by the number of `stories`. (See `iframe_figures/` directory for saved plots or run the notebook).
    *   Performed grouped analysis (`.groupby()`) to compare the mean values of numerical features based on `prefarea` and `bedrooms`.

## Key Findings & Observations

*   The dataset was clean with no missing values or duplicates.
*   **Price and Area:** These features are positively correlated and were initially positively skewed. Applying a `PowerTransformer` significantly reduced their skewness. Higher area generally corresponds to higher price.
*   **Other Features vs. Price:** `bathrooms`, `stories`, `parking`, `airconditioning`, and `prefarea` show positive correlations/associations with `price`. The influence of `bedrooms` appears slightly less pronounced.
*   **Feature Interactions:** The relationship between `price` and `area`/`bedrooms` is visibly influenced by factors like the number of `stories` and `furnishingstatus`.

## Visualizations

*   Kernel Density Estimation (KDE) Plots
*   Joint Plots (with KDE)
*   Categorical Plots (`sns.catplot`)
*   Scatter Plots (Interactive via Plotly)

## How to Use

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/Naeem1144/Exploratory-Data-Analysis.git
    cd Exploratory-Data-Analysis
    ```
2.  **Install dependencies:** Ensure you have Python installed. Install the required libraries:
    ```bash
    pip install pandas numpy matplotlib seaborn plotly scikit-learn jupyter
    ```
    *(Consider creating a `requirements.txt` file for easier dependency management)*
3.  **Launch Jupyter Notebook:**
    ```bash
    jupyter notebook "Exploratory Data Analysis.ipynb"
    ```
4.  **Run the cells:** Execute the cells sequentially within the Jupyter environment to reproduce the analysis. The `Housing.csv` file is included and should be loaded correctly using the relative path in the notebook. Interactive plots will be generated within the notebook or saved as HTML in the `iframe_figures` directory if configured.
