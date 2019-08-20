# Supervised Learning

## Introduction

The goal in supervised learning is to make *predictions from data*. For example, one popular application of supervised learning is email filtering. Here, an email (the data instance) needs to be classified as *spam* or *not-spam*. Following the approach of traditional computer science, one might be tempted to write a carefully designed program that follows some rules to decide if an email is spam or not. Although such a program might work reasonably well for a while, it has significant drawbacks. As email spam changes it would have to be rewritten. Spammers could attempt to reverse engineer the software and design messages that circumvent it. And even if it is successful, it could probably not easily be applied to different languages. Machine learning uses a different approach to generate a program that can make predictions from data. Instead of programming it by hand it is *learned* from past data. This process works if we have data instances for which we know exactly what the right prediction would have been. For example past data might be user-annotated as spam or not-spam. A machine learning algorithm can utilize such data to learn a program, a *classifier*, to predict the correct *label* of each annotated data instance. Other successful applications of machine learning include web-search ranking (predict which web-page the user will click on based on his/her search query), placing of online advertisements (predict the expected revenue of an ad, when placed on a homepage, which is seen by a specific user), visual object recognition (predict which object is an image -- e.g. a camera mounted on a self-driving car), face-detection (predict if an image patch contains a human face or not).

## Setup

Let us formalize the supervised machine learning setup. Our training data comes in pairs of inputs <a href="https://www.codecogs.com/eqnedit.php?latex=(\mathbf{x},&space;y)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(\mathbf{x},&space;y)" title="(\mathbf{x}, y)" /></a>, where <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{x}&space;\in&space;\mathcal{R}^d" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{x}&space;\in&space;\mathcal{R}^d" title="\mathbf{x} \in \mathcal{R}^d" /></a> is the input instance and <a href="https://www.codecogs.com/eqnedit.php?latex=y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?y" title="y" /></a> is its label. The entire training data is denoted as

<a href="https://www.codecogs.com/eqnedit.php?latex=D=\{&space;(\mathbf{x}_1,&space;y_1),&space;\ldots,&space;(\mathbf{x}_n,&space;y_n)&space;\}&space;\subseteq&space;\mathcal{R}^d&space;\times&space;\mathcal{C}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?D=\{&space;(\mathbf{x}_1,&space;y_1),&space;\ldots,&space;(\mathbf{x}_n,&space;y_n)&space;\}&space;\subseteq&space;\mathcal{R}^d&space;\times&space;\mathcal{C}" title="D=\{ (\mathbf{x}_1, y_1), \ldots, (\mathbf{x}_n, y_n) \} \subseteq \mathcal{R}^d \times \mathcal{C}" /></a>

where:

- <a href="https://www.codecogs.com/eqnedit.php?latex=\mathcal{R}^d" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathcal{R}^d" title="\mathcal{R}^d" /></a> is the d-dimensional feature space
- <a href="https://www.codecogs.com/eqnedit.php?latex=\mathbf{x}_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathbf{x}_i" title="\mathbf{x}_i" /></a> is the input vector of the <a href="https://www.codecogs.com/eqnedit.php?latex=i^{th}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?i^{th}" title="i^{th}" /></a> sample
- <a href="https://www.codecogs.com/eqnedit.php?latex=y_i" target="_blank"><img src="https://latex.codecogs.com/gif.latex?y_i" title="y_i" /></a> is the label of the <a href="https://www.codecogs.com/eqnedit.php?latex=i^{th}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?i^{th}" title="i^{th}" /></a> sample
- <a href="https://www.codecogs.com/eqnedit.php?latex=\mathcal{C}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathcal{C}" title="\mathcal{C}" /></a> is the label space

The data point <a href="https://www.codecogs.com/eqnedit.php?latex=(\mathbf{x}_i,&space;y_i)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(\mathbf{x}_i,&space;y_i)" title="(\mathbf{x}_i, y_i)" /></a> are drawn from some (unknown) distribution <a href="https://www.codecogs.com/eqnedit.php?latex=\mathcal{P}(X,&space;Y)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\mathcal{P}(X,&space;Y)" title="\mathcal{P}(X, Y)" /></a>. Ultimately we would like to learn a function <a href="https://www.codecogs.com/eqnedit.php?latex=h" target="_blank"><img src="https://latex.codecogs.com/gif.latex?h" title="h" /></a> such that for a new pair <a href="https://www.codecogs.com/eqnedit.php?latex=(\mathbf{x},&space;y)&space;\sim&space;\mathcal{P}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?(\mathbf{x},&space;y)&space;\sim&space;\mathcal{P}" title="(\mathbf{x}, y) \sim \mathcal{P}" /></a>, we have <a href="https://www.codecogs.com/eqnedit.php?latex=h(\mathbf{x})=y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?h(\mathbf{x})=y" title="h(\mathbf{x})=y" /></a> with high probability (or <a href="https://www.codecogs.com/eqnedit.php?latex=h(\mathbf{x})\approx&space;y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?h(\mathbf{x})\approx&space;y" title="h(\mathbf{x})\approx y" /></a>). We will get to this later. For now let us go through some examples of <a href="https://www.codecogs.com/eqnedit.php?latex=X" target="_blank"><img src="https://latex.codecogs.com/gif.latex?X" title="X" /></a> and <a href="https://www.codecogs.com/eqnedit.php?latex=Y" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Y" title="Y" /></a>.

