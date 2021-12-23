# Recipe's Originated Country Prediction

Given a recipe(json format), we would like to analyze the characteristic between different cuisines from different countries. 

The below is the distinct recipe count over the countries.

<img width="465" alt="Screen Shot 2021-12-23 at 3 13 00 PM" src="https://user-images.githubusercontent.com/54965707/147287767-13555957-59ba-40ea-a05d-c68b0d80d0ba.png">

The below is the distinct ingredient count over the countries.

<img width="494" alt="Screen Shot 2021-12-23 at 3 20 52 PM" src="https://user-images.githubusercontent.com/54965707/147288375-37bd8111-9bb5-4b82-9232-77ee80414d6b.png">

We can see that Italian uses the most number of distinct sauces. As we know, Italian food is considered very delicate and sophisticated, it's understandable that it's the top 1 country in this metric, which is also similar to French. For Mexican, Southern US, Chinese and Indian food, these food requires strong taste and lots of spices, which results in many distinct ingredients.

More interestingly, the country that has most distinct recipes also has most distinct ingredients and the order is also the same!

Before fitting the model, I tried to vectorize the inputs and perform dimensionality reduction. Due to the fact that the resulting vectorized input is a sparse matrix, it violates the PCA inverse operations. Hence, I tried TruncatedSVD to perform dimensionality reduction. However, the accuracy is really low, which might results from information loss due to dimensionality reduction.

I tried vectorize the inputs by using the tokenizer that filters out the word that has length less than 2. Then, we tried to fit Logistic Regression, Soft Margin Classifier and Random Forest and Extra Trees. In the end, we found SVC(Soft Margin Classifier) performs the best among these models.

<img width="864" alt="Screen Shot 2021-12-23 at 3 23 29 PM" src="https://user-images.githubusercontent.com/54965707/147288572-bd321a53-057c-4e63-9034-8e90f2988b67.png">

We can see that for Indian, Italian, Chinese and Mexican food we performed really well. Even though the results seem good, the important thing we need to remember is that the imbalanced data.

From the above Exploratory Analysis, we know that Italian, Chinese, Indian and Mexican food are among the top ones, which makes sense to see that predicting performance of cuisine's originated country is generally well for these top ones as well
