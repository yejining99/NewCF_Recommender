# NewCF

This is the implementation for our project:
A New Collaborative Filtering at Recommendation System Using Yahoo! Music Data
[Paper](https://unistackr0-my.sharepoint.com/:b:/g/personal/kimyejin99_unist_ac_kr/EXZigCmUMgJNmdNzPI6PuwcBpJNfQfO-dlgulpihyfNyMQ?e=ksKFGl), [Presentation](https://unistackr0-my.sharepoint.com/:p:/g/personal/kimyejin99_unist_ac_kr/EbUhvBCSi3VOo9JyyVESZlUBue-F3U0qMKzo19b53RUIYQ?e=mLUGTR)

This project was conducted to make the new recommendation system more efficient with the Yahoo! Music data. We were focused on the reducing the time that takes for the algorithm to run when the new user come in. In addition, we thought of ways to reflect information such as album and singer of song, different from the existing SVD algorithm that used only users, songs.

The algorithm shows in the following steps

'''
Step 1: Prepare ‘Yahoo! Music User Ratings’ data and merge each data set.
Step 2: Get Cosine-Similarity of Album to Cluster ‘Unknown’ genre
Step 3: Use UMAP as pre-processing to boost HDBSCAN.
Step 4: Cluster ‘Unknown’ genre using HDBSCAN.
Step 5: Classify user into each genre category using upper bound formula.
Step 6: Run the SVD algorithm for each genre category to predict the rating.
Step 7: List predicted rating descending order. Step 8: select songs to recommend.
'''
