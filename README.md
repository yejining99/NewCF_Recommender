# NewCF

This is the implementation for our project:
A New Collaborative Filtering at Recommendation System Using Yahoo! Music Data
[Paper](https://unistackr0-my.sharepoint.com/:b:/g/personal/kimyejin99_unist_ac_kr/EXZigCmUMgJNmdNzPI6PuwcBpJNfQfO-dlgulpihyfNyMQ?e=ksKFGl), [Presentation](https://unistackr0-my.sharepoint.com/:p:/g/personal/kimyejin99_unist_ac_kr/EbUhvBCSi3VOo9JyyVESZlUBue-F3U0qMKzo19b53RUIYQ?e=mLUGTR)


## About the our model
This project was conducted to make the new recommendation system more efficient with the Yahoo! Music data. We were focused on the reducing the time that takes for the algorithm to run when the new user come in. In addition, we thought of ways to reflect information such as album and singer of song, different from the existing SVD algorithm that used only users, songs.

The algorithm shows in the following steps

![algorithm](https://user-images.githubusercontent.com/93263147/210546023-9f6914d7-4d67-436e-9fa6-6910c71eacbf.png)

* Step 1: Prepare ‘Yahoo! Music User Ratings’ data and merge each data set.
* Step 2: Get Cosine-Similarity of Album to Cluster ‘Unknown’ genre
* Step 3: Use UMAP as pre-processing to boost HDBSCAN.
* Step 4: Cluster ‘Unknown’ genre using HDBSCAN.
* Step 5: Classify user into each genre category using upper bound formula.
* Step 6: Run the SVD algorithm for each genre category to predict the rating.
* Step 7: List predicted rating descending order. Step 8: select songs to recommend.


## What is Upper Bound formula?
The reason that why using upper bound expression is that we could give more suitable genre category to users by considering the rating count. It will be more understandable if you think about the following examples. Let's say that a user gave a rating of 4 and 3.9 for genre a and b. In fact, there is not much difference between 4 and 3.9. But means are the only reason why Genre a is chosen. In fact, the user only listened to two genre A songs. Therefore, genre b seems more appropriate to the user. Therefore, we used the upper bound formula to weight the genre that user heard more about to prevent this problem.


