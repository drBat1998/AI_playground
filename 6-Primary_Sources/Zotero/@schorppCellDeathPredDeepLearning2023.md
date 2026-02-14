---
tags: 
title: "CellDeathPred: a deep learning framework for ferroptosis and apoptosis prediction based on cell painting"
authors: "Kenji Schorpp, Alaa Bessadok, Aidin Biibosunov, Ina Rothenaigner, Stefanie Strasser, Tingying Peng, Kamyar Hadian"
---

> [!Cite] 1.

Schorpp, K. _et al._ CellDeathPred: a deep learning framework for ferroptosis and apoptosis prediction based on cell painting. _Cell Death Discov._ **9**, 277 (2023).

>[!md] QAC

>[!md]
> **FirstAuthor**:: Schorpp, Kenji  
> **Author**:: Bessadok, Alaa  
> **Author**:: Biibosunov, Aidin  
> **Author**:: Rothenaigner, Ina  
> **Author**:: Strasser, Stefanie  
> **Author**:: Peng, Tingying  
> **Author**:: Hadian, Kamyar  
~    
> **Title**:: CellDeathPred: a deep learning framework for ferroptosis and apoptosis prediction based on cell painting  
> **Year**:: 2023   
> **Citekey**:: schorppCellDeathPredDeepLearning2023  
> **itemType**:: journalArticle  
> **Journal**:: *Cell Death Discovery*  
> **Volume**:: 9  
> **Issue**:: 1   
> **Pages**:: 277  
> **DOI**:: 10.1038/s41420-023-01559-y    

> [!LINK] 
>
>  [Schorpp et al. - 2023 - CellDeathPred a deep learning framework for ferroptosis and apoptosis prediction based on cell pain.pdf](file:///Users/romankoval/Library/Mobile%20Documents/com~apple~CloudDocs/Library%20of%20Alexandria/ZotMove_files/Schorpp%20et%20al.%20-%202023%20-%20CellDeathPred%20a%20deep%20learning%20framework%20for%20ferroptosis%20and%20apoptosis%20prediction%20based%20on%20cell%20pain.pdf).

> [!Abstract]
>
> Cell death, such as apoptosis and ferroptosis, play essential roles in the process of development, homeostasis, and pathogenesis of acute and chronic diseases. The increasing number of studies investigating cell death types in various diseases, particularly cancer and degenerative diseases, has raised hopes for their modulation in disease therapies. However, identifying the presence of a particular cell death type is not an obvious task, as it requires computationally intensive work and costly experimental assays. To address this challenge, we present CellDeathPred, a novel deep-learning framework that uses high-content imaging based on cell painting to distinguish cells undergoing ferroptosis or apoptosis from healthy cells. In particular, we incorporate a deep neural network that effectively embeds microscopic images into a representative and discriminative latent space, classifies the learned embedding into cell death modalities, and optimizes the whole learning using the supervised contrastive loss function. We assessed the efficacy of the proposed framework using cell painting microscopy data sets from human HT-1080 cells, where multiple inducers of ferroptosis and apoptosis were used to trigger cell death. Our model confidently separates ferroptotic and apoptotic cells from healthy controls, with an average accuracy of 95% on non-confocal data sets, supporting the capacity of the CellDeathPred framework for cell death discovery.
>.
>
### Ideas, thoughts, useful information

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/FEZHZJSF?page=2&annotation=H2AJ86QG))
> Guided by the results of the pilot study, cell painting experiments were conducted using the optimized compound concentrations. HT-1080 cells were seeded in 384-well plates and treated with the five defined concentrations of the cell death inducers (Table 1) for 24 and 72 h. We used five (Hoechst 33342, Wheat Germ Agglutinin, Concanavalin A, TRITC-Phalloidin, Mitotracker) instead of the six dyes, which are described in the standard cell painting protocol, allowing us to run the staining at the same time without generating fluorescence overlay. Image sets of two slightly modified independent experiments were collected as training data sets: in experiment 1 the cells were imaged with ×40 magnification and a confocal spinning disk, while for experiment 2 a ×40 magnification and widefield was used. 

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/FEZHZJSF?page=2&annotation=5SR2IBZE))
> By this, we were able to select only images for training that reflected a certain level of intracellular ATP reduction. In all the experiments, we normalized the absolute ATP values to the DMSO levels. So, the wells with values close to 1.0 are considered not to be affected. While those approaching 0.0 are ”dead”. We selected wells with ATP values that fall into the range [0.3–0.8]. 

