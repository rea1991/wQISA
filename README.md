# Weighted Quasi Interpolant Spline Approximation for Rainfall Fields

We here provide a quantitative evaluation of a novel approach - the Weighted Quasi Interpolant Spline Approximation (w-QISA) -  in the approximation of observed rain data, in real conditions of sparsity of the observations. For a formal definition of w-QISA and its properties, see [1].

This implementation is not optimized for high performance computing, but wants rather to be as intuitive as possible. This implementation rely on the library for tensor product and LR B-splines proposed at https://github.com/qTipTip/LRSplines, which has the advantage to be very simple and thus accessible to a larger public. For industrial grade performance and a more complete set of tools, see the [GoTools library](https://github.com/SINTEF-Geometry/GoTools) written in C++.

### About the model

Let $\mathcal{P}$ be a given point cloud that we aim to approximate through a height field $z=f(x,y)$. Let $\mathbf{p}=(p_x,p_y)$ be a vector of positive integers. Lastly, let
- $\mathbf{x}=[x_1,\ldots,x_{n_x+p_x+1}]$ be a $(p_x+1)$-regular knot vector with boundary knots $x_{p_x+1}=a_1$ and $x_{n_x+1}=b_1$.
- $\mathbf{y}=[y_1,\ldots,y_{n_y+p_y+1}]$  be a $(p_y+1)$-regular knot vector with boundary knots $y_{p_y+1}=a_2$ and $y_{n_y+1}=b_2$.

The *Weighted Quasi Interpolant Spline Approximation* of bi-degree $\mathbf{p}$ to $\mathcal{P}$ on the knot vectors $\mathbf{x}$ and $\mathbf{y}$ is defined by
$$f_w(x,y):=\sum_{i=1}^{n_x}\sum_{j=1}^{n_y}\hat{z}_w(x_i^\ast,y_j^\ast)B[x_i,\ldots,x_{i+p_x+1};y_j,\ldots,y_{j+p_y+1}](x,y)$$
where
$$
x_i^\ast:=\dfrac{x_{i+1}+\ldots+x_{i+p_x}}{p_x}, \quad i=1,\ldots,n_x
$$
and
$$
y_j^\ast:=\dfrac{y_{j+1}+\ldots+y_{j+p_y}}{p_y}, \quad j=1,\ldots,n_y
$$
are the *knot averages* and where
$$
\hat{z}(u,v):=\dfrac{\sum\limits_{(x,y,z)\in\mathcal{P}}z\cdot w(x,y,u,v)}{\sum\limits_{(x,y,z)\in\mathcal{P}} w(x,y,u,v)}
$$
is the *control points estimator* of weight function $w:\mathbb{R}^2\times\mathbb{R}^2\to[0,1]$.

**In a nutshell.** We approximate a pointcloud $\mathcal{P}$ by using a tensor mesh and estimation of the control points by weighted averages.

### About the data

As test case, we present an anonymized version of the dataset adopted in [2]. We have performed an affine transformation of the original coordinates and preserving the average and variance of the rainfall field. The rain gauge network (owned by the ARPAL team of Regione Liguria) consists of 143 professional measure stations distributed over the whole region. The measures are acquired every 5-20 minutes. The resolution of the rain gauges is 0; 2mm while their accuracy is in the range of 2% error threshold.

### References

[1] A. Raffo and S. Biasotti. Weighted Quasi Interpolant Spline Approximations for Point Clouds: Properties and Applications, 2019.

[2] G. Patane', A. Cerri, V. Skytt, S. Pittaluga, S. Biasotti, D. Sobrero, T. Dokken and M. Spagnuolo. Comparing Methods for the Approximation of Rainfall Fields in Environmental Applications. *ISPR Journal of Photogrammetry and Remote Sensing*, 127:57–72, 2017.

[3] T. Hastie, R. Tibshirani and J. Friedman. The Elements of Statistical Learning. Data Mining, Inference, and Prediction. Springer. Second Edition. Corrected 12th printing - Jan 13, 2017.
