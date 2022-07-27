
## SFDI in the present code

1. ASSEMATRIX (G)
	- SFDI Gradient of pressure for wall BC
2. FILL_MATRIX (Option) (I)
	- Choice for SFDI and MLS
	- SFDI interpolation only
3. PRESSURE_SMOOTH (Option) (I)
	- Choice for SFDI and MLS
	- type9 is always MLS
	- SFDI interpolation only
4. GRADIENT_POM (G)
	- SFDI Gradient for internal nodes
5. GRADIENT_PCYL
	- SFDI Gradient for cylinder nodes
6. GRADIENT_2P
	- SFDI Gradient for wall nodes

Ningbo's paper applies QSFDI Laplacian to PPE. 
I can implement QSFDI for Laplacian of velocity for viscous terms.

## Subroutines

- interp_SFDI_gradient vs  interp_SFDI_gradient_homegeneous



## QSFDI functions and subroutines?

Linear SFDI Interpolation

- interp_SFDI_shapeFun()
	- Using QSFDI weighting, so is this the QSFDI interpolation shape function?
- interp_ISFDI_shapeFun()
	- Improve SFDI with weighting divided by distance (?)
	- Using QSFDI weighting
- interp_SFDI_shapeFun_wei() and interp_ISFDI_shapeFun_wei()
	- Version of the above, where weighting is passed into the function by the user.
- What is the homogenous version?


Linear SFDI Derivative 

- interp_SFDI_shapeFunDer()
- interp_ISFDI_shapeFunDer()
- interp_SFDI_shapeFunDerW()
- interp_ISFDI_shapeFunDerW()
- atI version?
	- Calculation at the ith node in the passed array?

All in one function QSFDI function

- interp_QSFDI_shapeFun
	- shpDer2: questions regarding the dimension
- interp_QSFDI_shapeFunS
	- Difference with the previous function are
		- Doesnt return dis
		- Uses 'h' parameter
- interp_QSFDI_shapeFunW
	- User given weights
	- Doesnt use 'h' and doesnt return dis

QFSI Derivative function

- interp_QSFDI_shapeFunDer
- interp_QSFDI_shapeFunDerW
- interp_QSFDI_shapeFunDerS
	- It uses 'h'
	- It uses atI versions
- interp_QSFDI_shapeFun1stDer

Weight function
- interp_QSFDI_weighting (6,7,8,9)

## Missing function definitions

- qale_sqrt()
- weighting()
- interp_QSFDI_weighting()
- LUSolver_Matrix()
- matrix_BRINV_noIndex()

## Others

- What is the 'h' value?
- idw values?
- There are some MPS and MLS functions too
- Implementations for SPH?