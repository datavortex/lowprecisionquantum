[Link to main repository](https://github.com/datavortex/lowprecisionquantum)

## A low precision quantum simulation library

- For simulations of quantum circuits with Schrodinger's formulation 
- Uses low precision arithmetic to save memory and bandwidth
- The paper "The limits of quantum circuit simulation with low precision arithmetic" contains the mathematical analysis of the error. Between 16 and 32 bits per coefficient are sufficient for almost any simulation
- Most precise when the states are random and maximally entangled.

## How to compile and run
Compile with gcc and MPI
```bash
mpicc -march=native -Ofast test-smallcomplex.c -o test -lm
```
In a single node computer, run as:
```bash
mpirun ./test
```
On a multinode system run with Slurm 
```bash
sbatch slurmscript.batch
```
Suggested Slurm script:
```bash
#SBATCH –o output-%J.txt
#SBATCH --nodes=8     # 8 nodes (must be a power of 2)
#SBATCH –n 64         # 8 ranks per node (must be a power of 2)
#SBATCH –p normal     # what queue
#SBATCH –t 02:00:00   
srun ./test
```
**The number of nodes must be a power of two.**
