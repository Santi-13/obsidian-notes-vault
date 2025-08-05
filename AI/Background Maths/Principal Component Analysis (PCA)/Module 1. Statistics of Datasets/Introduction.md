#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 1
---
***Principal Component Analysis (PCA)*** is a mathematical tool to reduce the dimensionality of high dimensional data (i.e The multiple factors of house prices; or even a 640x480 pixels image, where every pixel corresponds to three dimensions).

The reason we do this is because working with high dimensional *data* is difficult. It is hard to **analyze**, **interpretation** is difficult, **visualization** is nearly impossible and **storage** can be quite expensive.

Not that all is bad. For example, high dimensional data is often **over-complete**, that is, often times many dimensions are redundant and can be explained by a combination of other dimensions. For example, for a color image with four channels (*red*, *green*, *blue*, & *gray-scale* channels). 

![[Pasted image 20250211172003.png]]

The *gray-scale* channel can be explained in terms of either of the other channels or by a combination of them. In other words, we can **reconstruct** that channel just by using the others.

We see how **Dimensionality Reduction** exploits **structure** and **correlation** to allow us to work with a more compact representation of the data without losing much (or ideally any) information.

The lower **dimensional representation** of a *high-dimensional* data point is often called a ***feature*** or a ***code***.