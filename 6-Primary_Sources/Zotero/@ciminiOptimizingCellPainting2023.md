---
tags: 
title: "Optimizing the Cell Painting assay for image-based profiling"
authors: "Beth A. Cimini, Srinivas Niranj Chandrasekaran, Maria Kost-Alimova, Lisa Miller, Amy Goodale, Briana Fritchman, Patrick Byrne, Sakshi Garg, Nasim Jamali, David J. Logan, John B. Concannon, Charles-Hugues Lardeau, Elizabeth Mouchet, Shantanu Singh, Hamdah Shafqat Abbasi, Peter Aspesi, Justin D. Boyd, Tamara Gilbert, David Gnutt, Santosh Hariharan, Desiree Hernandez, Gisela Hormel, Karolina Juhani, Michelle Melanson, Lewis H. Mervin, Tiziana Monteverde, James E. Pilling, Adam Skepner, Susanne E. Swalley, Anita Vrcic, Erin Weisbart, Guy Williams, Shan Yu, Bolek Zapiec, Anne E. Carpenter"
---

> [!Cite] 1.

Cimini, B. A. _et al._ Optimizing the Cell Painting assay for image-based profiling. _Nat Protoc_ **18**, 1981–2013 (2023).

>[!md] QAC

>[!md]
> **FirstAuthor**:: Cimini, Beth A.  
> **Author**:: Chandrasekaran, Srinivas Niranj  
> **Author**:: Kost-Alimova, Maria  
> **Author**:: Miller, Lisa  
> **Author**:: Goodale, Amy  
> **Author**:: Fritchman, Briana  
> **Author**:: Byrne, Patrick  
> **Author**:: Garg, Sakshi  
> **Author**:: Jamali, Nasim  
> **Author**:: Logan, David J.  
> **Author**:: Concannon, John B.  
> **Author**:: Lardeau, Charles-Hugues  
> **Author**:: Mouchet, Elizabeth  
> **Author**:: Singh, Shantanu  
> **Author**:: Abbasi, Hamdah Shafqat  
> **Author**:: Aspesi, Peter  
> **Author**:: Boyd, Justin D.  
> **Author**:: Gilbert, Tamara  
> **Author**:: Gnutt, David  
> **Author**:: Hariharan, Santosh  
> **Author**:: Hernandez, Desiree  
> **Author**:: Hormel, Gisela  
> **Author**:: Juhani, Karolina  
> **Author**:: Melanson, Michelle  
> **Author**:: Mervin, Lewis H.  
> **Author**:: Monteverde, Tiziana  
> **Author**:: Pilling, James E.  
> **Author**:: Skepner, Adam  
> **Author**:: Swalley, Susanne E.  
> **Author**:: Vrcic, Anita  
> **Author**:: Weisbart, Erin  
> **Author**:: Williams, Guy  
> **Author**:: Yu, Shan  
> **Author**:: Zapiec, Bolek  
> **Author**:: Carpenter, Anne E.  
~    
> **Title**:: Optimizing the Cell Painting assay for image-based profiling  
> **Year**:: 2023   
> **Citekey**:: ciminiOptimizingCellPainting2023  
> **itemType**:: journalArticle  
> **Journal**:: *Nature protocols*  
> **Volume**:: 18  
> **Issue**:: 7   
> **Pages**:: 1981-2013  
> **DOI**:: 10.1038/s41596-023-00840-9    

