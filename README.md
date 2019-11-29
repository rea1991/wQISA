# Weighted Quasi Interpolant Spline Approximation for Rainfall Fields

This code performs Weighted Quasi Interpolant Spline Approximation with k-nearest neighbour weight functions. 

### Parameters setting
The optimal k is chosen, together with the optimal refinement level of the tensor mesh, by minimizing some prediction error (here: mean square error). The prediction error is estimated by performing 5 times a 5-gold cross-validation on the original dataset. For the sake of simplicity, we here directly upload the splitted data.
