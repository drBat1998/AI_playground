---
tags: 
title: "Data-analysis strategies for image-based cell profiling"
authors: "Juan C. Caicedo, Sam Cooper, Florian Heigwer, Scott Warchal, Peng Qiu, Csaba Molnar, Aliaksei S. Vasilevich, Joseph D. Barry, Harmanjit Singh Bansal, Oren Kraus, Mathias Wawer, Lassi Paavolainen, Markus D. Herrmann, Mohammad Rohban, Jane Hung, Holger Hennig, John Concannon, Ian Smith, Paul A. Clemons, Shantanu Singh, Paul Rees, Peter Horvath, Roger G. Linington, Anne E. Carpenter"
---

> [!Cite] 1.

Caicedo, J. C. _et al._ Data-analysis strategies for image-based cell profiling. _Nat Methods_ **14**, 849–863 (2017).

>[!md] QAC

>[!md]
> **FirstAuthor**:: Caicedo, Juan C.  
> **Author**:: Cooper, Sam  
> **Author**:: Heigwer, Florian  
> **Author**:: Warchal, Scott  
> **Author**:: Qiu, Peng  
> **Author**:: Molnar, Csaba  
> **Author**:: Vasilevich, Aliaksei S.  
> **Author**:: Barry, Joseph D.  
> **Author**:: Bansal, Harmanjit Singh  
> **Author**:: Kraus, Oren  
> **Author**:: Wawer, Mathias  
> **Author**:: Paavolainen, Lassi  
> **Author**:: Herrmann, Markus D.  
> **Author**:: Rohban, Mohammad  
> **Author**:: Hung, Jane  
> **Author**:: Hennig, Holger  
> **Author**:: Concannon, John  
> **Author**:: Smith, Ian  
> **Author**:: Clemons, Paul A.  
> **Author**:: Singh, Shantanu  
> **Author**:: Rees, Paul  
> **Author**:: Horvath, Peter  
> **Author**:: Linington, Roger G.  
> **Author**:: Carpenter, Anne E.  
~    
> **Title**:: Data-analysis strategies for image-based cell profiling  
> **Year**:: 2017   
> **Citekey**:: caicedoDataanalysisStrategiesImagebased2017  
> **itemType**:: journalArticle  
> **Journal**:: *Nature Methods*  
> **Volume**:: 14  
> **Issue**:: 9   
> **Pages**:: 849-863  
> **DOI**:: 10.1038/nmeth.4397    

> [!LINK] 
>
>  [Caicedo et al. - 2017 - Data-analysis strategies for image-based cell profiling.pdf](file:///Users/romankoval/Library/Mobile%20Documents/com~apple~CloudDocs/Lib/ZotMove_files/Caicedo%20et%20al.%20-%202017%20-%20Data-analysis%20strategies%20for%20image-based%20cell%20profiling.pdf).

> [!Abstract]
>
> This Review covers the steps required to create high-quality image-based profiles from high-throughput microscopy images.
>.
>
### Ideas, thoughts, useful information

> [!quote]+ Note ([Page 2](zotero://open-pdf/library/items/IBIZEFBY?page=850&annotation=KRELKUPI))
  **Cell profiling different from high throughput screening. The usual high throuput screening concentrate upon ditermine phenotypes, while cell profiling use all available morphological information.**

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/IBIZEFBY?page=850&annotation=PGNLX5RG))
> step 1: image analysis 

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/IBIZEFBY?page=850&annotation=922ZKYBR))
> Field-of-view illumination correction 
  **Every image acquired by a microscope exhibits inhomogeneous illumination**

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/IBIZEFBY?page=850&annotation=PG8657G4))
> Illumination correction is an important step for high-throughput quantitative profiling; the strategy of choice in most of our laboratories is a retrospective multi-image correction function. This procedure produces more robust results, particularly when separate functions are calculated for each batch of images (often with a different function for each plate and always with a different function for different imaging sessions or instruments). We recommend use of prospective and single-image methods for only qualitative experiments. 
  **Retrospective multi-image methods build the corection function by using the images acquired in the experiment.**

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/IBIZEFBY?page=850&annotation=NNP4WND2))
> Segmentation 

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/IBIZEFBY?page=850&annotation=3FKASW6K))
> Model based. 
  **Cellprofiler**

> [!quote]+ Highlight ([Page 3](zotero://open-pdf/library/items/IBIZEFBY?page=851&annotation=J99RWG3Q))
> Machine learning. 
  **Cellpose**

> [!quote]+ Highlight ([Page 3](zotero://open-pdf/library/items/IBIZEFBY?page=851&annotation=4SZZP97X))
> Feature extraction 
  **Feature extraction is the procese of measurement of mmultiple phtnotypic characteristics.**

> [!quote]+ Note ([Page 3](zotero://open-pdf/library/items/IBIZEFBY?page=851&annotation=WNEM5M7J))
  **Feature extraction include shape features, intensity-based features, texture features(?), microenvironmental and context features**

> [!quote]+ Highlight ([Page 3](zotero://open-pdf/library/items/IBIZEFBY?page=851&annotation=ZTD8NCD4))
> step 2: image quality control 
  **It is impssible to manually verify image quality in high throuput imaging.**

> [!quote]+ Highlight ([Page 3](zotero://open-pdf/library/items/IBIZEFBY?page=851&annotation=2NMUBNHP))
> Field-of-view quality control. 
  **Field-of-view quality control including blurring (poor autofocusing) and saturated pixel(debris)**

> [!quote]+ Highlight ([Page 3](zotero://open-pdf/library/items/IBIZEFBY?page=851&annotation=79MU54JR))
> Metrics can be computed to detect blurring, including the ratio of the mean and the s.d. of each image’s pixel intensities, the normalized measure of the intensity variance37, and the image correlation across subregions of the image38. The log–log slope of the power spectrum of pixel intensities is another effective option, because the high-frequency components of an image are lost as it becomes more blurred39; this procedure has been found to be the most effective in a recent comparison for highthroughput microscopy40. For detecting saturation artifacts, the percentage of saturated pixels has been found to be the best among all tested metrics. 
### Important papers that I have to read

> [!quote]+ Highlight ([Page 2](zotero://open-pdf/library/items/IBIZEFBY?page=850&annotation=KXWJW7IA))
> We do not cover the upstream steps (sample preparation and image-acquisition recommendations)1,2 or computational practicalities such as the necessary informationtechnology infrastructure to store and process images or data. 

> [!quote]+ Highlight ([Page 12](zotero://open-pdf/library/items/IBIZEFBY?page=860&annotation=BTUA5KU9))
> 1. Boutros, M., Heigwer, F. & Laufer, C. Microscopy-based high-content screening. Cell 163, 1314–1325 (2015). 

> [!quote]+ Highlight ([Page 12](zotero://open-pdf/library/items/IBIZEFBY?page=860&annotation=NIMGGJFE))
> 2. Mattiazzi Usaj, M. et al. High-content screening for quantitative cell biology. Trends Cell Biol. 26, 598–611 (2016). 