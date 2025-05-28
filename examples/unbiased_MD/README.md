# Unbiased MD example - 0.2 M NaCl solution

We include example scripts to run the unbiased MD simulations and the associated analysis. The output data from the simulations and analysis are stored in `/data/unbiased_MD/NaCl/OPC3/Sengupta_etal/C0.2M/P1bar/`.

* `solvate_ions.job` is our job submission scipt for PSC Bridges-2 to run MD with Gromacs 2023.1. All input files are in `/solvation_shells/inputs/` or `/solvation_shells/top/`. This script simply calls `solvate_ions.py` with the appropriate inputs. The outputs `solution.gro`, `prod.tpr`, and `prod.xtc` are included in the data directory.
* `solvate_ions.py` writes Packmol and Gromacs input files and runs MPI-enabled Gromacs. Packmol > energy minimization > 50 ps NVT > 1 ns NPT > 20 ns NPT.
* `run_equilibrium_hydration.py` has options to calculate RDFs, shell speciation, and average coordination numbers. This analysis takes advantage of the MDAKit [SolvationAnalysis](https://solvation-analysis.readthedocs.io/en/latest/).
* `run_polyhedron.py` calculates the coordination shell volumes and areas using the polyhedron analysis described in the paper.