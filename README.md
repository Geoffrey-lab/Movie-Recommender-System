# Movie-Recommender-System
Sure! Here is a sample GitHub description for your Streamlit-based movie recommender system project:

---

## Movie Recommender System

Welcome to the Movie Recommender System! This project leverages the power of Streamlit, natural language processing, and machine learning to recommend movies based on user input. Simply type in the name of a movie, and the app will suggest similar movies for you to enjoy.

### Features

- **User-friendly Interface**: Built using Streamlit, providing an easy and interactive way to get movie recommendations.
- **Natural Language Processing**: Utilizes FuzzyWuzzy to handle variations in movie titles and find the closest match.
- **Content-Based Filtering**: Recommends movies based on the content of movie descriptions and genres using a combination of TF-IDF and cosine similarity.
- **Extensive Database**: Works with a dataset of the top 10,000 movies from TMDB.

### Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/your-username/movie-recommender-system.git
   cd movie-recommender-system
   ```

2. Install the required packages:
   ```sh
   pip install -r requirements.txt
   ```

3. Make sure you have the `movies_list.pkl` file generated from the preprocessing step. If not, follow the steps below to preprocess the data.

### Data Preprocessing

To preprocess the movie data and generate the `movies_list.pkl` file:

1. Load the movie dataset (ensure you have the `top10K-TMDB-movies.csv` file).
2. Run the preprocessing script to create `movies_list.pkl`:
   ```python
   import pandas as pd
   import pickle
   from sklearn.feature_extraction.text import CountVectorizer

   # Load data
   movies = pd.read_csv('top10K-TMDB-movies.csv')

   # Select relevant columns
   movies = movies[['id', 'title', 'genre', 'overview']]

   # Combine 'overview' and 'genre' into a new column 'tags'
   movies['tags'] = movies['overview'].fillna('') + ' ' + movies['genre'].fillna('')

   # Drop unnecessary columns
   new_data = movies.drop(columns=['genre', 'overview'])

   # Save the processed DataFrame
   pickle.dump(new_data, open('movies_list.pkl', 'wb'))
   ```

### Running the App

1. Start the Streamlit app:
   ```sh
   streamlit run app.py
   ```

2. Open your web browser and navigate to the URL provided by Streamlit (usually `http://localhost:8501`).

### Usage

- Enter the name of a movie in the input field.
- Click the "Recommend" button.
- View the list of recommended movies similar to the one you entered.

### Contributing

Contributions are welcome! Please fork the repository and submit a pull request.

### License

This project is licensed under the MIT License. See the `LICENSE` file for more details.

### Acknowledgements

- The Movie Database (TMDB) for providing the movie dataset.
- The creators of Streamlit, FuzzyWuzzy, and Scikit-Learn for their powerful tools and libraries.
