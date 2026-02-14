Title: HTI and regulated necrosis
tags: #atomic_note #cell_death 


# Notes
I want to write an article about the state of using cell imaging approaches to detect specific cell death types, such as regulated necrosis. Apparently, it is quite an easy task to differentiate morphologically and use some fluorescence approaches between apoptosis and necrosis morphology. However, inside different types of regulated cell death that all manifest simmilar necrotic morphology it is quite challenging. 

High-throughput screening (HTS) has been instrumental in advancing our understanding of cell-death mechanisms. The use of small-molecule libraries in combination with high-content imaging has enabled the discovery of key modulators such as necrosulfonamide (an MLKL inhibitor that blocks necroptosis) and biomifilins (Biomifi), which act as inducers of extrinsic apoptosis. Studies like those by Bai et al. exemplify how systematic chemical screening can dissect complex death pathways at the molecular level, revealing specific regulatory nodes and providing valuable pharmacological tools for distinguishing between apoptosis, necroptosis, and other programmed cell-death processes. [^6]

The author clearly saw the problem that was quite significant in 2016, how to distinguished apoptosis and necroptosis, but with the development of high-content microscopy, the problem has shifted. The main question is how to distinguished different regulatory necrosis that has being discovered seens then. [^1]

Live cell imaging using a CASP3/7-sensitive probe can separate secondary necrosis from primary and regulated forms of necrosis. This is especially important due to the lack of phagocytosis in the context of general in vitro models. Overal real-time kinetic studies may be further beneficial specialy in cancer treatment and neurotoxicity research. [^11]

Maybe death is binary at the end, but the dying  is prolonged and complicated. Even when perturbations are uniformly lethal, cell-death kinetics are shaped by pathway choice, cell-intrinsic variability, and microenvironment. STACK (scalable time-lapse analysis of cell death kinetics) models lethal-fraction (LF) trajectories using a lag–exponential death form and extracts two parameters: D₀ (lag to death onset) and Dᴿ (maximal death rate). This compact summary captures tempo, not just extent, of killing. However, LF readouts based on membrane-impermeant dyes (SYTOX, PI, DRAQ7) mostly report necrosis or post-apoptotic secondary necrosis and cannot disambiguate which pathway killed a cell. Because cells within one line can die via different mechanisms, single-cell, pathway-resolved analysis is required to improve the kinetics model beyond a single curve.[^3]

Gelles et al. developed SPARKL (Single-cell and Population-level Analyses using Real-time Kinetic Labeling) to quantify cell-death kinetics using live-cell imaging with Annexin V and YOYO-3 dyes. The method distinguishes death types by labeling order: apoptosis shows Annexin V first, ferroptosis both simultaneously, and necroptosis late Annexin V labeling. To improve accuracy, they applied several quantitative metrics: onset (t₀); rate (Rᴅ); t₅₀ and t₉₀ (50 % and 90 % positivity); Δt (AV→Y3); Δt (Y3→AV); pathway fractions (% AV-first, % Y3-first, % simultaneous); event-rate curves; AUCₙₒᵣₘ (area under normalized curve); Annexin V − YOYO difference curve; event histograms per hour; and co-label dependency tests.[^5]

High-content imaging of cell death is also a powerful tool for assessing specific cytotoxicity. In this study, the authors engineered two prostate cancer–derived cell lines representing distinct states of the epithelial-to-mesenchymal transition (EMT) and used a high-throughput screening (HTS) platform to test how different treatments affected each subpopulation. By co-culturing fluorescently labeled epithelial (PC-3E-GFP) and EMT-like (TEM 4-18-mCherry) cells and tracking changes in their fluorescence over time, they could simultaneously measure drug sensitivity in both populations. This approach enabled the identification of compounds—such as salinomycin, monensin, and nigericin—that were selectively toxic to EMT-like cells, providing a framework for discovering treatments that target aggressive, therapy-resistant cancer phenotypes. Unfortunetely, in this study the HCI was used only to measure overall cell death, not to deistinguish amoung different death pathwya. To determine the specific cell deeath type, the authors followed up flow cytometry and treatmenr with pathway spcific inhibitors. 

Digital holographic microsopy with deep learning also may be a valuble addition to high content screening approch. However, this approach has identical problem to [^8]

Good information that MTT analogy show poor responce in cell death in oncological drug study.
[[@mikheevaImprovingPowerDrug2024]]


Single cell morphology based on cell painting assay sufficient to determine cell death with sufficient accuracy.
[[@freySinglecellMorphologicalProfiling2025]]

