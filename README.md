# Weighted Quasi Interpolant Spline Approximation (wQISA) for Rainfall Fields

This code performs wQISA with k-nearest neighbour weight functions. More details on the input data and the method itself are provided in the main file (wQISA for Rainfall Fields.ipynb).

### Parameters setting
The optimal k is chosen, together with the optimal refinement level of the tensor mesh, by minimizing some prediction error (here: mean square error). The prediction error is estimated by performing 5 times a 5-gold cross-validation on the original dataset. For the sake of simplicity, we here directly upload the splitted data.

### Acknowledgements
This project has received funding from the European Union’s Horizon 2020 research and innovation programme under the Marie Skłodowska-Curie grant agreement No 675789.
