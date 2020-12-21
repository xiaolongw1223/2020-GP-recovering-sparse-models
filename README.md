# 2020-GP-recovering-sparse-models
Mixed Lp norm inversion
==========================
Gravity gradient data inversion using mixed Lp norm regularization.

**Authors:**
- Xiaolong Wei (xwei7@uh.edu)
- Jiajia Sun (jsun20@uh.edu)

## Requirements

- Python 3.6 or later

- SimPEG (https://simpeg.xyz/) can be installed following (https://docs.simpeg.xyz/content/basic/installing.html).

- After successful installation of the official SimPEG, install a modified version from Xiaolong's github (https://github.com/xiaolongw1223). Xiaolong made a few changes, yet haven't pull request so far.

  - The modifed version of SimPEG can be installed by using pip:

        pip install git+https://github.com/xiaolongw1223/simpeg.git@Joinv_0.13.0_gzz --upgrade --user

## Running codes

After unzipping the two zipped files,

- In an IPython console

      run MixedLpInversion.py Input.json

- In a command terminal

      $ python MixedLpInversion.py Input.json


## Introduction of "Input.json" file

- data_file: observed gravity gradient data.

- mesh_file: model discretization or parameterization.

- example: we can select either "spheric" or "horse" to perform inversion using spherical anomaly body or horse shoe shaped model, respectively. And the results (e.g., figures and data) will be stored in the corresponding folders named by the date and time.

- topography: added topography.

- lower_bound and upper_bound: lower and upper bound applied to constraint inversion.

- norm_p: norm value implemented on the smallness component of regularization term.

- norm_q: norm value implemented on the three smoothness componenets of regularization term.

- alpha_s: a constant weighting parameter for smallness component.

- alpha_x: a constant weighting parameter for smoothness component in x direction.

- alpha_y: a constant weighting parameter for smoothness component in y direction.

- alpha_z: a constant weighting parameter for smoothness component in z direction.

## Examples

- p=q=2: classic L2 norm inversion (Li and Oldenburg, 1996, 1998)

- p=q=1 or 0: sparse inversion (Farquharson, 2008; Sun and Li, 2014)

- p!=q: mixed Lp norm inversion (Fournier and Oldenburg, 2019)

- alpha_s=0, q=0: focusing inversion (Portniaguine and Zhdanov, 1999)

- alpha_s=0, q=1: total variation inversion (Rudin et al., 1992)

## Reproducibility

- To reproduce our results, we have created two example folders: Example1_spheric and Example2_horseShoe, that contain the observed data, mesh and topography files. To reproduce the inversion results in Figure 2(a), the Input.json file looks like the following:

		"data_file": "gzz.obs",
		"mesh_file": "mesh.txt",
		"example": "spheric",
		"topography": "topo.topo",
		"lower_bound": -1,
		"upper_bound": 0.2,
		"norm_p": 1,
		"norm_q": 2,
		"alpha_s": 1,
		"alpha_x": 0,
		"alpha_y": 0,
		"alpha_z": 0

## References

Cockett, R., Kang, S., Heagy, L.J., Pidlisecky, A. and Oldenburg, D.W., 2015. SimPEG: An open source framework for simulation and gradient based parameter estimation in geophysical applications. Computers & Geosciences, 85, pp.142-154.

Farquharson, C.G., 2008. Constructing piecewise-constant models in multidimensional minimum-structure inversions. Geophysics, 73(1), pp.K1-K9.

Fournier, D. and Oldenburg, D.W., 2019. Inversion using spatially variable mixed ℓ p norms. Geophysical Journal International, 218(1), pp.268-282.

Li, Y. and Oldenburg, D.W., 1996. 3-D inversion of magnetic data. Geophysics, 61(2), pp.394-408.

Li, Y. and Oldenburg, D.W., 1998. 3-D inversion of gravity data. Geophysics, 63(1), pp.109-119.

Portniaguine, O. and Zhdanov, M.S., 1999. Focusing geophysical inversion images. Geophysics, 64(3), pp.874-887.

Rudin, L.I., Osher, S. and Fatemi, E., 1992. Nonlinear total variation based noise removal algorithms. Physica D: nonlinear phenomena, 60(1-4), pp.259-268.

Sun, J. and Li, Y., 2014. Adaptive L p inversion for simultaneous recovery of both blocky and smooth features in a geophysical model. Geophysical Journal International, 197(2), pp.882-899.
