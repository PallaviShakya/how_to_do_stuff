## You can start an interactive session and test out each command first like so: 
```srun -p med --time=9:00:00 --cpus-per-task=4 --mem=5G --pty /bin/bash -l```

## First, load module conda
```module load conda```

## open nano to get this batch script in

```
#! /bin/bash -login
#SBATCH -J rstudio-server
#SBATCH -t 3:00:00
#SBATCH -p med
#SBATCH -N 1
#SBATCH -n 1
#SBATCH -c 1
#SBATCH --mem=5gb
#SBATCH -e rstudio-%u.%j.err           # write stderr to this file - user/job
#SBATCH -o rstudio-%u.%j.out           # write stderr to this file - user/job


# Make things fail on errors
set -o nounset
set -o errexit
set -x


conda activate r-4.2.2
module load rstudio-server/2022.12.0-353

rstudio-launch

```

### SSH tunnel

tunnel into the ssh in new terminal 

e.g. 
Run the following command in a new terminal on your computer:

    ssh -L47551:cpu-9-70:47551 pshakya@farm.hpc.ucdavis.edu

### Open the link and copy username and password. 

Login with given username and password.