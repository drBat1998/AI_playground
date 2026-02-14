---
tags: 
title: "Pipeline for illumination correction of images for high-throughput microscopy"
authors: "S. Singh, M.-A. Bray, T. R. Jones, A. E. Carpenter"
---

> [!Cite] 1.

Singh, S., Bray, M.-A., Jones, T. R. & Carpenter, A. E. Pipeline for illumination correction of images for high-throughput microscopy. _J Microsc_ **256**, 231–236 (2014).

>[!md] QAC

>[!md]
> **FirstAuthor**:: Singh, S.  
> **Author**:: Bray, M.-A.  
> **Author**:: Jones, T. R.  
> **Author**:: Carpenter, A. E.  
~    
> **Title**:: Pipeline for illumination correction of images for high-throughput microscopy  
> **Year**:: 2014   
> **Citekey**:: singhPipelineIlluminationCorrection2014  
> **itemType**:: journalArticle  
> **Journal**:: *Journal of Microscopy*  
> **Volume**:: 256  
> **Issue**:: 3   
> **Pages**:: 231-236  
> **DOI**:: 10.1111/jmi.12178    

> [!LINK] 
>
>  [Singh et al. - 2014 - Pipeline for illumination correction of images for high-throughput microscopy.pdf](file:///Users/romankoval/Library/Mobile%20Documents/com~apple~CloudDocs/Library%20of%20Alexandria/ZotMove_files/Singh%20et%20al.%20-%202014%20-%20Pipeline%20for%20illumination%20correction%20of%20images%20for%20high-throughput%20microscopy.pdf).

> [!Abstract]
>
> The presence of systematic noise in images in high-throughput microscopy experiments can significantly impact the accuracy of downstream results. Among the most common sources of systematic noise is non-homogeneous illumination across the image field. This often adds an unacceptable level of noise, obscures true quantitative differences and precludes biological experiments that rely on accurate fluorescence intensity measurements. In this paper, we seek to quantify the improvement in the quality of high-content screen readouts due to software-based illumination correction. We present a straightforward illumination correction pipeline that has been used by our group across many experiments. We test the pipeline on real-world high-throughput image sets and evaluate the performance of the pipeline at two levels: (a) Z'-factor to evaluate the effect of the image correction on a univariate readout, representative of a typical high-content screen, and (b) classification accuracy on phenotypic signatures derived from the images, representative of an experiment involving more complex data mining. We find that applying the proposed post-hoc correction method improves performance in both experiments, even when illumination correction has already been applied using software associated with the instrument. To facilitate the ready application and future development of illumination correction methods, we have made our complete test data sets as well as open-source image analysis pipelines publicly available. This software-based solution has the potential to improve outcomes for a wide-variety of image-based HTS experiments.
>.
>
### Ideas, thoughts, useful information

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/L7DD72UC?page=232&annotation=BMPNQ9IF))
> n practical use, when conditions are not so carefully controlled, differences can be more substantial; in our experience, illumination can routinely vary 10–30% across a single image when using standard microscope hardware, even when white-referencing has been applied (see below). 

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/L7DD72UC?page=232&annotation=PHWBJ4ZY))
> We have found that a straightforward approach to retrospective illumination correction (Jones et al., 2006) works well in practice for high-throughput microscopy experiments; here we validate its use. The approach is as follows. The ICF is calculated by averaging all images in an experimental batch (usually, all images for a particular channel from a particular multi-well plate), followed by smoothing using a median filter. Then, each image is corrected by dividing it by the ICF. For the results presented in this paper, we have used a median filter with window size = 500 pixels for the smoothing (Fig. 1). 

> [!quote]+ Highlight ([Page 3](zotero://open-pdf/library/items/L7DD72UC?page=233&annotation=2NFKNPUU))
> We find that viewing the functions themselves is good practice to identify quality control issues (Bray & Carpenter, 2013). For example, a sudden change in the pattern of ICFs for some plates may alert to a problem with microscope hardware, or a single unusual ICF from a plate may identify a single image with intense debris (Fig. S7). 
### Important papers that I have to read

> [!quote]+ Highlight ([Page 5](zotero://open-pdf/library/items/L7DD72UC?page=235&annotation=MBNR4DY8))
> Bray, M.-A., Fraser, A. N., Hasaka, T. P. & Carpenter, A. E. (2012) Workflow and metrics for image quality control in large-scale high-content screens. J. Biomol. Screening, 17(2), 266–274. 
### Questions, things that I didn't understand

> [!quote]+ Highlight ([Page 3](zotero://open-pdf/library/items/L7DD72UC?page=233&annotation=SKBUCIPF))
> For testing, we selected a high-throughput image set BBBC021v1 (Caie et al., 2010) from the Broad Bioimage Benchmark Collection (Ljosa et al., 2012) that is publicly available. Images in this set have already been corrected by white referencing using the image acquisition software (MetaMorph software; images acquired on ImageXpress 5000A microscope manufactured by Molecular Devices, Union City, CA, USA). We computed ICFs using images from each 96-well plate as the experimental batch (Fig. 1). We find that despite the previously applied white referencing correction, the intensity response across the field of view for these images still varies 10–30%, depending on the channel and the plate (Figs. S1 and S2 shows ICFs from all the plates in the experiment). 
  **How can I visualise intensity response across the field of view?**

[[ICF]]