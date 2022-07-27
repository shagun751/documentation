# Develpoment log for version mlpgrv01

**Details**  
continued from mlpgr\_3DS\_v5.03.f23003.dt0075.m043.base
  
1. [Common bugs in the code](./log_mlpgrv01_vBugs.md)
1. [Common algorithm developments in the code](./log_mlpgrv01_vAlgo.md)
1. [Initial development log](./log_mlpgrv01_v0001.md)
1. [Boundaries and subroutines [2020-06-02]](./log_mlpgrv01_v0002.md)
1. [Depth Integrated Velocity [2020-09-28]](./log_mlpgrv01_v0003.md)
1. [Sloping bottom [2021-04-09]](./log_mlpgrv01_v0004.md)
1. [Coupling in 3D [2021-09-29]](./log_mlpgrv01_v0005.md)

## List of Work
- [ ] 0002 : Probable bug of 3D gradP calculation in GRADIENT_POM_SHA
- [ ] 0002 : Probably disable GRADIENT_2P for type8 nodes
- [ ] 0002 : Remove TEMP_UN for type8 in U_BOUNDARY
- [ ] 0002 : Collision for wall nodes
- [ ] 0002 : Initialsing large temporary matrices

-----------------------------------------------


## References
1. Ma, Q. W. (2005). MLPG method based on Rankine source solution for simulating nonlinear water waves. CMES - Computer Modeling in Engineering and Sciences, 9(2), 193–209.

1. Ma, Q. W. (2008). A new meshless interpolation scheme for MLPG_R method. CMES - Computer Modeling in Engineering and Sciences, 23(2), 75–89.

1. Zhou, J. T., & Ma, Q. W. (2010). MLPG method based on rankine source solution for modelling 3D breaking waves. CMES - Computer Modeling in Engineering and Sciences, 56(2), 179–210.

1. Zhou, J. (2010). Numerical investigation of breaking waves and their interactions with structures using MLPG_R method. PhD Thesis. City University, London.