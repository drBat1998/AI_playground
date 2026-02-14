Title: The Live Cell Imaging Facility Microscopy course
Author: [[]]
Tags: #youtube #microscopy #bioimage_analysis 


# Notes
#### Anatomy of a microscope
Type of light microscope
1. Wide-field
2. Confocal

Anatomy: 
1. Light source 
2. Optical elements
	1. Lens
	2. Filters
	3. Dichrome mirrors
	4. Pinhole
	5. Samples etc.
3. Sensor

System = microscope + satellite equipment
Satellite equipment conected by:
1. Hard connection
2. Optical fibers 
3. Cables

Microscope without camera:
- single-point confocal
Microscope with a camera:
- all other
- no scanner: wide field
- scanner - multi-point confocals

Transmitted light microscopy 
- low contrast
- contrast can be enhanced using DIC or Phase
- phase-gradient-contrast in our case

Every pixel is represented by a square with x,y values plus uniform intensity.

A single-point confocal microscope detects only one pixel at a time, whereas a wide-field microscope with a camera detects millions of pixels at once. 

Pixel size in a confocal microscope is the length of the jump from one point to another. 
![[Screenshot 2025-10-02 at 13.47.04.png]]

Module 4: Working with objectives
Lecture: Objectives
- point spread function as an quality control.
How to choose an objective
1. Magnification and fieeld of view
	1. A number followed by x. 
	2. Field of view:
		1. Size of the sample area that fits in the image. 
		2. Depends on the objective magnification, the size of the sensor area and th microscope. 
2. Working distance
	1. [[Questions to Zeiss - working distance]]
	2. Dont clamp your sample!! - unclamped make less damage to the objective
3. Numerical aperture
	1. Na = n(sin u)
	2. n = refractivve index of the objective immersion medium
	3. sin u = half of the light acceptance angle
4. xy otical resolution
	1. Ressolution smallest resovable distance between 2 dots
	2. wide field 0.61em* delta / NA
	3. confocal 0.61em* delta / NA
	4. pinhole size and xy optical reolution are not related
	5. Closing the pinhole increases the contrast
5. Z optical resolution (depth of field)
	1. Z optical resolution
	2. 2 em* delta n / NA^2
6. Brightness
	1. NA^4/magnification^2
7. Immersion medium
8. Sensitivity to aberrations and correction collar
9. Coverslip thickness
10. Contrasting methods for transmitted
11. Aberation correction

Lecture: Point Spread Function and Resolution
[[point spread function]]
We can distinguish distances that are equal to 1 PSF diameter, but can not distinguish distances that are equal to 1 PSF radius. 
Resolution is the smallest distance between 2 points that can be reliably distinguished. 
Small distance -> higher resolution
All objects smaller than the PSF have the same size: the PSF!

diameter> radius - good
d=radius - worst
d < radius undistinctible. 

FWHM xy = 0.51 * lambda/NA
Rayleigh xy optical resolution = 0.61 * lambda/NA

WF = lambda for emission
Confocal = lambda for excitation.
![[Screenshot 2025-10-05 at 18.48.44.png]]

Refractive index mismatch and optical aberrations
Refractive index mismatch -> optical aberrations
if we did not match the refraction indexes the image would be distorchen. Speccially if you want a z stack.
Manual correction collars do not correct for aberrationd due to RI mismatch in the sample differ.
![[Screenshot 2025-10-06 at 13.12.25.png]]
So if aquesous medium has been used for imaging, wather immersion objective better. And if we use sample with mounting it leads to [[RI mismatch]]!
RI mismatch -> lower effective NA
glass 1.5

Efficient strategies to find the area of interest: large FOV, tiling and autofocus
1. Overview + re-imaging
	1. Overview - fast speed, large pinhole, undersampling
	2. List of interest possition
	3. Re-imaging - all colours, correct pixel size, low noise

Autofocus 
- problem with outofocus in the big sample
- sample is not flat
	Solution
	- cobine hardware and software autofocus
	- smaller field of view
	- adding a small z stack
