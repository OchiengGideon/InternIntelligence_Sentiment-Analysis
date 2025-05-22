# Product Reviews Sentiment Analysis

This project performs exploratory data analysis (EDA) and sentiment analysis on customer reviews for electronic products (e.g., Xbox Series S) using Natural Language Processing (NLP) techniques. The analysis involves reading multiple `.csv` files, preprocessing data, visualizing trends, and using VADER sentiment scoring.

---

## Project Structure

```
.
├── Data/                  # Directory containing CSV files
├── sentiment_analysis.py  # Main Python script for EDA & NLP
├── README.md              # Project overview and usage
```

---

## Libraries Used

* `pandas`, `numpy` – Data manipulation
* `matplotlib`, `seaborn` – Visualization
* `nltk` – Natural Language Processing (tokenization, lemmatization, stopwords, sentiment)
* `tqdm` – Progress bar for loops

---

## Data Loading

The script reads all `.csv` files from the `./Data/` directory using the `read_all_data()` function and combines them into one DataFrame for analysis.

---

## Dataset Overview

| Column          | Description                                                |
| --------------- | ---------------------------------------------------------- |
| Unnamed: 0      | Row identifier/index                                       |
| product\_name   | Name of the reviewed product                               |
| review\_text    | Text of the customer review (some missing values handled)  |
| product\_rating | Customer rating (1 to 5 scale)                             |
| review\_date    | Date when the review was submitted (converted to datetime) |
| avg\_rating     | Average rating of the product across all reviews           |

* Total Records: `7095` before cleaning
* Cleaned Records: `7069` after dropping `NaN` in `review_text`

---

## Data Preprocessing

* Dropped 26 rows with missing `review_text`.
* Converted `review_date` to datetime.
* Extracted year from `review_date` for time series analysis.

---

## Exploratory Data Analysis (EDA)

1. **Ratings Distribution**: Most reviews have a 5-star rating.
2. **Time Trends**: Line plot shows how different ratings are distributed over time.
3. **Yearly Breakdown**: Helps identify product feedback trends across years.

---

## Sentiment Analysis

* Used NLTK’s **VADER (Valence Aware Dictionary and sEntiment Reasoner)**.
* Extracted `neg`, `neu`, `pos`, and `compound` scores for each review.
* Created a new column `sentiment` based on the compound score.

### Interpretation of Scores

| Score      | Description                             |
| ---------- | --------------------------------------- |
| `compound` | Overall sentiment score (-1 to 1 scale) |
| `pos`      | Proportion of positive words            |
| `neu`      | Proportion of neutral words             |
| `neg`      | Proportion of negative words            |

---

## Visualizations

* Histogram of compound sentiment scores.
* Bar chart showing average sentiment per product rating.
* Line plot of rating count over time.

---

## Key Insights

* Majority of reviews are highly positive (rating 5).
* Compound sentiment scores generally correlate with product ratings.
* Some reviews with low ratings still have mixed sentiment due to nuanced language.

---

## How to Run

1. Clone the repository.
2. Place `.csv` review files in the `Data/` folder.
3. Run the script in a Python environment:

```bash
python sentiment_analysis.py
```

Make sure to install required packages:

```bash
pip install pandas numpy matplotlib seaborn nltk tqdm
```

And download necessary NLTK assets:

```python
import nltk
nltk.download('vader_lexicon')
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('wordnet')
```

---

## Future Improvements

* Integrate deep learning models (e.g., BERT) for sentiment analysis.
* Include review helpfulness/likes for weighting.
* Visualize geographic or demographic trends if data is available.
* Perform topic modeling on reviews using LDA.

---

## Author

**Giddy** – Data Scientist
Project showcasing NLP and data visualization using Python.

---

