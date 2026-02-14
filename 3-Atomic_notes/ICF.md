Title: The Illumination Correction Function 
tags: #atomic_note #bioimage_analysis 


# Notes
The Illumination Correction Function (ICF) is an image-sized map that describes how light intensity varies across the microscope’s field of view (FOV).

Calculated by 
1. Collect many images
2. Take the pixel-wise median
3. Smooth with large filter 
4. Normalize so that the median intensity = 1
5. Result → an image of the same size as your FOV, where:
	1.0 ≈ average brightness,
	< 1 = dim region,
	1 = bright region.

# Links
[[@singhPipelineIlluminationCorrection2014]]