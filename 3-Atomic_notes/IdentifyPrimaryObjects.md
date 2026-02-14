Title: IdentifyPrimaryObjects
tags: #atomic_note


# Notes
IdentifyPrimaryObjects identifies biological objects of interest. It requires grayscale images containing bright objects on a dark background.

Typical diameter of objects, in pixel units (min and max)
- You can measure diameters by opening the image and use the "measure length"
- typical diameter of objects use for discard objects outside the diameter range.

Typical diameter (in pixels):
	10×, 0.65–1.3 µm/px: 8–40 px
	20×, 0.32–0.65 µm/px: 12–60 px
	40×, 0.16–0.33 µm/px: 24–120 px
	Quick math: pixels = microns / (µm per pixel). If nucleus ≈ 10 µm and px size = 0.5 µm, diameter ≈ 20 px.

Threshold strategy determines the type of input is used to calculate the threshold. 
1. Global → fast, clean, relies on good illumination correction.
2. Adaptive → slower, safer when background drifts, but still benefits from prior correction.

Thresholding metod:
may be calculate authomatically by several method or by enter a number mannyally.

What is FlagImage module
- It doesn’t segment or measure anything — it simply marks images that look suspicious according to rules you define.
- Too few or too many objects (e.g., focus failure or debris).
- Low mean intensity (e.g., light source drop).
- High saturation (e.g., overexposure).
- Uneven illumination (via std/mean ratio).
- Outliers in any measured feature (e.g., object count per image deviating >3 SD from plate mean).

Thersholds automatically:
Minimum Cross-Entropy
- Finds the threshold that minimizes the difference (cross-entropy) between the original image and the binary version.
- Images with smooth intensity transitions; often works better than Otsu on dim or noisy data.
Otsu 
- Splits the intensity histogram into two (or three) classes so that the variance within each class is minimal.
- Most fluorescent images after illumination correction.
Robust Background
- Estimates background intensity using a robust statistic (mode or median) and sets the threshold based on deviation above background.
- Datasets with clear separation between bright spots and low, stable background.
Meausurement
- Uses a numeric threshold previously calculated and stored from another module (e.g., from a control image).
- For standardizing across plates; useful when you want consistent thresholds across wells.
Manual
- if your image is rescaled 0–1).
- For debugging or enforcing consistency.

Threshold smoothing scale
- This controls how much CellProfiler blurs the image before finding the threshold.
- it applies a Gaussian blur with the radius (in pixels) that you set.
- Higher numbers = smoother threshold map = fewer false edges.
- Lower numbers = more detail but also more noise.

How to choose
	Use your object size as the anchor:
	For nuclei 15–30 px across → smoothing 1–3 px.
	For large, soft-edged objects (cytoplasm, cells) → 3–8 px.
	If outlines look jagged or noisy, increase by 1 px and test again.
	If outlines swell and lose small details, reduce it.

Threshold correction factor
Too low → halos, merged cells, background fog.
Too high → missing faint apoptotic nuclei.

Think of it like this:
- Smoothing scale = “how myopic is the algorithm”
- Correction factor = “how paranoid is it about background.”

Lower and upper
Log transformation before thresholding -> use with minimum entropy and Otsu, helps with the detection of not uniformly stained cells. 

Method to distinguish clumped objects

| Option        | When to use                                                        | What it relies on                      | Good for                                                       |
| ------------- | ------------------------------------------------------------------ | -------------------------------------- | -------------------------------------------------------------- |
| **Intensity** | Interior is brighter than edges                                    | Peaks of fluorescence inside each cell | Live-cell dyes, cytoplasm uneven but noticeable bright centers |
| **Shape**     | Clear indentations between cells even if brightness inside is flat | Object geometry                        | Round nuclei, bright membranes, segmentation cores             |
| **None**      | Everything is already nicely separate                              | Nothing fancy                          | Single cells that actually behave for once                     |

Method to drawdividing lines between clumped objects
intensity
shape
propagation
none

Smoothing Filter Size
Think of it as blurring the image a bit before detecting nuclei peaks.
• Too few objects detected? → lower smoothing
• Too many objects detected? → raise smoothing

Minimum Distance Between Maxima
Basically: How close can two nuclei be before the software calls them one nucleus?
• Nuclei touching like star-crossed lovers? → decrease distance
• Image looks like nuclear mitosis party? → increase distance

Minimum distance between local maxima
How close two nuclei can be before they are merged.
• Too many merged → lower the value
• Too many splits → increase the value
Rule of thumb:
Set it about equal to the smallest nucleus radius in pixels.
That’s it. The manual turned that into a novel.

Lower-resolution trick
CellProfiler trying to save your CPU from a meltdown.
✔ Use if identifying maxima takes forever
✘ Doesn’t help if nuclei smaller than ~10 px
It’s just subsampling, not magic.

Fill holes in objects
Do your nuclei ever look like donuts?
Three choices:
• After both threshold & declump → usually correct for nuclei
• After declumping only → preserves intensity shape a bit more
• Never → leave nuclear donuts untouched, very metal
For DNA stains: After both is the standard.
Biologists don’t enjoy counting hollow nuclei.
# Links