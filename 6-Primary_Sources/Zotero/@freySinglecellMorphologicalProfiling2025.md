---
tags: 
title: "Single-cell morphological profiling reveals insights into cell death"
authors: "Benjamin Frey, David Holmberg, Petter Byström, Ebba Bergman, Polina Georgiev, Martin Johansson, Patrick Hennig, Jonne Rietdijk, Dan Rosén, Jordi Carreras-Puigvert, Ola Spjuth"
---

> [!Cite] 1.

Frey, B. _et al._ Single-cell morphological profiling reveals insights into cell death. 2025.01.15.633042 Preprint at [https://doi.org/10.1101/2025.01.15.633042](https://doi.org/10.1101/2025.01.15.633042) (2025).

>[!md] QAC

>[!md]
> **FirstAuthor**:: Frey, Benjamin  
> **Author**:: Holmberg, David  
> **Author**:: Byström, Petter  
> **Author**:: Bergman, Ebba  
> **Author**:: Georgiev, Polina  
> **Author**:: Johansson, Martin  
> **Author**:: Hennig, Patrick  
> **Author**:: Rietdijk, Jonne  
> **Author**:: Rosén, Dan  
> **Author**:: Carreras-Puigvert, Jordi  
> **Author**:: Spjuth, Ola  
~    
> **Title**:: Single-cell morphological profiling reveals insights into cell death  
> **Year**:: 2025   
> **Citekey**:: freySinglecellMorphologicalProfiling2025  
> **itemType**:: preprint  
> **DOI**:: 10.1101/2025.01.15.633042    

> [!LINK] 
>
>  [Frey et al. - 2025 - Single-cell morphological profiling reveals insights into cell death.pdf](file:///Users/romankoval/Library/Mobile%20Documents/com~apple~CloudDocs/Library%20of%20Alexandria/ZotMove_files/Frey%20et%20al.%20-%202025%20-%20Single-cell%20morphological%20profiling%20reveals%20insights%20into%20cell%20death.pdf).

> [!Abstract]
>
> Analysis of single-cell data has emerged as a powerful tool for studying biological processes and response to perturbations. However, its application in morphological profiling is less explored. In this study we profile six cell death subtypes induced by 50 small molecule drugs across six concentrations using the Cell Painting assay. We evaluate the performance of three feature extraction methods at single-cell and aggregated level and apply supervised and unsupervised analyses to uncover factors contributing to cell death mechanisms. Our results show that a bagged LightGBMXT model, trained on single-cell DeepProfiler achieved classification accuracy of 77.23%, with a top overall performance of 89.97% for corresponding aggregated profiles. Furthermore, self-supervised learning using the transformer-based DINO network revealed highly resolved and biologically meaningful subpopulations, shedding light on perturbation- and concentration-specific molecular targets and dose-dependant morphological changes. Our findings demonstrate the potential of studying phenomic data on single-cell level to enhance the characterization of cell death pathways, advancing our understanding of perturbation effects at a granular level.
>.
>
### Table of context

> [!quote]+ Highlight ([Page 4](zotero://open-pdf/library/items/EP7QEMF8?page=4&annotation=YQ7M7IHA))
> 2.10 Energy distance  Energy distance (e-distance) (Peidli et al., 2024) was originally implemented for single-cell sequencing data as a metric for perturbation strength. We calculated e-distances per compound concentration set using single-cell profiles and the first 50 principal components.  Let x1, ...xN ∈ C1 and y1, ...yM ∈ C2 be single-cell profiles, where N, M represent the respective sample size and CT be our treatment spaces. We further define: 
### Ideas, thoughts, useful information

> [!quote]+ Note ([Page ](zotero://open-pdf/library/items/EP7QEMF8?page=1&annotation=8AYEUTLF))
  **Cell painting for distinguished different cell death!**

> [!quote]+ Highlight ([Page 4](zotero://open-pdf/library/items/EP7QEMF8?page=4&annotation=6AYQZY63))
> 2.9 Data post-processing  To ensure comparability, we applied the same post-processing and analysis pipeline to all three feature sets. In the following, we will also refer to the extracted feature vectors as "profiles". Feature vectors were first standardized to the negative control (DMSO) by subtracting the mean and dividing by the standard deviation of the DMSO cells per plate. For our aggregated analysis, we calculated the median profile per site. Feature selection was performed by removing missing value features, highly correlated (>99%), low variance (<0.01%) and blacklisted features as defined in the pycytominer package (Way et al., 2022). Additionally, features with >25% constant values across cells were removed. This resulted in just over 1,400 features for CellProfiler, 384 features for DINO, and 672 for DeepProfiler, respectively 

> [!quote]+ Highlight ([Page 5](zotero://open-pdf/library/items/EP7QEMF8?page=5&annotation=2X6WW7K4))
> 2.11 Grit score  Grit score measures the perturbation strength and reproducibility of a given treatment group. We calculated grit scores on a compound-concentration level using aggregated profiles. We filtered compound concentrations with a grit score below 1.5.  Let d1, ...dN ∈ N be morphological profiles of a control group and t ∈ CT a target profile of given treatment T with M replicate profiles r1, ..., rM . Then define D := {d1, ..., dM } where di = corr(t, ci) and S := {s1, ..., sM } where si = corr(t, ri). Let further μD, σD be the respective statistics of D. Then the grit score G is defined as: 
### Questions, things that I didn't understand

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/EP7QEMF8?page=2&annotation=CTRP6PNB))
> DINO 

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/EP7QEMF8?page=2&annotation=D2B9L9SZ))
> Masked Autoencoders 

[[high content imaging]]
[[HTI and regulated necrosis]]