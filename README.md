## Principal Component Analysis (PCA), 3D to 2D, from scratch

Here we have:
- $$N$$ the number of features, $$N = 3$$.
- $$I$$ the number of samples, $$I = 50$$.
- $$P$$ is the dimension target, $$P = 2$$.

Our dataset is $$X^{(i)}$$ such as:
$$X^{(i)} = (x_1^{(i)},  x_2^{(i)},  x_3^{(i)})$$, its dimension are $$(I$$ x $$N)$$


### Step 1: Compute the Mean

We compute $$\mu$$ which is the mean of the dataset:

$$\mu = \frac{1}{I} \sum_{n=1}^{I} X^{(i)}$$

### Step 2: Center the Data

We center $$X^{(i)}$$ to get $$\tilde{X^{(i)}}$$ such as:

$$\tilde{X^{(i)}} = X^{(i)} - \mu$$


### Step 3: Solve the Optimization Problem

We need to solve:


$$\max_{u} \left( \frac{1}{I} \sum_{i=1}^{I} (\tilde{X^{(i)}} \cdot u)^2 \right)$$

where $$u$$ is a vector created by the projection of $$X^{(i)}$$ on the line passing by the origin and trying to shape $$X^{(i)}$$.

This is equivalent to:

$$\max_{u} \left( u^T \Sigma u \right)$$

where $$\Sigma$$ is the covariance matrix.

### Step 4: Use Lagrange Multipliers

Using the Lagrange method, we get:

$$
\max_{u} \left( u^T \Sigma u - \lambda (u^T u - 1) \right)
$$

Let's define:

$$
\mathcal{L} = u^T \Sigma u - \lambda (u^T u - 1)
$$

We need to solve:

$$
\nabla_u \mathcal{L} = 0
$$

This leads to:

$$\Sigma u - \lambda u = 0$$

Which is equivalent to:

$$\Sigma u = \lambda u$$

where:
- $$U = (u_1, u_2, u_p..., u_N)$$ are the eigenvectors.
- $$\lambda = (\lambda_1, \lambda_2, \lambda_p ..., \lambda_N)^T$$ are the eigenvalues.

We take the $$P$$-largest eigenvectors:

$$
U_P = (u_1, u_2, ..., u_P)
$$

### Step 5: Project the Data

Finally, we compute the projection:

$$
\tilde{Y^{(i)}} = X^{(i)} \cdot U_P
$$

Reconstructing the output in 3D:

$$
\tilde{Y_{3D}^{(i)}} = \tilde{Y^{(i)}} \cdot U_P^T
$$

Reconstructing the output in the original data:

$$
Y^{(i)} = \tilde{Y_{3D}^{(i)}} + \mu
$$

s/o to my professor Jae Yun JUN KIM.
