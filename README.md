# GRISLI
## Gene Regulation Inference for Single-cell with LInear differential equations and velocity inference

#### Abstract
Single-cell RNA sequencing (scRNA-seq) offers new possibilities to infer gene regulation networks (GRN) for biological processes involving a notion of time, such as cell differentiation or cell cycles. It also raises many challenges due to the destructive measurements inherent to the technology. In this work we propose a new method named GRISLI for *de novo* GRN inference from scRNA-seq data. GRISLI infers a velocity vector field in the space of scRNA-seq data from profiles of individual data, and models the dynamics of cell trajectories with a linear ordinary differential equation to reconstruct the underlying GRN with a sparse regression procedure. We show on real data that GRISLI outperforms a recently proposed state-of-the-art method for GRN reconstruction from scRNA-seq data.

## Reference

Biorxiv link: https://www.biorxiv.org/content/10.1101/464479v1

doi: https://doi.org/10.1101/464479

## Requirements

GRISLI is written in Matlab, it uses the SPAMS toolbox (http://spams-devel.gforge.inria.fr/) to solve the lasso problem. Therefore one may need to install the .mex files of SPAMS before using GRISLI (a spams-matlab-v2.6 folder is provided).

Two experimental scRNA-seq. datasets (373 and 758 cells) studied in GRISLI had previsouly been used in SCODE (Matsumoto et al., 2017) and can be found as well on https://github.com/hmatsu1226/SCODE
The third experimental scRNA-seq. dataset (3,696 cells), introduced to compare velocity inference algorithms, comes from the tutorial of the scvelo method https://scvelo.readthedocs.io/index.html (github: https://github.com/theislab/scvelo).

GRISLI has been compared to SCODE (Matsumoto et al., 2017) and TIGRESS (Haury et al. 2012). The TIGRESS code can be found on http://members.cbio.mines-paristech.fr/~ahaury/svn/dream5/html/index.html while SCODE is on https://github.com/hmatsu1226/SCODE.
SCODE is written in R. We call Rscript in Matlab and slightly modified the .r code of SCODE. Thus if ones wishes to test SCODE through the GRISLI code, it is required to install Rscript. See SCODE-master for the corresponding files.
TIGRESS is written in Matlab. If ones wishes to test TIGRESS through the GRISLI code, please download TIGRESS-PKG-2.1 as a subfolder of GRISLI/.

## Download

```
git clone https://github.com/PCAubin/GRISLI
cd GRISLI
```
Or download from the "Download ZIP" button and unzip it.

## Running GRISLI
See demo_GRISLI_paper_results.m to reproduce our numerical experiments and compare them to TIGRESS, SCODE or your own methods. Various tables of results are provided in the AUROC_boxplots and AUROC_files. These results are used in demo_GRISLI_paper_results.m to plot the various curves of the article. If only one set of GRISLI parameters is tested, computation should take between 10s to 400s depending on the chosen R (typically chosen between 10 and 3000). Computation time also increases with larger L.

If you wish to use GRISLI on your own dataset in a _de novo_ fashion, have a try at demo_GRISLI_denovo_analysis.m The result (Rnk_array_TIGRESS_area_L) is a list of matrices containing the edges ranked by their importance (from 1 (the first predicted) to GxG (the last predicted)). These ranks are used in demo_GRISLI_paper_results.m to compute ROC_scores if you have a reference matrix **A** under hand. 

Pierre-Cyril Aubin-Frankowski, 31/10/2018
