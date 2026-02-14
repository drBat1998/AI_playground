---
tags: 
title: "Deep transfer learning approach for automated cell death classification reveals novel ferroptosis-inducing agents in subsets of B-ALL"
authors: "Paweł Stachura, Zhe Lu, Raphael M. Kronberg, Haifeng C. Xu, Wei Liu, Jia-Wey Tu, Katerina Schaal, Ersen Kameri, Daniel Picard, Silvia von Karstedt, Ute Fischer, Sanil Bhatia, Philipp A. Lang, Arndt Borkhardt, Aleksandra A. Pandyra"
---

> [!Cite] 1.

Stachura, P. _et al._ Deep transfer learning approach for automated cell death classification reveals novel ferroptosis-inducing agents in subsets of B-ALL. _Cell Death Dis_ **16**, 396 (2025).

>[!md] QAC

>[!md]
> **FirstAuthor**:: Stachura, Paweł  
> **Author**:: Lu, Zhe  
> **Author**:: Kronberg, Raphael M.  
> **Author**:: Xu, Haifeng C.  
> **Author**:: Liu, Wei  
> **Author**:: Tu, Jia-Wey  
> **Author**:: Schaal, Katerina  
> **Author**:: Kameri, Ersen  
> **Author**:: Picard, Daniel  
> **Author**:: von Karstedt, Silvia  
> **Author**:: Fischer, Ute  
> **Author**:: Bhatia, Sanil  
> **Author**:: Lang, Philipp A.  
> **Author**:: Borkhardt, Arndt  
> **Author**:: Pandyra, Aleksandra A.  
~    
> **Title**:: Deep transfer learning approach for automated cell death classification reveals novel ferroptosis-inducing agents in subsets of B-ALL  
> **Year**:: 2025   
> **Citekey**:: stachuraDeepTransferLearning2025  
> **itemType**:: journalArticle  
> **Journal**:: *Cell Death & Disease*  
> **Volume**:: 16  
> **Issue**:: 1   
> **Pages**:: 396  
> **DOI**:: 10.1038/s41419-025-07704-y    

> [!LINK] 
>
>  [Stachura et al. - 2025 - Deep transfer learning approach for automated cell death classification reveals novel ferroptosis-in.pdf](file:///Users/romankoval/Library/Mobile%20Documents/com~apple~CloudDocs/Lib/ZotMove_files/Stachura%20et%20al.%20-%202025%20-%20Deep%20transfer%20learning%20approach%20for%20automated%20cell%20death%20classification%20reveals%20novel%20ferroptosis-in.pdf).

> [!Abstract]
>
> Ferroptosis is a recently described type of regulated necrotic cell death whose induction has anti-cancer therapeutic potential, especially in hematological malignancies. However, efforts to uncover novel ferroptosis-inducing therapeutics have been largely unsuccessful. In the current investigation, we classified brightfield microscopy images of tumor cells undergoing defined modes of cell death using deep transfer learning (DTL). The trained DTL network was subsequently combined with high-throughput pharmacological screening approaches using automated live cell imaging to identify novel ferroptosis-inducing functions of the polo-like kinase inhibitor volasertib. Secondary validation showed that subsets of B-cell acute lymphoblastic leukemia (B-ALL) cell lines, namely 697, NALM6, HAL01, REH and primary patient B-ALL samples were sensitive to ferroptosis induction by volasertib. This was accompanied by an upregulation of ferroptosis-related genes post-volasertib treatment in cell lines and patient samples. Importantly, using several leukemia models, we determined that volasertib delayed tumor growth and induced ferroptosis in vivo. Taken together, we have applied DTL to automated live-cell imaging in pharmacological screening to identify novel ferroptosis-inducing functions of a clinically relevant anti-cancer therapeutic.
>.
>
### Ideas, thoughts, useful information

> [!quote]+ Note ([Page 2](zotero://open-pdf/library/items/U2E6DB6R?page=2&annotation=VKX4DIHQ))
  **Why brightfield has been chosen for this study?**

> [!quote]+ Note ([Page 2](zotero://open-pdf/library/items/U2E6DB6R?page=2&annotation=8EY5PYUQ))
  **Apoptosis induced by stauro., ferroptosis by RSL3 and inhibit by Fer1, necroptosis inudce by TNFa+zVAD and inhibit by Nec1**

> [!quote]+ Highlight ([Page 12](zotero://open-pdf/library/items/U2E6DB6R?page=12&annotation=NNY37UNR))
> Training: We trained the network with the batch size of 100 and 50 epochs, Early Stopping of 25 on the images of the samples from the data set (ntrain = 1024 patches for each class) using the expert annotations data set as ground truth. The predicted probability for each image patch to contain each of the labels (‘apo’, ‘aut’, ‘fer’, ‘hea’, ‘nec’) was used as the objective/loss function (Cross Entropy Loss) in the training. We used Adam as the optimizer for this deep transfer learning approach and initial learning rate of 0.0001 and a decrease it by 5% each five epochs. Training and validation was performed on a Nvidia A100 of the high performance cluster (HPC, Hilbert) of the HHU, and on Quadro T2000 with Max-Q Design (Nvidia Corp., Santa Clara, CA, USA), depending on the computational power needed. 


[[Deep Learning with HTI]]