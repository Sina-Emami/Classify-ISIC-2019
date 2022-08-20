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

I have used **imagenet weights** and just changed the last layer for better and faster learning.
Also, I used **signmoid** for the multi-class classification. When you use a softmax, basically you get a probability of each class, (join distribution and a multinomial likelihood) whose sum is bound to be one. In case you use sigmoid for multi-class classification, it’d be like a marginal distribution and a Bernoulli likelihood, p(y0/x), p(y1/x), etc. I wanted to test and find out about the result of the sigmoid.

</br>

I wanted to compare the softmax and sigmoid for multi-class classification. **Softmax** is kind of Multi Class Sigmoid, but if you see the function of Softmax, the sum of all softmax units are supposed to be 1. In sigmoid it’s not really necessary. In the case of softmax, increasing the output value of one class makes the the others go down (sigma=1). To put it more simple, if there are multiple classes and each input can belong to exactly one class, then it absolutely makes sense to use softmax, in the other cases, sigmoid seems better. The softmax activation had a better result.
</br>

For the loss function I had chosen **categorical_crossentropy**.
categorical_crossentropy: Used as a loss function for multi-class classification model where there are two or more output labels. The output label is assigned one-hot category encoding value in form of 0s and 1. The output label, if present in integer form, is converted into categorical encoding using keras.

<h3>challenge:</h3>
The most important challenge that I had faced was handling the overfitting problem. I had tried different **regularization** techniques so that I can overcome this issue. The combination of **L2**(**Ridge Regression**) and **Dropout** gave me the best result.
