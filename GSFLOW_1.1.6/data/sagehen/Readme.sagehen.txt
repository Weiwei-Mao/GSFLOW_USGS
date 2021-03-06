
                      Sagehen Sample Problem for GSFLOW
                                 March 2013
 
A sample problem with GSFLOW data sets is provided in this subdirectory
to verify that GSFLOW is correctly installed and running on the system.
The sample problem also may be looked at as an example of how to use the 
program. The sample GSFLOW model is for the Sagehen Creek Watershed, 
and is described in the GSFLOW documentation (Markstrom and others,
2008).

Several Control and batch files are provided to run the sample problem
in different model modes and for different module, solver, and input-data
set options that are available for a GSFLOW simulation. These example 
files are provided for use with the executable compiled for 32-bit operating
systems (see subdirectory control_32) and for use with the 64-bit  executable
(subdirectory control_64). The Control and batch files found in the two 
subdirectories are for the following seven simulation conditions:

1. GSFLOW mode using the PCG solver and PRMS parameters split into five 
     separate Parameter Files. This condition also provides an example of the 
     use of the subbasin module, and a separate PRMS Parameter File 
     (subbasin.params) is provided to illustrate specification of the relevant 
     parameters: gsflow.bat and gsflow.control
2. GSFLOW mode using the NWT solver and PRMS Parameter Files for condition 1:
     gsflow_NWT.bat and gsflow_NWT.control
3. GSFLOW mode using the PCG solver and climate_hru module using pre-processed
     input climate data, to replace PRMS modules temp_1sta, precip_1sta, 
     ddsolrad, and potet_jh. Four of the Parameter Files used
     for conditions 1 and 2 are unchanged, and the fifth modified to include
     parameters required for use with the climate_hru model and to remove
     parameters not needed for climate_hru: gsflow_climate_hru.bat 
     and gsflow_climate_hru.control
4. PRMS-only mode using four Parameter Files, three of which are the same
     as those used in condition 1 and one of which was modified for a PRMS-only
     simulation. The Control File includes only those parameters needed for
     a PRMS-only simulation: gsflow_prms.bat and gsflow_prms.control
5. PRMS-only mode using pre-processed climate data using Parameter Files 
     very similar to condition 3, with the addition of a Parameter File that 
     contains parameters for groundwater cascades (ncascdgw.params): 
     gsflow_prms_climate_hru.bat and prms_climate_hru_control
6. PRMS-only mode demonstrating use of the Map Results module using five Parameter
     Files, four of which are the same as used in condition 4 and an additional
     file that specifies the mapping between the HRU and MODFLOW cell maps (file
     gvr.params): gsflow_prms_map_results.bat and gsflow_prms_map_results.control
7. MODFLOW-only mode using the PCG solver, a minimum-input Control File, and
     a PRMS Parameter File that contains GSFLOW-specific parameters required 
     for MODFLOW-only mode (a Data File is not necessary for a MODFLOW-only
     simulation): gsflow_modflow.bat and gsflow_modflow.control

The data-input files for the problem can be found in the input subdirectory, 
which contains modflow and prms subdirectories. The modflow subdirectory contains 
files related to the MODFLOW and MODFLOW-NWT components of GSFLOW. The prms 
subdirectory contains the Data and Parameter files for each simulation. The 
files ending in 'day' refer to pre-processed climate-data files used with the 
Climate by HRU Distribution module.

Double-click on one of the .bat files to run the model. The sample problem also 
can be run from a Windows command-prompt window (see the Readme.txt file in the 
main GSFLOW directory).

A gsflow.log file will be written directly to the control_32 or control_64 
subdirectory in which the batch and Control files are located (for GSFLOW or
MODFLOW modes). Output files generated by the Map Results module also will be 
written to the control_32 or control_64 subdirectories. Additional output files 
will be written to the output subdirectory and to the modflow and prms sub-
directories under the output subdirectory. The names of the output files are 
specified in either the GSFLOW Control File or the MODFLOW name file for each 
simulation. Several types of files will be generated, each of which is described 
in detail in the GSFLOW documentation. These include:

1. GSFLOW water-budget file (example: gsflow.out)
2. GSFLOW comma-separated-values (CSV) File (example: gsflow.csv)
3. PRMS water-budget file (example: sagehen_prms.out)
4. MODFLOW or MODFLOW-NWT listing file (example: sagehen.mf.list)
5. Calculated heads file for MODFLOW or MODFLOW-NWT (example: 
     head_sagehen.out)
6. MODFLOW GAGE Package output files (example: sagehen_sfrseg13.out)
7. MODFLOW UZF Package output files (example:uz1_sagehen.out)

Several output files are provided with the distribution for comparison
to the results of your simulations. These files are provided in the 
output-test subdirectory and are arranged by the simulation mode and
seven model conditions described above. (The results provided were
generated using the 32-bit executable; results for the 64-bit executable
should be nearly identical to those provided.) Note that the results
calculated using the version 1.1.6 release of the code differ somewhat
from previous results because of bugs identified and fixed for the 1.1.6 
release (see the file "GSFLOW_v1.1.6_Updates.pdf").


Reference:

Markstrom, S.L., Niswonger, R.G., Regan, R.S., Prudic, D.E., and
Barlow, P.M., 2008, GSFLOW--Coupled Ground-water and Surface-water
FLOW model based on the integration of the Precipitation-Runoff
Modeling System (PRMS) and the Modular Ground-Water Flow Model
(MODFLOW-2005): U.S. Geological Survey Techniques and Methods
6-D1, 240 p.
