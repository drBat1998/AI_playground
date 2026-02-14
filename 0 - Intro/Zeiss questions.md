
Zeiss Celldiscovery:
[[Autofocus in Zeiss Celldiscovery]]
[[Questions to Zeiss - working distance]]
POC_R2 system, and how it can be used?
Humidity control on Zeiss CD7?
does celldiscovery substract background automatically during camera based image acquisition?

[[ICF]]
🧩 1. During acquisition — hardware & acquisition-level correction

If you can control illumination during imaging (e.g. on Celldiscoverer 7), always start here.

🔧 A. Use microscope “flat-field” or “white-reference” calibration

In Zeiss ZEN, there’s usually a Flat-field correction (FFC) or Shading Correction option.

It records an image of an empty, evenly fluorescent field and automatically applies this to all acquisitions.

This creates an internal ICF and applies division at acquisition time.

📘 When to do it:

Each time you change objectives, filter sets, or illumination settings.

After maintenance, lamp/LED replacement, or large realignment.

Once per experiment batch (e.g., each multi-well plate).

Zeiss blue:
File organization & metadata

