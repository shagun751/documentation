# Initial development log

1. [Note : Old subroutines moved [2020-05-06]](#log_mlpgrv01_v0001_1)
1. [Note : COMMON.F is being removed [2020-05-08]](#log_mlpgrv01_v0001_2)
1. [Note : Input file for all settings [2020-05-13]](#log_mlpgrv01_v0001_3)
1. [Note : .f90 for main program [2020-05-18]](#log_mlpgrv01_v0001_4)

## Attempting
- Prepare the code before coupling with Bsnq
- Generalising the inputs


## List of Work
- [x] Input file : waveProbe
- [x] Input file : pressureProbe
- [x] Input file : meshFile
	- [ ] DRMIN is pending
- [x] Input file : Cylinder position
- [x] Input file : FNPT setup
- [ ] Input file : Cylinder/Body force
- [x] Remove implicit variables
- [x] Terminal output file. mlpgTerOut.txt. code = 8
- [x] mlpgrParaview, with terminal input

-----------------------------------------------

<a name = 'log_mlpgrv01_v0001_4' />

## Note : .f90 for main program [2020-05-18]
- Move all content of _mlpgrMain.f_ to _subroutines/mlpgMainSubs.f_, except for the main PROGRAM and INPUT subroutine.
- The remaining file is renamed as _mlpgrMain.f90_
- The Makefile is modified accordingly.
- This is done to make it more comfortable to do coupling with Bsnq.
	- Other than the PROGRAM and INPUT subrouines others do not need to be largely modified for coupling. Therefore modifications in _bqml_ will be seen more precisely.
	- The Sublime Text colouring for .f90 is necessary to see the object structure of the Bsnq code, purely to make it easier visually.

-----------------------------------------------

<a name = 'log_mlpgrv01_v0001_3' />

## Note : Input file for all settings [2020-05-13]
- Adding all the inputs to _mlpgrInput.dat_.
- This is done to avoid multiple copies of the same code 
- More importantly this will make it easier to run different cases without the need to remember all the changes that had to be made in the code to properly set a case up.
- Created module PROBESMOD for generic probes with option to have variable data columns. Verified using "v5.03_f23001.dt0075.m043".
	- Created WP (wave probes) and PP (pressure probe) using this with input from _mlpgrInput.dat_
- Created FNPTCPLMOD to move most of FNPT coupling related variables and subroutines under an object. Verified using "v5.03_f23001.dt0075.m043".
	- File : _fnptCoupling.f90_
- LNODE can now be specified within the _mlpgrInput.dat_ file. 
	- Used PROTECTED attribute for LNODE to ensure that LNODE is only allowed to be modified inside the module COMMONMOD.
- Verified using : f23002c.dt0100.m24.R30 from the JCP (2019) paper.
	- mlpgrv01/Test_700e9d7_f23002c.dt0100.m24.R30

Also

- Moved MLPGCONN from MODCONN (renamed to DOMAINMOD) to NEIGBOURNODES (renamed to NEIGHNODES)
- MODCONN renamed to DOMAINMOD
- NEIGBOURNODES renamed to NEIGHNODES
- Moved TYPE(CPUTIMETYP) from MODCONN (renamed to DOMAINMOD) to the main PROGRAM.
- Moved the files of unused subroutines to folder subroutines/archivedSubs
- **libparalution.so** moved to within run folder to potentially allow running in any linux system. Makefile changed appropriately. 


-----------------------------------------------

<a name = 'log_mlpgrv01_v0001_2' />

## Note : COMMON.F is being removed [2020-05-08]
- _COMMON.F_ contained too many unused variables. The code in general had most subroutines with junk variables. 
- The implicit assumption has quite often created a lot of confusion in the code regarding scope of variables.
- For most old functions the variables werent passed properly.
- This change aims at replacing _COMMON.F_ with a module _COMMONMOD_ for the common variables to avoid too large changes.
- Also removing all implicit variable assumptions.
- I have prepared module _COMMONMOD_  
- I modified every function in use so that it works without _COMMON.F_ and works with _COMMONMOD_ and IMPLICIT NONE.
- Initially I had retained COMMON.F and commented away !USE COMMONMOD and !IMPLICIT NONE.
	- At every stage the results were verified by comparing with the old run "v5.03_f23001.dt0075.m043". ( 8 stages. All give matching results.)
- Now I have removed _COMMON.F_ to subroutines folder. I have enabled _COMMONMOD_ and IMPLICIT NONE everywhere.
	- A few unused functions had to be moved to archive file _replacedSubsCOMMON.f_
	- Tested and verified using "v5.03_f23001.dt0075.m043".

-----------------------------------------------

<a name = 'log_mlpgrv01_v0001_1' />

## Note : Old subroutines moved [2020-05-06]
- I had shifted a lot of old subroutines from _mlpgrMain.f_ in UK and placed them in _replaceSubroutines.f_
- Now I have shifted more unused subroutines from _mlpgrMain.f_ to _replacedSubroutines2.f_.
- Further I removed all the wavemaker code, except for the FNPT one-way coupling part (I\_WM = 15). I have moved the code from _mlpgrMain.f_ to _replacedSubroutines3_wavemaker.f_.
- I have removed 2000+ lines of code from the _mlpgrMain.f_
- Removed many variables like ICELLX1, RCELL1, and lots more from _COMMON.F_.

-----------------------------------------------

## References
1. Ma, Q. W. (2005). MLPG method based on Rankine source solution for simulating nonlinear water waves. CMES - Computer Modeling in Engineering and Sciences, 9(2), 193–209.

1. Ma, Q. W. (2008). A new meshless interpolation scheme for MLPG_R method. CMES - Computer Modeling in Engineering and Sciences, 23(2), 75–89.

1. Zhou, J. T., & Ma, Q. W. (2010). MLPG method based on rankine source solution for modelling 3D breaking waves. CMES - Computer Modeling in Engineering and Sciences, 56(2), 179–210.

1. Zhou, J. (2010). Numerical investigation of breaking waves and their interactions with structures using MLPG_R method. PhD Thesis. City University, London.