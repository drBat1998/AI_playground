Title: Fundamentals of Fluorescence Microscopy - Lecture 3 2025
Author: [[Biological Optical Microscopy Platform]]
Tags: #youtube #microscopy


# Notes
Image analysis workflow
1. Planning
2. Acquisition
3. Pre-processing
4. Object detection
5. Measurement and data analysis
6. Reporting

Planning
1. Run a pilot to optimise the experiment

Acquisition
- appropriate resolution
	- appropriate objective lens
- sampling rate
	- Nyquist sampling rate -> sampling at a rate that's at least twice the highest frequency present in that signal
	- In microscopy images, the pixel size should be at least 2.3 times smaller than the object you're trying to resolve.
	- Also, oversampled gives a bit better quality image, it also provides larger files and takes longer. 
- proper bit depth
	- For visualisation, 8-bit is good. 
	- For image analysis, 16-bit is much better. 
- dynamic range
	- The histogram should be in full range!
- saturation
	- Avoid saturation.

! The same setting should be used to compare two samples. In addition, a good practice is to record a raw microscopy format.

Pre-processing
	De-noising
		- Median filter
		- Gaussian filter
		- deep learning
	Background correction
		- flat field
		- bandpass filter
	Bleaching correction
	Alignment
	Deconvolution

Object detection
Measurement
- intencity
- shape

# Links
link:
https://youtu.be/71kJ_sheXF0?si=A2CwDMyzncFcjXea