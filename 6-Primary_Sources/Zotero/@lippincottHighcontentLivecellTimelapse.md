---
tags: 
title: "High-content live-cell time-lapse imaging predicts cells about to die via apoptosis"
authors: "Michael J Lippincott, Jenna Tomkinson, Ibrahim Bilem, Mahomi Suzuki, Akiko Nakde, Toshiaki Endou, Simon Mathien, Felix Lavoie-Perusse, Carla Basualto-Alarcón, Gregory P Way"
---

> [!Cite] 1.

Lippincott, M. J. _et al._ High-content live-cell time-lapse imaging predicts cells about to die via apoptosis.

>[!md] QAC

>[!md]
> **FirstAuthor**:: Lippincott, Michael J  
> **Author**:: Tomkinson, Jenna  
> **Author**:: Bilem, Ibrahim  
> **Author**:: Suzuki, Mahomi  
> **Author**:: Nakde, Akiko  
> **Author**:: Endou, Toshiaki  
> **Author**:: Mathien, Simon  
> **Author**:: Lavoie-Perusse, Felix  
> **Author**:: Basualto-Alarcón, Carla  
> **Author**:: Way, Gregory P  
~    
> **Title**:: High-content live-cell time-lapse imaging predicts cells about to die via apoptosis  
> **Year**:: Error: `format` can only be applied to dates. Tried for format object   
> **Citekey**:: lippincottHighcontentLivecellTimelapse  
> **itemType**:: journalArticle  
> **Journal**:: **    

> [!LINK] 
>
>  [Lippincott et al. - High-content live-cell time-lapse imaging predicts cells about to die via apoptosis.pdf](file:///Users/romankoval/Library/Mobile%20Documents/com~apple~CloudDocs/Lib/ZotMove_files/Lippincott%20et%20al.%20-%20High-content%20live-cell%20time-lapse%20imaging%20predicts%20cells%20about%20to%20die%20via%20apoptosis.pdf).

> [!Abstract]
>
> Cell death is a dynamic process that unfolds through time. Live-cell time-lapse imaging captures these dynamics in a way that’s impossible for static snapshots. High-content imaging (HCI), which has been developed for static microscopy, applied to time-lapse imaging can quantify how single-cell states change through time. Here we show the ability of high-content live-cell time-lapse imaging (HCLTI) to quantify the onset and progression of one form of cell death called apoptosis. We apply the Live Cell Painting assay called ChromaLIVETM and develop an HCLTI analysis pipeline. We show that HCLTI can discern the morphology dynamics of cells undergoing apoptosis, and demonstrate that machine learning can predict apoptosis as early as 100 minutes after exposing HeLa cells to the apoptosis inducer Staurosporine. This technical advancement paves the way for future studies to better understand the dynamics of other forms of cell death. Understanding cell death dynamics is one piece of solving larger biomedical puzzles like understanding how cells resist death (e.g., therapeutic resistance of cancer cells) and how cells die too soon (e.g., neurodegeneration).
>.
>
### Ideas, thoughts, useful information

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/KCDI8I6S?page=2&annotation=3KKEN5P4))
> Developing a time analysis pipeline  We developed an HCLTI pipeline to process all images taken at each timepoint. The pipeline is similar to how we would process a single-timepoint HCI (e.g., Cell Painting21) experiment, with a few notable differences after cells are segmented (Figure 1B). Briefly, we maximally projected z-stacks, performed illumination correction, and segmented every single cell, nucleus, and cytoplasm using Cellpose and CellProfiler.14,22 We then performed feature extraction in two ways. First, we used CellProfiler to extract hand-engineered, computer vision features. Second, we used scDINO to extract classification (CLS) token embeddings of each single cell.13 These CLS token embeddings are a learned high-dimensional token in the DINO architecture, acting as a deep learning embedding.23 However, because our data are time-lapse, we diverged from the standard image-based profiling workflow.10 Specifically, we tracked single cells across time using the open-source Python package Ultrack.24 Ultrack assigns a unique ID to a single cell that is tracked through time, making it possible to relate profiled single cells across timepoints as paired data. After feature extraction, we merged single-cell profiles and single-cell tracks into a harmonized format using CytoTable25, and performed normalization and feature selection using Pycytominer.26 We normalized using the DMSO vehicle-treated cells at the first observed timepoint as a reference. In total, our time-lapse image-based profiles consisted of 188,065 total observations, with 20,677 single cells tracked through time (unique cells observed). Our two feature extraction pipelines measured 3,837 features (2,301 CellProfiler [CP] features and 1,536 scDINO embeddings). We performed feature selection on the concatenated (CP and scDINO) feature space, which resulted in 2,336 total features (800 CP and 1,536 scDINO). See the Methods section for complete data processing details. We subsequently generated aggregate profiles by calculating the median per feature of all single cells per well per time point. Additionally, we generated consensus profiles, which are the median of all single cells across all replicate wells per time point, giving a profile representation for each dose of staurosporine. 

