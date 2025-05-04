# Housing Price Exploratory Data Analysis

## Overview

This project performs an Exploratory Data Analysis (EDA) on the `Housing.csv` dataset. The primary goal is to understand the dataset's structure, identify key features influencing housing prices, analyze distributions, check for correlations, and prepare the data for potential future modeling tasks. The analysis utilizes various Python libraries for data manipulation, visualization, and preprocessing.

## Dataset

The analysis uses the `Housing.csv` dataset, which contains information about various characteristics of houses and their corresponding prices.

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

## Exploratory Data Analysis Steps

1.  **Data Loading & Initial Inspection:**
    *   Loaded the `Housing.csv` dataset into a Pandas DataFrame.
    *   Examined the first few rows (`.head()`) and the overall shape (`.shape`).
2.  **Data Cleaning:**
    *   Checked for missing values (`.isna().sum()`). **Result:** No missing values found.
    *   Checked for duplicate rows (`.duplicated().sum()`). **Result:** No duplicate rows found.
3.  **Data Preprocessing:**
    *   Set display options for float formatting.
    *   Encoded binary categorical features (`guestroom`, `basement`, `hotwaterheating`, `airconditioning`, `prefarea`) into numerical format (0/1) using `pd.get_dummies`. *Note: `mainroad` was likely intended to be encoded similarly but wasn't explicitly shown in the provided code snippet after the EDA function definitions.*
4.  **Univariate Analysis:**
    *   Analyzed the distribution of numerical features (`price`, `area`, `bedrooms`, `bathrooms`, `stories`, `parking`) using Kernel Density Estimation (KDE) plots (`sns.kdeplot`).
    *   Calculated skewness for numerical features (`.skew()`).
    *   Applied `PowerTransformer` (specifically Box-Cox or Yeo-Johnson, depending on data) to reduce skewness in `price` and `area` and visualized the distributions before and after transformation.
    *   Defined a function for count plots (`sns.countplot`) for categorical features (though not explicitly called on original categoricals in the provided snippets).
5.  **Bivariate/Multivariate Analysis:**
    *   Used joint plots (`sns.jointplot`) with KDE to visualize the relationship and distribution between:
        *   `price` and `area` (colored by `furnishingstatus`)
        *   `price` and `bedrooms` (colored by `stories`)
    *   Created an interactive scatter plot (`px.scatter`) to visualize the relationship between `price` and `area`, with points colored by the number of `stories`.
    *   Performed grouped analysis (`.groupby()`) to compare the mean values of numerical features based on `prefarea` and `bedrooms`.

## Key Findings & Observations

*   The dataset was clean with no missing values or duplicates.
*   **Price and Area:** These features are positively correlated and were initially positively skewed. Applying a `PowerTransformer` significantly reduced their skewness, making them more suitable for models assuming normality. Higher area generally corresponds to higher price.
*   **Other Features vs. Price:**
    *   `bathrooms`, `stories`, and `parking` show a positive correlation with `price`.
    *   `bedrooms` appears to have a weaker positive correlation with `price` compared to `area` or `bathrooms`. Houses with 4 bedrooms have a slightly higher average price than those with 5 (though the sample size for 5/6 bedrooms is small).
    *   Features like `airconditioning` and `prefarea` likely increase the price (inferred from encoding and common sense, confirmed by groupby analysis for `prefarea`).
*   **Categorical Insights:**
    *   Binary features like `guestroom`, `basement`, `hotwaterheating`, `airconditioning`, `prefarea` were converted to numerical representations. Their presence or absence likely impacts the price.
    *   `furnishingstatus` also seems to play a role, with furnished/semi-furnished potentially commanding higher prices.
*   **Feature Interactions:** The relationship between `price` and `area`/`bedrooms` is influenced by the number of `stories` and `furnishingstatus`.

## Visualizations

*   Kernel Density Estimation (KDE) Plots
*   Count Plots (function defined)
*   Joint Plots (with KDE)
*   Scatter Plots (Interactive via Plotly)

## How to Use

1.  **Clone the repository:**
    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```
2.  **Install dependencies:** Ensure you have Python installed. Install the required libraries:
    ```bash
    pip install pandas numpy matplotlib seaborn plotly scikit-learn jupyter
    ```
3.  **Launch Jupyter Notebook:**
    ```bash
    jupyter notebook "Exploratory Data Analysis.ipynb"
    ```
4.  **Run the cells:** Execute the cells sequentially to reproduce the analysis. Make sure `Housing.csv` is in the same directory as the notebook or update the file path accordingly.
