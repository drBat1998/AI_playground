# Abstract

Quantitative PCR (qPCR) remains a cornerstone method for the analysis of gene expression in models of ischemia and oxygen–glucose deprivation (OGD). It enables time-resolved detection of immediate-early genes and regulated cell death markers, providing mechanistic insights into neuronal stress responses. Despite the development of RNA sequencing technologies, qPCR continues to be widely used because of its sensitivity, cost-effectiveness, and rapid turnaround. However, RNA isolation from brain-derived material presents challenges due to low tissue yield, high lipid and protein content, and susceptibility to degradation. These difficulties are amplified in primary neuronal cultures, where cell numbers are limited compared with immortalized lines. Here we describe and benchmark optimized workflows for RNA extraction and qPCR in hippocampal neuronal cultures subjected to OGD. The optimized phase-separation protocol improves RNA purity without compromising yield, while the GeneJET column kit ensures highly pure RNA suitable for low-input applications. Together, these methods establish a reproducible pipeline for accurate gene expression analysis in ischemia research.

# Introduction

Oxygen–glucose deprivation (OGD) is a widely accepted in vitro model of ischemia that triggers stage-dependent transcriptional programs across neurons and glia. These programs regulate stress responses, metabolic adaptation, inflammation, and multiple forms of regulated cell death. Characterizing transcriptional changes in OGD is therefore essential for understanding the mechanisms of neuronal injury and identifying targets for neuroprotection.

While RNA sequencing provides a broad overview of transcriptional landscapes, qPCR remains the workhorse for most OGD studies. Its advantages include high sensitivity, low cost, rapid data acquisition, and the ability to focus on a defined set of target genes. In addition, qPCR supports time-resolved profiling across minutes to hours, which is critical for dissecting early transcriptional events.

Despite its advantages, qPCR in brain-derived material poses challenges. Brain tissue is characterized by high lipid and myelin content that interferes with RNA isolation, while neuronal cultures provide limited cell numbers compared with immortalized lines. Contamination with proteins, phenol, or salts during extraction can severely impair reverse transcription and PCR. Addressing these issues requires optimized workflows that balance yield, purity, and reproducibility.

In this study, we describe protocols for RNA isolation and qPCR tailored to primary hippocampal neurons subjected to OGD. We compare three approaches: the manufacturer’s standard TRIzol method, an optimized low-input TRIzol modification, and the GeneJET column kit. We evaluate RNA purity and yield, followed by downstream qPCR performance using the housekeeping gene β-actin (BACT) and the apoptosis marker caspase-3 (CASP3).

# Methods
## 1. Cell and Tissue Preparation

Primary hippocampal neurons were prepared from one-day-old Wistar rat pups following a published protocol (reference) with minor modifications. Hippocampal suspensions were plated at densities of 5,000 or 25,000 cells per well in poly-L-lysine–coated 96- and 24-well plates, respectively. Cultures were maintained in Neurobasal medium (pH 7.4) supplemented with 20 mM HEPES, 100 U/mL penicillin/streptomycin, 0.4% bovine serum albumin, and B27 supplement at 37 °C in a humidified 5% CO₂ incubator. Half of the medium was replaced every two days. Experiments were performed on cultures at 11–12 days in vitro (DIV).

OGD was induced as previously described (reference). Briefly, cultures were washed three times and transferred into glucose- and serum-free artificial cerebrospinal fluid (ACSF) containing 124 mM NaCl, 1.6 mM KCl, 24 mM NaHCO₃, 1.2 mM KH₂PO₄, 2 mM ascorbic acid, 2.5 mM CaCl₂, 1.5 mM MgCl₂, and 10 mM sucrose instead of glucose (pH 7.4). The plates were placed in a hypoxia chamber equilibrated with 95% N₂ and 5% CO₂. After 40 min of OGD, cultures were washed once with Neurobasal medium and returned to normoxic conditions for 4 h.

The experimental design included control and OGD groups at both 25,000 and 4,000 cells per sample. Due to insufficient RNA recovery, the 4,000-cell groups were excluded from further analysis. Each remaining condition was performed with n = 3 biological replicates.

## 2. RNA Extraction

RNA was isolated using either TRIzol™ Reagent (Invitrogen) or the GeneJET™ RNA Purification Kit (Thermo Scientific). Three approaches were compared:

Standard TRIzol protocol: 1 mL TRIzol per 10⁵–10⁷ cells, 0.2 mL chloroform, centrifugation at 12,000 × g for 15 min at 4 °C, precipitation with isopropanol, ethanol wash, and resuspension in 20–50 μL RNase-free water.

GeneJET column kit: Lysis in 600 μL buffer with dithiothreitol (DTT), ethanol precipitation, column binding, sequential washes, and elution in 50 μL nuclease-free water.

