---
tags: 
title: "Workflow and metrics for image quality control in large-scale high-content screens"
authors: "Mark-Anthony Bray, Adam N. Fraser, Thomas P. Hasaka, Anne E. Carpenter"
---

> [!Cite] 1.

Bray, M.-A., Fraser, A. N., Hasaka, T. P. & Carpenter, A. E. Workflow and metrics for image quality control in large-scale high-content screens. _J Biomol Screen_ **17**, 266–274 (2012).

>[!md] QAC

>[!md]
> **FirstAuthor**:: Bray, Mark-Anthony  
> **Author**:: Fraser, Adam N.  
> **Author**:: Hasaka, Thomas P.  
> **Author**:: Carpenter, Anne E.  
~    
> **Title**:: Workflow and metrics for image quality control in large-scale high-content screens  
> **Year**:: 2012   
> **Citekey**:: brayWorkflowMetricsImage2012  
> **itemType**:: journalArticle  
> **Journal**:: *Journal of Biomolecular Screening*  
> **Volume**:: 17  
> **Issue**:: 2   
> **Pages**:: 266-274  
> **DOI**:: 10.1177/1087057111420292    

> [!LINK] 
>
>  [Bray et al. - 2012 - Workflow and metrics for image quality control in large-scale high-content screens.pdf](file:///Users/romankoval/Library/Mobile%20Documents/com~apple~CloudDocs/Library%20of%20Alexandria/ZotMove_files/Bray%20et%20al.%20-%202012%20-%20Workflow%20and%20metrics%20for%20image%20quality%20control%20in%20large-scale%20high-content%20screens.pdf).

> [!Abstract]
>
> Automated microscopes have enabled the unprecedented collection of images at a rate that precludes visual inspection. Automated image analysis is required to identify interesting samples and extract quantitative information for high-content screening (HCS). However, researchers are impeded by the lack of metrics and software tools to identify image-based aberrations that pollute data, limiting experiment quality. The authors have developed and validated approaches to identify those image acquisition artifacts that prevent optimal extraction of knowledge from high-content microscopy experiments. They have implemented these as a versatile, open-source toolbox of algorithms and metrics readily usable by biologists to improve data quality in a wide variety of biological experiments.
>.
>
### Table of context

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/B3F63L3T?page=267&annotation=MLPFBEK5))
> QC metrics for out-of-focus images 

> [!quote]+ Highlight ([Page 3](zotero://open-pdf/library/items/B3F63L3T?page=268&annotation=DVKZFNZH))
> QC metrics for saturation artifacts 
### Ideas, thoughts, useful information

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/B3F63L3T?page=267&annotation=BM4T8AXV))
> Common artifacts that confound image analysis algorithms include out-of-focus images, debris, image overexposure, fluorophore saturation, and uneven field illumination, among others. 

[[quality control for high content image analysis]]

> [!quote]+ Highlight ([Page 3](zotero://open-pdf/library/items/B3F63L3T?page=268&annotation=62YQUISB))
> The power log-log slope (PLLS) evaluates the slope of the power spectrum density of the pixel intensities on a log-log scale.8 The PLLS is relatively insensitive to C and decreases as F increases because high-frequency image components are lost as an image is blurred 
  **The best way to qc out-of-focus images**

[[power log-log slope]]

> [!quote]+ Highlight ([Page 6](zotero://open-pdf/library/items/B3F63L3T?page=271&annotation=Z97BDCVK))
> Our analysis indicates that PM detects saturation artifacts more robustly than the other candidate metrics 
  The Percent Maximal (PM) metric was most robust and reliable. PM = Nmax/NtotalX100%
Nmax​ = number of pixels with intensity equal to the maximum (e.g., 255 for 8-bit images) NtotalN_\text{total}Ntotal​ = total number of pixels in the image If PM is high, the image likely contains saturation artifacts.
In practice: PM < 0.01 % → good PM > 0.5 % → likely saturated

[[percent maximal]]