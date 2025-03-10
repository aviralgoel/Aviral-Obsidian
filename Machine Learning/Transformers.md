1. ![[Transformer Architecture.pdf]]
2. Embedding Vectors are learnt by the model, i.e. they change over time.
3. Add & Norm step: Adds two matrices and then normalizes
## Layer Normalization

1. Let us say, for a 4 x 512 input to the encoder, we will get 4 x 512 output.
2. In layer normalization, these matrices are added and the resulting matrix is called residual matrix.
3. Then for each row in 4 x 512, mean and standard deviation is calculated and each element is normalized with respect to its row's mean and SD.
4. After normalization of each element, it is again multiplied by gamma and added to beta (both of which are learnable parameters). This process is called layer normalization.
5. $$
y_{i,j} = \gamma_j \cdot \left( \frac{(x_{i,j} + \text{encoder\_output}_{i,j}) - \mu_i}{\sigma_i} \right) + \beta_j
$$
