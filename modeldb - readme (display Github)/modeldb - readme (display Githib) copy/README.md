# NeuroGPU + BBP TTPC Example 

## Prerequisites
  - CUDA > 10
  - NEURON > 7.6.7
  - Makefile
  - GCC > 8.3.0
  - see requirements.txt for other python requirments
## Getting Started
There are a few steps for porting NEURON models to NeuroGPU:
1. Upload hoc/mod files to a directory (like BBP_TTPC_Example folder).
2. Compile with `nrnivmodl`.
3.  run `python extractModel.py`to build a directory called `PyNeuroGPU_Unix`.
4. run `moveFiles.sh` to copy files into `PyNeuroGPU_Unix`.
5. chdir to `PyNeuroGPU_Unix/python`
6. Inside that directory you run `python extractModel.py` again.
7. Then run `python extractModel_mappings.py`.
8. Now you can run NeuroGPU by running `python runBBP.py`

## Moving the Model
 - We commonly move the simulation (NeuroGPU executable in `PyNeuroGPU_Unix` folder) to other repos / places for convienence.
 - To do this you can just move the 	whole `PyNeuroGPU_Unix` folder to wherever you want to run the simulation.
 - NeuroGPU requires that:
	 - If you change the params you use `allparams_from_mapping(param_values)`.
	 - There needs to be two folders available one directory up from the directory `NeuroGPU` is being called from -- `Data` and `src`. `Data` contains files NeuroGPU needs to accesss and `src` contains the source code for the CUDA model.

## Building Out from the Example
 - To use another model one just needs to replace the hoc/mod files in BBP_TTPC_Example folder.
 - Not all hoc and mod files are supported.


Please reach out to zladd@berkeley.edu or rbenshalom@ucdavis.edu if you encounter any issues. Or you can open an issue in https://github.com/roybens/NeuroGPU.

## Changelog
2022-12: MOD-C-2-CPP: Compatibility fixed for NEURON 9.0, 8.2 and 8.1
2023-04: Remove generated C files and hidden files. Update branching.mod for
         compatibility with new data structures coming in NEURON 9.0.
