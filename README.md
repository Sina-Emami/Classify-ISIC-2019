# classify-ISIC-2019

The goal for <a href="https://challenge.isic-archive.com/landing/2019/">ISIC 2019</a> is classify dermoscopic images among nine different diagnostic categories:

* Melanoma
* Melanocytic nevus
* Basal cell carcinoma
* Actinic keratosis
* Benign keratosis (solar lentigo / seborrheic keratosis / lichen planus-like keratosis)
* Dermatofibroma
* Vascular lesion
* Squamous cell carcinoma
* None of the others
**25,331** images are available for training across **8** different categories. Additionally, the test
dataset (planned release August 2nd) will contain an additional outlier class not represented in
the training data, which developed systems must be able to identify.

</br>

I have used **imagenet weights** and just changed the last layer for better and faster learn.
Also, I used **signmoid** for the multi-class classification. When you use a softmax, basically you get a probability of each class, (join distribution and a multinomial likelihood) whose sum is bound to be one. In case you use sigmoid for multi class classification, it’d be like a marginal distribution and a Bernoulli likelihood, p(y0/x) , p(y1/x) etc. I wanted to test and findout about the result of sigmoid.

