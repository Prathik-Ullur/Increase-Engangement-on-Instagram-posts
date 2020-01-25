# How to increase engangement on Instagram posts?

![](https://mymodernmet.com/wp/wp-content/uploads/archive/kZenXSay7u0YkqoPAoY0_nat_geo_contest3.jpg)

We shall determine the features that increase engangment on Instagram posts especially posts on the National Geographic (natgeo) page. 

We shall write a scraper to extract around 400-500 
(i) image URLs, 
(ii) post caption (the text description of a post), 
(iii) # likes and 
(iv) # comments.

Using the image URLs, we obtain image labels from Google Vision cloud and write a script to access the Google Vision API. Here is some documentation regarding Google Vision API: https://cloud.google.com/vision/docs/quickstart

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
