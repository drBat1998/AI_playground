Title: IdentifySecondaryObjects
tags: #atomic_note


# Notes
What a “secondary object” is
In CellProfiler-speak:
1. Primary object = something well-defined and compact (nuclei, usually from AO-green or Hoechst).
2. Secondary object = something around that, like the whole cell body, cytoplasm, or membrane region, grown outward from each nucleus.

How it works
It does two things:
1. Finds the border between neighbouring cells (so one cell per nucleus).
2. Separates those cells from the background (via thresholding of the cytoplasmic or membrane channel).

Inputs you need
Primary objects = your nuclei from IdentifyPrimaryObjects (the AO-green channel).
Optional secondary image = a cytoplasmic or cell-body channel.
For AO, the red/orange emission sometimes helps outline cytoplasm, but it’s weak.
If you don’t have a clean cytoplasmic signal, skip it and use the “Expand N pixels” option.

Measurements made by IdentifySecondaryObjects
Image-level measurements
These describe the whole image, not individual cells.
Count
How many secondary objects (cells) were identified in this image.
→ useful for cell density or viability metrics.
OriginalThreshold
The initial global threshold value computed from the image’s intensity histogram.
→ relevant only if you’re curious how CellProfiler decided the cutoff.
FinalThreshold
For global methods, this equals OriginalThreshold.
For adaptive methods, it’s the average of all local thresholds used across the image.
→ you can use this to compare brightness shifts across wells or treatments.
WeightedVariance
A single number capturing how distinct foreground and background intensities were (basically, segmentation confidence).
→ higher = clearer separation between cells and background; low = muddy images.
SumOfEntropies
The sum of foreground/background entropy values — another indicator of how cleanly the algorithm divided the image.
→ you rarely need it, but it’s a QC metric if you’re debugging thresholding performance.
Object-level measurements
These are stored per object (cell) and link each secondary object back to its nucleus.
Parent
The ID of the corresponding primary object (nucleus) that this cell was grown from.
→ crucial for calculating per-cell features like “cytoplasm = cell – nucleus” or linking nuclear and cytoplasmic intensities.
Location_X / Location_Y
The (x, y) coordinates of the cell’s centroid in pixel units.
→ lets you map cell positions, make spatial plots, or trace them back to overlays.

## Methods to identify secondary objects
#### 1. Propagation (recommended)
What it does:
	Uses the nuclei (primary objects) as seeds, then spreads outward through the secondary image (cytoplasm or membrane stain) until it finds edges based on intensity changes.
	Boundaries are placed where local similarity to neighbours drops — basically, where brightness or texture shifts.
Why it’s good:
	Smooth boundaries, tolerates small gaps, and respects real intensity gradients (unlike the old-school Watershed).
	It’s the default for a reason — it handles typical fluorescent cytoplasm well.
Key parameter:
Regularization factor (λ) controls how much it trusts distance vs intensity:
	λ = 0.0 → boundaries follow intensity perfectly (great if cytoplasm is clean).
	λ = 1.0 → boundaries depend entirely on distance (basically uniform cell expansion).
Start around 0.2–0.4 for mixed AO staining.
#### 2. Watershed – Gradient
Works on an intensity gradient map (from Sobel filter).
Best when boundaries show sharp intensity drops — e.g. strong membrane staining.
Very sensitive to noise; produces ragged borders on weak stains.
→ Skip this unless you have clean membrane labels (like CellMask or phalloidin).
#### 3. Watershed – Image
Uses the inverted intensity image directly.
Assigns pixels to nuclei until hitting low-intensity “valleys.”
Works for smooth gradients between cells but merges easily when the signal is flat.
→ Also skip for AO. AO’s cytoplasmic gradient is too messy.
#### 4. Distance
When you have no proper cytoplasmic stain — just nuclei — you can define cells by distance only.
Two flavours:
Distance – N: simply expand each nucleus by a fixed number of pixels (say, 10–15 px).
→ Quick and dirty way to estimate cytoplasm size.
Distance – B: same as above, but stops the expansion when reaching a thresholded background region.
→ Slightly smarter; prevents cell masks from growing into empty space.


# Links
[[CellProfiler]]