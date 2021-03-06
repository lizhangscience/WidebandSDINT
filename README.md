# WidebandSDINT
Joint Reconstruction of Wideband Single Dish and Interferometer data for Radio Astronomy

### Publication
[A Joint Deconvolution Algorithm to Combine Single-dish and Interferometer Data for Wideband Multiterm and Mosaic Imaging](https://iopscience.iop.org/article/10.3847/1538-3881/ab1aa7/meta) , Rau, U. ; Naik, N. ; Braun, T. Astronomical Journal, Volume 158, Number 1, June 2019 

![Algorithm](https://github.com/urvashirau/WidebandSDINT/blob/master/Fig_Algo.png)


### Running the tests

This repository contains python scripts that work with [CASA](https://casa.nrao.edu), a download link for two simulated datasets, and a series of output PNG figures to compare and evaluate the results of different algorithmic options. 

(1) Download simulated [DATA](http://www.aoc.nrao.edu/~rurvashi/DataFiles/Data_For_WidebandSDINT_UR_github.tgz) and untar inside the Data directory.

(2) Run scripts from the Runs directory, within CASA.  

execfile('../Scripts/runsdint.py');runtest(1);runtest(2);runtest(3); etc.... 

Generated outputs are CASA log files, output CASA image files, and PNG figure files that summarize the imaging results for each example. Scripts/runsdint.py contains documentation on each of the tests triggered by runtest(num). 

Note : To only re-make the PNG figures one by one, set " action='plot' " in the call to onetest()

### Examples

A pair of datasets were simulated for single pointing and mosaic imaging for the VLA and GBT across L-Band (1-2 GHz). 

The simulated sky brightness consists of large scale structures at and just below the spatial frequency range sampled by the interferometer as well as three point sources. The spectral indices of the extended component and the right-most point source is 0.0 and the other two point sources have spectral indices of -1.0.  Single pointing simulations were done without primary beams and a mosaic simulation was done along with primary beams.  

Imaging examples includes wideband multi-term imaging (intensity and spectral index) as well as spectral cube imaging where each of three channels are treated separately. These data were designed to illustrate the situation where interferometer-only reconstructions incur sufficient error (and instability) that a single-step post-deconvolution merge with single dish data is insufficient to recover the source structure accurately and therefore a joint reconstruction is required. For example, the interferometer-only reconstructions require masks and frequent major cycles to avoid divergence, whereas the joint reconstructions are stable even without masks and with fewer major cycles. 

#### Single Pointing : A wideband imaging simulation devoid of primary beams

 Single Pointing : Joint Reconstruction with Single Dish + Interferometer Data
 ![Fig](https://github.com/urvashirau/WidebandSDINT/blob/master/Runs/fig.try_standard_mfs_mtmfs_sdint.png)
 
 Single Pointing : Interferometer Data only 
 ![Fig](https://github.com/urvashirau/WidebandSDINT/blob/master/Runs/fig.try_standard_mfs_mtmfs_intonly.png)
 
 Single Pointing : Single Dish Data only
 ![Fig](https://github.com/urvashirau/WidebandSDINT/blob/master/Runs/fig.try_standard_mfs_mtmfs_sdonly.png)

#### Mosaic : A wideband imaging simulation with frequency-dependent primary beams and wideband mosaic primary beam correction

 Mosaic : Joint Reconstruction with Single Dish + Interferometer Data
 ![Fig](https://github.com/urvashirau/WidebandSDINT/blob/master/Runs/fig.try_mosaic_mfs_mtmfs_sdint.png)
 
 Mosaic : Interferometer Data only 
 ![Fig](https://github.com/urvashirau/WidebandSDINT/blob/master/Runs/fig.try_mosaic_mfs_mtmfs_intonly.png)
 
 
 #### A Cube Imaging Example  
 
 Cube single pointing : Joint Reconstruction with Single Dish + Interferometer Data
 ![Fig](https://github.com/urvashirau/WidebandSDINT/blob/master/Runs/fig.try_standard_cube_multiscale_sdint.png)
 
 Cube single pointing : Interferometer Data only 
 ![Fig](https://github.com/urvashirau/WidebandSDINT/blob/master/Runs/fig.try_standard_cube_multiscale_intonly.png)
 
 Cube single pointing : Single Dish Data only
 ![Fig](https://github.com/urvashirau/WidebandSDINT/blob/master/Runs/fig.try_standard_cube_multiscale_sdonly.png)
 

Additional examples are located in the Runs subdirectory.

An initial version of this algorithm is expected to be made available as a CASA task in the next year. 
