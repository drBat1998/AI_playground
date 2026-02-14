Title: CellProfiler with CellPose
tags: #atomic_note


# Notes

1. Install CellProfiler
2. Clone the CellProfiler-plugins repository
``` shell
git clone https://github.com/CellProfiler/CellProfiler-plugins.git

```
3. Set the plugins path in CellProfiler.
	Open CellProfiler.
	Go to CellProfiler => Preferences and set the path in the CellProfiler plugins directory to the active_plugins folder in the GitHub repository that you just cloned.
	Select Save at the bottom of the Preferences window
	Close CellProfiler
4. Create conda env and install cellpose
``` shell
conda create -n cellpose-env python=3.10 -y
conda activate cellpose-env
python -m pip install -U pip wheel
pip install cellpose
```


# Links
[[Cellpose]]
[[CellProfiler]]