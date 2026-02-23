# social_media_unsupervised_learning
Social media classification and prediction based on unsupervised learning.

Unsupervised Learning Final
Project Topic

I am analyzing over a million entries of social media and health data by using unsupervised K means/and Principal Component Analysis to group them into meaningful categories and groups. I want to see the relationships between the features and learn what features determine health or high social media usage.

I will then use a supervised model to predict stress levels (between 1-40) based on PCA feeding into a linear regression model.

Data

Rocky. (2025). Social Media User Analysis. Kaggle.com. https://www.kaggle.com/datasets/rockyt07/social-media-user-analysis

The dataset is extremely large. There are is 1547896 entires along with 57 features. There are 38 numerical features (37 if you drop user ID) . There are 20 object features where some are ordinal and others are purely nominal. The data however is very clean and does not have any null values however it is a synthetic data set.

Data Cleaning/EDA

I did a describe and info on all the data. I also looked at all the objects and what unique values they had. Some objects were nominal like gender or country while most of the objects were ordinal.

For a first pass to get to a quick kmeans k's I dropped the objects. I then sent them all through the standard scaler in order to not overvalue/overweight a feature with large numbers.

I started trying to replace the objects with ordinal or nominal encoding but when i was running correlation alaysis these objects appeared to be 'plugs' and not meaningful. (I did extensive work to try and tie people that favored fitness content would have better health outcomes but the health outcomes were the same in every content prefernce)

I droped app name due to the only value being 'instagram' as well as user ID where where it was just the index of the row. When I left user ID in the k-means used it and grouped user ids that were close to one another which is not a true correlation.

I also expected that high stress would be closely tied to high usage.

K means results

I seperated k means with as many as five groups. I found the k of 3 served as a meaningful seperation of the data. Category 2 in kmeans had very strong correlations between elevated stress and long time using the app on reels and messages and slighlty younger age. The first category was kind of like the average user category they dont spend as much time as category 2 on the app and their health data is pretty close to the mean. The thrid group showed exellent health data and very low stress a strong correlation of using the app much less then the other two categories. They also leaned closer to an older average user.

PCA results

I wanted to use PCA to determine a linear regression model of stress. I was able to find the right number of parameters to be able to get near the users stress level from 1-40 without overfitting. Afeter running a loop of every possible PCA compenent (1-36) I determined that the 18th and 19th componet provided the elbow or best fit by improving the RMSE the most before more the pca's after had little to no impact on improving the score.


Conclusion

Data selection is important, synthetic data can be produced without true correlation between features. I spent a large amount of time trying to predict health outcomes based on content preferences with getting really poor reults. I should have split the data early and described (while filtering categories) to see that a lot of the categorical features were 'plugs' rather than meaniful. I could have spent more time on EDA and data cleaning (removing user id, instagram, categorical plugs' as it can cause pain in the future when models are not producing predictible and stable results.
