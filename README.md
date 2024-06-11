# SLIDE: Significant Latent Factor Interaction Discovery and Exploration across biological domains 

## Overview of SLIDE
The Das Lab presents a novel data-distribution-free approach to analyze high-dimensional multiomic datasets and uncover latent factors that drive the outcome of interest, SLIDE. 

 - SLIDE makes no assumptions regarding the distribution of the underlying data as it significantly builds on a unique latent-factor regression framework.
 - It takes into account an extremely large search space of relationships to converge on a very small subset of biologically relevant and actionable latent factors.
 - Critically, SLIDE incorporates both linear and nonlinear relationships, including complex hierarchical structures.
 - The discovery of SLIDE is also coupled to rigorous false discovery rate (FDR) control via our unique analytical framework that creatively adapts ultramodern methods for FDR control


## Table of Contents

- [How to Use](#how-to-use)
- [Requirements and Restrictions](#requirements-and-resistrictions)
- [Downloading Outputs](#downloading-outputs)
- [For the Future](#for-the-future)

## How To Use

Read through these instructions and defitions to understand how to use SLIDE. 

The key input to SLIDE are just two csv files, the data matrix x and the response vector y file post pre-processing such as batch effect correction and/or normalization (for example, for scRN-seq data, first process with the standard Seurat pipeline).

The x file contains your data in a sample by feature format, such as single cell transcriptomics (**cell by gene**), or spatial proteomics (**region by protein**). The y file contains the responses of the data, such as severity of disease, spatial regions or clonal expansion. Since SLIDE is a regression method, when the response vector has multiple unique values (not just two classes), please make sure there are an ordinal relation between the y values. **Please make sure both csv files have row names and column names.*

SLIDE also provides other parameters (which will be displayed in a drop-down menu). However, we have set default values to many parameters that works well with majority of the data moralities. Read through the [SLIDE: Parameter Tuning](public/SLIDE.pdf) to find more information about each of the parameters. 

**Otherwise the main parameters are:**

x_path: a string of the path to the data matrix (x) in the csv format with row names and column names
where each row is samples (cells, patients, regions. . . ) and each column is a features (genes, proteins. . . )

y_path: a string of the path of the response vector (y) in the csv format with row names and column names where each row is a sample and the column would be the outcome of interest

delta: control the number of all latent factors. The higher the delta, the less number of latent factors will
be found. **Default as 0.01 and 0.1**

lambda: control the sparsity of all latent factors. The higher the lambda, the less number of features will
be in a latent factor. **Default as 0.5 and 1**


#### Recommendations
If you have **human single-cell data**, our recommended workflow is to pseudobulk your dataset since the cell-to-cell variability is high.

If you have **mouse single cell data**,  with the reduced cell-to-cell variability, you can consider each cell as a sample.

## Requirements and Resistrictions 
**It is extremely important that if the input data is sparse (such as scRNA-seq datasets), please pre-process the data as described in the [Preprocessing-and-Filtering](public/Preprocessing-and-Filtering%20(1).pdf) document.**

**Note:**
- Jobs put into SLIDE WILL HAVE AN EXCEEDING TIME, otherwise if it's too large, it will be terminated
- SLIDE will not run (smoothly atleast) if you exceed 5,000 features (could change: however, you may collapse them)
- NO k-fold-cross-validation!!! (For now for the simplest template)


## Downloading Outputs
Outputs will consist of: 
- A list of latent factors
- Correlation Plots
- Structure and composition information 

Outputs will be quickly produced, and you, the user should be able to keep a tab open while the results formulate. 

## For the Future
In the future, as SLIDE webserver becomes a more widely used server, more advanced technologies will be applied. 


