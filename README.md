# Book Recommendation System

## Overview
This repository contains a Proof of Concept (PoC) for a book recommendation system developed for an online bookshop to drive sales through personalized recommendations. The system uses collaborative filtering techniques (user-based and item-based) to recommend books based on user ratings and cart contents. The project is implemented in Python using a Jupyter Notebook and leverages the [Kaggle Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset).

The PoC was developed as part of a 40-day project to demonstrate the feasibility of a recommendation engine. It includes data visualization, model building, recommendation functions, and testing, with notes on known issues and future improvements.

## Features
- **Data Visualization**: Displays the top 10 most-rated books to understand dataset trends.
- **User-Based Collaborative Filtering**: Recommends books for a user based on ratings from similar users.
- **Item-Based Collaborative Filtering**: Recommends books similar to those in a user’s cart.
- **Sparse Matrix Implementation**: Efficiently handles large, sparse rating data using SciPy.
- **Fallback Mechanism**: Recommends popular books for new or unknown users.
- **Testing**: Includes test cases for specific users and cart scenarios.

## Dataset
The project uses the [Kaggle Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset), which includes:
- `Books.csv`: Book details (ISBN, title, author, etc.).
- `Ratings.csv`: User ratings for books (User-ID, ISBN, Book-Rating).
- `Users.csv`: User information (optional, not used in this PoC).

## Requirements
To run the code, install the following Python packages:
```bash
pip install pandas numpy matplotlib scikit-learn scipy
```
- Python 3.8+
- Jupyter Notebook or JupyterLab

## Setup
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/book-recommendation-system.git
   cd book-recommendation-system
   ```

2. **Download the Dataset**:
   - Download the dataset from [Kaggle](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset).
   - Place `Books.csv` and `Ratings.csv` in the `data/` directory.

3. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch Jupyter Notebook**:
   ```bash
   jupyter notebook
   ```
   Open `book_recommendation.ipynb` in your browser.

## Usage
1. **Run the Notebook**:
   - Execute the cells in `book_recommendation.ipynb` sequentially.
   - The notebook loads the dataset, visualizes top-rated books, builds the recommendation models, and tests the recommendation functions.

2. **Test Recommendations**:
   - Use the `recommend_books_for_user` function to get recommendations for a user:
     ```python
     recommendations_df = recommend_books_for_user(real_user_id=8, ...)
     print(recommendations_df)
     ```
   - Use the `recommend_books_from_cart` function to get recommendations based on ISBNs:
     ```python
     cart = ["0971880107", "0446672211"]
     recommendations_df = recommend_books_from_cart(isbn_list=cart, ...)
     print(recommendations_df)
     ```

3. **Explore Visualizations**:
   - The notebook generates a bar plot of the top 10 most-rated books.

## Code Structure
- `book_recommendation.ipynb`: Main Jupyter Notebook containing:
  - **Data Visualization**: Plotting top-rated books.
  - **Data Preprocessing**: Creating a sparse user-book rating matrix.
  - **Model Building**: User-based and item-based collaborative filtering using cosine similarity.
  - **Recommendation Functions**:
    - `recommend_books_for_user`: Recommends books for a user.
    - `recommend_books_from_cart`: Recommends books based on a cart.
  - **Testing**: Tests for specific user IDs and ISBNs.
- `data/`: Directory for storing `Books.csv` and `Ratings.csv` (not included in the repository).
- `requirements.txt`: Lists Python dependencies.

## Known Issues
- **Duplicate ISBNs**: Some books have multiple ISBNs (e.g., different editions), which may lead to duplicate recommendations.
- **Unrated Bestsellers**: Popular books (e.g., King James Bible) may lack ratings, possibly due to data collection issues.
- **Scalability**: Cosine similarity computation is memory-intensive for large datasets.
- **Cold-Start Problem**: New users or books with few ratings rely on a basic fallback (popular books).

## Future Improvements
- **Address Duplicate ISBNs**: Group books by title/author to ensure unique recommendations.
- **Handle Unrated Bestsellers**: Incorporate content-based filtering (e.g., using book titles, authors) for books with few ratings.
- **Optimize Scalability**: Use approximate nearest neighbors (e.g., Annoy, HNSW) for similarity computations.
- **Enhance Cold-Start Handling**: Combine collaborative filtering with content-based features or popularity-based recommendations.
- **Evaluate Recommendations**: Implement metrics (e.g., precision, recall) using a train-test split.
- **Productionization**: Develop a web application with an API to serve recommendations (see Task 4 in the assignment).

## Contributing
Contributions are welcome! Please:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -m 'Add your feature'`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Contact
For questions or feedback, please contact [your-email@example.com](mailto:your-email@example.com) or open an issue on GitHub.