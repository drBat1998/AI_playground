---
tags: 
title: "High content screening identifies monensin as an EMT-selective cytotoxic compound"
authors: "Marion Vanneste, Qin Huang, Mengshi Li, Devon Moose, Lei Zhao, Mark A. Stamnes, Michael Schultz, Meng Wu, Michael D. Henry"
---

> [!Cite] 1.

Vanneste, M. _et al._ High content screening identifies monensin as an EMT-selective cytotoxic compound. _Sci Rep_ **9**, 1200 (2019).

>[!md] QAC

>[!md]
> **FirstAuthor**:: Vanneste, Marion  
> **Author**:: Huang, Qin  
> **Author**:: Li, Mengshi  
> **Author**:: Moose, Devon  
> **Author**:: Zhao, Lei  
> **Author**:: Stamnes, Mark A.  
> **Author**:: Schultz, Michael  
> **Author**:: Wu, Meng  
> **Author**:: Henry, Michael D.  
~    
> **Title**:: High content screening identifies monensin as an EMT-selective cytotoxic compound  
> **Year**:: 2019   
> **Citekey**:: vannesteHighContentScreening2019  
> **itemType**:: journalArticle  
> **Journal**:: *Scientific Reports*  
> **Volume**:: 9  
> **Issue**:: 1   
> **Pages**:: 1200  
> **DOI**:: 10.1038/s41598-018-38019-y    

> [!LINK] 
>
>  [Vanneste et al. - 2019 - High content screening identifies monensin as an EMT-selective cytotoxic compound.pdf](file:///Users/romankoval/Library/Mobile%20Documents/com~apple~CloudDocs/Library%20of%20Alexandria/ZotMove_files/Vanneste%20et%20al.%20-%202019%20-%20High%20content%20screening%20identifies%20monensin%20as%20an%20EMT-selective%20cytotoxic%20compound.pdf).

> [!Abstract]
>
> Epithelial-to-mesenchymal transition (EMT) is implicated in cancer metastasis and drug resistance. Specifically targeting cancer cells in an EMT-like state may have therapeutic value. In this study, we developed a cell imaging-based high-content screening protocol to identify EMT-selective cytotoxic compounds. Among the 2,640 compounds tested, salinomycin and monensin, both monovalent cation ionophores, displayed a potent and selective cytotoxic effect against EMT-like cells. The mechanism of action of monensin was further evaluated. Monensin (10 nM) induced apoptosis, cell cycle arrest, and an increase in reactive oxygen species (ROS) production in TEM 4-18 cells. In addition, monensin rapidly induced swelling of Golgi apparatus and perturbed mitochondrial function. These are previously known effects of monensin, albeit occurring at much higher concentrations in the micromolar range. The cytotoxic effect of monensin was not blocked by inhibitors of ferroptosis. To explore the generality of our findings, we evaluated the toxicity of monensin in 24 human cancer cell lines and classified them as resistant or sensitive based on IC50 cutoff of 100 nM. Gene Set Enrichment Analysis identified EMT as the top enriched gene set in the sensitive group. Importantly, increased monensin sensitivity in EMT-like cells is associated with elevated uptake of 3H-monensin compared to resistant cells.
>.
>
### Ideas, thoughts, useful information

> [!quote]+ Note ([Page 2](zotero://open-pdf/library/items/KQ2VTA5A?page=2&annotation=J7QGH5DI))
  **Interesting way to validate:
Then they ran a <b>test plate</b> — half the wells with <b>vehicle (negative control)</b>, half with <b>hygromycin (positive control)</b>, which kills the hygromycin-sensitive cells. From that “half-half” plate, they calculated standard quality-control metrics for high-throughput screens: <b>Signal-to-noise ratio (S/N)</b> = (mean of negatives − mean of positives) ÷ standard deviation of negatives.
It shows how clearly the positive signal (cell death) can be distinguished from the negative (no death) above random variation. <b>Signal-to-background ratio (S/B)</b> = mean of negatives ÷ mean of positives.
It expresses the fold difference between untreated and treated signals. <b>Z′-factor</b>, a composite measure of assay robustness that combines both signal separation and variability; values between <b>0.5 and 1.0</b> indicate an assay suitable for high-throughput screening.**

Conclusion
High-content imaging of cell death is also a powerful tool for assessing specific cytotoxicity. In this study, the authors engineered two prostate cancer–derived cell lines representing distinct states of the epithelial-to-mesenchymal transition (EMT) and used a high-throughput screening (HTS) platform to test how different treatments affected each subpopulation. By co-culturing fluorescently labeled epithelial (PC-3E-GFP) and EMT-like (TEM 4-18-mCherry) cells and tracking changes in their fluorescence over time, they could simultaneously measure drug sensitivity in both populations. This approach enabled the identification of compounds—such as salinomycin, monensin, and nigericin—that were selectively toxic to EMT-like cells, providing a framework for discovering treatments that target aggressive, therapy-resistant cancer phenotypes. Unfortunetely, in this study the HCI was used only to measure overall cell death, not to deistinguish amoung different death pathwya. To determine the specific cell deeath type, the authors followed up flow cytometry and treatmenr with pathway spcific inhibitors. 

[[HTI and regulated necrosis]]