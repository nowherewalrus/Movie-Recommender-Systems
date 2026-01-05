# 🎬 Movie Recommender System

## 📌 Overview
A comprehensive movie recommendation system implementing both **Content-Based** and **Collaborative Filtering** approaches. This project analyzes user preferences and movie features to generate personalized movie recommendations using the MovieLens dataset.

---

## 📊 Dataset
The system uses two primary datasets from MovieLens:

### **movies.csv**
- **movieId**: Unique identifier for each movie
- **title**: Movie title with release year
- **genres**: Pipe-separated list of genres

### **ratings.csv**
- **userId**: Unique identifier for each user
- **movieId**: Movie identifier
- **rating**: User rating (0.5-5.0 scale)
- **timestamp**: Rating timestamp (removed during preprocessing)

---

## 🚀 Features

### **Content-Based Filtering**
- Recommends movies based on **genre similarity**
- Creates user profile from rated movies
- Uses weighted genre preferences
- Generates recommendations based on cosine similarity

### **Collaborative Filtering**
- Recommends movies based on **similar users' preferences**
- Uses Pearson correlation for similarity measurement
- Identifies users with similar rating patterns
- Generates weighted recommendations

### **Data Processing**
- Extracts release years from titles
- One-hot encodes genres
- Cleans and prepares rating data
- Handles missing values

---

## 🛠️ Installation & Usage

### **Prerequisites**
```bash
pip install pandas numpy matplotlib scikit-learn
```

### **Running the Project**
1. Clone the repository:
```bash
git https://github.com/nowherewalrus/Movie-Recommender-Systems.git
cd Movie-Recommender-Systems
```

2. Place the datasets in the project directory:
```
movie-recommender/
├── movies.csv
├── ratings.csv
├── recommender.ipynb
└── README.md
```

3. Run the Jupyter notebook:
```bash
jupyter notebook recommender.ipynb
```

---

## 📈 How It Works

### **1. Data Preprocessing**
```python
# Extract year from title
movies_df['year'] = movies_df.title.str.extract('(\(\d\d\d\d\))', expand=False)

# One-hot encode genres
for genre in row['genres']:
    moviesWithGenres_df.at[index, genre] = 1
```

### **2. Content-Based Filtering**
- **Step 1**: Create user profile from rated movies
- **Step 2**: Weight genres by user ratings
- **Step 3**: Calculate similarity scores
- **Step 4**: Recommend movies with highest similarity

### **3. Collaborative Filtering**
- **Step 1**: Find users who rated similar movies
- **Step 2**: Calculate Pearson correlation coefficients
- **Step 3**: Select top similar users
- **Step 4**: Generate weighted recommendations

---

## 🔧 Customization

### **Define Your Own Preferences**
```python
userInput = [
    {'title': 'The Dark Knight', 'rating': 5.0},
    {'title': 'Inception', 'rating': 4.5},
    {'title': 'The Shawshank Redemption', 'rating': 5.0},
    # Add your own movies here...
]
```

### **Adjust Recommendation Parameters**
- Number of similar users to consider
- Minimum similarity threshold
- Number of recommendations to generate
- Genre weighting preferences

---

## 📊 Sample Results

### **Content-Based Recommendations**
```
Top 10 Content-Based Recommendations:
1. Inception (2010) - Action, Crime, Drama, Mystery, Sci-Fi, Thriller
2. Shutter Island (2010) - Mystery, Thriller
3. Memento (2000) - Mystery, Thriller
4. Fight Club (1999) - Drama
5. American Psycho (2000) - Crime, Drama, Horror
```

### **Collaborative Filtering Recommendations**
```
Top 10 Collaborative Recommendations:
1. Band of Brothers (2001) - Action, Drama, War
2. Double Indemnity (1944) - Crime, Drama, Film-Noir
3. Out of the Past (1947) - Film-Noir
4. Most Hated Family in America, The (2007) - Documentary
5. George Carlin: Life Is Worth Losing (2005) - Comedy
```

---

## ⚙️ Model Parameters

### **Content-Based Filtering**
- **Similarity Metric**: Dot product of genre vectors
- **Normalization**: Sum of user profile weights
- **Output**: Top 20 movies by similarity score

### **Collaborative Filtering**
- **Similarity Metric**: Pearson correlation coefficient
- **Top Similar Users**: 100 most similar users
- **Weighting**: Ratings weighted by similarity scores
- **Output**: Top 50 movies by weighted average

---

## 🏗️ Project Structure
```
movie-recommender/
│
├── movies.csv                  # Movie metadata
├── ratings.csv                 # User ratings
├── recommender.ipynb           # Main Jupyter notebook
├── README.md                   # This file
├── requirements.txt            # Python dependencies
└── images/                     # Visualization outputs
    ├── content_based_results.png
    └── collaborative_results.png
```

---

## 📈 Performance Metrics

### **Content-Based Filtering**
- **Transparency**: Easy to understand why recommendations are made
- **Cold Start**: Works well for new items
- **Personalization**: Highly tailored to individual preferences

### **Collaborative Filtering**
- **Serendipity**: Can discover unexpected items
- **Social Aspect**: Leverages community preferences
- **Accuracy**: Often higher accuracy for users with sufficient history

---

## 🔍 Use Cases

1. **New Users**: Start with content-based filtering
2. **Active Users**: Combine both approaches for better results
3. **Genre Exploration**: Content-based for specific genre preferences
4. **Community Trends**: Collaborative for popular items

---

## 🚀 Future Enhancements

### **Planned Features**
- [ ] **Hybrid Approach**: Combine content-based and collaborative filtering
- [ ] **Matrix Factorization**: Implement SVD for improved collaborative filtering
- [ ] **Deep Learning**: Neural network-based recommendations
- [ ] **Real-time Updates**: Incremental model updates
- [ ] **Web Interface**: Flask/Django web application
- [ ] **API Endpoints**: REST API for recommendations

### **Technical Improvements**
- [ ] **Scalability**: Handle larger datasets
- [ ] **Performance**: Optimize similarity computations
- [ ] **Evaluation**: Add precision/recall metrics
- [ ] **Deployment**: Docker containerization

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

=

---

## ✉️ Contact

Parsa Khaghani - https://www.linkedin.com/in/parsa-khaghani-a22847326/

Project Link: https://github.com/nowherewalrus/Movie-Recommender-Systems.git

---

## 🙏 Acknowledgments

- MovieLens dataset providers
- Scikit-learn developers
- Open source community contributors

---

## ⚠️ Note

The warning about `numexpr` version is non-critical. To resolve:
```bash
pip install --upgrade numexpr
```

---

## 📚 References

1. MovieLens Dataset: https://grouplens.org/datasets/movielens/
2. Scikit-learn Documentation: https://scikit-learn.org/
3. Pandas Documentation: https://pandas.pydata.org/

---

## 🎯 Quick Start Guide

### **For Content-Based Recommendations:**
```python
# Modify user preferences
userInput = [
    {'title': 'Your Favorite Movie', 'rating': 5.0},
    # Add more movies...
]

# Run content-based filtering
# Results will be based on genre similarity
```

### **For Collaborative Recommendations:**
```python
# The system automatically finds similar users
# Recommendations are based on users with similar taste
```

### **For Hybrid Approach:**
```python
# Combine both methods for best results
# Average scores from both approaches
# Get diverse and accurate recommendations
```

---

**Happy Recommending! 🍿🎥**
