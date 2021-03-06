---
layout: post
title: "'Rate Your Face Photo' a ML&Wechaty practice"
date: 2017-09-17 21:00 +0800
author: huyingxi
---

> Author: [@huyingxi](https://github.com/huyingxi/wechaty_selfie) enjoying ML&Wechaty at BUPT

Recently I found a fun and easy to use middleware for WeChat, called [Wechaty](https://github.com/Chatie/wechaty).

Wechaty can help developers quickly build applications based on Wechat, and it was born with a huge number of Potential users. 

So I build a fun application based on Wechaty, called [wechaty_selfie](https://github.com/huyingxi/wechaty_selfie), which is a ChatBot that can score self-portraits.



<div align=center>
<img src=https://github.com/huyingxi/wechaty_selfie/blob/master/li.jpg width='700px' />
</div>

                                      Say goodbye to your choice of difficulty!

<!--more-->

## Screenshot of the application
<div align=center>
<img src=https://github.com/huyingxi/wechaty_selfie/blob/master/result.jpg width="400px" />
</div>

## Our development steps
-----
Once you have a little nodejs knowledge, and a little deep learning basis, you can build it. :)

* Crawl data : The most important of this application is data. We crawled data(eg. picture URL, release time, the number of praise, the number of comments)  with 'selfie' label from instagram. 


* Filter data : In order to make the training data more convincing, we crawl the data with earlier release time. It is obviously that if a selfie has just been released, then it must not get enough exposure, so the number of comments and comments at this time is unstable. Considering this, we set the realease time threshold to 2000 seconds. We will filter out data which have realease time smaller than the threshold.

* Scoring strategy selection : We get the data(picture URL, the number of praise, the number of comments) for visual analysis， and found that most of the number of praise are between 0-10, so we simply consider the number of praise as the selfie's score.


* Download  pictures : We download the selfies that we will use by URL that we already have, and reshape them into 224 * 224 dimensions.


* Build DL model : In order to build the neural network quickly, we choose the pre-build model VGG16 in keras, and add five full connection layer on the top of it. The top of our model is a softMax layer with 10 categories.


* Build project & training model : Build wechaty project and the training of deep learning model.


* Debugging, success!




## Appendix, packages we used

* pylab: for drawing
* matplotlib: for drawing
* requests: handle http requests
* numpy: matrix operations
* h5py: formatting data sets
* keras: deep learning
* Wechaty: wechat middleware
* Fs: transfer pictures


## Some optimization recommendations
If you are interested what I have done and would like to Develop a similar application.
* If you want to use pictures from Instagram that have the selfie label as the training data, you should crawl the pictures with earlier release time.
* You may try several different scoring strategies.
* You can build a more complex deep learning model.


## Finally
I strongly recommend that you now click on the link below, there are surprises waiting for you！

[Wechaty :)](https://github.com/Chatie/wechaty)


And more details you can find in [wechaty_selfie](https://github.com/huyingxi/wechaty_selfie)
