# README: Pratilipi Recommendation System

## Introduction
This project aims to build a recommendation system that predicts the top stories a user is likely to read in the future based on their historical reading behavior. The model uses Linear Regression to make predictions and incorporates metadata such as story categories to provide enriched recommendations.

---

## Features
- **Top N Recommendations**: Provides personalized story recommendations for existing users.
- **First-time User Recommendations**: Allows first-time users to get suggestions based on their category preferences.
- **Category Inclusion**: Displays the category (e.g., Romance, Comedy) alongside recommended stories for better context.

---

## Prerequisites and Dependencies
The following dependencies are required to run the code:
- Python 3.7+
- Pandas
- NumPy
- scikit-learn

To install these dependencies, run:
```bash
pip install pandas numpy scikit-learn
```

---

## Dataset Information
### Input Files
1. **user_interaction.csv**:
   - Contains user interactions with stories.
   - Columns: `user_id`, `pratilipi_id`, `read_percent`, `updated_at`

2. **metadata.csv**:
   - Contains metadata about stories.
   - Columns: `author_id`, `pratilipi_id`, `category_name`, `reading_time`, `updated_at`, `published_at`

### Output
1. **Top N Recommendations for Existing Users**:
   - List of story IDs along with their categories.
2. **Recommendations for First-time Users**:
   - Suggested stories based on the selected category.

---

## How to Run the Code
### Step 1: Load the Datasets
Ensure the files `user_interaction.csv` and `metadata.csv` are in the same directory as the script or provide their paths in the `user_interaction_path` and `metadata_path` variables.

### Step 2: Execute the Script
Run the Python script in your preferred environment (e.g., Jupyter Notebook, Google Colab, or a local IDE):
```bash
python pratilipi_recommendation.py
```

### Step 3: Get Recommendations
1. For existing users:
   - The script will output the top 5 recommendations for the first 5 users.
2. For first-time users:
   - Enter your preferred category (e.g., Romance, Comedy) when prompted.
   - The script will provide story suggestions from the chosen category.

---

## Code Explanation
This program is divided into three main phases:

### Phase 1: Data Analysis
- **Loading Datasets**:
  The datasets are loaded using Pandas.
- **Column Validation**:
  Ensures that all required columns are present in the datasets.
- **Merging Data**:
  Combines `user_interaction` and `metadata` using `pratilipi_id` for enriched analysis.

### Phase 2: Train-Test Split and Model Selection
- **Preprocessing**:
  - User and story IDs are encoded as integers to make the data compatible with machine learning algorithms.
  - The `read_percent` column is used as the target variable for prediction.
- **Model Selection**:
  - **Why Linear Regression?**:
    - Linear Regression is computationally efficient and interpretable, making it suitable for this project.
    - It works well for continuous target variables, such as `read_percent`, which represents the percentage of a story read by a user.
    - Compared to other models like Random Forest or SVM, Linear Regression requires less computational power and training time, especially for moderately sized datasets.
    - It avoids overfitting when the relationship between features (user and story IDs) and the target variable is approximately linear.
  - **Other Models Considered**:
    - Random Forest: Although robust, it is computationally expensive and may overfit the data.
    - SVM: Better for smaller datasets but less efficient for larger ones with high cardinality features.
    - Neural Networks: Overkill for this problem due to its simplicity and the lack of complex non-linear relationships.

### Phase 3: Building Recommendations
1. **Model Evaluation**:
   - **Root Mean Square Error (RMSE)**:
     Used to measure the model's prediction accuracy.
2. **Recommendations**:
   - For Existing Users:
     - Predicts `read_percent` for unseen stories and ranks them.
     - Retrieves top N stories with their categories.
   - For First-time Users:
     - Asks for the preferred category.
     - Filters stories from the metadata and provides recommendations.

---

## Example Outputs
### Top N Recommendations for Existing Users
```text
Top 5 Recommendations for Users with Categories:
User 148640: [(235324, 'Romance'), (234110, 'Comedy'), (229172, 'Drama')]
User 20029: [(12107, 'Thriller'), (9556, 'Mystery')]
...
```

### First-time User Recommendation
```text
First-time User Recommendation
Enter your preferred category (e.g., Romance, Comedy, etc.): Romance

Recommended Stories:
Story ID: 1377786216968011, Category: Romance
Story ID: 1377786221362075, Category: Romance
...
```

---

## Notes
1. Ensure the dataset files are properly formatted and contain the required columns.
2. For larger datasets, consider optimizing the code for better performance.

---

## Contact
For issues or queries, please contact [your-email@example.com].


