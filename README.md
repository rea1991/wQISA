# Weighted Quasi Interpolant Spline Approximation (wQISA) for Rainfall Fields

This code performs wQISA with k-nearest neighbours weight functions. More details on the input data and the method itself are provided in the main file (wQISA for Rainfall Fields.ipynb).

### Parameters setting
The optimal k is chosen, together with the optimal refinement level of the tensor mesh, by minimizing some prediction error (here: mean square error). The prediction error is estimated by performing 5 times a 5-fold cross-validation on the original dataset. For the sake of simplicity, we here directly upload the splitted data.

### Output
The main file is expected to print some statistics for the error distribution, together with the optimal parameters. By using the data provided in the folder "data" and the suggested spline library (see the main file), the output should be the following:

```python
Average min is    0.04710540096550549
Average max is    2.889891020683991
Average mean is   0.9970376033520634
Average median is 0.9013234682760833
Average std is    0.7082250055027819
Average MSE is    1.5138957396858879
```

and

```python
Optimal k is 9
Optimal n is 10
```