Software autofocus
	best using low NA objectives
	bleaching
	time consuming
	doesn't work if several possible focus plane
Hardware autofocus
	may not work if we have RI mismatch
	only works if the focus of interest is at a fixed distance
	
Sample preparation tips
1. Planning phase
	1. Dluorophores
	2. sample carriers
	3. microsopes
	4. solution
	5. Coverslips
		1. #1.5, ideal thickness 170 (160-180)
	6. Multiwell chambers
		1. you need glass or thin polymer 1.5 (1.5H)
	7. Multiwell plates
		1. Glass bottom 1.5
		2. thin polymer 1.5, polymer may display autofluorescence
		3. ! polymer might react with oil immersion!
		4. low skirt is good, high skirt 
2. Execusion phase

Fixation cells
1. If you do not need to stop a treatment always warm up the fixative to 37C
2. Add it to culture medium 8-15 min at RT or 37 degree

Autofluorescence
1. Endogenous flurophores
2. mounting media
3. cell culture media
4. fixative induced autofluorescence
5. bottom of your carrier(green)

Bridging concepts optical and digital resolutions, contrast and sampling
1. not the most beutiful you could acquire
2. good enough image resolution to reliably answers the scientific question.
3. good contrast
4. pinhole improve contrast rather then resolution
5. sampling/digitalization/pixel size

Image resolution 
optical resolution = radii of the point spread function
- Rayleigh 
contrast


The image is a rought simplification of the optical image. 
object -> optical image-> digital image

pixel size in the image is a distance between sampling points in the speciem.
From myquist sampling criterion leads that pixel should be smaller than 1/2 then resolution
Some company have specific button for the "optimal"

camera has a fixed size pixel.
Camera pixels are different from image pixels. 

The image pixel siz = camera pixel size/ magnification

How to increast the image pixel size on a camer-based system: Binning 2x2 -> 4 camer pixles contributes to 1 large image pixel.

Example:
When using a 40x/1.25 NA and a camera with 6.5 um pixels.
1. The image pixle size = pixel size/ magnification 6.5um/40 = 163
2. XY optical resolution 0.61* lambda/1.25, for green fluorophore 0.61* 520nm/1.25 =254
3. The image pixel are larger than the 1/2 of the ptical resolution
	1. Undersampling
	2. The digital resolution is limiting 
	3. The image resolution is the size of 2 image pixels (326 nm) instead of 254 nm(optical resolution)

For 802 Zeiss 20/0.95
	the image pixel size = 4.5 μm/(20) = 225 
XY optical resolution
	0.61* 520nm/0.95 = 333
	(0.61 * 650 nanometers) / 0.95 = 417.3
For green fluorescence, you’re undersampling (pixel too big).
For red, you’re almost at Nyquist, so acceptable in many cases.

Undersampling -> Artifacts: 
- moire
- pixelization

Lecture Sensors
Camera and detectors.
- high digital resolution and high dynamic range
- efficient photon detection - speciffications of the camera or the sensor
- efficient electron amplification
-  low noise creation
- high speed

Quantum effciency is % of photons that trigger a signal, in case of my axiocam 807 mono is quantum efficiency of 78%, 60% in 700 nm wavelength.

Color camer has 4 time larger size than mono. 

Speed
- detectors exposure time per pixle = pixel-dwell time. 
- cameras - all pixles at once, in our case 73 full-resolution images per second. 1 colour at a time. Camera chosse the speed not other stuff.


Signal, background and noise 
Signal - intensity in the pixels of interest
backgroun is intenisty outside the pixles of interest. 
SRR - enothg for meaningful, reliable data.

How to increase the signal in images:
	fixed samples: push the illumination power, longer exposure time/slower scan speed, averaging, binning, larger pinhole. 
	live cells: required to be able to reliably analyze the images, minimum ligh exposure.
	no under exposure in the area of interest, alway test the whole pipeline from sample preparation all the way to image anlaysis.

Background from sample
1. culture medium
2. mounting medium

