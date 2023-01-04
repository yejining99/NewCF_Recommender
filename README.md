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
![upperbount](https://user-images.githubusercontent.com/93263147/210547163-e03f7298-dd03-40a2-99e3-bd9edc6282e7.png)

## Results
We try to achieve various results through our project. First of all, we compare the running time between original SVD algorithm and the algorithms we made. Using the time module within Python, the algorithm could be determined how long it would take to run. The results are as follows
||Computing Time|
|:---:|:---:|
|Original SGD|590sec|
|Proposed model|60sec|

While original SVD takes 590 minutes, we can see that our algorithm takes only 60 minutes. Also, we assume the situation that new user come and express time complexity. Computing the SVD of and matrix has $O(mnmin(m,m))$ complexity.

We can see it becomes computationally expensive for large data sets. But our proposed model used only the category data in which target user belong. So based on the assumption that all categories have same number of songs and put the number of categories as k, time complexity of our proposed model is $O(m\frac{n}{k}min(\frac{n}{k},m))$.

Considering the situation in which new users come in, original SVD takes the same amount of time because it needs to rerun using all of the data, but our algorithm can reduce the time even more because new user can be applied in most appropriate category after identifying the taste and then we just need to run the algorithm of that category. In reality, new songs and new users come in so actively, so if we use our algorithm, we can present the recommended song more quickly to users.
