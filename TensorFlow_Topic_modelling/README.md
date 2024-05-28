# Topic Modelling of TensorFlow Posts

This project performs topic modeling on TensorFlow-related posts from Stack Overflow using Python, MySQL, and various natural language processing libraries. The goal is to identify popular and challenging topics in these posts.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)

## Installation

To get started with this project, you need to have Python, MySQL, and some Python libraries installed. Follow these steps to set up your environment:

1. **Install Python Packages**:
    ```bash
    pip install contractions
    pip install pandas
    pip install mysql-connector-python
    pip install gensim==3.8.0
    pip install spacy
    pip install nltk
    pip install pyLDAvis
    ```

2. **Download Mallet**:
    Download Mallet from [here](http://mallet.cs.umass.edu/download.php) and extract it. Set the `MALLET_HOME` environment variable to the path where Mallet is extracted.

3. **Download SpaCy Model**:
    ```bash
    python -m spacy download en_core_web_sm
    ```

## Usage

1. **Database Connection**:
    Modify the database connection details in the `create_db_connection` function.

    ```python
    db = "stackoverflow"
    pw = "Password"
    connection = create_db_connection("localhost", "root", pw, db)
    ```

2. **Retrieve Data**:
    Modify and execute the SQL query to retrieve data from your MySQL database.

3. **Text Preprocessing**:
    The text preprocessing steps include removing HTML tags, URLs, punctuation, contractions, stop words, and lemmatization.

4. **Topic Modelling**:
    - Build bigram and trigram models.
    - Use Gensim's LDA Mallet model to compute coherence values and determine the optimal number of topics.
    - Extract dominant topics, contribution, and keywords for each document.

5. **Analyze Results**:
    Analyze the popular and challenging topics based on average view counts, scores, and favorite counts.

6. **Visualization**:
    Use pyLDAvis to visualize the topics.

## Project Structure

```plaintext
.
├── README.md
├── requirements.txt
├── data
│   └── stackoverflow_posts.csv
├── notebooks
│   └── topic_modelling.ipynb
├── src
│   ├── data_preprocessing.py
│   ├── topic_modeling.py
│   ├── analysis.py
│   └── visualization.py
└── outputs
    └── lda.html