Upon interaction with caffeine, the synthetic, caffeine-responsive protein systems could be used for cell death study, by modifying key checkpoint mechanism. For example, the author successfully monitoring the necroptosis of HeLa cells transfected with MLKLNTmCherry–biCOSMO-S. [[@wangCaffeineOperatedSyntheticModules2021]]

## Pyroptosis 
Caspase 1 activity, crucial for pyroptosis, was for some time detected by commercial available bioluminescent, plate-based assay. [[@obrienBioluminescentCaspase1Activity2017]]


Tucey and colleagues used live-cell imaging to detect pyroptosis in macrophages. They employed mCerulean-tagged ASC inflammasome reporter macrophages together with DRAQ7-positive rupture scoring, allowing them to distinguish inflammasome activation from the execution phase of pyroptosis.[^2]

Glioblastoma multiforme cancer stem cells contribute to the highly infiltrative nature of the tumor, its resistance to drugs, and the promotion of tumor vascularization. The aim of the authors is use the high-throughput approach to identify a small molecule that induces selective cell death in GBM CSC cultures called RIPGBM. RIPGBM specifically transforms into cRIPGBM form inside GBM CSC and induces cell death through RIPK2 and CASP1. Although they use an interesting toolkit, they do not use any specific necrotic marker, which could help distinguish apoptosis, as they claimed, from pyroptosis. 
[[@luckiCellTypeselectiveApoptosisinducing2019]]


## Ferroptosis 

Ferroptosis is a regulated cell-death process marked by necrotic morphology and driven by iron-dependent lipid peroxidation. Although lipid peroxidation of cellular membranes is well established, the endoplasmic reticulum (ER)—the earliest and most vulnerable site of this oxidative damage—has been poorly explored. Li et al. (2025) developed ER-OH, a fluorescent probe that selectively targets the ER and emits far-red fluorescence upon reaction with hydroxyl radicals (·OH), one of the principal initiators of lipid peroxidation. Using ER-OH, they visualised hydroxyl radical bursts in the ER during ferroptosis and implemented a high-throughput imaging assay to screen natural compounds for anti-ferroptotic activity. The screen identified icariside I, a flavonoid derivative that suppressed ferroptosis by scavenging ·OH and lipid peroxides and restoring GPX4 levels. The ER-OH probe, therefore, provides both a sensitive tool for early ferroptosis monitoring and a platform for discovering ferroptosis inhibitors.[^4]

Evidence suggests that ferroptosis plays an important role in neuronal death during epilepsy. One of the key pathways associated with this is myeloperoxidase-mediated oxidative stress. Inhibition of this pathway shows promising therapeutic effects. In order to facilitate drug discovery, Chenwen and colleagues proposed a novel two-photon fluorescence probe, named HCP. Also, high-content screening and HCP provide great efficiency in finding antiepileptic agents with the ability to reduce MPO-generated oxidative stress. However, its use is limited by the fact that most high-content imaging systems lack two-photon excitation capability, restricting broader application in automated drug screening workflows.[^7]

VPCPP is a multifunctional probe enabling the detection of multiple environmental conditions (microviscosity, micropolarity, and carboxylesterase activity). In addition, the authors claimed to identify a specific ferroptosis phenotype: increased microviscosity and reduced carboxylesterase activity. However, no ferroptosis-specific tests were performed, and other regulated cell death pathways were not excluded. Therefore, while VPCPP is a valuable tool for high-throughput cellular imaging, its ability to specifically detect ferroptosis remains limited.[^9]

FerroOrange probe is another fluorescent assay that gives the ability to detect Fe²⁺ release during HCI.[^10]
# Links
[[high content imaging]]
[[regulated necrosis]]

[^1]: [[@feoktistovaTechniquesDistinguishApoptosis2016]]
[^2]: [[@tuceyEndoplasmicReticulumMitochondrionTether2016]]
[^3]: [[@forcinaSystematicQuantificationPopulation2017]]
[^4]: [[@liEndoplasmicReticulumtargetingHydroxyl2025]]
[^5]: [[@gellesSingleCellPopulationLevelAnalyses2019]]
[^6]: [[@baiDissectingProgrammedCell2020]]
[^7]: [[@shaoEpilepticBrainFluorescent2020]]
[^8]: [[@verduijnDeepLearningDigital2021]]
[^9]: [[@qiMultifunctionalFluorescentProbe2022]]
[^10]: [[@fromainPhotothermiaNanoscaleInduces2023]]

[^11]: [[@lekshmiRealTimeImageBasedApproach2018]]