Stray light from the desktop
Sensor offset in confocal - if the offset is too low without nuances, picture may be regected by good journal.
if offset is too high -> can be fixed by background saturration. 


Camera based system:
cameras cannot deal with 0 values
to remove the camera offset and sample background from images acquired with a camera.

Cammera offset may be acquire by an image with no llumination light. It is essential to extract backgroun from camer images before extracting intensity information. -> [[Zeiss questions]]

Signal to noise ration
- 3 timelapse of 3 images without interval
- background and signal are constant. Noise is random. What change between images is noise. 
- Noise hide dim signals.

Sources of noise
- shot noise - from light
- dark noise - from amplification
- readout noise 

Dark noise:
- by electronics in detector
- usually negligible
- we can't influence it
Shot noise:
- can neve be eliminated
- The more signal, the less shot noise we have
- increase the number of detected photons
	- increase illumnination power
	- increase exposure time
	- match between the fluorophore and the filters, and so on.
Readout noise:
- lower amplification (gain for confocal) or readout rate
- slower max speed
- lowerreadout rate if available

Reducing noise with averaging

Saturation, underexposure, bit depth, and image display 
Saturation profile
- all red pixels have the maximum possible intensity
- If saturation is high, lower the exposure time, gain, and illumination power. 
- If under-exposed, it would lead to loss of important information at cell edges.

Where do saturation and underexposure come from?

Dynamic range of the sensor
Camera-based systems:
- high quantum efficiency
- exposure times in msec
Detector-based systems:
- low quantum efficiency
- pixel dwell time in usec

Bit depth in the image is the number of intensity steps between the dimmest and brightest possible intensities in the image.
Human eyes have a 7-bit range
With high bit depth, we have a lower risk for saturation and better results for segmenting crowded objects. 

Size 12 and 16-bit images are the same.

! When shall I check for saturation and under exposure?
- ALWAYS have the saturation LUT on when imaging.
- Look at images in B/W to avoid colour bias where green looks brighter.

Background may be corrected after the acquisition. 

!Britness, contrast and gamma adjustment must be reported in a paper.

Confocal
1. Scientific question - What meatrics do you want to easure?
2. Objective - working distance, field of view, immersion medium.
3. Flurophores
4. Imaging strategy
5. Display - b/w and saturation and under exposure LUT 
6. Zoom/scan area
7. Pixel density -> first Optimal -> do you need such small pixel?
8. Pinhole size
9. Laser power
10. detector gain and offset - gain/speed, offset - not red and not blue in LUT
11. Noise
12. Pixel dwell time - 

Camera base
1. Scientific question - What meatrics do you want to easure?
2. Objective - working distance, field of view, immersion medium.
3. Flurophores
4. Imaging strategy
5. Display - b/w and saturation and under exposure LUT 
6. Binning
7. Extra magnification lens
8. Camera area
9. Readout noise
10. Illumination power
11. Averaging
12. Background correction

Artificial intelligence in light microscopy 2025
Basically we have some input and as a consequence of some disigian some output.
We use formula to simply summarise our disicion parameter and weight of each of them

If we add lable to some data we can influence the disicion, graund truth - correct answer -> suppervise system.

Hidden layer is intermediate layer consist with logical question.
Epoch is training atteration.

Introduction to super resolution microscopy 2025
Introduction to 2D and 3D deconvolution

Co-localisation
- Co-expression - two proteins are loacted within the same structure
- Co-occurence - at the current resolution, the positions of the tow labeling can't be distinguished
- Correlation - at the current resolution, for positions, the intensities of the two labelling are linked
- Co-distribution - at the current resolution, the spatial distributions of the two labeling are linked.

Data integrity
1. Dyes - check for bleethrough and cross-talk
2. Co-registration - make sure what should be colocalised is co-localised
3. Resolution - know your limits

Pre-processing 
Corrections
- image acqusition related
	- bleedthrough/crosstalk
	- chromatic shift
- background and noise
	- median filtering
	- denoising
Restoration
- Deconvolution
- Machine learning
Segmentation


