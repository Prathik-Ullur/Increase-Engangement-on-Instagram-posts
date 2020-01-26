# How to increase engangement on Instagram posts?

![](https://assets.recogmedia.net/1/77/Entry_Uploads/88563-thumb.jpg)


We shall determine factors that increase engangment on posts on the National Geographic (natgeo) Instagram page. 

We shall write a scraper to extract around 400-500 
(i) image URLs, 
(ii) post caption (the text description of a post), 
(iii) # likes and 
(iv) # comments.

Using the image URLs, we obtain image labels from Google Vision cloud and write a script to access the Google Vision API. Here is some documentation regarding Google Vision API: https://cloud.google.com/vision/docs/quickstart. With the image labels and captions, we run LDA topic modelling and Lift analysis to determine images and caption labels which increase engangement.

# Approach 

## Task A. 

We create a metric for engagement by using a weighted sum of # likes and # comments. However, we first normalize # likes and # comments such that they both have values between 0 and 1. We scale the # likes by dividing by the maximum # likes (for a post) in your data and do the same for # comments, so that # likes and comments will be in the range [0,1]. 

We now create an engagement score = .4*# likes (normalized) + .6*# comments (normalized) and define High (1) and Low (0) engagement based on whether the engagement score is above or below the median value. 

## Task B. 

We run a logistic regression with Engagement (binary) as the dependent variable, and the image labels obtained from Google Vision API as independent variables. We determine the accuracy by obtaining the confusion matrix.

We determine the accuracy we get by using the post caption words as the independent variables instead of image labels? Finally, we also determine the accuracy we get by combining the image labels and post captions and using them as independent variables?


## Task C. 

We perform topic modeling (LDA) on the image labels by choosing an appropriate number of topics. LDA produces two outputs: (i) A file showing which words load on which topics, and (ii) a file showing topic weights for each image. 

We now take the quartiles with highest and lowest engagement scores and determine the differences in the average topic weights of pictures across the two quartiles (e.g., greater proportion of some topics in highest engagement quartile) 

## Task D. 

At the end, we determine factors and features to increase engangement on National Geographic's Instagram page based on our findings in Tasks B and C.

# Models Built

1. Logistic regression using TF-IDF features from Labels --> AU-ROC 0.78

2. Logistic regression using TF-IDF features from Captions --> AU-ROC 0.82

3. Logistic regression using TF-IDF features from both Captions and Labels --> AU-ROC 0.82

# Results

Based on the topic modeling findings, if National Geographic wants to increase engagement, they should focus on posting pictures of animals, especially terrestrial animals. The posts which exhibit lower engagement on average are pictures of people, while the posts which exhibit higher engagement on average are posts of animals.

The top ten key words associated with the topic which generated the highest engagement were “wildlife”, “animal”, “plant”, “terrestrial”, “photography”, “vertebrate”, “tree”, “bird”, “elephant”, and “mammal”. Perhaps there is so much content of people on Instagram that National Geographic differentiates itself through pictures of wildlife. This theory is further substantiated by the low engagement for posts that contain either people or more domestic content. The key words in the topic which generated the lowest engagement were “photography”, “fun”, “human”, “people”, “adaptation”, “event”, “dog”, “smile”, “child”, and “room”.

Currently, engagement can be successfully predicted by the content of the captions, suggesting their importance. However, no additional information is gained by including both the photo labels and the captions. This seems to indicate that National Geographic is typically reiterating the content in the photo again in the caption. The company could try some A/B Testing with captions that include other insights related to the picture without reiterating the photo’s content to see if there is an impact on engagement. However, this should be considered a secondary priority, as the effects on engagement are uncertain.


![](https://pbs.twimg.com/media/D8ob7vtW4AEBvKU.jpg:large)