> [!quote]+ Highlight ([Page 13](zotero://open-pdf/library/items/KCDI8I6S?page=13&annotation=ZJ98Q3VV))
> Image Acquisition  After treatment of staurosporine, we imaged FOVs on the Yokogawa CellVoyager CQ1 spinning disk confocal microscope with an Olympus UPLXAPO 20x dry lens with a 0.75 NA. Live-cell imaging of ChromaLIVETM- and Hoechst-stained samples was performed every 30 minutes for six hours total. At the six hours endpoint, fixed and stained cells for AnnexinV and Hoechst were imaged. Four FOVs per well were imaged and each FOV included three z-slices spaced 3 um apart. Imaging settings are summarized in Table 

> [!quote]+ Highlight ([Page 14](zotero://open-pdf/library/items/KCDI8I6S?page=14&annotation=TWKE6RQA))
> Image analysis: Illumination correction and segmentation  We performed a standard image analysis pipeline to process each individual frame in the time-lapse experiment. Specifically, we processed all images through an illumination correction pipeline using CellProfiler. We then performed nuclei segmentation using CellPose V, which utilizes the segment anything model.22,23 We performed cell and cytoplasm segmentation using CellProfiler with a propagation-based minimum cross-entropy segmentation algorithm.14 We saved masks for use in tasks such as image registration and feature extraction. 

> [!quote]+ Highlight ([Page 14](zotero://open-pdf/library/items/KCDI8I6S?page=14&annotation=XT4J73PE))
> Image analysis: time-lapse feature extraction  We used a standard CellProfiler14 feature extraction pipeline, with the exception of cell segmentation, to extract hand-drawn features for every single cell in all images across all time points. We used the CellProfiler profiles to find every single cell’s x,y centroid to generate single-cell crops (188,065). We then calculated the mean and standard deviation of the signal across every single-cell crop to generate a normalization tensor needed for scDINO.13 We then used snakemake to run the scDINO featurization pipeline. scDINO outputs a learned class (CLS) token that has 384 dimensions. Effectively, this gives 384 deep learning (DL) features per image. Given that we have four channels per single-cell crop, we extract (4 x 384) 1,536 deep learning scDINO embeddings. All workflows and scDINO pipelines were modified from the original scDINO GitHub repository from a fixed commit hash; links to GitHub repositories can be found in code availability. 

> [!quote]+ Highlight ([Page 14](zotero://open-pdf/library/items/KCDI8I6S?page=14&annotation=5IVFXEM5))
> Image analysis: Image registration and alignment  We observed a slight x,y coordinate shift in the terminal images (containing nuclei and AnnexinV stains) compared to the final ChromaLive timepoint. To relate or track single cells across these time points, we performed image registration on the nuclei channels to register the offset of each FOV (Supplemental Figure 7). We then applied the specific offset to each of the terminal FOVs. 

> [!quote]+ Highlight ([Page 15](zotero://open-pdf/library/items/KCDI8I6S?page=15&annotation=YBHEBT45))
> mage analysis: Terminal segmentation and feature extraction  We imported the final ChromaLive timepoint cell segmentation masks to measure cytoplasm features in the terminal, AnnexinV images. We segmented terminal time point nuclei using the same CellProfiler-based approach we described for each ChromaLive time point. We used these cytoplasm and nuclei masks to featurize single-cells at the terminal time point. We also extracted whole image features from the registered and aligned terminal time point images.14 

> [!quote]+ Highlight ([Page 15](zotero://open-pdf/library/items/KCDI8I6S?page=15&annotation=CRNAF7RC))
> Image analysis: Single-cell tracking  To track single cells across time, we used Ultrack24, a fast and scalable open-source scientific software for tracking cells in high-dimensional data. We output a single parquet file per FOV that contains multiple single-cell tracks. We merged these single-cell tracks with the generated profiles. 

> [!quote]+ Highlight ([Page 15](zotero://open-pdf/library/items/KCDI8I6S?page=15&annotation=JAHB7U7H))
> Image-based profiling  We generated image-based profiles from every individual SQLite file output by CellProfiler and scDINO by using our open-source scientific software, CytoTable.14,25,26 We merged the single-cell tracks from Ultrack into the CellProfiler profiles prior to concatenating every single-cell CellProfiler and scDINO profile into one profile matrix (row = single cells, columns = metadata and morphology features). We next used our open-source software, Pycytominer26, to perform normalization of all single cells by fitting a standard scalar normalization (z-score) to the DMSO-treated cells at time point 0. The fit was then applied to all other wells and timepoints. We subsequently used Pycytominer to perform feature selection using standard parameters. Specifically, we removed features that had: more than 5% of values that were NA or NULL; a Pearson correlation coefficient across all samples greater than 0.9; and low variance. 

> [!quote]+ Highlight ([Page 15](zotero://open-pdf/library/items/KCDI8I6S?page=15&annotation=EVDBXSAM))
> Training elastic net models to predict AnnexinV  We trained two types of elastic net models. First, we trained an elastic net to predict the integrated intensity of AnnexinV in the cytoplasm using final timepoint profiles from the ChomaLiveTM and Hoechst profiles. Second, we trained an elastic net to predict the full terminal feature vector of AnnexinV and nuclear features using final timepoint profiles from the ChromaLiveTM and Hoechst profiles. We also trained negative control shuffled baseline models, in which we randomly permuted the final timepoint feature space (training data) to predict each endpoint. For every model trained regardless of input profile, we ran a five-fold cross-validation with hyperparameter optimization across the following hyperparameter space: alpha, [0.1, 1.0, 10.0, 100.0, 1000.0]; l1 ratio, [0.1, 0.25, 0.5, 0.75, 0.9]; with 10,000 max iterations. We trained each model using scikit-learn v1.6.1.40 We evaluated models only on the last timepoint to predict the terminal timepoint, we computed mean squared error and R-squared metrics on the testing dataset for both every model and its accompanying shuffled baseline model. 

[[High-content image-based analysis]]
[[high content imaging]]