Publishing images 2025
- no bleedthrough, no saturation and no under exposure in the area of interest
- the brightest pixel should be 2/3 to just below the full bit depth
- images must be acquired with the same microscope settings, including bit depth
- Using different setting for image analysis and publication. 
- If you do not remove information that change interpretation of the data cropin is ok.
- Always save the image in the original format
- Brightness, contrast and gamma may be adjust, but must be mentioned and justified in methods section or figure legend. 
- Individual channels in black and white and mix with color.
- 27;38

[[Camera workshop - 2025]]
# Links
Module 2: Working with light and fluorophores

Module 3: Anatomy of a microscope 
- https://youtu.be/bTrWMCBT8fQ?si=men5tYqfjOaeYJFp
- https://youtu.be/vRI0F6_e2Hw?si=0frubEBGezEXgnIm
Module 4: Working with objectives:
- Lecture: Objectives - https://youtu.be/ASNUysTu9l8?si=SdzUM8IwJy_U7H-_
- Lecture: Point Spread Function and resolution - https://youtu.be/mfLply8Fq58?si=8WVK1FbIh-QivRrh
- Lecture: Refraction index mismatch and optical aberrations https://youtu.be/AML5DzuBqV8?si=y4DQq4qWLTTRtyZX
- Lecture: Efficient strategies to find the area of interest: large FOV, tiling and autofocus https://youtu.be/mx9wUreX-MY?si=gNZ5zPtoVUwWmbz1
Module 5: Sample preparation
	Lecture: Sample preparation tips https://youtu.be/lCFDdYdlsKk?si=bq6_N_5HeyALIEl0
	Lecture: Immunostaining troubleshooting https://youtu.be/D5pQRzL5PWM?si=Xye46rZTmIppEUpu
	Lecture: Clearing and expansion microscopy https://youtu.be/xRRZObKp3bc?si=wJbwkszHOADVAorP
Module 6: The digital image
	Lecture: Bridging concepts: optical and digital resolutions, contrast and sampling
		1. https://youtu.be/CNMVVmW0zDw?si=agaW6Q_9nvmJ6vTl
		2. https://youtu.be/BbBOTp35N7E?si=buR-GYlftymT9bL0
	Lecture: Sensors - https://youtu.be/lUAj0SV-gKk?si=PYiRY1HyBj2EE8RE
	Lecture: Signal, background and noise https://youtu.be/81qZlUU_At4?si=rXXBKnRqyv-d1TfC
Module 7: Capturing light
	Lecture: Saturation, under exposure, bit depth and image display - Saturation, underexposure, bit depth and image display - part 1a, 2025 - https://youtu.be/yvWHO0rSAvY?si=Tvni_O6SjnVy19Bg
	Saturation, underexposure, bit depth and image display part 1b, 2025 - https://youtu.be/80kHnX2qz88?si=lJ5JVetgfHdSgcmk
	Lecture: Saturation, under exposure, bit depth and image display - https://youtu.be/TL4_atCOJPM?si=g4n0chCqs50W0_0c
	Saturation, underexposure, bit depth and image display - part 2, 2025
	Lecture: Imaging multiple colours at once
	Lecture: Typical workflow to set imaging parameters - https://youtu.be/Y_-gVR_TC7c?si=MzRtXODmBP_uj_RT
Module 8: Off the beaten track
Artificial intelligence in light microscopy 2025 - https://youtu.be/GKa63Qtk-QQ?si=DLVPD8WpZ0V7Q9Vw
Introduction to super resolution microscopy 2025 - https://youtu.be/x3UovWRtx44?si=rS41-aYhoqFPCd0n
Introduction to 2D and 3D deconvolution - https://youtu.be/F8ycd3d8WZY?si=1G7bFG3eWCYL_opG
Colocalization 2025 - https://youtu.be/_5_Bw3aKtxk?si=QVK3fnZN-yewnuWd
Module 9: Publishing images
Publishing images 2025 - https://youtu.be/EJYsnPyco_8?si=7UR7yOjTT5iV8iHV

Module 10: Image analysis and Course conclusions