> [!quote]+ Highlight ([Page 4](zotero://open-pdf/library/items/FEZHZJSF?page=4&annotation=R35P4JKG))
> DL versus ML classification to classify cell death from cell painting  In order to test the CellDeathPred model on a previously unseen data set, we performed a third experiment in the same way as described in Fig. 3 (Supplementary Fig. 4). In contrast to experiments 1 and 2, the cells were only treated for 24 h, but this time we imaged the plates of the same experiment both confocal and non-confocal to investigate whether this has an impact on the classification accuracy. Also, these images were analyzed with our imaging software, and 245 features were extracted. Before evaluating ML models on the features extracted by Columbus software, a preprocessing step was essential for training the models. Mainly, we removed columns with not a number (NaN) values, duplicated columns, and normalized the values. We chose three ML models widely used in the literature: Random Forest [26], Logistic Regression [27], and AdaBoost [28]. We used uniform manifold approximation and projection (UMAP) [29] as a dimension reduction technique to visualize how images of  ferroptosis drugs cluster from those of apoptosis, and the healthy cells. As shown in the UMAP of CellDeathPred learnt feature space (Fig. 4A (DL), images of healthy, apoptosis, and ferroptosis classes are clustered into three distinct clusters, whilst they are mixed in the UMAP of cellular features extracted from Columbus software (Fig. 4A (ML)). A side-by-side comparison of DL vs ML methods (Fig. 4B) show that CellDeathPred reached a classification accuracy of over 93% for Plate 1 and Plate 2, which is almost 10% increase over the best ML method. Also, in most cases, CellDeathPred with SupConLoss outperforms CellDeathPred w/o SupConLoss (Fig. 4B), suggesting better model generalizability. This could also be demonstrated by the UMAP of feature space when we color the images according to their batch whilst images of different plates are well mixed, suggesting SupConLoss is effective in avoiding the batch effect problem (Supplementary Fig. 5). 




> [!quote]+ Highlight ([Page 9](zotero://open-pdf/library/items/FEZHZJSF?page=9&annotation=3KXZ73LT))
> Model training and application  Designing a DL model for distinguishing between cell death modalities given a set of microscopic images is challenging due to several factors as explained previously: batch effect and reduced generalizability performance. To overcome these issues, we propose to train in a supervised contrastive learning fashion using the SupConLoss defined as follows:  Lsup 1⁄4 X  i2I  Lsup  i 1⁄4X  i2I  1 jPðiÞj  X  p2PðiÞ  log expðzi zp=τÞ  P  a2AðiÞ expðzi za=τÞ  $z_i$ is an embedding vector with class label $y_i$ generated by the embedder network. $i$ is an anchor in the batch $I$. $P(i) = {p ∈ A(i) : y_i = y_p}$ denotes positive samples that belong to the same class. SupConLoss first calculates the inner product of the anchor with samples in $P(i)$, second applies an exponential function in order to amplify large values. The outputs are summed up and normalized over all samples $A = I\[1]$. $τ$ denotes the supervised temperature, a hyperparameter that helps to disentangle positive and negative samples. The main benefit of our supervised contrastive learning is that it disentangles batch effects from relevant biological variables [24, 32] and this can be seen in the UMAP reported results (Fig. 4A). Mainly, we chose UMAP over other dimensionality reduction techniques 

> [!quote]+ Highlight ([Page 10](zotero://open-pdf/library/items/FEZHZJSF?page=10&annotation=R5M94JMD))
> such as t-distributed stochastic neighbor embedding (t-SNE) or principal component analysis (PCA) owing to its speed and performance for the preservation of the global structure of the data. To further tackle the batch effect problem, we propose a batch-aware sampling strategy to better train our network. We further use categorical cross-entropy as classification loss during training. Ultimately, in our CellDeathPred architecture, we define the overall loss function as:  L 1⁄4 λ1 Lsup þ λ2 Lce  where $\lambda_1$ and $\lambda_2$ are hyper-parameters that control the relative importance of SupConLoss and cross-entropy losses, respectively. Empirically, we set the temperature parameter of the SupConLoss, the learning rate, and both $\lambda_1$ and $\lambda_2$ to 0.1, 1.25e-5, and 0.5, respectively. We define the batch size $bs$ using the following formula: bs 1⁄4 nplates nsamples y For a batch of size 30, we compute it as 30 = 2 × 5 × 3, which means it consists of samples from two plates with 5 samples of each cell death modality. The batch-norm layers were frozen to reduce overfitting. In the contrastive learning context we define a sample triplets: anchor, positive and negative. We define the anchor as an image belonging to a plate $p_i$ and the class $y_i$, while we choose the positive sample to be an image from another plate $p_p$ ($p_i ≠ p_p$) having the same label as the anchor and we define a negative sample as an image belonging to the same plate of the anchor with a different label $y_n$ ($y_i ≠ y_n$). The ultimate goal is to minimize the distance between the anchor and positive samples and maximize the one between the anchor and negative samples. The main advantage of the sampling strategy is increasing heterogeneity of the batch during training thus increasing the generalizability of the model in the case of having a data set with batch effect. To evaluate our model, we first train it using 80% of the data set and test it on 20%. We report accuracy and F1-score results in the field level (Fig. 4B) and in the well level (Fig. 5A). Knowing that all fields belonging to a particular well have the same label, we define the prediction on the well level as the majority voting where we count the number of apoptosis, ferroptosis, healthy predictions of the fields and assign the class with the maximum votes as the well class. Equipped with the above components, the proposed CellDeathPred not only overcomes the issues of applying a DL model on cell painting data but also represents the first automatic labeling method of drugs that can be easily adopted for classification on other data sets. 
### Important papers that I have to read

> [!quote]+ Highlight ([Page 10](zotero://open-pdf/library/items/FEZHZJSF?page=10&annotation=4KQMHXHD))
> 16. Dmitrenko A, Masiero MM, Zamboni N Self-supervised learning for analysis of temporal and morphological drug effects in cancer cell imaging data. 2022. Available from: https://doi.org/10.48550/arXiv.2203.04289. 17. Siegismund D, Wieser M, Heyse S, Steigele S. Self-supervised representation learning for high-content screening 2022 Available from: https://openreview.net/ pdf?id=XIofcluPNu. 

> [!quote]+ Highlight ([Page 10](zotero://open-pdf/library/items/FEZHZJSF?page=10&annotation=UXESN95Y))
> 20. Verduijn J, Van der Meeren L, Krysko DV, Skirtach AG. Deep learning with digital holographic microscopy discriminates apoptosis and necroptosis. Cell Death Discov. 2021;7:229. 