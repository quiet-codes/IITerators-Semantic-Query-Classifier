# 🔎 Semantic Query Classifier

A semantic query relevance application built with **Python, Streamlit, and Sentence Transformers**. It compares search queries with category descriptions using MiniLM embeddings and cosine similarity.

## 🚀 Live Demo

[**Launch the Streamlit App**](https://iiterators-semantic-query-classifier-rcgkdvwwkvgcany8pzu8nm.streamlit.app/)

## ✨ Features

- Upload a CSV containing search queries and category paths.
- Generate text embeddings using Sentence Transformers.
- Calculate cosine similarity between each query and its corresponding category path.
- Adjust the similarity threshold interactively.
- Generate binary relevance predictions (`0` or `1`).
- View the complete results table, including similarity scores.
- Download predictions as a CSV containing the original columns, `score`, and `result`.

## 🧠 How It Works

1. Upload a CSV file.
2. Validate and preprocess the input data.
3. Convert queries and category paths into embeddings using `paraphrase-MiniLM-L6-v2`.
4. Calculate cosine similarity between the corresponding embedding pairs.
5. Apply a configurable threshold to generate binary predictions.
6. Display and download the results.

### Prediction Rule

- `result = 1` when `score >= threshold`
- `result = 0` when `score < threshold`

The default threshold is `0.20`. It is configurable and should be evaluated against labelled data before being used for real-world decisions.

## 🛠️ Tech Stack

- **Language:** Python
- **Frontend:** Streamlit
- **NLP / Embeddings:** Sentence Transformers
- **Model:** `paraphrase-MiniLM-L6-v2`
- **Data Processing:** Pandas, NumPy
- **Similarity Metric:** Cosine similarity

## 📂 Repository Structure

```text
IITerators-Semantic-Query-Classifier/
├── app.py
├── requirements.txt
├── README.md
├── .gitignore
└── .streamlit/
    └── config.toml
```

The `.streamlit/config.toml` file is optional. The actual repository may contain additional research notebooks or data files.

## 📥 Input Format

The uploaded CSV must contain these columns:

| Column          | Description                             |
| --------------- | --------------------------------------- |
| `origin_query`  | Search query to evaluate                |
| `category_path` | Category text to compare with the query |

Additional columns are preserved in the output but are not used to calculate similarity.

Example:

```csv
origin_query,category_path
wireless headphones,Electronics Audio Headphones
running shoes,Sports Footwear Running Shoes
cotton t shirt,Clothing Men T Shirts
```

## 💻 Run Locally

### 1. Clone the repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd IITerators-Semantic-Query-Classifier
```

Replace the placeholder with the actual repository URL.

### 2. Create a virtual environment

**Windows:**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Start the application

```bash
python -m streamlit run app.py
```

Open `http://localhost:8501` in your browser if it does not open automatically.

The model is downloaded when it is first required, so the first prediction may take longer.

## ⚠️ Limitations

- The application compares each query with its supplied category path rather than selecting from every possible category.
- Similarity scores are not probabilities of correctness.
- The threshold is configurable and requires validation on labelled data.
- A high similarity score does not guarantee that a category is correct.

## 🔮 Future Improvements

- Evaluate precision, recall, F1-score, and threshold performance on labelled data.
- Support ranking a query against multiple candidate categories.
- Improve inference speed for large CSV files.
- Add confidence analysis and error examples.
- Add automated tests and reproducible dependency versions.

## 👨‍💻 Author

Developed by the IITerators team for the Confluentia hackathon.
