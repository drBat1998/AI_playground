Title: Pathway enrichment analysis - simple explanation!
Author: [[Biostatsquid]]
Tags: #youtube #bioinfo 


# Notes
[[Pathway enrichment analysis]]

[[Over-Representation Analysis methods]]

Essential components: 
1. List of genes of interest (usually diff expressed genes)
2. List of Background genes
3. List of gene sets

Fisher's exact test for pathway overrepresentation, usually with multiple test correction

Wildly use the database of gene ontology is
- gene ontology - https://geneontology.org/
- kegg
- reactome

Background genes must be representative, for example, NeuN for neuronal cell culture.

Maybe the best practice to use to filter
DEGs
	p-val < 0.05 and FC > 2
	p-val < 0.01 and FC > 2
# Links
https://youtu.be/H1cUs6pql9s?si=Lsi0TrXXPMD0T27M

