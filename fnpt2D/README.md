# FNPT-2D 
Developed by [Dr. V. Sriram](http://www.doe.iitm.ac.in/vsriram/)<br>
at [Department of Ocean Engineering](http://www.doe.iitm.ac.in/)<br>
[Indian Institute of Technology Madras](https://www.iitm.ac.in/)

For doubts regarding running the program please contact Shagun Agarwal (shagun.1994@gmail.com).
<br><br>

## Details
FNPT-2D is a finite element based model for Fully-Nonlinear Potential Theory. A simple, robust and fastest computational tool to estimate the fully nonlinear wave kinematics for very steep non-breaking waves.

##### Features
- X-Z plane.
- Single fluid model.
- Lagrangian or Semi-lagrangian method due to moving free-surface.
- Exponentially varying mesh-size along the vertical direction.
- Velocities captured accurately by LSQ method for calculating gradients of potential function.
- 1st and 2nd order wavemaker theory, all types of waves.
- Variable bathymetry, steep non-breaking waves
- Moving piston-type wavemaker.

It has experimentally verified proven results for

1. regular waves 
1. irregular/random waves 
1. solitary waves 
1. cnoidal waves 
1. Gaussian wave packets 
1. focusing waves 
1. long waves - pulse, N-waves 
1. user defined waves 
1. Sloshing.

List of a few important publication from this model

1. Sriram, V. (2008). Finite element simulation of nonlinear free surface waves (Indian Institute of Technology Madras). PhD Thesis. Retrieved from [Link](ftp://doe.iitm.ac.in/download/Sriram_thesis_OE05D011.pdf)

1. Sriram, V., Sannasiraj, S. A., & Sundar, V. (2006). Simulation of 2-D nonlinear waves using finite element method with cubic spline approximation. Journal of Fluids and Structures, 22(5), 663–681. [Link](https://doi.org/10.1016/j.jfluidstructs.2006.02.007)

1. Sriram V., Sannasiraj S.A., and Sundar V. (2006). Numerical simulation of 2D sloshing waves due to horizontal and vertical random excitations. Applied Ocean Research, 28(1), 19-32. 

1. Sriram, V., Sannasiraj, S. A., Sundar, V., Schlenkhoff, A., & Schlurmann, T. (2010). Quantification of phase shift in the simulation of shallow water waves. International Journal for Numerical Methods in Fluids. [Link](https://doi.org/10.1002/fld.2072)

1. Sriram, V., Schlurmann, T., & Schimmels, S. (2013). Focused Wave Evolution in Intermediate Water Depth Using First and Second Order Wave Maker Theory. The Twenty-Third International Offshore and Polar Engineering Conference. Anchorage, Alaska: International Society of Offshore and Polar Engineers.

1. H. Fernándeza, V. Sriram, S. Schimmels, H. Oumeraci, 2014, Extreme wave generation using self-correcting method — Revisited. Coastal Engineering, 93, Pages 15–31.

1. Sriram, V., Schlurmann, T., & Schimmels, S. (2015). Focused wave evolution using linear and second order wavemaker theory. Applied Ocean Research, 53, 279–296. [Link](https://doi.org/10.1016/j.apor.2015.09.007)

1. V. Sriram, I. Didenkulova, A. Sergeeva, S. Schimmels, 2016, Tsunami evolution and run-up in a large scale experimental facility, Coastal Engineering, 111, 1-12. [Link](https://doi.org/10.1016/j.coastaleng.2015.11.006)

1. S. Schimmels, V.Sriram, I. Didenkulova, 2016, Tsunami generation in a large scale experimental facility, Coastal Engineering, 110, 32–41

---------------------------------------------------------------
<br>

## PhD thesis based on this code (Users)
Mayumi Wilms, 2018, Criteria of wave breaking onset and its variability in irregular wave trains (Englisch), Leibniz University of Hannover, Germany. [Link](https://www.tib.eu/de/suchen/id/TIBKAT%3A1028608276/Criteria-of-wave-breaking-onset-and-its-variability/)

---------------------------------------------------------------
<br>

## Users of this code outside IITM

1. Leibniz University of Hannover, Germany (Prof. T.Schlurmann and Prof. Arndt Hildebrandt group)
1. Grosser Wellen Kanal, GWK, Hannover. (Dr. Stephan Schimmels)

---------------------------------------------------------------
<br>

## User-guide

The executable provided here is compiled using Intel Fortran and can only be used on Linux based OS such as Ubuntu.  
The code is proven to compile on Windows OS too, however that executable is not yet provided in the release.

The required files and outputs will be created in the folder fnpt.

##### Program files
| File | Description |
| ------------- |-------------|
| **fnpt** | FNPT-2D program. **Execute using command** `./fnpt` |
| fnpt_plot.m | Matlab script for displaying the moving mesh over time |
| fnptMlpg3D.f90 | Fortran code used for converting the _Output PHIT.out_ to a form compaitable with the MLPG_RS input | 

<br>

##### Input files
| File | Description |
| ------------- |-------------|
| **FEMINPUT.dat** | Contains all required parameter for setting up a case |
| **wavePaddle.dat** | Contains the piston type wave-paddle motion. <br> Assume that the paddle motion is a time series of P(N,2), where N is the number of enteries, column 1 is the time and column 2 is the paddle displacement in meters. Then the first line of the file in the number N followed by the matrix P(N,2). <br> `N` <br> `P(1,1)  P(1,2)` <br> `P(2,1)  P(2,2)` <br> `...` <br> `P(N,1)  P(N,2)` |

<br>

##### Output files
<table>
	<tr> <th>File </th> 
		<th>Description</th> 
		<th></th> </tr>
	<tr> <td>FEMELE.DAT</td> 
		<td>FEM element information</td> 
		<td>Constant file </td> </tr>
	<tr> <td>FEMNODE.DAT</td> 
		<td>Instantaneous FEM nodes information</td> 
		<td>Dynamic file</td></tr>
    <tr> <td>INPUTSIGNAL.DAT</td> 
    	<td>Calculated information about wave-paddle motion at the simulation time-step.</td> 
    	<td>Constant file</td></tr>
    <tr> <td>Output bveta.dat</td> 
    	<td>Instantaneous free-surface</td> 
    	<td> Dynamic file </td> </tr>
    <tr> <td><b>Output bvout.dat</b></td> 
    	<td>Wave elevation probe reading at every simulation time-step at prescirbed X locations for 6 wave probes and wave paddle. 
    		<br> The columns are: <br> 
    		<table>
    			<tr> <th>C1</th> <th>C2</th> <th>C3</th> <th>C4</th> <th>C5</th> <th>C6</th> <th>C7</th> <th>C8</th> <th>C9</th> </tr>
        		<tr> <td>Time (s)</td> <td>Wave paddle (m)</td> <td>WP1 (m)</td> <td>WP2 (m)</td> <td>WP3 (m)</td> <td>WP4 (m)</td> <td>WP5 (m)</td> <td>WP6 (m)</td> <td>Right wall (m)</td> 
        	</table>
       	</td> 
        <td>Dynamic file </td></tr>
    <tr> <td>Output INFO.dat </td>
    	<td> Verify paramters for mesh, time-step, duration and wave-probe position set-up.</td>
    	<td> Constant file </td> </tr>
    <tr>
    <tr> <td>Output out.dat</td>
    	<td> Pressure at each wave paddle point at every time-step. A method to check the set-up. </td>
    	<td> Dynamic file </td></tr>
    <tr> <td><b>Output PHIT.dat</b></td>
    	<td> The program can output variables at a 2D grid of points (NX x NZ). This grid is horizontanlly fixed and it moves vertically with the free-surface. Each row corresponds to variables at one of these grid point. Each block of (NX x NZ) rows corresponds to a single simulation time-step, followed by the next block for the next time-step, and so-on.
    		<br> <table>
    			<tr> <th>C1</th> <th>C2</th> <th>C3</th> <th>C4</th> <th>C5</th> <th>C6</th> <th>C7</th> <th>C8</th> </tr>
        		<tr> <td>Time (s)</td> <td>X (m)</td> <td>Z (m)</td> <td>pressure (Pa/1000)</td> <td>vel_x (m/s)</td> <td>vel_z (m/s)</td> <td>accel_x (m/s2)</td> <td>accel_z (m/s2)</td>
        	</table>
        </td> 
        <td>Dynamic file </td></tr>
      <tr> <td> Output PRESS.dat</td>
      	<td> Value of pressure, vel_x and vel_z at locations specified after line-25 in _FEMINPUT.dat_ </td>
      	<td> Dynamic file </td></tr>
</table>
Please ignore the other output files.
<br> <br>

#### Input File Description
File name: FEMINPUT.dat

Format:

| Line | Variables | Description |
| :--- | :-------: | :---------- |
| L06  | `int` |    1 = hotstart. 0 = coldstart
| L07  | `float, float` | water-dep left-end D1, water-dep right-end D2. <br> The 2D vertical tank has a starting (D1) and ending (D2) water-depth. If the two depths are same then the tank as uniform depth. If the two depths are different then there will be a slope starting and ending at locations as mentioned in L28. In L28 the first depth (D1) lies between the locations D1X1 and D1X2; and the second depth (D2) lies between D2X1 and D2X2. A linear slope will be generated between D1X2 and D2X1. |
| L08  | `float` |  length of the tank |
| L09  | `int`  |   1 = Input from time series. 0 = Wave of period as L10 |
| L10  | `float` | value of time-period of wave in case of 0 value in L09 |
| L11  | `filename` |  value of full filename in case of 1 value in L09 |
| L12  | `int` |  Total simulation time-steps |
| L13  | `float` |  time-step |
| L15  | `int` | Regridding of the free surface. Recommended 30. <br> The FEM grid is regridding at regular intervals to improve the quality of meshing. The regridding is done with the same number of free-surface nodes, vertical nodes and alpha coefficient as given by the user for the initial mesh. For steeper waves, keep a lower value. |
| L16  | `int` | Type of velocity calculations. Recommended 4 |
| L17  | `float` | Sponge-layer length. If -1 vertical wall |
| L18  | `int`   | Number of nodes free surface. Recommended L/40
| L19  | `int` |  Number of vertical nodes (>12) |
| L20  | `float` | Alpha coefficient. <br> The vertical points under a free surface nodes are distributed with a spacing that increase exponentially. Alpha coefficient controls this exponential function. If alpha = 0 then the points distribution under the free-suraface node will be uniform. A high value of the coefficient means small vertical spacing for points near the free surface and large vertical spacing for points away from the free-surface. Do not exceed alpha = 2. For low-steepness recommend alpha = 1.2 |
| L21  | `float, float, float, float, float, float` | Wave-probe X locations | 
| L24  | `float, float, int, int` | X1, X2, NX-1, NZ <br> Output of variable pressure, velocity and acceleration can be obtained at a grid of points (probe-grid). The grid point are equally distributed between X1 and X2, in NX-1 intervals. At each X point on the grid, NZ number of points are generate along the Z direction. These points on the probe-grid are not the same as the FEM mesh points. Their output is given in file _Output PHIT.dat_  |
| L25  | `int` | Number of custom probes. The values of pressure and velcoities at these probes will be in _Output PRESS.dat_. After specifying the N number of probes in this line, the location of the probes in XZ plane in given in the next N lines. In the shown example N=2, hence line L26 and L27 are the location of the probes |
| L28 | `float, float, float, float` | D1X1, D1X2, D2X1, D2X2 <br> Slope defining points. Please check the description for L07 |

Eaxmple FEMINPUT.dat

```
L01  !INPUT DATA FILE - Created through WaveGen
L02  !***************************
L03  !MORE DETAILS ABOUT THE FULLY NONLINEAR POTENTIAL FLOW THEORY AND NUMERICAL BACKGROUND CAN BE FOUND IN
L04  ! V. SRIRAM(2008) FINITE ELEMENT SIMULATION OF NONLINEAR WATER WAVES, PH.D. THESIS, IIT Madras, INDIA
L05  !*************************** 
L06  1   ! Hotstart
L07  0.7d0,0.7d0 ! water depth, variable water depth
L08  70.d00000  ! length of the tank
L09  1             ! Input from time series
L10  1d0
L11  wavePaddle.dat
L12  5200  !total simulation time in cycle
L13  0.01 ! time step
L14  0,0,1500  ! START TIME, END TIME OF VELOCITY EXTRACTION, INTERVAL OF SURFACE PROFILE ALONG TANK
L15  30  ! regridding of the free surface
L16  4 ! type of velocity calculations
L17  20d0 ! beach length if -1 vertical wall
L18  1600 ! number of nodes free surface (L/40)
L19  20 ! number of vertical nodes (>12)
L20  2.0 !alpha coefficient
L21  4.975d0, 13.928d0, 14.178d0, 14.428d0, 37.0429d0, 20.6114d0 ! wave gauge locations
L22  RK4 ! method of integration
L23  Output !name file of the file.
L24  28,29,10,21 !STARTING, ENDING, NUMBER OF LAYERS IN X, NUMBER OF LAYERS IN Y DIRECTION FOR WEAK COUPLING
L25  2  ! NUMBER OF PRESSURE AND VELOCITY OUTPUTS
L26  20.00000000,    -0.50000000 ! COORDINATES
L27  21.00000000,    -0.50000000
L28  10.D0,12.D0,200.D0,201.D0  ! SLOPE LOCATIONS

```

---------------------------------------------------------------