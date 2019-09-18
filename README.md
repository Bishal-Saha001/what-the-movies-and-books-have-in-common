# Perception of literature and cinematography according to NLP

According to Global English Editing, India, Thailand, and China are the countries with best reading habits in 2018, spending on reading between 8:00 and 10:42 hours per week. The U.S., with **5:42 hours**, is in 22nd position. **37% of American adults** with a high school degree or less and **7% of college graduates** have reported not reading a book in any format in the past year. 

This project tries to find relations between movies and books through genres ables to give us priceless information. Genres are determined by key-words of overviews, descriptions, using Part of Speech filters and NLP preprocessing pipelines to normalized unstructured data. If we are able to connect books and movies, we could recommend books depending on the people preferences or give us a guide about how to predict the success of the metamorphosis from novels to cinematographic adaptations and discovering what genres would achieve more acceptance by the audience. 

## Contents:
1. Proposal 
- Details on [`Reports/Project_Proposal.pdf`](./Reports/Project_Proposal.pdf).

2. Data Extraction and Wrangling
- In [`Data_extraction`](./Data_extraction) 0.8M of books are acquired from Goodreads Dataset and 1.38M of reviews from Book Reviews in Goodreads. The analysis of outliers in number of pages, publication date, vote counts and others and the NLP preprocessing pipeline applied to reviews is done in [`Data_wrangling`](./Data_wrangling). In this section, Movies Dataset, with 45 thousand movies and 26M of ratings is read and preprocessed through regular expressions to extract key-words, id movies and genres.

3. Initial Findings
- Separed analysis for movies and books [`EDA_Statistics`](./EDA_Statistics) are leading us to discover the most popular languages in movies and books, how many languages we can find in the same movie, averages runtimes and number of pages, how loved or hated are long movies and books. **ANOVA** and **Levene** to compare distributions of movies and **Kolmogorov-Smirnov**, **bootstrapping** to validate sample data in books are some statistic test used to get solid and statistical base to answer our questions. Besides, **AFINN** and **TextBlob** are used to analyze polarity and subjectivity of reader reviews. More details could be found in [`Reports/Milestone_Report.pdf`](./Reports/Milestone_Report.pdf) 

4. In-Depth Analysis
   - Section 1: Overviews, titles, and keywords of movies are used to predict genres, through cosine similarity between documents by genres. Documents by genre include normalized titles (NLP preprocessing pipeline for deleting **stop-words**, expanding **constractions**, removing special characters, **tokenization** and **lemmatization**), overviews filtered by **Part of Speech** and keywords. Documents by genre are used to build dictionaries and measure the **cosine similarity** between movie overviews and the dictionary of every genre. 
   - Section 2: Documents by genre are used in books to get genres as new features. Using genres, number of pages, number of ratings and reviews, a binary classification problem of quality of books (good scores and bad scores) is resolved. Ensemble tree models are used, as **Gradient Boosting**, **Random Forest** and two variations using trees as transformers of features in high dimensional spaces before applying a **Logistic Regression** approach.
   - Section 3: *Cinephiles* profiles allow us look for similar users and then, applying a **User Based Collaborative Filtering** algorithm, we predict the score of a determined user for a specific movie genre unexplored.
   - Section 4: Finally, *spacy* library is used to get dates, places and people in description of books. 9 clusters of books, according to the genres labeled, are determined using **PCA** to reduce dimensionality of data and **Agglomerative Clustering**. 
   - The step by step of every section could be found in [`depth_analysis`](./depth_analysis)
7. Presentation and Final Report
- The [`Final report`](./Reports/Capstone2_Final_Report.pdf) compiles the complete project, including the most relevant results (collection, wrangling, EDA) and in-depth analysis using machine learning. Additionally, you can see a summarization in the [`Presentation`](./Reports/Presentation.pdf) slides deck.


## Getting Started
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

### Prerequisites
- [Download Anaconda](https://www.anaconda.com/distribution/).
- Run Anaconda Navigator and launch a jupyter notebook and open the experience-coffee-searcher folder. 
- Using Anaconda Navigator, you can install the following packages:
  - request
  - nltk
  - textblob
  - spacy
 
 - **AFINN** and the specific **spacy** model used in the project, *en_core_web_sm* are installed as part of the coding in Jupyter notebooks. Details are included in the corresponding sections and they don't require any extra work from the user.

Other libraries applied in this project (numpy, scipy, matplotlib, pandas, seaborn, sklearn, re, json) do not require installation (default packages in anaconda). They only need to be imported in the notebooks.