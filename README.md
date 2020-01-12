## A low precision quantum simulation library

- For simulations of a quantum computer with Schrodinger's formulation 
- Uses low precision arithmetic to save memory and bandwidth
- The paper contains the mathematical analysis of the errorr. Typically 24 bits per coefficient are sufficient for almost any simulation
- Most useful when the states have maximal entanglement and entropy at some point of the computation

## How to compile and run
Compile with gcc and MPI
```bash
mpicc -Ofast random-circuit-example.c -o executable -lm
```
Run the program with
```bash
sbatch slurmscript.batch
```
use a Slurm script:
```bash
#SBATCH –o output-%J.txt
#SBATCH --nodes=8     # 8 nodes (must be a power of 2)
#SBATCH –n 64         # 8 ranks per node (must be a power of 2)
#SBATCH –p normal     # what queue
#SBATCH –t 02:00:00   # usually less than 3 hours
mpirun ./executable
```
**The number of nodes and number of cores must be a power of two.**
