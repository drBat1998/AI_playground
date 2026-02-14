Title: Bioimage analysis basics
Author: [[ibiology.org]]
Tags: #youtube #bioimage_analysis


# Notes
### Bioimage Analysis 1: The Basics: Getting Started
- single-cell resolution
- multiplexed
- quantitative

Pre-processing
Segmentation
Tracking 
Measurement and phenotype classification
Best practice

[[ image.sc]]
 [[Neubias]]

Controls are crusial.
### Bioimage Analysis 2: Pre-Processing (Kevin Eliceiri)
Crop
Invert
Filtering 
- Median
- Gaussian
- Kuwahara
Color extraction
3D datasets
- Z- projections
- 3D rendering

[[Illumination correction]] - as I understand improve image quality
[[Increase Signal-to-Noise ration]] - usefull for segmentation

Deconvolution
### Bioimage Analysis 3: Segmentation (Anne Carpenter)

Segmentation is a process of dividing the cell in the region of iterest.

Threshoding 
- histogram where first values come from dark part of image, and the large values from bright.
- how to chose correct value for the separation?
Seed-Based Whatershedding
- smothing is requere for see-based whatershedding
- landscape -> mountpeaks 
Untangling

Supervised ML
- you supervise ML to do something
- [[ilastik]]
Deep learning

Manipulating Found Objects
- Expand, dilate
- Shrink (erode)
- Skeletonize
- Substract 
- Merge
### Bioimage Analysis 4: Tracking (Kevin Eliceiri)
Segmentation
Linking
Measuer

### Bioimage Analysis 5: Measurement and Phenotype Classification (Anne Carpenter)
Counts
Size
Shaper
Intensity
- Min
- Max
- Mean
- Integrated intensity
Radial distribution of intensity
Colocalization
Texture, smoothness
- sd of intensities
- haralick
- gabor
- granularity

Spatial relationships

ML Cautions
1. Avoid overfitting 
	1. Annotations for training
	2. test accuracy on completly held out samples
	3. Check what features are being by the trained classify
### Bioimage Analysis 6: Tips and Best Practices (Anne Carpenter and Kevin Eliceiri)
1. Keep raw data
2. Document your workflows
3. Safely store your data
	1. Open microscopy environment
	2. image data resource
	3. cell image library https://www.cellimagelibrary.org/home
	4. tigshare


# Links
1: https://youtu.be/1xo4vi6Ub4I?si=fqsYhovlEUY0T8uB
2: https://youtu.be/MIDK8BqJY_8?si=Hh3QPQzUpP6cZ2lL
3: https://youtu.be/jLd2I2adQtw?si=arEhzBrXdAuoNWLv
4: https://youtu.be/bLd4JXhjlqU?si=EJe8NV6Pdd4I02vI
5: https://youtu.be/Odi9pIerT7I?si=iRB0JsuB8UWA1QEM
6: https://youtu.be/lfU4DUIQovs?si=01ai0mIxsbsdLfLv