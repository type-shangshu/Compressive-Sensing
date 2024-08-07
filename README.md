# Adaptive and Cascaded Compressive Sensing
## Big picture
### Sampling process
image($\hat{\vec{x}}$) --> patches of smaller images -->  flatten to 1D vector --> DCT & Randomly Sample --> $\vec{y}$

$$
\vec{y} = \Phi \Psi \vec{x}
$$
### Restoring process

$$
\text{min} ||\vec{y} - \Phi \alpha||_2 + \lambda ||alpha||_1
$$
This is also known as LASSO Regression. If sampling array can be designed, the restoration would have higher quality.
### Adaptive: scene dependent
The Restricted Isometry Property of compressive sensing indicates the connection between sampling error (the error of solving $\vec{\alpha}$ from $\vec{y}$) and reconstruction quality (PSNR). So, sampling error may be an estimation of reconstruction quality, and higher error means that in this region, higher sampling rate needed.
### Cascaded: fuse result among different stages
Since in every stage a number of patches are picked to be sampled with higher rate, a cascaded structure is needed to fuse the result into an image with the same shape as input.
