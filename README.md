# Adaptive and Cascaded Compressive Sensing
## About
This is my course research project for *Computational Photography*. I cooperate with my teammate and reproduced an algorithm for compressive sensing.
## Idea
The basic idea of compressive sensing is making use of sparsity. Natural signals exhibit sparsity after DCT. After sampling in the DCT domain, the sparse signal can be restored with L1-norm regularization (LASSO Regression).
The novel part is to use RIP (Restricted Isometry Property) of compressive sensing. This property builds the bridge between sampling error and reconstrustion quality. The blocks with higher error are sampled with higher rate in the next stage. To fuse all the result, we built a cascaded structure.
## Details
### Sampling process
image($\hat{\vec{x}}$) --> patches of smaller images -->  flatten to 1D vector --> DCT & Randomly Sample --> $\vec{y}$

$$
\vec{y} = \Phi \Psi \vec{x}
$$
### Restoring process

$$
\text{min} \|\vec{y} - \Phi \alpha\|_2 + \lambda \|\alpha\|_1
$$

This is also known as LASSO Regression. If sampling array can be designed, the restoration would have higher quality.
### Adaptive Sampling: scene dependent
The **R**estricted **I**sometry **P**roperty of compressive sensing indicates the connection between sampling error (the error of solving $\vec{\alpha}$ from $\vec{y}$) and reconstruction quality (PSNR). So, sampling error may be an estimation of reconstruction quality, and higher error means that higher sampling rate is needed.
### Cascaded structure: fuse result among different stages
Since in every stage a number of patches are picked to be sampled with higher rate, a cascaded structure is needed to fuse the result into an image with the same shape as input.