Optimized TRIzol protocol: Adapted for ~2.5 × 10⁴ cells. Pellets were lysed in 300 μL TRIzol, mixed with 100 μL chloroform, centrifuged, and the aqueous phase was recovered leaving ~1 mm above the interphase. RNA was precipitated with 250 μL isopropanol, centrifuged, washed three times with 500 μL 75% ethanol, air-dried, and resuspended in 30 μL RNase-free water.

## 3. RNA Quality Control

RNA concentration and purity were assessed spectrophotometrically (NanoDrop). A260/280 and A260/230 ratios were recorded. Aliquots were stored at –20 °C until further use.

## 4. Reverse Transcription

RNA was reverse-transcribed using the High-Capacity cDNA Reverse Transcription Kit (Applied Biosystems). Each 20 μL reaction contained 2.0 μL 10× RT Buffer, 0.8 μL dNTP Mix (100 mM), 2.0 μL Random Primers, 1.0 μL MultiScribe™ Reverse Transcriptase, 4.2 μL nuclease-free water, and 10 μL RNA template. Thermal cycling was programmed as follows: 25 °C for 10 min, 37 °C for 120 min, 85 °C for 5 min.

## 5. Quantitative PCR

qPCR was carried out in 10 μL reactions using Luna® Universal qPCR Master Mix (New England Biolabs). Each reaction contained 5 μL 2× Master Mix, 0.25 μL forward primer (10 μM), 0.25 μL reverse primer (10 μM), ≤50 ng cDNA template, and nuclease-free water to 10 μL. Reactions were performed in duplicate.
Thermal cycling (QuantStudio®, Applied Biosystems): 95 °C for 60 s; 40–45 cycles of 95 °C for 15 s and 60 °C for 30 s with plate read. Melt curve analysis (60–95 °C) was performed to confirm specificity. SYBR® detection settings were used.

# Results
## RNA Yield and Purity

RNA purity and concentration are summarized in Table X. The GeneJET method yielded RNA of high purity with A260/280 ratios of 1.90–2.08 and A260/230 ratios of 1.89–2.10. Concentrations were moderate (25.8–45.9 ng/μL).
The standard TRIzol protocol produced the highest concentrations (81.2–87.8 ng/μL) but very poor purity, with A260/280 ratios of 1.25–1.45 and A260/230 ratios below 0.7, indicating contamination.
The optimized TRIzol method provided intermediate yields (30.5–84.9 ng/μL) and markedly improved purity, with A260/280 ratios of 1.66–1.96 and A260/230 ratios of 1.91–2.21. This confirms that the triple ethanol wash step reduced phenol and salt contamination.

## qPCR Performance

qPCR amplification of β-actin (BACT) and caspase-3 (CASP3) revealed strong dependence on RNA extraction method.

GeneJET: BACT detected at 28.1 ± 0.1 (control) and 30.7 ± 0.1 (OGD). CASP3 detected at 31.9 ± 0.3 (control) and 31.1 ± 0.1 (OGD). Reproducibility was excellent (SD < 0.3 cycles).

Standard TRIzol: Cq values were elevated (>35 for BACT, >34 for CASP3) with high variability (SD up to 2.5 cycles), indicating PCR inhibition.

Optimized TRIzol: BACT detected at ~32.5 with reduced variability (SD 0.2–0.7). CASP3 detected at 33.1 (control) and 30.7 (OGD) with SD <1.2, approaching GeneJET performance.

# Conclusion

The comparison of RNA isolation methods highlights a critical balance between yield and purity in neuronal OGD models. Standard TRIzol extraction generated the highest RNA concentrations, but contamination with phenol and proteins severely compromised downstream qPCR, resulting in elevated Cq values and poor reproducibility. The GeneJET column kit provided RNA of excellent purity and supported reproducible amplification of both housekeeping and apoptosis-related genes, though yields were comparatively modest.

Importantly, the optimized TRIzol method bridged these limitations. By incorporating additional ethanol washes, it reduced contaminants and improved A260/230 ratios while maintaining reasonable yields. This translated into improved qPCR performance, with Cq values and variability closer to those obtained using GeneJET.

These findings demonstrate that while column-based methods are preferable for highest reproducibility, optimized TRIzol extraction offers a practical compromise for experiments constrained by sample size. For neuronal OGD studies, where cell numbers are often limited and contamination risk is high, the optimized workflow provides a reliable foundation for accurate qPCR analysis of genes involved in stress and cell death pathways.



###
Вписати в нормальний формат який буде 
Зробити українською
Декілька варіантів назви
Нейродегенер

Запитати Чернінського про обʼєм та параметри статті, якщо відома дату
Статистика!