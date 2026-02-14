---
tags: 
title: "Single-Cell and Population-Level Analyses Using Real-Time Kinetic Labeling Couples Proliferation and Cell Death Mechanisms"
authors: "Jesse D. Gelles, Jarvier N. Mohammed, Luis C. Santos, Diana Legarda, Adrian T. Ting, Jerry E. Chipuk"
---

> [!Cite] 1.

Gelles, J. D. _et al._ Single-Cell and Population-Level Analyses Using Real-Time Kinetic Labeling Couples Proliferation and Cell Death Mechanisms. _Dev Cell_ **51**, 277-291.e4 (2019).

>[!md] QAC

>[!md]
> **FirstAuthor**:: Gelles, Jesse D.  
> **Author**:: Mohammed, Jarvier N.  
> **Author**:: Santos, Luis C.  
> **Author**:: Legarda, Diana  
> **Author**:: Ting, Adrian T.  
> **Author**:: Chipuk, Jerry E.  
~    
> **Title**:: Single-Cell and Population-Level Analyses Using Real-Time Kinetic Labeling Couples Proliferation and Cell Death Mechanisms  
> **Year**:: 2019   
> **Citekey**:: gellesSingleCellPopulationLevelAnalyses2019  
> **itemType**:: journalArticle  
> **Journal**:: *Developmental Cell*  
> **Volume**:: 51  
> **Issue**:: 2   
> **Pages**:: 277-291.e4  
> **DOI**:: 10.1016/j.devcel.2019.08.016    

> [!LINK] 
>
>  [Gelles et al. - 2019 - Single-Cell and Population-Level Analyses Using Real-Time Kinetic Labeling Couples Proliferation and.pdf](file:///Users/romankoval/Library/Mobile%20Documents/com~apple~CloudDocs/Library%20of%20Alexandria/ZotMove_files/Gelles%20et%20al.%20-%202019%20-%20Single-Cell%20and%20Population-Level%20Analyses%20Using%20Real-Time%20Kinetic%20Labeling%20Couples%20Proliferation%20and.pdf).

> [!Abstract]
>
> Quantifying cytostatic and cytotoxic outcomes are integral components of characterizing perturbagens used as research tools and in drug discovery pipelines. Furthermore, data-rich acquisition, coupled with robust methods for analysis, is required to properly assess the function and impact of these perturbagens. Here, we present a detailed and versatile method for single-cell and population-level analyses using real-time kinetic labeling (SPARKL). SPARKL integrates high-content live-cell imaging with automated detection and analysis of fluorescent reporters of cell death. We outline several examples of zero-handling, non-disruptive protocols for detailing cell death mechanisms and proliferation profiles. Additionally, we suggest several methods for mathematically analyzing these data to best utilize the collected kinetic data. Compared to traditional methods of detection and analysis, SPARKL is more sensitive, accurate, and high throughput while substantially eliminating sample processing and providing richer data.
>.
>
### Ideas, thoughts, useful information

> [!quote]+ Highlight ([Page 3](zotero://open-pdf/library/items/49H7IVDX?page=279&annotation=CEEZYBUE))
> This technology eliminates the requirement for disruptive handling (e.g., trypsinization, pipet-induced shear  forces, centrifugation, and incubation in labeling buffers) and is non-invasive to cells in culture. The repeated observation of samples and coupled automated real-time analysis also collects richer datasets in a workflow that is less labor and time intensive than analogous workflows using flow cytometry 

> [!quote]+ Note ([Page 8](zotero://open-pdf/library/items/49H7IVDX?page=284&annotation=6RHVB37H))
  **<b>SPARKL</b> (single-cell and population-level analyses using real-time kinetic labeling) uses HTI for cell death kinetic

Using this approach they claim that AV occure early than cell membrane permebility in apoptosis, in the same time in ferroptosis, and latter in necroptosis.**

> [!quote]+ Note ([Page 11](zotero://open-pdf/library/items/49H7IVDX?page=287&annotation=ASK2LJX5))
  **Minimum viable set you should report every time: <b>Onset (t₀)</b> and <b>rate (Rᴅ)</b> from a lagged exponential fit (their “LOPE/LED”). Model: for t ≥ t₀, F(t) = D_max·(1 − e^{−Rᴅ·(t − t₀)}); else 0. <b>t₅₀</b> and <b>t₉₀</b> of positivity for each label (AV, Y3). <b>Δt sequence lags</b> per cell: Δt_AV→Y3 = t(Y3⁺) − t(AV⁺) Δt_Y3→AV = t(AV⁺) − t(Y3⁺)
Report distributions, not just means. <b>Pathway fractions</b>: % AV-first, % Y3-first, % simultaneous. That alone separates apoptosis vs necroptosis vs ferroptosis in most cases. <b>Event rate curves</b>: first derivative of F(t) for AV and Y3; record <b>max rate</b> and <b>time-to-max rate</b>. <b>AUC_norm</b> for quick comparisons across large screens. Normalize by starting nuclei count or confluence, not “whatever the y-axis was.” Nice-to-have if you’re being thorough: <b>AV−Y3 difference curve</b> over time (their Fig. 3A idea): highlights windows where mechanisms diverge. <b>Event histograms per hour</b> (their Fig. 3E): shows heterogeneity, shelves, multimodality. <b>Co-label dependency tests</b>: is double-positivity kinetics ≈ Y3 kinetics (i.e., permeability is the gate), or ≈ AV (PS exposure the gate)?**

> [!quote]+ Highlight ([Page 18](zotero://open-pdf/library/items/49H7IVDX?page=291.e2&annotation=TWC9P7C6))
> Data Acquisition  Kinetic experiments were performed with the IncuCyte ZOOM (Model 4459, Essen Bioscience, Ann Arbor, MI, USA) residing in a tissue culture incubator maintained as above, but other high-content live-cell fluorescent imagers are capable of replicating these data (e.g., IN CELL analyzer). Experiments were conducted for 24–96 hours with data collection every 1–2 hours to avoid photobleaching of fluorescent reporters. Using the 103 objective, a single plane of view was collected per well for 96-well plate assays. Phase contrast, green channel (Ex: 440/80 nm; Em: 504/44 nm; acquisition time: 400 ms), and red channel (Ex: 565/05 nm; Em: 625/ 05 nm; acquisition time: 800 ms) were collected for all experiments with spectral unmixing set as 3% of red removed from green (except for studies assessing dual-labeling kinetics, in which case spectral unmixing was set at 0%). Images collected were 1392 3 1040 pixels at 1.22 mm/pixel. A


Gelles et al. developed SPARKL (Single-cell and Population-level Analyses using Real-time Kinetic Labeling) to quantify cell-death kinetics using live-cell imaging with Annexin V and YOYO-3 dyes. The method distinguishes death types by labeling order: apoptosis shows Annexin V first, ferroptosis both simultaneously, and necroptosis late Annexin V labeling. To improve accuracy, they applied several quantitative metrics: onset (t₀); rate (Rᴅ); t₅₀ and t₉₀ (50 % and 90 % positivity); Δt (AV→Y3); Δt (Y3→AV); pathway fractions (% AV-first, % Y3-first, % simultaneous); event-rate curves; AUCₙₒᵣₘ (area under normalized curve); Annexin V − YOYO difference curve; event histograms per hour; and co-label dependency tests.

[[HTI and regulated necrosis]]