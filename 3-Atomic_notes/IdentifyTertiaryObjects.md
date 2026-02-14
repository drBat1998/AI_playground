Title: IdentifyTertiaryObjects
tags: #atomic_note


# Notes
A tertiary object is a region defined between two already-identified structures — for instance, the cytoplasm, which lies outside the nucleus (primary object) but inside the whole cell (secondary object).

Input: You need two sets of objects — a larger one (like cell boundaries) and a smaller one contained within it (like nuclei). The module subtracts the smaller from the larger.

Output: The result is a new set of objects (e.g., cytoplasmic regions) that can be measured in later modules.

Measurements produced:
• Count (number of tertiary objects)
• Parent identity (which nucleus/cell each tertiary region belongs to)
• Location (X,Y of the centroid of each region)
# Links
[[CellProfiler]]