> [!LINK] 
>
>  [Cimini et al. - 2023 - Optimizing the Cell Painting assay for image-based profiling.pdf](file:///Users/romankoval/Library/Mobile%20Documents/com~apple~CloudDocs/Library%20of%20Alexandria/ZotMove_files/Cimini%20et%20al.%20-%202023%20-%20Optimizing%20the%20Cell%20Painting%20assay%20for%20image-based%20profiling.pdf).

> [!Abstract]
>
> In image-based profiling, software extracts thousands of morphological features of cells from multi-channel fluorescence microscopy images, yielding single-cell profiles that can be used for basic research and drug discovery. Powerful applications have been proven, including clustering chemical and genetic perturbations on the basis of their similar morphological impact, identifying disease phenotypes by observing differences in profiles between healthy and diseased cells and predicting assay outcomes by using machine learning, among many others. Here, we provide an updated protocol for the most popular assay for image-based profiling, Cell Painting. Introduced in 2013, it uses six stains imaged in five channels and labels eight diverse components of the cell: DNA, cytoplasmic RNA, nucleoli, actin, Golgi apparatus, plasma membrane, endoplasmic reticulum and mitochondria. The original protocol was updated in 2016 on the basis of several years’ experience running it at two sites, after optimizing it by visual stain quality. Here, we describe the work of the Joint Undertaking for Morphological Profiling Cell Painting Consortium, to improve upon the assay via quantitative optimization by measuring the assay’s ability to detect morphological phenotypes and group similar perturbations together. The assay gives very robust outputs despite various changes to the protocol, and two vendors’ dyes work equivalently well. We present Cell Painting version 3, in which some steps are simplified and several stain concentrations can be reduced, saving costs. Cell culture and image acquisition take 1–2 weeks for typically sized batches of ≤20 plates; feature extraction and data analysis take an additional 1–2 weeks.
>.
>
### Ideas, thoughts, useful information

> [!quote]+ Note ([Page ](zotero://open-pdf/library/items/ZQ8DVGAV?page=1&annotation=W8PKNGGE))
  **1. Microscope type: widefield vs confocal Result: No consistent difference in profile quality between widefield and confocal imaging

2. Pixel binning Compared 1×1 (full resolution) vs 2×2 binning (pixel averaging). Result: No detectable loss of morphological profile quality with 2×2 binning
3. Exposure times Tested higher vs lower exposure settings across several channels. Result: No meaningful change in profile quality (Figure 5D). As long as exposures are: within dynamic range, avoiding saturation, and capturing sufficient signal,→ differences are negligible. Recommendation: Select exposure times that maximise signal-to-noise but prioritise speed and minimal phototoxicity.
4. Z-plane acquisition
multi-plane imaging may be worthwhile for: neuronal cultures, thicker samples, or confocal systems.
5. Number of fields of view (FOVs) Increasing FOVs per well improved reproducibility: Each additional field increased percent replicating up to ~10 FOVs. Beyond 10 FOVs, gains plateaued.
Objective & magnification 20× water-immersion objective (NA 1.0) recommended — balances: organelle-level resolution field of view imaging throughput
5. Photobleaching management Image channels in order of decreasing excitation wavelength (from longest to shortest) to reduce bleaching of weak fluorophores by shorter-wavelength excitation. Example (long → short): Cy5 (~630 nm) Texas Red (~590 nm) TRITC (~555 nm) GFP/FITC (~470 nm) DAPI/Hoechst (~385 nm) If your microscope has multiple cameras (e.g., Opera Phenix), separate simultaneous channels across cameras to minimize total illumination time.
6. Exposure and dynamic range Avoid saturation: For 16-bit images (0–65,535), typical max intensity ≈ 32,000 (≈50% dynamic range). This prevents clipping if a perturbation increases fluorescence intensity. Slightly shorter exposures can be used to improve throughput as long as the signal-to-noise ratio remains high. CRITICAL: Never exceed saturation (65,535 intensity); ensure signal uses ~50% of range.

Pre-run verification Before full acquisition: Image 3–5 wells at several plate positions (center, edges, corners). Check: Focus stability Illumination evenness Channel separation Absence of well-edge artifacts

9. Well-edge exclusion Avoid capturing edges of wells — they distort illumination and segmentation. Configure site coordinates to remain within the flat, central region of each well. Post-processing removal is possible but inefficient and error-prone.**

[[High-content image-based analysis]]